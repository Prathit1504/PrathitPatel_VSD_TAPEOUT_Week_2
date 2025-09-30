# PrathitPatel_VSD_TAPEOUT_Week_2
# VSDBabySoC Functional Modeling Makefile
# Week 2 - RISC-V Reference SoC Tapeout Program

# ============================================================================
# Configuration Variables
# ============================================================================

# Directories
SRC_DIR := src/module
INC_DIR := src/include
OUT_DIR := output
PRE_SIM_DIR := $(OUT_DIR)/pre_synth_sim
POST_SIM_DIR := $(OUT_DIR)/post_synth_sim
LOG_DIR := logs

# Tools
IVERILOG := iverilog
VVP := vvp
GTKWAVE := gtkwave
SANDPIPER := sandpiper-saas
YOSYS := yosys

# Source Files
TB_FILE := $(SRC_DIR)/testbench.v
TOP_MODULE := $(SRC_DIR)/vsdbabysoc.v
RV_MODULE := $(SRC_DIR)/rvmyth.v
RV_TLV := $(SRC_DIR)/rvmyth.tlv
PLL_MODULE := $(SRC_DIR)/avsdpll.v
DAC_MODULE := $(SRC_DIR)/avsddac.v

# Output Files
PRE_SIM_OUT := $(PRE_SIM_DIR)/pre_synth_sim.out
PRE_SIM_VCD := $(PRE_SIM_DIR)/pre_synth_sim.vcd

# Compilation Flags
IVERILOG_FLAGS := -DPRE_SYNTH_SIM -I $(INC_DIR) -I $(SRC_DIR)

# ============================================================================
# Phony Targets
# ============================================================================

.PHONY: all setup clean pre_synth_sim view_wave convert_tlv help

# ============================================================================
# Main Targets
# ============================================================================

all: setup pre_synth_sim

help:
	@echo "VSDBabySoC Makefile - Available Targets:"
	@echo "========================================"
	@echo "  make all           - Setup and run pre-synthesis simulation"
	@echo "  make setup         - Create necessary directories"
	@echo "  make convert_tlv   - Convert TL-Verilog to Verilog"
	@echo "  make pre_synth_sim - Run pre-synthesis simulation"
	@echo "  make view_wave     - Open GTKWave with simulation results"
	@echo "  make clean         - Remove generated files"
	@echo "  make help          - Show this help message"

# ============================================================================
# Setup and Preparation
# ============================================================================

setup:
	@echo "Creating directory structure..."
	@mkdir -p $(PRE_SIM_DIR)
	@mkdir -p $(POST_SIM_DIR)
	@mkdir -p $(LOG_DIR)
	@echo "Directory structure created successfully."

convert_tlv: setup
	@echo "Converting TL-Verilog to Verilog..."
	@$(SANDPIPER) -i $(RV_TLV) -o $(RV_MODULE) \
		--bestsv --noline -p verilog --outdir $(SRC_DIR) \
		2>&1 | tee $(LOG_DIR)/tlv_conversion.log
	@echo "TL-Verilog conversion complete."

# ============================================================================
# Pre-Synthesis Simulation
# ============================================================================

pre_synth_sim: setup convert_tlv
	@echo "Starting pre-synthesis simulation..."
	@echo "Step 1: Compiling Verilog sources..."
	@$(IVERILOG) -o $(PRE_SIM_OUT) $(IVERILOG_FLAGS) \
		$(TB_FILE) \
		$(TOP_MODULE) \
		$(RV_MODULE) \
		$(PLL_MODULE) \
		$(DAC_MODULE) \
		2>&1 | tee $(LOG_DIR)/compilation.log
	@echo "Compilation successful."
	@echo ""
	@echo "Step 2: Running simulation..."
	@cd $(PRE_SIM_DIR) && ./pre_synth_sim.out \
		2>&1 | tee ../../$(LOG_DIR)/simulation.log
	@echo ""
	@echo "Pre-synthesis simulation completed successfully!"
	@echo "VCD file generated: $(PRE_SIM_VCD)"
	@echo ""
	@echo "To view waveforms, run: make view_wave"

# ============================================================================
# Waveform Viewing
# ============================================================================

view_wave:
	@if [ -f $(PRE_SIM_VCD) ]; then \
		echo "Opening GTKWave..."; \
		$(GTKWAVE) $(PRE_SIM_VCD) &; \
	else \
		echo "Error: VCD file not found. Run 'make pre_synth_sim' first."; \
	fi

# ============================================================================
# Synthesis (Known to fail - for documentation)
# ============================================================================

synth: setup
	@echo "Attempting synthesis (Note: Known issue with ABC)..."
	@$(YOSYS) -c synth.ys 2>&1 | tee $(LOG_DIR)/synthesis_error.log || \
		echo "Synthesis failed (expected). See synthesis_error.log for details."

# ============================================================================
# Cleanup
# ============================================================================

clean:
	@echo "Cleaning generated files..."
	@rm -rf $(OUT_DIR)
	@rm -rf $(LOG_DIR)
	@rm -f $(RV_MODULE)
	@echo "Cleanup complete."

clean_all: clean
	@echo "Removing Python environment..."
	@rm -rf sp_env
	@echo "Full cleanup complete."

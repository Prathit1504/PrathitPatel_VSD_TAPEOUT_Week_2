@tailwind base;
@tailwind components;
@tailwind utilities;

/* GitHub-inspired design system for RISC-V SoC documentation
All colors MUST be HSL.
*/

@layer base {
  :root {
    /* GitHub color palette */
    --background: 0 0% 100%;
    --foreground: 220 9% 9%;

    --card: 0 0% 100%;
    --card-foreground: 220 9% 9%;

    --popover: 0 0% 100%;
    --popover-foreground: 220 9% 9%;

    /* GitHub blue theme */
    --primary: 212 92% 45%;
    --primary-foreground: 0 0% 100%;
    --primary-hover: 212 92% 40%;

    --secondary: 220 14% 96%;
    --secondary-foreground: 220 9% 9%;

    --muted: 220 14% 96%;
    --muted-foreground: 220 9% 46%;

    --accent: 212 92% 45%;
    --accent-foreground: 0 0% 100%;

    --destructive: 0 84% 60%;
    --destructive-foreground: 0 0% 100%;

    --border: 216 12% 84%;
    --input: 216 12% 84%;
    --ring: 212 92% 45%;

    --radius: 6px;

    /* GitHub specific colors */
    --github-bg: 246 8% 98%;
    --github-border: 216 12% 84%;
    --github-text-primary: 220 9% 9%;
    --github-text-secondary: 101 6% 34%;
    --github-blue: 212 92% 45%;
    --github-green: 137 72% 27%;
    --github-orange: 32 95% 44%;
    --github-red: 0 84% 60%;
    
    /* Code syntax highlighting */
    --code-bg: 220 13% 18%;
    --code-text: 220 14% 71%;
    --code-comment: 220 10% 40%;
    --code-keyword: 207 61% 59%;
    --code-string: 119 34% 47%;
    --code-number: 5 74% 59%;
    
    /* Professional gradients */
    --gradient-primary: linear-gradient(135deg, hsl(var(--primary)), hsl(var(--primary-hover)));
    --gradient-secondary: linear-gradient(135deg, hsl(var(--secondary)), hsl(var(--muted)));
    --gradient-hero: linear-gradient(135deg, hsl(212 92% 45%), hsl(229 76% 66%));
    
    /* Animations */
    --transition-smooth: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    --transition-fast: all 0.15s ease;

    --sidebar-background: 0 0% 98%;

    --sidebar-foreground: 240 5.3% 26.1%;

    --sidebar-primary: 240 5.9% 10%;

    --sidebar-primary-foreground: 0 0% 98%;

    --sidebar-accent: 240 4.8% 95.9%;

    --sidebar-accent-foreground: 240 5.9% 10%;

    --sidebar-border: 220 13% 91%;

    --sidebar-ring: 217.2 91.2% 59.8%;
  }

  .dark {
    --background: 222.2 84% 4.9%;
    --foreground: 210 40% 98%;

    --card: 222.2 84% 4.9%;
    --card-foreground: 210 40% 98%;

    --popover: 222.2 84% 4.9%;
    --popover-foreground: 210 40% 98%;

    --primary: 210 40% 98%;
    --primary-foreground: 222.2 47.4% 11.2%;

    --secondary: 217.2 32.6% 17.5%;
    --secondary-foreground: 210 40% 98%;

    --muted: 217.2 32.6% 17.5%;
    --muted-foreground: 215 20.2% 65.1%;

    --accent: 217.2 32.6% 17.5%;
    --accent-foreground: 210 40% 98%;

    --destructive: 0 62.8% 30.6%;
    --destructive-foreground: 210 40% 98%;

    --border: 217.2 32.6% 17.5%;
    --input: 217.2 32.6% 17.5%;
    --ring: 212.7 26.8% 83.9%;
    --sidebar-background: 240 5.9% 10%;
    --sidebar-foreground: 240 4.8% 95.9%;
    --sidebar-primary: 224.3 76.3% 48%;
    --sidebar-primary-foreground: 0 0% 100%;
    --sidebar-accent: 240 3.7% 15.9%;
    --sidebar-accent-foreground: 240 4.8% 95.9%;
    --sidebar-border: 240 3.7% 15.9%;
    --sidebar-ring: 217.2 91.2% 59.8%;
  }
}

@layer base {
  * {
    @apply border-border;
  }

  body {
    @apply bg-background text-foreground;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Noto Sans", Helvetica, Arial, sans-serif;
  }
  
  /* Code styling */
  code {
    @apply bg-muted px-1.5 py-0.5 rounded text-sm font-mono;
  }
  
  pre code {
    @apply bg-transparent p-0;
  }
  
  /* GitHub-style headers */
  h1, h2, h3, h4, h5, h6 {
    @apply font-semibold tracking-tight;
  }
  
  /* Professional animations */
  .animate-fade-in {
    animation: fadeIn 0.5s ease-in-out;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  /* Custom GitHub components */
  .github-btn {
    @apply inline-flex items-center px-3 py-1.5 text-sm font-medium rounded-md border transition-colors;
    @apply bg-secondary border-border text-foreground hover:bg-muted;
  }
  
  .github-btn-primary {
    @apply bg-primary text-primary-foreground border-primary hover:bg-primary/90;
  }
  
  .github-file-tree {
    @apply text-sm font-mono;
  }
  
  .github-code-block {
    @apply bg-[hsl(var(--code-bg))] text-[hsl(var(--code-text))] p-4 rounded-lg overflow-x-auto;
    @apply border border-border;
  }
  
  .github-stats {
    @apply flex items-center gap-4 text-sm text-muted-foreground;
  }
  
  .documentation-content {
    @apply max-w-none;
  }
  
  .documentation-content h1,
  .documentation-content h2,
  .documentation-content h3,
  .documentation-content h4,
  .documentation-content h5,
  .documentation-content h6 {
    @apply text-foreground font-semibold mb-4;
  }
  
  .documentation-content p {
    @apply text-foreground mb-4 leading-relaxed;
  }
  
  .documentation-content strong {
    @apply text-foreground font-semibold;
  }
  
  .documentation-content code {
    @apply text-primary bg-muted px-1 py-0.5 rounded text-sm;
  }
}


## Styling Guidelines

### Styling Approach

The project uses **Tailwind CSS** as the primary styling solution integrated with **shadcn/ui** components. This approach provides:
- Utility-first CSS for rapid development
- Consistent design system through shadcn/ui
- Responsive design patterns
- Dark mode support preparation
- Custom CSS for GSAP animations

**Styling Hierarchy:**
1. **Tailwind utilities** for layout, spacing, and basic styling
2. **shadcn/ui components** for interactive elements
3. **Custom CSS classes** for GSAP animations and complex effects
4. **CSS custom properties** for theme variables and consistency

### Global Theme Variables

```css
/* src/styles/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  /* Brand Colors */
  --color-primary: 34 197 94;        /* Green-500 for agricultural theme */
  --color-primary-dark: 22 163 74;   /* Green-600 */
  --color-secondary: 59 130 246;     /* Blue-500 for trust */
  --color-accent: 245 158 11;        /* Amber-500 for highlights */
  
  /* Neutral Colors */
  --color-background: 255 255 255;   /* White */
  --color-surface: 249 250 251;      /* Gray-50 */
  --color-border: 229 231 235;       /* Gray-200 */
  --color-text-primary: 17 24 39;    /* Gray-900 */
  --color-text-secondary: 75 85 99;  /* Gray-600 */
  --color-text-muted: 156 163 175;   /* Gray-400 */

  /* Typography */
  --font-primary: 'Inter', system-ui, sans-serif;
  --font-secondary: 'Playfair Display', serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* Spacing Scale */
  --spacing-xs: 0.25rem;    /* 4px */
  --spacing-sm: 0.5rem;     /* 8px */
  --spacing-md: 1rem;       /* 16px */
  --spacing-lg: 1.5rem;     /* 24px */
  --spacing-xl: 2rem;       /* 32px */
  --spacing-2xl: 3rem;      /* 48px */
  --spacing-3xl: 4rem;      /* 64px */

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);

  /* Animation Timing */
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
  --easing-standard: cubic-bezier(0.4, 0.0, 0.2, 1);
  --easing-decelerate: cubic-bezier(0.0, 0.0, 0.2, 1);
  --easing-accelerate: cubic-bezier(0.4, 0.0, 1, 1);

  /* Border Radius */
  --radius-sm: 0.375rem;  /* 6px */
  --radius-md: 0.5rem;    /* 8px */
  --radius-lg: 0.75rem;   /* 12px */
  --radius-xl: 1rem;      /* 16px */
}

/* Dark mode support (preparation) */
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: 17 24 39;     /* Gray-900 */
    --color-surface: 31 41 55;        /* Gray-800 */
    --color-border: 75 85 99;         /* Gray-600 */
    --color-text-primary: 249 250 251; /* Gray-50 */
    --color-text-secondary: 209 213 219; /* Gray-300 */
    --color-text-muted: 156 163 175;  /* Gray-400 */
  }
}

/* Shimmer animation for loading states */
@keyframes shimmer {
  0% {
    background-position: -200px 0;
  }
  100% {
    background-position: calc(200px + 100%) 0;
  }
}

.shimmer {
  background: linear-gradient(
    90deg,
    rgb(var(--color-surface)) 0px,
    rgb(var(--color-border)) 40px,
    rgb(var(--color-surface)) 80px
  );
  background-size: 200px 100%;
  animation: shimmer 1.5s infinite;
}

/* GSAP animation classes */
.gsap-fade-in {
  opacity: 0;
  transform: translateY(30px);
}

.gsap-parallax-bg {
  will-change: transform;
}

.gsap-stagger-item {
  opacity: 0;
  transform: translateY(20px);
}
```
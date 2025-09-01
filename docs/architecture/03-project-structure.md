## Project Structure

```plaintext
agroventia-homepage/
├── README.md
├── next.config.js              # Next.js configuration with i18n
├── tailwind.config.js          # Tailwind CSS configuration
├── tsconfig.json              # TypeScript configuration
├── package.json
├── .env.local                 # Environment variables
├── .env.example               # Environment template
├── .eslintrc.json             # ESLint configuration
├── .gitignore
├── public/
│   ├── images/                # Static images and assets
│   ├── icons/                 # SVG icons and favicons
│   └── locales/               # Translation files for Next.js i18n
│       ├── en/
│       │   └── common.json
│       ├── fr/
│       │   └── common.json
│       └── esp/
│           └── common.json
├── src/
│   ├── app/                   # Next.js App Router
│   │   ├── [locale]/          # Dynamic locale routing
│   │   │   ├── layout.tsx     # Root layout with i18n
│   │   │   ├── page.tsx       # Homepage SPA
│   │   │   └── loading.tsx    # Loading UI with shimmer
│   │   ├── globals.css        # Global styles
│   │   └── layout.tsx         # Root layout
│   ├── components/            # Reusable UI components
│   │   ├── ui/                # shadcn/ui components
│   │   ├── sections/          # Homepage sections
│   │   │   ├── Hero.tsx
│   │   │   ├── About.tsx
│   │   │   ├── Services.tsx
│   │   │   └── Contact.tsx
│   │   ├── layout/            # Layout components
│   │   │   ├── Header.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── LanguageSelector.tsx
│   │   └── common/            # Common components
│   │       ├── LoadingSkeleton.tsx
│   │       ├── ShimmerEffect.tsx
│   │       └── ScrollProgress.tsx
│   ├── lib/                   # Utility functions and configurations
│   │   ├── api/               # API integration
│   │   │   ├── wix-client.ts  # Wix Studio Headless client
│   │   │   └── email-service.ts # EmailJS integration
│   │   ├── gsap/              # GSAP animations
│   │   │   ├── animations.ts  # Animation utilities
│   │   │   └── parallax.ts    # Parallax effects
│   │   ├── i18n/              # Internationalization
│   │   │   └── config.ts      # i18n configuration
│   │   └── utils.ts           # General utilities
│   ├── hooks/                 # Custom React hooks
│   │   ├── useGSAP.ts         # GSAP integration hooks
│   │   ├── useScrollPosition.ts
│   │   └── useWixContent.ts   # Wix CMS hooks
│   ├── types/                 # TypeScript type definitions
│   │   ├── wix.ts             # Wix CMS types
│   │   ├── global.ts          # Global types
│   │   └── components.ts      # Component prop types
│   └── styles/                # Global styles and themes
│       ├── globals.css        # Global CSS
│       ├── animations.css     # GSAP animation styles
│       └── components.css     # Component-specific styles
└── __tests__/                 # Test files
    ├── components/            # Component tests
    ├── lib/                   # Utility tests
    └── __mocks__/             # Mock files
```
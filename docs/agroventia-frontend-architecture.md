alignkk# AgroVentia Inc. Homepage SPA Frontend Architecture Document

## Template and Framework Selection

### Project Context Review

Based on the PRD and project brief, the AgroVentia Inc. homepage SPA will be built using **Next.js 15+** as the primary framework with the following technical requirements:

- Single Page Application (SPA) architecture
- GSAP for animations and parallax effects
- Next.js native i18n for multi-language support (English, French, Spanish)
- Wix CMS Direct HTTP API Integration for content management (without SDK)
- shadcn/ui for component library
- 2-week development timeline

### Framework Decision

**Next.js 15+ with App Router** has been selected as the framework foundation. This project will use the **Next.js Create App** template as the starting point with the following justifications:

- Built-in TypeScript support and optimization
- Native internationalization (i18n) capabilities
- Excellent performance optimization features
- Seamless Vercel deployment integration
- Strong ecosystem for required integrations
- Turbopack support for faster development

### Starter Template Analysis

Using `create-next-app` with TypeScript template provides:

- Pre-configured TypeScript setup
- ESLint configuration
- App Router structure
- Built-in optimization features
- Standardized folder structure
- Turbopack integration

No additional starter template is required as the project scope is focused and the base Next.js template provides sufficient foundation.

### Change Log

| Date       | Version | Description                                                                                  | Author             |
| ---------- | ------- | -------------------------------------------------------------------------------------------- | ------------------ |
| 2025-08-18 | 1.0     | Initial frontend architecture creation                                                       | Frontend Architect |
| 2025-08-26 | 2.0     | Updated to reflect current implementation with Next.js 15, React 19, and direct Wix HTTP API | System Architect   |

## Frontend Tech Stack

### Technology Stack Table

| Category          | Technology                   | Version     | Purpose                             | Rationale                                                  |
| ----------------- | ---------------------------- | ----------- | ----------------------------------- | ---------------------------------------------------------- |
| Framework         | Next.js                      | 15.4.7+     | React framework with SSR/SSG        | Built-in i18n, performance optimization, Turbopack support |
| UI Library        | React                        | 19.1.0+     | Component-based UI development      | Industry standard, excellent ecosystem, latest features    |
| State Management  | @tanstack/react-query        | 5.59.15+    | Server state management and caching | Optimal for API integration, cache management              |
| Routing           | Next.js App Router           | 15+         | Application routing and navigation  | Native Next.js routing with i18n support                   |
| Build Tool        | Next.js/Turbopack            | Built-in    | Module bundling and optimization    | Integrated build system with faster development            |
| Styling           | Tailwind CSS                 | 4.1.12+     | Utility-first CSS framework         | Rapid development, consistent design system                |
| Testing           | Jest + React Testing Library | Latest      | Unit and integration testing        | React ecosystem standard                                   |
| Component Library | shadcn/ui                    | Latest      | Pre-built accessible components     | Modern, customizable, accessible components                |
| Form Handling     | React Hook Form              | 7+          | Form validation and management      | Performance-focused, minimal re-renders                    |
| Animation         | GSAP                         | 3.12.5+     | Advanced animations and parallax    | Superior performance for complex animations                |
| Dev Tools         | TypeScript + ESLint          | 5.9.2+      | Type safety and code quality        | Development efficiency and error prevention                |
| Email Service     | EmailJS                      | Latest      | Client-side email functionality     | No backend required, easy integration                      |
| Email Provider    | Namecheap Private Email      | N/A         | Professional email hosting          | Cost-effective business email solution                     |
| CMS Integration   | Wix Data API                 | Direct HTTP | Content management via REST API     | Direct API integration without SDK dependency              |
| Image Handling    | Custom Wix Image Component   | Custom      | Optimized Wix image loading         | Handles Wix image URLs with proper error handling          |

## Project Structure

```
agroventia-homepage/
├── README.md
├── next.config.ts             # Next.js configuration with i18n (TypeScript)
├── postcss.config.mjs         # PostCSS configuration
├── tailwind.config.js         # Tailwind CSS configuration
├── tsconfig.json              # TypeScript configuration
├── package.json
├── .env.local                 # Environment variables (to be created)
├── .env.example               # Environment template (to be created)
├── eslint.config.mjs          # ESLint configuration
├── jest.config.js             # Jest testing configuration
├── jest.setup.js              # Jest setup file
├── components.json            # shadcn/ui configuration
├── .gitignore
├── public/
│   ├── images/                # Static images and assets
│   ├── icons/                 # SVG icons and favicons
│   └── locales/               # Translation files (to be created)
│       ├── en/
│       │   └── common.json
│       ├── fr/
│       │   └── common.json
│       └── esp/
│           └── common.json
├── src/
│   ├── app/                   # Next.js App Router
│   │   ├── api/               # API routes
│   │   │   ├── collections/   # Wix collections API endpoint
│   │   │   │   └── route.ts   # Main collections API route
│   │   │   └── wix-collections/ # Additional Wix endpoints
│   │   ├── test/              # Test pages
│   │   │   └── wix-content-test/
│   │   ├── globals.css        # Global styles with Tailwind
│   │   ├── layout.tsx         # Root layout
│   │   ├── page.tsx           # Homepage (currently shows WixDataFetcher)
│   │   └── providers.tsx      # React Query provider setup
│   ├── components/            # Reusable UI components
│   │   ├── ui/                # shadcn/ui components
│   │   │   ├── button.tsx
│   │   │   └── dropdown-menu.tsx
│   │   ├── layout/            # Layout components
│   │   │   ├── Header.tsx     # Basic header with language selector
│   │   │   ├── Footer.tsx     # Basic footer
│   │   │   ├── HeroSection.tsx # Hero section with Wix content
│   │   │   └── LanguageSelector.tsx # Language dropdown component
│   │   ├── WixDataFetcher.tsx # Comprehensive Wix data display (1184 lines)
│   │   └── WixImage.tsx       # Custom Wix image component
│   ├── lib/                   # Utility functions and configurations
│   │   ├── api/               # API integration (legacy structure)
│   │   ├── gsap/              # GSAP animations (setup but not implemented)
│   │   ├── utils/             # Image utilities
│   │   │   └── image.ts       # Wix image URL conversion utilities
│   │   ├── utils.ts           # General utilities (cn function)
│   │   └── wix-config.ts      # Wix API configuration
│   ├── services/              # Business logic services
│   │   ├── wix-api.service.ts # Direct HTTP Wix API service
│   │   └── wix-data.service.ts # Wix data fetching service
│   ├── hooks/                 # Custom React hooks
│   │   ├── useGSAP.ts         # GSAP integration hooks
│   │   ├── useScrollPosition.ts
│   │   ├── useWixContent.ts   # Wix CMS hooks (legacy)
│   │   └── useWixImages.ts    # Wix image handling hooks
│   ├── types/                 # TypeScript type definitions
│   │   └── wix.ts             # Wix CMS types
│   ├── NEXTJS_NO_SDK_IMPLEMENTATION.md # Implementation guide
│   ├── WIX_CMS_IMAGE_LOADING_GUIDE.md # Image loading guide
│   └── wix-collections.data.json # Sample Wix data
└── __tests__/                 # Test files (to be implemented)
    ├── components/            # Component tests
    ├── lib/                   # Utility tests
    └── __mocks__/             # Mock files
```

## Component Standards

### Component Template

```
import React from "react";
import { cn } from "@/lib/utils";

interface ComponentNameProps {
  className?: string;
  children?: React.ReactNode;
  // Add specific props here
}

const ComponentName: React.FC<ComponentNameProps> = ({
  className,
  children,
  ...props
}) => {
  return (
    <div className={cn("default-component-classes", className)} {...props}>
      {children}
    </div>
  );
};

export default ComponentName;

// Export types for other components
export type { ComponentNameProps };
```

### Naming Conventions

- **Components**: PascalCase (e.g., `HeroSection`, `LanguageSelector`)
- **Files**: kebab-case for pages, PascalCase for components (e.g., `hero-section.tsx`, `LanguageSelector.tsx`)
- **Hooks**: camelCase starting with 'use' (e.g., `useGSAP`, `useScrollPosition`)
- **Utilities**: camelCase (e.g., `formatText`, `validateEmail`)
- **Constants**: SCREAMING_SNAKE_CASE (e.g., `API_ENDPOINTS`, `ANIMATION_DURATION`)
- **Types/Interfaces**: PascalCase with descriptive suffixes (e.g., `UserProps`, `ApiResponse`)
- **CSS Classes**: kebab-case following Tailwind conventions
- **API Routes**: kebab-case (e.g., `/api/contact-form`)

## State Management

### Store Structure

```
src/app/providers.tsx          # React Query provider (implemented)
src/services/                  # Business logic services (implemented)
├── wix-api.service.ts        # Direct HTTP Wix API service
└── wix-data.service.ts       # Wix data fetching service
src/hooks/                     # State management hooks (implemented)
├── useWixContent.ts          # Wix CMS data fetching (legacy)
├── useWixImages.ts           # Wix image handling hooks
├── useGSAP.ts               # GSAP integration hooks
└── useScrollPosition.ts      # Scroll position tracking
src/types/                     # State-related types
└── wix.ts                    # Wix CMS types
```

### Current State Management Implementation

```
// app/providers.tsx - React Query Provider (Implemented)
"use client";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { useState } from "react";

export default function Providers({ children }: { children: React.ReactNode }) {
  const [queryClient] = useState(
    () =>
      new QueryClient({
        defaultOptions: {
          queries: {
            staleTime: 5 * 60 * 1000, // 5 minutes
            gcTime: 10 * 60 * 1000,   // 10 minutes
            retry: 3,
            retryDelay: (attemptIndex) =>
              Math.min(1000 * 2 ** attemptIndex, 30000),
          },
        },
      })
  );

  return <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>;
}

// hooks/useWixContent.ts - React Query Hooks (Legacy - needs update)
import { useQuery } from '@tanstack/react-query';

export const useHeroContent = () => {
  return useQuery<HeroContent[], Error>({
    queryKey: ['heroContent'],
    queryFn: getHeroContent,
    staleTime: 5 * 60 * 1000,
    gcTime: 10 * 60 * 1000,
    retry: 3,
    retryDelay: (attemptIndex) => Math.min(1000 * 2 ** attemptIndex, 30000),
  });
};

// New pattern using direct API service
export const useAllCollections = () => {
  return useQuery({
    queryKey: ['allCollections'],
    queryFn: () => fetch('/api/collections').then(res => res.json()),
    staleTime: 5 * 60 * 1000,
    gcTime: 10 * 60 * 1000,
    retry: 3,
  });
};
```

## API Integration

### Direct HTTP Wix API Service (No SDK)

```
// services/wix-api.service.ts - Current Implementation
import { wixConfig } from '@/lib/wix-config';

export interface WixApiResponse<T> {
  dataItems: Array<{
    id: string;
    dataCollectionId: string;
    data: T;
  }>;
  pagingMetadata: {
    count: number;
    total: number;
    tooManyToCount: boolean;
    cursors: Record<string, any>;
    hasNext: boolean;
  };
}

export class WixApiService {
  private readonly queryUrl = `${wixConfig.baseUrl}/query`;

  async queryCollection<T>(
    collectionName: string,
    options: WixQueryOptions = {}
  ): Promise<TransformedResponse<T>> {
    const requestBody = {
      dataCollectionId: collectionName,
      includeReferencedItems: options.includeReferencedItems || ['*'],
      returnTotalCount: options.returnTotalCount ?? true,
      cursorPaging: { limit: options.limit || 100 },
      ...(Object.keys(options.filter || {}).length > 0 && { filter: options.filter }),
    };

    try {
      const response = await fetch(this.queryUrl, {
        method: 'POST',
        headers: {
          Authorization: `Bearer ${wixConfig.apiToken}`,
          'Content-Type': 'application/json',
          'wix-site-id': wixConfig.siteId,
        },
        body: JSON.stringify(requestBody),
      });

      if (!response.ok) {
        const errorText = await response.text();
        throw new Error(`HTTP ${response.status}: ${response.statusText}`);
      }

      const data = (await response.json()) as WixApiResponse<T>;
      return this.transformResponse(data);
    } catch (error) {
      throw new Error(`Failed to fetch ${collectionName}`);
    }
  }
}

export const wixApiService = new WixApiService();
```

### Wix Configuration

```
// lib/wix-config.ts - Current Implementation
export interface WixConfig {
  apiToken: string;
  siteId: string;
  baseUrl: string;
}

export const wixConfig: WixConfig = {
  apiToken: process.env.WIX_API_TOKEN!,
  siteId: process.env.WIX_SITE_ID!,
  baseUrl: process.env.WIX_API_BASE_URL || 'https://www.wixapis.com/wix-data/v2/items',
};
```

### Custom Wix Image Component

```
// components/WixImage.tsx - Current Implementation
import React, { useState } from 'react';
import Image from 'next/image';
import { convertWixImageUrl } from '@/lib/utils/image';

interface WixImageProps {
  src: string;
  alt: string;
  width: number;
  height: number;
  className?: string;
  onLoadError?: (error: Error) => void;
}

const WixImage: React.FC<WixImageProps> = ({
  src, alt, width, height, className = '', onLoadError,
}) => {
  const [imageError, setImageError] = useState(false);
  const [isLoading, setIsLoading] = useState(true);

  const convertedSrc = convertWixImageUrl(src);

  if (imageError) {
    return (
      <div className={`bg-gray-200 flex items-center justify-center ${className}`}>
        <span className="text-gray-500 text-sm">Image not available</span>
      </div>
    );
  }

  return (
    <div className="relative">
      {isLoading && <div className={`absolute inset-0 bg-gray-200 animate-pulse ${className}`} />}
      <Image
        src={convertedSrc}
        alt={alt}
        width={width}
        height={height}
        className={className}
        onError={() => setImageError(true)}
        onLoad={() => setIsLoading(false)}
      />
    </div>
  );
};
```

### API Client Configuration

```
import emailjs from "@emailjs/browser";

// EmailJS Configuration
export const emailConfig = {
  serviceId: process.env.NEXT_PUBLIC_EMAILJS_SERVICE_ID!,
  templateId: process.env.NEXT_PUBLIC_EMAILJS_TEMPLATE_ID!,
  publicKey: process.env.NEXT_PUBLIC_EMAILJS_PUBLIC_KEY!,
};

// Initialize EmailJS
export const initializeEmailJS = () => {
  emailjs.init(emailConfig.publicKey);
};

// Email service wrapper
export const emailService = {
  sendContactForm: async (formData: ContactFormData) => {
    try {
      const response = await emailjs.send(
        emailConfig.serviceId,
        emailConfig.templateId,
        {
          from_name: formData.name,
          from_email: formData.email,
          company: formData.company || "Not specified",
          inquiry_type: formData.inquiryType,
          message: formData.message,
          to_email: "contact@agroventia.com", // Namecheap Private Email
        },
        emailConfig.publicKey
      );
      return response;
    } catch (error) {
      console.error("Email sending failed:", error);
      throw new Error("Failed to send email. Please try again.");
    }
  },
};

// Types
interface ContactFormData {
  name: string;
  email: string;
  company?: string;
  inquiryType: "b2b" | "b2c" | "general";
  message: string;
}

export type { ContactFormData };
```

## Routing

### Current Route Configuration

```
// next.config.ts - Current Implementation (TypeScript)
import type { NextConfig } from 'next';

const nextConfig: NextConfig = {
  // i18n: {
  //   locales: ['en', 'es'], // Commented out - to be implemented
  //   defaultLocale: 'en',
  // },
};

export default nextConfig;

// app/api/collections/route.ts - Current API Implementation
import { NextResponse } from 'next/server';
import { wixDataService } from '@/services/wix-data.service';

export async function GET() {
  try {
    const allData = await wixDataService.fetchAllCollections();
    return NextResponse.json({
      ...allData,
      _metadata: {
        fetchedAt: new Date().toISOString(),
        totalCollections: Object.keys(allData).length,
      },
    });
  } catch (error) {
    return NextResponse.json(
      { error: 'Failed to fetch collections' },
      { status: 500 }
    );
  }
}
```

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

```
/* src/styles/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  /* Brand Colors */
  --color-primary: 34 197 94; /* Green-500 for agricultural theme */
  --color-primary-dark: 22 163 74; /* Green-600 */
  --color-secondary: 59 130 246; /* Blue-500 for trust */
  --color-accent: 245 158 11; /* Amber-500 for highlights */

  /* Neutral Colors */
  --color-background: 255 255 255; /* White */
  --color-surface: 249 250 251; /* Gray-50 */
  --color-border: 229 231 235; /* Gray-200 */
  --color-text-primary: 17 24 39; /* Gray-900 */
  --color-text-secondary: 75 85 99; /* Gray-600 */
  --color-text-muted: 156 163 175; /* Gray-400 */

  /* Typography */
  --font-primary: "Inter", system-ui, sans-serif;
  --font-secondary: "Playfair Display", serif;
  --font-mono: "JetBrains Mono", monospace;

  /* Spacing Scale */
  --spacing-xs: 0.25rem; /* 4px */
  --spacing-sm: 0.5rem; /* 8px */
  --spacing-md: 1rem; /* 16px */
  --spacing-lg: 1.5rem; /* 24px */
  --spacing-xl: 2rem; /* 32px */
  --spacing-2xl: 3rem; /* 48px */
  --spacing-3xl: 4rem; /* 64px */

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 /
          0.1);

  /* Animation Timing */
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
  --easing-standard: cubic-bezier(0.4, 0, 0.2, 1);
  --easing-decelerate: cubic-bezier(0, 0, 0.2, 1);
  --easing-accelerate: cubic-bezier(0.4, 0, 1, 1);

  /* Border Radius */
  --radius-sm: 0.375rem; /* 6px */
  --radius-md: 0.5rem; /* 8px */
  --radius-lg: 0.75rem; /* 12px */
  --radius-xl: 1rem; /* 16px */
}

/* Dark mode support (preparation) */
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: 17 24 39; /* Gray-900 */
    --color-surface: 31 41 55; /* Gray-800 */
    --color-border: 75 85 99; /* Gray-600 */
    --color-text-primary: 249 250 251; /* Gray-50 */
    --color-text-secondary: 209 213 219; /* Gray-300 */
    --color-text-muted: 156 163 175; /* Gray-400 */
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

## Testing Requirements

### Component Test Template

```
import React from "react";
import { render, screen, fireEvent, waitFor } from "@testing-library/react";
import "@testing-library/jest-dom";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { NextIntlClientProvider } from "next-intl";
import ComponentName from "../ComponentName";

// Mock GSAP
jest.mock("gsap", () => ({
  registerPlugin: jest.fn(),
  timeline: jest.fn(() => ({
    to: jest.fn().mockReturnThis(),
    from: jest.fn().mockReturnThis(),
    set: jest.fn().mockReturnThis(),
  })),
  to: jest.fn(),
  from: jest.fn(),
}));

// Test wrapper with providers
const createWrapper = () => {
  const queryClient = new QueryClient({
    defaultOptions: {
      queries: { retry: false },
      mutations: { retry: false },
    },
  });

  const messages = {
    common: {
      "test.key": "Test Value",
    },
  };

  return ({ children }: { children: React.ReactNode }) => (
    <QueryClientProvider client={queryClient}>
      <NextIntlClientProvider messages={messages} locale="en">
        {children}
      </NextIntlClientProvider>
    </QueryClientProvider>
  );
};

describe("ComponentName", () => {
  it("renders correctly", () => {
    const Wrapper = createWrapper();

    render(
      <Wrapper>
        <ComponentName />
      </Wrapper>
    );

    expect(screen.getByRole("...", { name: /.../ })).toBeInTheDocument();
  });

  it("handles user interactions", async () => {
    const Wrapper = createWrapper();

    render(
      <Wrapper>
        <ComponentName />
      </Wrapper>
    );

    const button = screen.getByRole("button");
    fireEvent.click(button);

    await waitFor(() => {
      expect(screen.getByText("Expected Result")).toBeInTheDocument();
    });
  });
});
```

### Testing Best Practices

1. **Unit Tests**: Test individual components in isolation with proper mocking of GSAP, EmailJS, and Wix CMS
2. **Integration Tests**: Test component interactions, language switching, and form submission flows
3. **E2E Tests**: Test critical user flows including homepage navigation, language switching, and contact form submission
4. **Coverage Goals**: Aim for 80% code coverage with focus on business logic and user interactions
5. **Test Structure**: Follow Arrange-Act-Assert pattern with descriptive test names
6. **Mock External Dependencies**: Mock GSAP animations, EmailJS service, Wix CMS API calls, and Next.js router

## Environment Configuration

```
# .env.local - Local development environment
NEXT_PUBLIC_WIX_API_URL=https://your-wix-site.wixsite.com/_functions
WIX_API_TOKEN=your_wix_api_token

# EmailJS Configuration
NEXT_PUBLIC_EMAILJS_SERVICE_ID=your_emailjs_service_id
NEXT_PUBLIC_EMAILJS_TEMPLATE_ID=your_emailjs_template_id
NEXT_PUBLIC_EMAILJS_PUBLIC_KEY=your_emailjs_public_key

# Namecheap Private Email
CONTACT_EMAIL=contact@agroventia.com
ADMIN_EMAIL=admin@agroventia.com

# Analytics (optional)
NEXT_PUBLIC_GA_MEASUREMENT_ID=G-XXXXXXXXXX

# Development
NODE_ENV=development
NEXT_PUBLIC_SITE_URL=http://localhost:3000

# .env.production - Production environment
NODE_ENV=production
NEXT_PUBLIC_SITE_URL=https://agroventia.com
```

## Frontend Developer Standards

### Critical Coding Rules

1. **GSAP Integration**: Always register GSAP plugins at component level, use useLayoutEffect for DOM-dependent animations
2. **Next.js i18n**: Use `useTranslations` hook for all text content, never hardcode text strings
3. **State Management**: Use React Query for server state, React state for UI state only
4. **Component Props**: Always define TypeScript interfaces for component props with proper optional/required properties
5. **Error Boundaries**: Wrap async components with error boundaries, especially for Wix CMS integration
6. **Performance**: Use React.memo for expensive components, useMemo for complex calculations
7. **Accessibility**: Include proper ARIA labels, keyboard navigation, and semantic HTML structure
8. **Image Optimization**: Always use Next.js Image component with proper alt text and lazy loading
9. **Environment Variables**: Use NEXT*PUBLIC* prefix only for client-side variables
10. **Shimmer Loading**: Implement loading skeletons for all async content with consistent shimmer animations

### Quick Reference

**Common Commands:**

```
# Development
npm run dev                    # Start development server
npm run build                  # Build for production
npm run start                  # Start production server
npm run lint                   # Run ESLint
npm run test                   # Run Jest tests
npm run test:watch             # Run tests in watch mode
```

**Key Import Patterns:**

```
// Next.js imports
import { useRouter } from "next/navigation";
import { useTranslations } from "next-intl";
import Image from "next/image";

// React Query
import { useQuery, useMutation } from "@tanstack/react-query";

// GSAP
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

// shadcn/ui
import { Button } from "@/components/ui/button";
import { Card } from "@/components/ui/card";

// Utilities
import { cn } from "@/lib/utils";
```

**File Naming Conventions:**

- Components: `PascalCase.tsx` (e.g., `HeroSection.tsx`)
- Pages: `page.tsx` (Next.js App Router)
- Layouts: `layout.tsx` (Next.js App Router)
- Hooks: `use-kebab-case.ts` (e.g., `use-gsap-animation.ts`)
- Utilities: `kebab-case.ts` (e.g., `wix-client.ts`)
- Types: `kebab-case.types.ts` (e.g., `content.types.ts`)

**Project-Specific Patterns:**

- Always use `useTranslations('section')` for text content
- Wrap Wix CMS calls with React Query hooks
- Use GSAP animations with `useGSAP` hook
- Implement shimmer loading for all async content
- Use EmailJS for contact form submissions to Namecheap Private Email
- Follow shadcn/ui component patterns for consistency

## Current Implementation Status

### ✅ Implemented Features

- **Next.js 15 + React 19**: Modern framework setup with Turbopack
- **Direct HTTP Wix API**: Complete integration without SDK dependency
- **React Query**: Configured with proper caching and error handling
- **Tailwind CSS 4**: Modern styling with custom color system
- **shadcn/ui Components**: Button and dropdown components
- **Custom Wix Image Component**: Optimized image loading with error handling
- **TypeScript Configuration**: Strict typing throughout the application
- **Jest Testing Setup**: Ready for test implementation

### 🚧 Partially Implemented

- **GSAP Animations**: Dependencies installed but not yet integrated
- **Internationalization**: Configuration exists but not fully implemented
- **Layout Components**: Basic header and hero section only

### ❌ Not Yet Implemented

- **Contact Form**: EmailJS integration not configured
- **Homepage Sections**: About, Services, Contact sections missing
- **GSAP Animations**: No actual animations implemented
- **Environment Configuration**: No .env files created
- **Testing**: No test files written

### 📋 Next Steps Priority

1. **Environment Setup**: Create .env files for Wix and EmailJS configuration
2. **Homepage Structure**: Implement proper homepage layout with all sections
3. **GSAP Integration**: Add animations to hero and scroll sections
4. **Contact Form**: Implement EmailJS integration for form submissions
5. **Testing**: Write comprehensive component tests

## Frontend Developer Standards

### Critical Implementation Notes

1. **Wix API Integration**: Always use the direct HTTP service, never install Wix SDK
2. **Image Handling**: Use WixImage component for all Wix-sourced images
3. **State Management**: Use React Query for server state, React state for UI only
4. **Component Structure**: Follow the established patterns in existing components
5. **Environment Variables**: Configure WIX_API_TOKEN, WIX_SITE_ID, and EmailJS variables
6. **Error Handling**: Implement proper loading and error states for all async operations

### Quick Reference Commands

```
# Development
npm run dev                    # Start with Turbopack
npm run build                  # Production build
npm run test                   # Run Jest tests
npm run lint                   # ESLint check
npm run query-collections      # Test Wix API connection
```

### Key Import Patterns (Current)

```
// Wix Integration
import { wixDataService } from '@/services/wix-data.service';
import { wixApiService } from '@/services/wix-api.service';
import WixImage from '@/components/WixImage';

// React Query
import { useQuery } from '@tanstack/react-query';

// Components
import { Button } from '@/components/ui/button';
import { cn } from '@/lib/utils';

// Next.js
import Image from 'next/image';
import { NextResponse } from 'next/server';
```

# AI Frontend Development Prompt for AgroVentia Homepage SPA

## Project Context

You are tasked with building a modern, engaging homepage for AgroVentia Inc., an agricultural import startup. The site should establish a professional digital presence with a focus on creating memorable first impressions through smooth animations and parallax effects.

**Current Implementation Status**: The project has a solid foundation with Next.js 15, React 19, direct Wix HTTP API integration, and React Query setup. You will build upon this existing foundation.

### Tech Stack (Current Implementation)

- Next.js 15.4.7+ with App Router and Turbopack
- React 19.1.0+
- TypeScript 5.9.2+
- Tailwind CSS 4.1.12+
- shadcn/ui component library (button, dropdown-menu implemented)
- GSAP 3.12.5+ for animations and parallax effects (dependencies ready)
- @tanstack/react-query 5.59.15+ for state management (configured)
- Direct HTTP Wix Data API integration (no SDK - fully implemented)
- Custom WixImage component for optimized image loading
- EmailJS for contact form submissions (not yet configured)
- Next.js native i18n for multi-language support (setup ready)

### Visual Style

The design should be professional and modern with clean aesthetics, using a color palette that suggests reliability and growth:

- Primary: #22c55e (Green-500 for agricultural theme)
- Primary Dark: #16a34a (Green-600)
- Secondary: #3b82f6 (Blue-500 for trust)
- Accent: #f59e0b (Amber-500 for highlights)
- Neutrals for backgrounds and text

Typography should use Inter font (already configured) with a clear hierarchy.

## High-Level Goal

Transform the current data-fetching demo into a professional homepage SPA by implementing the core user stories:

**Story 1.3 - Basic Homepage Structure and Layout**: Create a semantic homepage structure with proper navigation, main content sections (hero, about, services, product category, contact), and responsive design using the existing foundation.

**Story 2.1 - Design System and Component Library Setup**: Establish a consistent design system with reusable components, including the color palette, typography scale, spacing system, and accessible component variants.

## Current Foundation Analysis

### ✅ Already Implemented

- Next.js 15 + React 19 project setup with Turbopack
- Direct HTTP Wix API integration (wixApiService, wixDataService)
- React Query provider with proper configuration
- Custom WixImage component with error handling
- Basic Header with LanguageSelector
- Basic HeroSection component (needs integration)
- Tailwind CSS 4 with design system variables
- shadcn/ui components (Button, DropdownMenu)
- Comprehensive Wix data fetching (1184-line WixDataFetcher)

### 🚧 Needs Implementation

- Replace WixDataFetcher with proper homepage sections
- Implement GSAP animations (dependencies ready)
- Create About, Services, product category, Contact sections using existing Wix data
- Setup environment variables for Wix and EmailJS
- Complete i18n implementation
- Add form handling and EmailJS integration

## Detailed Instructions

### Phase 1: Homepage Structure Implementation (Story 1.3)

1. **Transform Main Page Structure**

   - Replace the current WixDataFetcher display with proper homepage sections
   - Create semantic HTML structure with proper ARIA attributes
   - Implement responsive grid/flexbox layout using Tailwind CSS
   - Ensure keyboard navigation and screen reader accessibility

2. **Enhance Layout Components**

   - Expand the existing Header component with proper navigation links
   - Complete the Footer component with company information
   - Maintain the existing LanguageSelector functionality
   - Ensure responsive design across all screen sizes

3. **Create Homepage Section Components**
   - **Hero Section**: Enhance existing HeroSection to use real Wix data
   - **About Section**: Create using AboutContent from Wix with core values
   - **Services Section**: Build using ProductsContent and categories data
   - **Product Listings Section**: Build using Import2 and categories data
   - **Contact Section**: Implement using ContactContent from Wix

### Phase 2: Design System Enhancement (Story 2.1)

4. **Establish Design System Tokens**

   - Implement the agricultural color palette using CSS custom properties
   - Configure typography scale with Inter font family and proper weights
   - Set up consistent spacing and sizing system using design tokens
   - Create component variants following accessibility guidelines

5. **Create Reusable Component Variants**

   - Extend Button component with agricultural theme variants (primary, secondary, outline)
   - Create Card components for content sections with proper shadows and borders
   - Design Form components with validation states for contact section
   - Ensure all components have proper focus states and ARIA attributes

6. **Integrate with Existing Wix Data**
   - Use the existing wixDataService.fetchAllCollections() API
   - Leverage the comprehensive WixDataFetcher logic for data handling
   - Implement proper loading states and error handling
   - Use WixImage component for all Wix-sourced images

### Phase 3: Animations and Interactions

7. **Implement GSAP Animations**

   - Create smooth parallax effects in the hero section using existing background images
   - Add scroll-triggered animations for content reveal
   - Implement hover effects for service cards and buttons
   - Use the existing useGSAP and useScrollPosition hooks

8. **State Management Integration**
   - Use the configured React Query setup for all data fetching
   - Implement custom hooks for animations and form handling
   - Leverage existing provider configuration

### Phase 4: Contact Integration

9. **EmailJS Contact Form**
   - Implement functional contact form using React Hook Form
   - Integrate with EmailJS for form submissions
   - Use existing ContactContent data for contact information display
   - Add proper validation and error handling

### Phase 5: Accessibility and Polish

10. **Accessibility Implementation**
    - Ensure proper color contrast ratios (minimum 4.5:1)
    - Implement clear focus indicators for keyboard navigation
    - Add semantic HTML structure and ARIA attributes
    - Test with screen readers and keyboard-only navigation

## Code Examples and Implementation Patterns

### Current Wix Data Integration (Use This Pattern)

```typescript
// Use existing data fetching service
import { wixDataService } from "@/services/wix-data.service";

// Fetch all collections (already implemented)
const useAllCollections = () => {
  return useQuery({
    queryKey: ["allCollections"],
    queryFn: () => fetch("/api/collections").then((res) => res.json()),
    staleTime: 5 * 60 * 1000,
    gcTime: 10 * 60 * 1000,
    retry: 3,
  });
};

// Use WixImage for all Wix images
import WixImage from "@/components/WixImage";

<WixImage
  src={heroData.backgroundImage}
  alt="Hero Background"
  width={1920}
  height={1080}
  className="w-full h-full object-cover"
  onLoadError={(error) => console.warn("Image failed:", error)}
/>;
```

### Component Template (Follow This Pattern)

```typescript
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
export type { ComponentNameProps };
```

### Design System Implementation

```typescript
// Use existing Tailwind classes with agricultural theme
const buttonVariants = {
  primary: "bg-green-600 hover:bg-green-700 text-white",
  secondary: "bg-blue-600 hover:bg-blue-700 text-white",
  outline: "border-2 border-green-600 text-green-600 hover:bg-green-50",
};

// Card component for services/products
const Card = ({ children, className, ...props }) => (
  <div
    className={cn(
      "bg-white rounded-xl shadow-md border border-gray-200",
      "hover:shadow-lg transition-shadow duration-300",
      "p-6 space-y-4",
      className
    )}
    {...props}
  >
    {children}
  </div>
);
```

### GSAP Animation Setup (Ready to Implement)

```typescript
// lib/gsap/animations.ts
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export const fadeInUp = (element: HTMLElement) => {
  gsap.fromTo(
    element,
    { opacity: 0, y: 30 },
    {
      opacity: 1,
      y: 0,
      duration: 0.8,
      ease: "power2.out",
      scrollTrigger: {
        trigger: element,
        start: "top 80%",
        toggleActions: "play none none reverse",
      },
    }
  );
};

export const parallaxBackground = (element: HTMLElement) => {
  gsap.to(element, {
    yPercent: -50,
    ease: "none",
    scrollTrigger: {
      trigger: element,
      start: "top bottom",
      end: "bottom top",
      scrub: true,
    },
  });
};
```

### Environment Variables (Create These Files)

Define these in .env.local:

```bash
# Wix CMS Configuration (Direct HTTP API - No SDK)
WIX_API_TOKEN=your_wix_api_token_here
WIX_SITE_ID=your_wix_site_id_here
WIX_API_BASE_URL=https://www.wixapis.com/wix-data/v2/items

# EmailJS Configuration
NEXT_PUBLIC_EMAILJS_SERVICE_ID=your_emailjs_service_id
NEXT_PUBLIC_EMAILJS_TEMPLATE_ID=your_emailjs_template_id
NEXT_PUBLIC_EMAILJS_PUBLIC_KEY=your_emailjs_public_key

# Development
NEXT_PUBLIC_SITE_URL=http://localhost:3000
NODE_ENV=development
```

Create .env.example:

```bash
# Wix CMS Configuration
WIX_API_TOKEN=your_wix_api_token_here
WIX_SITE_ID=your_wix_site_id_here
WIX_API_BASE_URL=https://www.wixapis.com/wix-data/v2/items

# EmailJS Configuration
NEXT_PUBLIC_EMAILJS_SERVICE_ID=your_emailjs_service_id
NEXT_PUBLIC_EMAILJS_TEMPLATE_ID=your_emailjs_template_id
NEXT_PUBLIC_EMAILJS_PUBLIC_KEY=your_emailjs_public_key

# Development
NEXT_PUBLIC_SITE_URL=http://localhost:3000
NODE_ENV=development
```

### Critical Implementation Rules

- **DO NOT** install Wix SDK packages; use the existing direct HTTP API implementation
- **DO** use the existing wixDataService and wixApiService for all Wix data
- **DO** use WixImage component for all Wix-sourced images
- **DO** use the configured React Query setup with existing providers
- **DO** follow the existing component patterns and file structure
- **DO NOT** use class-based components; use functional components with hooks
- **DO NOT** hardcode text strings; prepare for translation files
- **DO NOT** use inline styles; use Tailwind CSS classes
- **DO NOT** implement complex backend logic; this is a frontend-only task
- **DO** ensure all components have proper TypeScript interfaces
- **DO** implement proper loading and error states for all async operations

## Current File Structure to Work With

### ✅ Existing Files (Do Not Modify Structure)

```
src/
├── app/
│   ├── api/collections/route.ts    # Wix API endpoint (working)
│   ├── layout.tsx                  # Root layout (configured)
│   ├── page.tsx                    # Homepage (needs transformation)
│   ├── providers.tsx               # React Query setup (configured)
│   └── globals.css                 # Tailwind + design system (configured)
├── components/
│   ├── ui/                         # shadcn/ui components (ready)
│   ├── layout/                     # Layout components (basic structure)
│   ├── WixDataFetcher.tsx          # Comprehensive data display (reference)
│   └── WixImage.tsx                # Custom Wix image component (use this)
├── services/
│   ├── wix-api.service.ts          # Direct HTTP Wix API (working)
│   └── wix-data.service.ts         # Business logic layer (working)
├── hooks/                          # Custom hooks (ready for use)
├── lib/
│   ├── utils.ts                    # Utilities (cn function)
│   ├── wix-config.ts               # Wix configuration (configured)
│   └── utils/image.ts              # Image utilities (working)
└── types/wix.ts                    # Type definitions (comprehensive)
```

### 🎯 Implementation Focus

**Primary Task**: Transform `src/app/page.tsx` from showing WixDataFetcher to displaying proper homepage sections while leveraging all existing functionality.

**Key Integration Points**:

1. Use `/api/collections` endpoint for data fetching
2. Leverage WixImage component for all images
3. Follow existing React Query patterns
4. Build upon existing layout components
5. Implement GSAP animations using existing hooks

### 📋 Implementation Checklist

**Story 1.3 - Homepage Structure**:

- [ ] Create semantic HTML structure in page.tsx
- [ ] Implement responsive layout with CSS Grid/Flexbox
- [ ] Create section components (Hero, About, Services, Products, Contact)
- [ ] Ensure proper navigation and accessibility
- [ ] Use existing Header/Footer components

**Story 2.1 - Design System**:

- [ ] Implement color palette using CSS custom properties
- [ ] Create button variants (primary, secondary, outline)
- [ ] Design card components for content sections
- [ ] Implement form components with validation states
- [ ] Ensure accessibility with proper focus states

## Success Criteria

After implementation, the homepage should demonstrate:

**Story 1.3 Success Criteria**:

1. ✅ Semantic HTML structure with proper ARIA attributes
2. ✅ Responsive design working on mobile (320px), tablet (768px), and desktop (1024px+)
3. ✅ Header with logo and navigation elements
4. ✅ Main content sections (hero, about, services, contact) properly structured
5. ✅ Footer with company information and links
6. ✅ Keyboard navigation and screen reader accessibility
7. ✅ Consistent styling using Tailwind CSS and existing design system

**Story 2.1 Success Criteria**:

1. ✅ Color palette implemented with CSS custom properties
2. ✅ Typography scale with Inter font and proper hierarchy
3. ✅ Consistent spacing and sizing using design tokens
4. ✅ Button variants (primary, secondary, outline) with agricultural theme
5. ✅ Card components with proper shadows and borders
6. ✅ Form components with validation states
7. ✅ Accessibility features with focus states and ARIA attributes

**Technical Success Criteria**:

1. ✅ All data fetched using existing Wix API integration
2. ✅ Images loaded using WixImage component
3. ✅ Proper loading and error states implemented
4. ✅ GSAP animations functioning at 60fps
5. ✅ React Query caching working correctly
6. ✅ TypeScript compilation without errors
7. ✅ Responsive design validated across screen sizes

**Quality Assurance**:

- All animations perform smoothly without janky behavior
- Wix CMS integration displays real content correctly
- Image loading handles errors gracefully
- Code follows existing patterns and conventions
- Accessibility requirements are met (color contrast, keyboard navigation)
- Components are properly typed with TypeScript interfaces

Remember: Build upon the solid foundation that exists. Do not reinvent what's already working well.

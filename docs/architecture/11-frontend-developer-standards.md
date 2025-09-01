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
9. **Environment Variables**: Use NEXT_PUBLIC_ prefix only for client-side variables
10. **Shimmer Loading**: Implement loading skeletons for all async content with consistent shimmer animations

### Quick Reference

**Common Commands:**
```bash
# Development
npm run dev                    # Start development server
npm run build                  # Build for production
npm run start                  # Start production server
npm run lint                   # Run ESLint
npm run test                   # Run Jest tests
npm run test:watch             # Run tests in watch mode
```

**Key Import Patterns:**
```typescript
// Next.js imports
import { useRouter } from 'next/navigation';
import { useTranslations } from 'next-intl';
import Image from 'next/image';

// React Query
import { useQuery, useMutation } from '@tanstack/react-query';

// GSAP
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

// shadcn/ui
import { Button } from '@/components/ui/button';
import { Card } from '@/components/ui/card';

// Utilities
import { cn } from '@/lib/utils';
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
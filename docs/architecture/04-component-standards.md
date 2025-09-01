## Component Standards

### Component Template

```typescript
import React from 'react';
import { cn } from '@/lib/utils';

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
    <div 
      className={cn(
        "default-component-classes",
        className
      )}
      {...props}
    >
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
## State Management

### Store Structure

```plaintext
src/lib/state/
├── providers/                 # Context providers
│   ├── QueryProvider.tsx     # React Query provider
│   └── LanguageProvider.tsx  # i18n context provider
├── hooks/                     # State management hooks
│   ├── useWixContent.ts      # Wix CMS data fetching
│   ├── useContactForm.ts     # Contact form state
│   └── useLanguage.ts        # Language switching logic
└── types/                     # State-related types
    ├── content.ts            # Content data types
    └── forms.ts              # Form state types
```

### State Management Template

```typescript
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query';
import { wixClient } from '@/lib/api/wix-client';

// Content fetching hook
export const useWixContent = (section: string, locale: string) => {
  return useQuery({
    queryKey: ['wix-content', section, locale],
    queryFn: async () => {
      const response = await wixClient.getContent(section);
      return response.data;
    },
    staleTime: 5 * 60 * 1000, // 5 minutes
    gcTime: 10 * 60 * 1000,   // 10 minutes
    retry: 3,
    retryDelay: (attemptIndex) => Math.min(1000 * 2 ** attemptIndex, 30000),
  });
};

// Contact form mutation
export const useContactForm = () => {
  const queryClient = useQueryClient();
  
  return useMutation({
    mutationFn: async (formData: ContactFormData) => {
      // EmailJS integration
      const response = await emailjs.send(
        process.env.NEXT_PUBLIC_EMAILJS_SERVICE_ID!,
        process.env.NEXT_PUBLIC_EMAILJS_TEMPLATE_ID!,
        formData,
        process.env.NEXT_PUBLIC_EMAILJS_PUBLIC_KEY!
      );
      return response;
    },
    onSuccess: () => {
      // Handle success
      queryClient.invalidateQueries({ queryKey: ['contact-submissions'] });
    },
    onError: (error) => {
      // Handle error
      console.error('Contact form submission failed:', error);
    },
  });
};

// TypeScript interfaces
interface ContactFormData {
  name: string;
  email: string;
  company?: string;
  message: string;
  inquiryType: 'b2b' | 'b2c' | 'general';
}

interface WixContentResponse {
  id: string;
  title: string;
  content: string;
  updatedAt: string;
}
```
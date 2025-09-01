## Testing Requirements

### Component Test Template

```typescript
import React from 'react';
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import '@testing-library/jest-dom';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { NextIntlClientProvider } from 'next-intl';
import ComponentName from '../ComponentName';

// Mock GSAP
jest.mock('gsap', () => ({
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
      'test.key': 'Test Value'
    }
  };

  return ({ children }: { children: React.ReactNode }) => (
    <QueryClientProvider client={queryClient}>
      <NextIntlClientProvider messages={messages} locale="en">
        {children}
      </NextIntlClientProvider>
    </QueryClientProvider>
  );
};

describe('ComponentName', () => {
  it('renders correctly', () => {
    const Wrapper = createWrapper();
    
    render(
      <Wrapper>
        <ComponentName />
      </Wrapper>
    );

    expect(screen.getByRole('...', { name: /.../ })).toBeInTheDocument();
  });

  it('handles user interactions', async () => {
    const Wrapper = createWrapper();
    
    render(
      <Wrapper>
        <ComponentName />
      </Wrapper>
    );

    const button = screen.getByRole('button');
    fireEvent.click(button);

    await waitFor(() => {
      expect(screen.getByText('Expected Result')).toBeInTheDocument();
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
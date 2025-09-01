## Routing

### Route Configuration

```typescript
// next.config.js - i18n configuration
/** @type {import('next').NextConfig} */
const nextConfig = {
  i18n: {
    locales: ['en', 'fr', 'esp'],
    defaultLocale: 'en',
    localeDetection: true,
  },
  experimental: {
    appDir: true,
  },
  images: {
    domains: ['your-wix-domain.com'], // Add Wix image domains
    formats: ['image/webp', 'image/avif'],
  },
};

module.exports = nextConfig;

// app/[locale]/layout.tsx - Locale layout
import { notFound } from 'next/navigation';
import { NextIntlClientProvider } from 'next-intl';
import { getMessages } from 'next-intl/server';

interface LocaleLayoutProps {
  children: React.ReactNode;
  params: { locale: string };
}

export default async function LocaleLayout({
  children,
  params: { locale }
}: LocaleLayoutProps) {
  // Validate locale
  const isValidLocale = ['en', 'fr', 'esp'].includes(locale);
  if (!isValidLocale) notFound();

  // Load messages
  const messages = await getMessages();

  return (
    <html lang={locale}>
      <body>
        <NextIntlClientProvider messages={messages}>
          {children}
        </NextIntlClientProvider>
      </body>
    </html>
  );
}

// Generate static params for supported locales
export function generateStaticParams() {
  return [
    { locale: 'en' },
    { locale: 'fr' },
    { locale: 'esp' }
  ];
}
```
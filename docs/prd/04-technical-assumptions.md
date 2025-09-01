## Technical Assumptions

### Repository Structure
**Monorepo**: Single repository structure supporting current SPA development with clear organization for future expansion into full website, mobile app, and admin interfaces.

### Service Architecture
**Serverless**: Next.js application with serverless functions deployed on Vercel, integrated with Wix Studio Headless CMS for basic content management only. Multi-language functionality will be handled through Next.js native i18n instead of Wix premium features. This architecture provides optimal performance and cost-effectiveness for the SPA while supporting future e-commerce expansion through additional API layers.

### Email Service Integration
**Client-side Email**: EmailJS service integrated with Namecheap Private Email hosting for contact form submissions. This approach eliminates the need for a backend service while providing reliable email delivery through professional email infrastructure.

### Testing Requirements
**Unit + Integration**: Implement comprehensive testing including component unit tests, integration tests for Wix Studio API interactions, and end-to-end testing for critical user flows including multi-language functionality and form submissions.

### Additional Technical Assumptions and Requests
- Use Next.js 14+ with App Router for optimal performance and SEO
- Implement React Query for efficient API state management and caching
- Utilize shadcn/ui component library for consistent, modern UI elements
- Integrate GSAP for smooth animations and parallax effects with superior performance
- Configure TypeScript for type safety throughout the application
- Implement proper error boundaries and loading states with shimmer effects for robust user experience
- Set up ESLint and Prettier for code consistency and quality
- Configure automated deployment pipeline with Vercel integration
- Implement proper environment variable management for API keys and configuration
- **Next.js Native i18n:** Replaced Wix Studio multilingual with Next.js native i18n implementation
- **Updated URL routing structure:** (/en, /fr, /esp) for English, French, and Spanish support
- **Separation of Systems:** Wix Studio Headless CMS handles content management independently from Next.js i18n language switching
- Implement loading skeletons with shimmer animations for enhanced perceived performance
# AgroVentia Inc. Homepage SPA Product Requirements Document (PRD)

## Goals and Background Context

### Goals
- Establish professional digital presence for AgroVentia Inc. startup launch
- Create engaging, modern homepage experience with parallax effects and animations
- Implement multi-language support for Canadian and international markets
- Build scalable technical foundation for future full website and e-commerce expansion
- Enable contact pathways for B2B and B2C customer inquiries
- Deliver production-ready SPA within 2-week development timeline

### Background Context

AgroVentia Inc. is an agricultural import startup launching operations in Canada with plans for international expansion. As a new company in the competitive agricultural import market, they need to establish immediate credibility and professional presence to attract B2B partners and consumers. The current lack of digital presence creates barriers to business development and market entry.

This homepage SPA serves as the critical first touchpoint for the company's digital strategy, requiring modern design aesthetics with smooth animations and parallax effects to create memorable first impressions. The solution must support multiple languages to serve both Canadian (English/French) and international markets while providing a scalable foundation for future e-commerce development.

### Change Log

| Date | Version | Description | Author |
|------|---------|-------------|---------|
| 2025-08-18 | 1.0 | Initial PRD creation | PM |

## Requirements

### Functional

1. **FR1**: The homepage displays company branding, mission, and value proposition with engaging visual hierarchy
2. **FR2**: The system implements smooth parallax scrolling effects throughout the single-page experience
3. **FR3**: The application provides multi-language switching functionality using Next.js native i18n with English, French, and Spanish support (/en, /fr, /esp routing)
4. **FR4**: The homepage showcases agricultural product categories and import services with visual elements
5. **FR5**: The system integrates contact information and inquiry submission capabilities within the SPA flow
6. **FR6**: The application displays company location and operational regions (Canada + International)
7. **FR7**: The system implements responsive design optimized for desktop, tablet, and mobile devices
8. **FR8**: The homepage includes animations and micro-interactions to enhance user engagement
9. **FR9**: The application integrates with Wix Studio Headless CMS for basic content management independently from Next.js i18n multi-language system
10. **FR10**: The system provides clear navigation elements despite single-page structure

### Non Functional

1. **NFR1**: Homepage load time must be under 2 seconds on 3G connections globally
2. **NFR2**: All animations and parallax effects must maintain 60fps performance on modern devices
3. **NFR3**: The application must be fully responsive across screen sizes from 320px to 2560px width
2. **NFR4**: Multi-language switching must occur instantly using Next.js native i18n without page reload
5. **NFR5**: The system must be optimized for SEO with proper meta tags and structured data
6. **NFR6**: All interactive elements must be accessible via keyboard navigation
7. **NFR7**: The system must integrate with Wix Studio Headless APIs for basic CMS functionality only
8. **NFR8**: Code architecture must support easy expansion to multi-page site structure
9. **NFR9**: The system must be deployable to Vercel with automated CI/CD pipeline
10. **NFR10**: All visual elements must maintain quality across high-DPI displays

## User Interface Design Goals

### Overall UX Vision
Create a premium, modern digital experience that positions AgroVentia as a forward-thinking agricultural import company. The design should blend professional business credibility with innovative visual storytelling through smooth animations and parallax effects. Users should immediately understand the company's value proposition while being impressed by the technical execution and visual polish.

### Key Interaction Paradigms
- **Parallax Storytelling**: Progressive content revelation through GSAP-powered scroll-triggered animations
- **Smooth Navigation**: Anchor-link based navigation within single-page structure
- **Micro-interactions**: Hover effects, button animations, and shimmer loading states enhance engagement
- **Language Toggle**: Seamless language switching using Next.js native i18n without disrupting user flow
- **Progressive Enhancement**: Core functionality works without JavaScript, enhanced experience with GSAP animations

### Core Screens and Views
- **Hero Section**: Company introduction with striking visual elements and clear value proposition
- **About Overview**: Mission, vision, and startup story with engaging animations
- **Services Showcase**: Agricultural import capabilities and product categories with visual hierarchy
- **Contact Integration**: Contact form and information seamlessly integrated into overall flow
- **Language Selector**: Prominent, accessible language switching functionality

### Accessibility
**WCAG AA**: Implement WCAG AA compliance including proper color contrast, keyboard navigation, screen reader compatibility, and alternative text for all visual elements. Ensure animations can be reduced for users with motion sensitivity preferences.

### Branding
Modern, clean aesthetic that conveys trust and professionalism suitable for agricultural B2B market while appealing to consumers. Design will be developed from scratch with emphasis on:
- Professional color palette suggesting reliability and growth
- Typography that balances readability with modern appeal  
- Visual elements that subtly reference agricultural themes without being cliché
- Animation style that feels premium and purposeful rather than gratuitous

### Target Device and Platforms
**Web Responsive**: Optimized for all devices with particular attention to:
- Desktop business users (primary B2B audience)
- Mobile consumers (secondary B2C audience)  
- Tablet users for both segments
- Cross-browser compatibility across modern browsers

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

## Epic List

**Epic 1: Foundation & Core Infrastructure**: Establish Next.js project setup, Wix Studio integration, and basic homepage structure with deployment pipeline

**Epic 2: Visual Design & Animation System**: Implement modern design system, parallax effects, and smooth animations throughout the SPA experience

**Epic 3: Multi-language & Content Integration**: Build multi-language functionality and integrate all content sections with Wix Studio CMS

**Epic 4: Contact Integration & Polish**: Implement contact functionality, final optimizations, and production deployment

**Epic 5: Email Service Integration**: Implement EmailJS service with Namecheap Private Email hosting for reliable contact form submissions

## Epic 1: Foundation & Core Infrastructure

Establish the technical foundation for the AgroVentia homepage SPA including project setup, Wix Studio Headless integration, and basic homepage structure. This epic delivers a deployable application with core infrastructure and initial content display, providing the foundation for all subsequent development while ensuring proper CI/CD pipeline configuration.

### Story 1.1: Project Setup and Initial Configuration

As a developer,
I want to set up the Next.js project with required dependencies and configuration,
so that I have a solid foundation for building the AgroVentia homepage SPA with GSAP animations and native i18n support.

#### Acceptance Criteria
1. Next.js 14+ project is initialized with TypeScript configuration and native i18n setup
2. Required dependencies are installed: React Query, shadcn/ui, GSAP, and Wix Studio SDK (basic CMS only)
3. ESLint and Prettier are configured with appropriate rules for code quality
4. Basic folder structure is created following Next.js best practices including i18n structure
5. Environment variables are properly configured for development and production
6. Git repository is initialized with appropriate .gitignore and README
7. Package.json scripts are configured for development, build, and deployment

### Story 1.2: Wix Studio Headless CMS Integration

As a developer,
I want to establish connection with Wix Studio Headless CMS for basic content management,
so that content can be managed dynamically without requiring premium subscription features.

#### Acceptance Criteria
1. Wix Studio SDK is properly configured and connected for basic CMS functionality only
2. API endpoints are established for basic content retrieval (no premium features)
3. Content models are defined for homepage sections (hero, about, services, contact) using free tier capabilities
4. React Query is configured for API calls with proper error handling
5. API responses are properly typed with TypeScript interfaces
6. Basic content fetching functionality is tested and working with free tier limitations
7. Content structure supports future multi-language expansion through Next.js i18n

### Story 1.3: Basic Homepage Structure and Layout

As a user,
I want to see a basic homepage structure with navigation and content sections,
so that I can understand the site organization and access different areas.

#### Acceptance Criteria
1. Basic homepage layout is implemented with proper semantic HTML structure
2. Header section includes logo placeholder and navigation elements
3. Main content area is structured for hero, about, services, and contact sections
4. Footer section includes basic company information and links
5. CSS Grid/Flexbox layout system is implemented for responsive design
6. Basic styling is applied using Tailwind CSS through shadcn/ui
7. Page is accessible via keyboard navigation and screen readers

### Story 1.4: Deployment Pipeline and CI/CD Setup

As a developer,
I want automated deployment to Vercel with proper CI/CD pipeline,
so that code changes can be deployed efficiently and reliably.

#### Acceptance Criteria
1. Vercel deployment is configured and connected to Git repository
2. Automated builds are triggered on code commits
3. Environment variables are properly configured in Vercel
4. Preview deployments are generated for pull requests
5. Production deployment is configured for main branch
6. Build optimization is configured for best performance
7. Deployment status and logs are accessible and monitored

## Epic 2: Visual Design & Animation System

Implement the modern visual design system and engaging animation effects that define the AgroVentia brand experience. This epic delivers the premium look and feel through parallax scrolling, smooth animations, and responsive design that creates memorable first impressions for both B2B and B2C users.

### Story 2.1: Design System and Component Library Setup

As a developer,
I want to establish a consistent design system with reusable components,
so that the homepage maintains visual consistency and professional appearance.

#### Acceptance Criteria
1. Color palette is defined with CSS custom properties for brand consistency
2. Typography scale is implemented with appropriate font families and weights
3. Spacing and sizing system is configured using consistent design tokens
4. Button components are created with multiple variants (primary, secondary, outline)
5. Card components are designed for content sections with proper shadows and borders
6. Form components are styled for contact sections with validation states
7. All components follow accessibility guidelines with proper focus states

### Story 2.2: Hero Section with Parallax Effects

As a visitor,
I want to see an impressive hero section with smooth GSAP-powered parallax animations,
so that I immediately understand AgroVentia's value proposition and feel engaged by the modern presentation.

#### Acceptance Criteria
1. Hero section displays compelling headline and subheading about AgroVentia
2. Background includes subtle GSAP-powered parallax scrolling effect with agricultural imagery
3. Call-to-action buttons are prominently displayed with smooth GSAP hover animations
4. Scroll indicator encourages users to explore more content below with animated effects
5. Hero content is fully responsive across all device sizes
6. GSAP animation performance maintains 60fps on modern devices
7. Hero section loads quickly with proper image optimization and shimmer loading states

### Story 2.3: About Section with Animated Content Reveal

As a visitor,
I want to learn about AgroVentia's mission and story through engaging GSAP-powered visual presentation,
so that I can build trust and understanding of the company's background and values.

#### Acceptance Criteria
1. About section includes company mission, vision, and startup story
2. Content reveals progressively through GSAP scroll-triggered animations
3. Visual elements (icons, images) complement the textual content with smooth transitions
4. GSAP animations are smooth and purposeful, enhancing rather than distracting from content
5. Section maintains readability and accessibility while being visually engaging
6. Content is structured for easy scanning and comprehension
7. Mobile experience preserves impact while adapting to smaller screens with optimized GSAP performance

### Story 2.4: Services Showcase with Interactive Elements

As a potential customer,
I want to explore AgroVentia's agricultural import services and capabilities,
so that I can understand how the company can meet my needs.

#### Acceptance Criteria
1. Services section showcases different agricultural product categories
4. Interactive elements reveal additional information with smooth GSAP transitions on hover or click
3. Visual hierarchy guides users through different service offerings
4. Icons or imagery represent different agricultural product types
5. Smooth GSAP transitions between different content states enhance user experience
6. Section clearly communicates AgroVentia's import capabilities and expertise
7. Content is organized for both B2B and B2C audience understanding

## Epic 3: Multi-language Implementation & Content Integration

Build Next.js native multi-language functionality and integrate content management through Wix Studio CMS as separate systems. This epic enables AgroVentia to serve Canadian bilingual requirements and international markets through Next.js i18n while providing dynamic content management capabilities through Wix Studio basic CMS for future updates and expansion.

**Architecture Clarification:**
- **Next.js Native i18n:** Handles all multi-language functionality including URL routing (/en, /fr, /esp) and language switching
- **Wix Studio Headless CMS:** Provides content management for homepage sections (basic/free tier only)
- **Separation of Concerns:** Language switching and content management operate independently

### Story 3.1: Next.js Native Multi-language Infrastructure

As an international visitor,
I want to view the homepage content in my preferred language using Next.js native i18n system,
so that I can understand AgroVentia's offerings and communicate effectively with the company.

#### Acceptance Criteria
1. Next.js i18n configuration is set up with support for English, French, and Spanish (/en, /fr, /esp routing)
2. Language selector is prominently displayed in the header with clear visual indicators
3. Language switching occurs instantly using Next.js i18n without page reload or content flash
4. All static text content supports multiple languages through Next.js i18n localization files
5. Language preference is stored and managed through Next.js i18n routing and cookies
6. URL structure accommodates language routing with proper fallbacks and redirects
7. Right-to-left language support is prepared for future expansion within Next.js i18n framework

### Story 3.2: Wix Studio Headless CMS Content Integration

As a content manager,
I want all homepage content to be manageable through Wix Studio Headless CMS basic functionality,
so that content updates can be made without code changes while operating independently from the multi-language system.

#### Acceptance Criteria
1. Hero section content is dynamically loaded from Wix Studio basic CMS with proper fallbacks
2. About section story and mission content is CMS-managed with basic rich text support (free tier)
3. Services information is dynamically loaded within free tier constraints for adding/removing categories
4. Contact information and business details are manageable through basic CMS functionality
5. CMS content structure is language-agnostic, allowing Next.js i18n to handle language switching independently
6. Content updates reflect immediately on the live site through proper cache management
7. CMS integration includes proper error handling and shimmer loading states

### Story 3.3: SEO Optimization and Meta Content

As a business stakeholder,
I want the homepage to be discoverable through search engines in multiple languages,
so that potential customers can find AgroVentia through organic search.

#### Acceptance Criteria
1. Dynamic meta titles and descriptions are generated for each language version
2. Structured data markup is implemented for business information and services
3. Open Graph and Twitter Card meta tags are properly configured
4. XML sitemap includes all language versions of the homepage
4. Hreflang tags are implemented for proper international SEO using Next.js i18n routing
6. Page loading performance meets Core Web Vitals requirements
7. Analytics tracking is configured for user behavior and conversion monitoring

### Story 3.4: Integration Testing and System Coordination

As a user,
I want smooth coordination between Next.js i18n language switching and Wix CMS content loading,
so that the homepage provides a seamless experience regardless of language selection or content updates.

#### Acceptance Criteria
1. Language switching works seamlessly with CMS content loading without conflicts
2. Shimmer loading states appear consistently across all language versions
3. Error handling works properly for both language switching and content fetching failures
4. CMS content displays correctly regardless of active language setting
5. Performance remains optimal when combining Next.js i18n with Wix CMS integration
6. Fallback content ensures homepage functionality if either system experiences issues
7. User experience remains consistent across all supported languages (/en, /fr, /esp)

## Epic 4: Contact Integration & Polish

Implement comprehensive contact functionality and apply final optimizations to deliver a production-ready homepage SPA. This epic ensures users can easily connect with AgroVentia while providing the performance and polish expected from a professional business website.

### Story 4.1: Contact Form and Information Integration

As a potential customer,
I want to easily contact AgroVentia with inquiries about their services,
so that I can start a business relationship or get questions answered.

#### Acceptance Criteria
1. Contact form is seamlessly integrated within the SPA flow without disrupting user experience
2. Form includes fields for name, email, company, inquiry type, and detailed message
3. Form validation provides real-time feedback with clear error messaging
4. Form submission triggers confirmation messaging and email notifications
5. Contact information (phone, email, address) is prominently displayed
6. Business hours and response time expectations are clearly communicated
7. Form integrates with Wix Studio for inquiry management and follow-up
8. Form submissions are sent via EmailJS service to Namecheap Private Email hosting
9. Email notifications are sent to contact@agroventia.ca for all form submissions
10. Email service gracefully handles delivery failures with appropriate user feedback

### Story 4.2: Performance Optimization and Core Web Vitals

As a user,
I want the homepage to load quickly and respond smoothly to interactions,
so that I have a positive experience that reflects AgroVentia's professionalism.

#### Acceptance Criteria
1. Largest Contentful Paint (LCP) occurs within 2.5 seconds
2. First Input Delay (FID) is less than 100 milliseconds
3. Cumulative Layout Shift (CLS) is less than 0.1
4. Images are optimized with proper formats (WebP, AVIF) and lazy loading
5. JavaScript bundles are optimized with code splitting and tree shaking
6. Critical CSS is inlined with non-critical styles loaded asynchronously
7. Performance monitoring is configured to track real user metrics

### Story 4.3: Final Visual Polish and Micro-interactions

As a visitor,
I want delightful GSAP-powered micro-interactions and polished visual details throughout the homepage,
so that AgroVentia appears innovative and attention-to-detail focused.

#### Acceptance Criteria
1. Button hover states and click animations provide satisfying feedback using GSAP
2. Form interactions include smooth focus transitions and validation animations powered by GSAP
3. Scroll progress indicator shows user position with smooth GSAP animations
4. Shimmer loading animations are branded and consistent with overall design aesthetic
5. GSAP transition effects between content sections feel natural and purposeful
6. Animation preferences are respected for users with reduced motion settings
7. All interactive elements have appropriate touch targets for mobile users

### Story 4.4: Final Testing and Production Deployment

As a business stakeholder,
I want assurance that the homepage functions correctly across all target browsers and devices,
so that all potential customers have a positive experience with AgroVentia's digital presence.

#### Acceptance Criteria
1. Cross-browser testing confirms functionality in Chrome, Firefox, Safari, and Edge
2. Responsive design testing validates experience across mobile, tablet, and desktop
3. Multi-language functionality is tested for content accuracy and technical functionality
4. Contact form submission is tested end-to-end including email delivery
5. Performance testing confirms Core Web Vitals requirements are met
6. Accessibility testing validates WCAG AA compliance across all features
7. Production deployment is completed with proper monitoring and analytics configured

## Epic 5: Email Service Integration

Implement EmailJS service with Namecheap Private Email hosting to ensure reliable contact form submissions and professional email communication. This epic establishes the email infrastructure that supports all contact functionality while maintaining security and deliverability standards.

### Story 5.1: EmailJS Service Configuration and Integration

As a developer,
I want to configure and integrate EmailJS service with the contact form,
so that form submissions are reliably sent to the company's professional email address.

#### Acceptance Criteria
1. EmailJS account is created and configured with appropriate service and template IDs
2. EmailJS public key is properly configured in environment variables
3. Contact form submissions trigger EmailJS service calls with all form data
4. EmailJS service is configured to send emails to contact@agroventia.ca
5. Email template includes all form fields with appropriate formatting and structure
6. Error handling is implemented for EmailJS service failures
7. EmailJS integration is tested with various form submission scenarios
8. Security best practices are followed for handling EmailJS credentials

### Story 5.2: Namecheap Private Email Hosting Setup

As a system administrator,
I want to configure Namecheap Private Email hosting for AgroVentia,
so that the company has professional email communication with reliable deliverability.

#### Acceptance Criteria
1. Namecheap Private Email account is set up with contact@agroventia.ca and admin@agroventia.ca addresses
2. DNS records are properly configured for email hosting (MX, SPF, DKIM, DMARC)
3. Email accounts are configured with appropriate storage and security settings
4. Email forwarding rules are set up if needed for team distribution
5. Spam filtering is configured to prevent false positives for legitimate contact form submissions
6. Email account access is tested and verified for all authorized team members
7. Documentation is created for email account management and troubleshooting

### Story 5.3: Email Notification System and Error Handling

As a business stakeholder,
I want to ensure contact form submissions are reliably delivered and errors are properly handled,
so that no potential customer inquiries are lost and issues can be quickly resolved.

#### Acceptance Criteria
1. Email notifications are sent immediately upon form submission with all relevant information
2. Confirmation message is displayed to users upon successful email delivery
3. Error messages are displayed to users if email delivery fails with clear next steps
4. Email delivery failures are logged for monitoring and troubleshooting
5. Retry mechanism is implemented for temporary delivery failures
6. Fallback notification method is available if primary email service is unavailable
7. Email delivery success rate is monitored and reported
8. Alerting system is configured for critical email delivery failures

### Story 5.4: Email Testing and Validation

As a quality assurance specialist,
I want to thoroughly test the email service integration,
so that contact form submissions work reliably in production with professional deliverability.

#### Acceptance Criteria
1. Email delivery is tested with various form submission scenarios and data inputs
2. Email formatting and content are validated for professional appearance and readability
3. Delivery time is measured and optimized for sub-5-second delivery
4. Error handling is tested with various failure scenarios (network issues, service outages)
5. Email deliverability is tested to ensure messages reach inbox rather than spam
6. Cross-browser and cross-device testing confirms consistent email functionality
7. Security testing validates that email service credentials are properly protected
8. Performance testing confirms email service integration doesn't impact form submission speed

## Next Steps

## Next Steps

### UX Expert Prompt
Review this PRD and create detailed UI/UX specifications for the AgroVentia homepage SPA, focusing on modern design principles, effective use of parallax animations, and optimal user experience for both B2B and B2C audiences. Emphasize professional credibility while showcasing innovation through visual design.

### Architect Prompt  
Use this PRD to create a comprehensive technical architecture for the AgroVentia homepage SPA, implementing Next.js with Wix Studio Headless integration, React Query state management, and shadcn/ui components. Ensure the architecture supports the specified 2-week development timeline while providing scalable foundation for future e-commerce expansion.
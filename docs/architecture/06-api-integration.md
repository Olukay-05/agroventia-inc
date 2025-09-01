## API Integration

### Service Template

```typescript
import axios, { AxiosInstance, AxiosResponse } from 'axios';

// Wix Studio Headless Client
class WixStudioClient {
  private client: AxiosInstance;

  constructor() {
    this.client = axios.create({
      baseURL: process.env.NEXT_PUBLIC_WIX_API_URL,
      headers: {
        'Authorization': `Bearer ${process.env.WIX_API_TOKEN}`,
        'Content-Type': 'application/json',
      },
      timeout: 10000,
    });

    this.setupInterceptors();
  }

  private setupInterceptors() {
    // Request interceptor
    this.client.interceptors.request.use(
      (config) => {
        console.log(`API Request: ${config.method?.toUpperCase()} ${config.url}`);
        return config;
      },
      (error) => Promise.reject(error)
    );

    // Response interceptor
    this.client.interceptors.response.use(
      (response: AxiosResponse) => response,
      (error) => {
        console.error('API Error:', error.response?.data || error.message);
        return Promise.reject(error);
      }
    );
  }

  async getContent(section: string): Promise<WixContentResponse> {
    try {
      const response = await this.client.get(`/content/${section}`);
      return response.data;
    } catch (error) {
      throw new Error(`Failed to fetch content for section: ${section}`);
    }
  }

  async updateContent(section: string, data: Partial<WixContentResponse>): Promise<WixContentResponse> {
    try {
      const response = await this.client.put(`/content/${section}`, data);
      return response.data;
    } catch (error) {
      throw new Error(`Failed to update content for section: ${section}`);
    }
  }
}

export const wixClient = new WixStudioClient();

// Types
interface WixContentResponse {
  id: string;
  section: string;
  title: string;
  content: string;
  metadata?: Record<string, any>;
  updatedAt: string;
}

export type { WixContentResponse };
```

### API Client Configuration

```typescript
import emailjs from '@emailjs/browser';

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
          company: formData.company || 'Not specified',
          inquiry_type: formData.inquiryType,
          message: formData.message,
          to_email: 'contact@agroventia.com', // Namecheap Private Email
        },
        emailConfig.publicKey
      );
      return response;
    } catch (error) {
      console.error('Email sending failed:', error);
      throw new Error('Failed to send email. Please try again.');
    }
  },
};

// Types
interface ContactFormData {
  name: string;
  email: string;
  company?: string;
  inquiryType: 'b2b' | 'b2c' | 'general';
  message: string;
}

export type { ContactFormData };
```
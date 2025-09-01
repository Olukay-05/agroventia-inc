# Wix Studio Configuration for Development

## Account Information
- Site ID: 351090e5-24e6-4e64-a449-67d7ee407a86
- Account Type: Free
- Access Level: Administrator

## Content Collections Structure

### Hero Section Collection
- **Collection Name**: HeroContent
- **Fields**:
  - title (text)
  - subtitle (text)
  - ctaText (text)
  - ctaLink (url)
  - backgroundImage (image)
  - overlayOpacity (number, 0-100)

### About Section Collection
- **Collection Name**: AboutContent
- **Fields**:
  - title (text)
  - content (rich text)
  - imageUrl (image)
  - missionTitle (text)
  - missionContent (rich text)

### Services Section Collection
- **Collection Name**: ServicesContent
- **Fields**:
  - serviceName (text)
  - description (rich text)
  - icon (image)
  - sortOrder (number)

### Products Section Collection
- **Collection Name**: ProductsContent
- **Fields**:
  - productName (text)
  - productDescription (rich text)
  - productImage (image)
  - price (number)
  - category (text)
  - sortOrder (number)

### Products Catalog Collection
- **Collection Name**: Import1
- **Fields**:
  - productName (text)
  - productDescription (rich text)
  - productImage (image)
  - price (number)
  - category (text)
  - sku (text)
  - inStock (boolean)

### Contact Section Collection
- **Collection Name**: ContactContent
- **Fields**:
  - title (text)
  - address (text)
  - phone (text)
  - email (email)
  - businessHours (rich text)
  - mapEmbedCode (text)

## Implementation Notes

1. All collections should be created as "Multiple Items" collections
2. The "ServicesContent" and product collections should allow multiple items
3. Use appropriate field types for validation (email for email field, URL for links, etc.)
4. Add at least one sample item to each collection for testing
5. Ensure all images are uploaded and properly linked

## Multi-language Considerations

For multi-language support, create content for:
- English (default)
- French (fr)
- Spanish (esp)

Each content item should have translations for all text fields in these languages.

## Sample Content

After creating the collections, add at least one sample item to each collection with realistic content that matches the agricultural business context of AgroVentia.

## Testing Checklist

- [ ] All collections created with correct names
- [ ] All fields created with correct types
- [ ] Sample content added to each collection
- [ ] Images uploaded and linked properly
- [ ] Multi-language content added where applicable
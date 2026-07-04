# Image Optimization

## What it is
The set of techniques for serving images at the smallest size and most efficient format a user's device/viewport actually needs — using modern formats (WebP, AVIF), responsive `srcset`/`sizes`, lazy loading offscreen images, and tooling like `next/image` that automates this per-request.

## Why it's useful
- Images are typically the largest portion of a page's total byte weight, so optimizing them has an outsized effect on load time.
- Serving correctly-sized images (rather than one large image scaled down by CSS) avoids wasting bandwidth on pixels the user never sees at full resolution.
- Directly improves Largest Contentful Paint (LCP), one of the Core Web Vitals search engines and users care about most.

## Classic use-cases
- Content/marketing sites and e-commerce product pages where images dominate page weight.
- Responsive designs serving different image resolutions to mobile vs. desktop viewports.
- Any page where LCP is driven by a hero image, and shaving that image's load time directly improves the metric.

## Pros
- Often the single highest-leverage performance change available — big win for relatively low effort with modern tooling.
- Modern formats (AVIF/WebP) can cut file size dramatically vs. JPEG/PNG at equivalent visual quality.
- Framework-level tools (`next/image`, Cloudinary, Imgix) automate resizing, format negotiation, and lazy loading.

## Cons
- Modern formats need fallbacks for older browsers, adding some complexity to the delivery pipeline.
- Automatic optimization services/tools add infrastructure dependency and sometimes cost.
- Lazy loading offscreen images incorrectly (e.g., lazy-loading the LCP image itself) can hurt the exact metric it's meant to help.

## Interview questions
1. Why do unoptimized images often dominate a page's Largest Contentful Paint time?
2. What's the difference between resizing an image with CSS vs. serving a correctly-sized image via `srcset`?
3. When should you avoid lazy-loading an image, and why?
4. How do modern formats like AVIF/WebP achieve smaller file sizes than JPEG/PNG, and what's the browser support tradeoff?
5. How does a tool like `next/image` decide what size/format to serve for a given request?

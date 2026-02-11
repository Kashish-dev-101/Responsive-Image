# Responsive Images Demo

Demo project showcasing different responsive image techniques. Each technique has its own dedicated HTML file for easy understanding.

---

## Techniques Covered

### 1. srcset with Density Descriptors (DPR)

**Demo:** [https://kashish-dev-101.github.io/Responsive-Image/srcset-density.html](https://kashish-dev-101.github.io/Responsive-Image/srcset-density.html)

Uses `srcset` with density descriptors like `1x`, `2x`, and `3x` to serve different image resolutions based on device pixel ratio.

```html
<img
  src="image.jpg"
  srcset="
    image.jpg?tr=w-300 1x,
    image.jpg?tr=w-600 2x,
    image.jpg?tr=w-900 3x
  "
  alt="Responsive image"
/>
```

**When to use:** Fixed-size images that need to look sharp on high-DPI displays.

**Learn more:** [srcset with Density Descriptors](https://imagekit.io/responsive-images/#chapter-4---srcset)

---

### 2. srcset with Width Descriptors and sizes

**Demo:** [https://kashish-dev-101.github.io/Responsive-Image/srcset-sizes.html](https://kashish-dev-101.github.io/Responsive-Image/srcset-sizes.html)

Uses `srcset` with width descriptors (e.g., `640w`, `1080w`) combined with the `sizes` attribute. The browser picks the best file based on rendered image size and device pixel ratio.

```html
<img
  src="image.jpg"
  srcset="
    image.jpg?tr=w-256 256w,
    image.jpg?tr=w-640 640w,
    image.jpg?tr=w-1080 1080w,
    image.jpg?tr=w-1920 1920w
  "
  sizes="(max-width: 600px) 100vw, (max-width: 900px) 50vw, 33vw"
  alt="Responsive image"
/>
```

**When to use:** Images that change size based on viewport width (most common use case).

**Learn more:** [srcset with sizes](https://imagekit.io/responsive-images/#chapter-5---srcset-with-sizes)

---

### 3. Art Direction with picture Element

**Demo:** [https://kashish-dev-101.github.io/Responsive-Image/picture.html](https://kashish-dev-101.github.io/Responsive-Image/picture.html)

Uses the `<picture>` element to serve completely different images based on viewport width. This is useful for art direction where you want to show a cropped or different composition on mobile vs desktop.

```html
<picture>
  <source media="(max-width: 600px)" srcset="image-mobile.jpg" />
  <source media="(min-width: 601px)" srcset="image-desktop.jpg" />
  <img src="image-fallback.jpg" alt="Art directed image" />
</picture>
```

**When to use:** When you need different image crops or compositions for different screen sizes.

**Learn more:** [Using picture Element](https://imagekit.io/responsive-images/#chapter-6---using-picture-element)

---

### 4. Client Hints with ImageKit

**Demo:** [https://kashish-dev-101.github.io/Responsive-Image/clientHint.html](https://kashish-dev-101.github.io/Responsive-Image/clientHint.html)

Uses ImageKit transformations `w-auto` and `dpr-auto` with Client Hints. The browser sends hints like `Sec-CH-DPR` and `Sec-CH-Width`, and ImageKit responds with an optimized image automatically.

```html
<meta http-equiv="Accept-CH" content="Sec-CH-DPR, Sec-CH-Width" />

<img
  src="https://ik.imagekit.io/your-id/image.jpg?tr=w-auto,dpr-auto"
  sizes="(max-width: 600px) 100vw, 50vw"
  alt="Client hints image"
/>
```

**When to use:** When using ImageKit and you want automatic optimization without maintaining multiple srcset URLs.

**Learn more:** [Using Client Hints](https://imagekit.io/responsive-images/#chapter-7---using-client-hints) | Read more on how to use [ImageKit Transformations with Client Hints](https://imagekit.io/docs/image-transformation#client-hints)

---

## Learn More

For a comprehensive guide on responsive images, check out the [ImageKit Responsive Images Guide](https://imagekit.io/responsive-images/).

- [Chapter 4 - srcset with Density Descriptors](https://imagekit.io/responsive-images/#chapter-4---srcset-with-density-descriptors)
- [Chapter 5 - srcset with sizes](https://imagekit.io/responsive-images/#chapter-5---srcset-with-sizes)
- [Chapter 6 - Using picture Element](https://imagekit.io/responsive-images/#chapter-6---using-picture-element)
- [Chapter 7 - Using Client Hints](https://imagekit.io/responsive-images/#chapter-7---using-client-hints)

---

## How to Test

1. Open any demo file in Chrome
2. Open DevTools (F12)
3. Toggle device toolbar to simulate different devices
4. Check the "Selected image URL" shown below each image to see which variant was loaded
5. For Client Hints demo, check the Network tab to see request headers

> **Note: Simulating Different Devices in Chrome DevTools**
>
> To properly test responsive images you need to simulate different viewport widths, device sizes, and DPR values. Here's how:
>
> **Viewport Width & Device Sizes**
> 1. Open DevTools (F12) and enable the **Device Toolbar** (Ctrl+Shift+M / Cmd+Shift+M)
> 2. Use the **device dropdown** at the top to pick a preset device (e.g., iPhone 14, iPad, Pixel 7) or select **Responsive** to manually set any width and height
> 3. In **Responsive** mode, drag the viewport handles or type exact pixel values to test specific breakpoints (e.g., 600px, 900px, 1920px)
>
> **Device Pixel Ratio (DPR)**
> 1. In the device toolbar, click the **three-dot menu (⋮)**
> 2. Select **Add device pixel ratio**
> 3. A DPR dropdown appears — switch between **1x**, **2x**, and **3x** to simulate different screen densities
>
> Reload the page after changing viewport or DPR to see the browser pick a different image variant.
>
> Reference: [Chrome DevTools — Simulate Mobile Devices](https://developer.chrome.com/docs/devtools/device-mode)

---

## Project Structure

```
Responsive-Image/
├── srcset-density.html   # DPR-based responsive images
├── srcset-sizes.html     # Width descriptor + sizes
├── picture.html          # Art direction with picture element
├── clientHint.html       # Client Hints with ImageKit
├── style.css             # Shared styles (ImageKit branding)
└── README.md
```

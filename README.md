# Free HTML to Image API

A free API for generating images using HTML + Tailwind CSS.

## Example Use Cases

#### 📣 Social & Marketing

* Generate social media images (X, LinkedIn, Instagram, etc.)
* Create shareable announcement graphics
* Produce campaign visuals at scale

#### 🌐 Web & SEO / GEO

* Improve link previews for SEO and sharing (Open Graph (OG) / preview images)
* Create dynamic blog post thumbnails

### APPs (Swift / React Native)

* Create "sharing card" images that users can share on socials

#### ⚙️ Automation & Scripting

* Batch-generate images from templates (e.g. cards)
* Create scheduled or event-based image generation pipelines

#### 🤖 AI / Agent Workflows

* Allow LLMs and agents to generate structured visual outputs
* Turn structured data into rendered images (charts, summaries, cards)
* Generate UI mockups or concept visuals programmatically

#### 🧪 Prototyping & Design

* Generate static previews for components or layouts

#### 🧩 Other

* One-off image generation scripts
* Internal tools and dashboards

---

## Usage

Send a server-side `POST` request to `https://free-html-to-image.studiobrace.com/?creator=your@email.com`. The post request body should be HTML and the returned response body will be a `PNG` image data.

### JavaScript (Node / Fetch)

```js
const html = `
<div class="w-[800px] h-[500px] overflow-hidden">
  <div class="text-red-500">Hello World</div>
</div>
`;

const imageData = await fetch(
  'https://free-html-to-image.studiobrace.com/?creator=your@email.com',
  {
    method: 'POST',
    body: html
  }
).then(res => res.arrayBuffer());
```

### Notes

* Replace `?creator=your@email.com` with your actual email (or your Git author email).
  This is required for abuse prevention under fair usage.
* You can include up to **5 remote images** per request. Images must be publically hosted (or exposed via a public tunnel when generating on your own computer)
* Google Fonts are supported (e.g. `style="font-family: Inter"`).
* Tailwind classes and inline styles (`style=""`) are supported.
* Always define an explicit width and height on the outer container.

---

## Usage with curl

```bash
curl -X POST \
  "https://free-html-to-image.studiobrace.com/?creator=my@email.com" \
  --data '<div class="w-[800px] h-[500px] bg-white flex items-center justify-center"><div class="text-[#f00] text-[30px]">Hello World 🥺👉👈</div></div>' \
  --output image.png
```

---

## Usage with React (Next.js / Cloudflare Workers / Node)

```jsx
import { renderToString } from "react-dom/server";

const Image = () => (
  <div className="w-[800px] h-[500px] overflow-hidden">
    <div className="text-red-500">Hello World</div>
  </div>
);

function generateImageResponse() {
  const html = renderToString(<Image />);
  
  const imageResponse = await fetch(
    'https://free-html-to-image.studiobrace.com/?creator=your@email.com',
    {
      method: 'POST',
      body: html
    }
  );
  
  return imageResponse;
}
```

---

## Example

```js
const html = `
<div class="w-[1000px] h-[500px] bg-gradient-to-br from-yellow-100 via-yellow-50 to-orange-100 flex items-center justify-between p-10 font-sans">
  
  <!-- Left content -->
  <div class="text-left">
    <h1 class="text-5xl font-bold text-gray-800 tracking-tight">
      hello world
    </h1>
    <p class="mt-3 text-xl font-medium text-gray-700">
      This is my first generated image
    </p>
  </div>

  <!-- Right image -->
  <div class="flex items-center justify-end h-full">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/b/b8/Banana_cat_character_in_Among_Us.svg"
      class="h-full max-h-[420px] object-contain"
    />
  </div>

</div>
`;

const imageData = await fetch(
  'https://free-html-to-image.studiobrace.com/?creator=your@email.com',
  {
    method: 'POST',
    body: html
  }
).then(res => res.arrayBuffer());

await import("node:fs/promises").then(fs =>
  fs.writeFile("my-generated-image.png", Buffer.from(imageData))
);
```

---

## Frequently Asked Questions

### How can this be free?

It is currently subsidized by other Studio Brace products. We built this for our own use and are sharing it freely with love :)

### What is fair usage?

If you generate **100+ images in quick succession**, or **1000+ images per day**, you may be see errors (rate limited)

For higher-volume use cases we’ll work with you to find a suitable solution, contact us at:
**[hi@studiobrace.com](mailto:hi@studiobrace.com)**

### What is your uptime?

We aim for best-effort high availability.
If you require strict reliability or isolation from free-tier usage, please contact us at:

**[hi@studiobrace.com](mailto:hi@studiobrace.com)**

### Is this actually free?

Absolutley! Please just follow the fair usage guidelines above to keep it sustainable

## More information:

Please visit: [https://free-html-to-image.studiobrace.com](https://free-html-to-image.studiobrace.com)

Here’s a clean, technical GitHub description you can drop into your README:

---

# Interactive 3D IP Geolocation Demo (Next.js + React Three Fiber)

An interactive Next.js page showcasing a 3D, GPU-rendered call-to-action built with **@react-three/fiber** and **@react-three/drei**. On user interaction, the app performs a client-side request to retrieve **IP geolocation** data and renders the results.

## Features

* **3D UI**: Layered, beveled button rendered in WebGL with lighting, shadows, and hover animations.
* **Processing View**: Fullscreen console-style visualization during the “processing” phase.
* **Geolocation Lookup**: Client-side fetch to `https://ipapi.co/json/` to obtain IP, city, and country.
* **TypeScript**: Typed React components and Three.js refs for safer stateful animation.
* **Zero server code**: Pure client-side demo—easy to deploy on static hosts.

## Tech Stack

* **Framework**: Next.js (App Router, React 18)
* **3D/Rendering**: @react-three/fiber, @react-three/drei, three.js
* **Language**: TypeScript

## Quick Start

```bash
# install
pnpm install    # or npm install / yarn

# dev
pnpm dev        # http://localhost:3000

# build
pnpm build
pnpm start
```

## How It Works

1. **Intro Phase**: Renders a 3D button (RoundedBox + lighting/shadows). Hover state is animated via `useFrame` to smoothly scale the group.
2. **Processing Phase**: Switches to a console-style visualization while work is “in progress”.
3. **Result Phase**: Performs the geolocation lookup and displays:

   * `ip`
   * `city`
   * `country_name`

### API Call (Client-Side)

```ts
async function fetchGeoData() {
  const res = await fetch("https://ipapi.co/json/");
  if (!res.ok) throw new Error("Failed to fetch geo data");
  return res.json(); // { ip, city, country_name, ... }
}
```

## Code Structure (excerpt)

* `Home` – orchestrates the UI flow with a minimal state machine: `intro` → `processing` → `results`.
* `Button3D` – encapsulates the 3D CTA (geometry, materials, hover animation).
* `ProcessingView` – console-like visualization during the request.
* `GeoInfo` – small presenter for IP, city, country.

## Accessibility & UX Notes

* Pointer interactions are handled on the 3D object; controls are disabled to avoid input conflicts.
* Cursor feedback on hover.
* Results are shown in plain text beneath the scene for readability.

## Privacy

This demo performs a **client-side** request to a third-party geolocation service (`ipapi.co`) which returns approximate IP-based location data. No server is involved here.

## Deployment

* Works on any platform that supports Next.js static output or Node hosting (e.g., Vercel).
* No environment variables required for the basic demo.

## License

MIT (see `LICENSE`).

---

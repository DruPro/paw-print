# Paw-Print Technical Assessment

## Project Overview

Paw-Print is a high-fidelity, mobile-first link-in-bio platform engineered specifically for the pet owner demographic. Unlike standard link aggregators, Paw-Print prioritizes contextual safety and personality, providing a structured "User Manual" for pets.

## Core Implementation

* **Profile Section:** Dynamic display of pet identity (Avatar, Name, Bio).
* **Link Management:** A vertical stack of high-performance link buttons with interactive hover states.
* **Aesthetics:** A minimalist "Global Black" and warm neutral color palette, utilizing professional typography for readability and brand authority.
* **Responsiveness:** Mobile-first architecture with fluid breakpoints for seamless viewing on mobile, tablet, and desktop.
* **Code Structure:** Modular, component-driven architecture using Svelte 5 (Runes) for optimized state management and reactive updates.

## System Architecture

The following diagram illustrates the ingestion, retrieval, and mini-view distribution pipelines designed for scale, utilizing CDN caching, Redis for hot-spot handling, and non-SQL storage for template JSON data.

## The Feature Pitch: Mini-View Embeddable Hubs

### What is the feature?

Mini-View is a lightweight, embeddable widget that allows users to place a live, interactive version of their Paw-Print profile directly onto external websites (blogs, portfolios, or business sites) via a simple script injection.

### Why Linktree needs it

Current link-in-bio platforms suffer from "click-away friction." Users must leave their primary destination to view links. Mini-View solves this by bringing the link hub to the content. It turns a static link into a portable, integrated digital identity, significantly increasing audience retention and providing a professional touchpoint for brands or influencers.

### How it was built

* **Component Structure:** The Mini-View is built as a self-contained Web Component. This ensures encapsulation and prevents style leakage from the host website's CSS.
* **Dynamic Resizing:** To ensure a native experience, the Mini-View uses `window.postMessage` to communicate its internal `scrollHeight` to the parent window, allowing the host container to dynamically resize and preventing layout issues.
* **State Management:** Utilizes Svelte's reactivity to fetch and update pet metadata in real-time, ensuring that edits made on the Paw-Print platform reflect immediately on all external embeds.
* **Tradeoffs:** To maintain performance, the initial load is lazy-loaded, ensuring the host site's Core Web Vitals remain unaffected.

### Production Scaling

At Linktree’s scale, Mini-View would require a robust edge-caching strategy. The data model for millions of users would rely on a CDN-backed JSON structure to ensure near-instant load times globally, as depicted in the system architecture above.

**Engineering Considerations:**

* **Performance:** All embed assets must be delivered via an optimized CDN, with strict bundle-size limits to ensure they do not slow down the host website.
* **Abuse Prevention:** We would implement strict Origin-Check headers and allow-lists to prevent unauthorized embedding of profiles. Rate-limiting would be enforced at the API gateway level to prevent DDoS attacks via high-traffic host sites.
* **Security (Sandboxing):** The embed is delivered with `sandbox="allow-scripts allow-forms"` attributes to isolate the widget from the parent page's DOM, mitigating XSS risks.
* **Rollout Strategy:** I would approach this via a canary release, starting with a subset of high-engagement power users. Success would be measured through "CTR" (Click-Through Rate) comparison between traditional links and embedded widgets, and latency monitoring on third-party host environments.

## Technical Stack

* **Framework:** Svelte 5
* **Styling:** CSS Modules / PostCSS
* **Hosting:** Vercel (Edge Functions)
* **Database/Cache:** Redis (for hot-spot handling) / Non-SQL Template JSON Storage
* **Build Tool:** Vite

## Setup Instructions

1. Clone the repository.
2. Run `npm install` to install dependencies.
3. Run `npm run dev` to start the development server.
4. Open `localhost:5173` to view the implementation.

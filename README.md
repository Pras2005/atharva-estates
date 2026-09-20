# Atharva Estates Portfolio Platform

A dynamic, front-end intensive portfolio platform for Atharva Estates, highlighting real estate, hospitality, and corporate leadership. It features a fully static multi-page architecture with a modern serverless backend for streamlined communication.

## Table of Contents
- [Architecture & Tech Stack](#architecture--tech-stack)
- [Key Features](#key-features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Usage / Running Locally](#usage--running-locally)

## Architecture & Tech Stack

- **Frontend:** Vanilla HTML, CSS, JavaScript (ES6+), optimized for quick load times and zero dependency overhead.
- **Backend / API:** Serverless function (`api/contact.mjs`) implementing `POST` email delivery.
- **Email Delivery:** Resend API integration.
- **Asset Management:** Dedicated local directories for raw binary assets, optimizing network requests for images and web fonts.

## Key Features

1. **Multi-Faceted Content Pages:** Displays extensive information via localized DOM manipulation in `scripts/`, driving pages like `hospitality.html`, `journey.html`, `leadership.html`.
2. **Serverless Contact Pipeline:** Includes a honeypot mechanism (`payload.company`) to trap bots quietly. Validates standard schemas for `Residential`, `Commercial`, and `General Enquiry` queries securely via edge functions.
3. **Resend API Integration:** Automates lead generation notifications seamlessly from client inputs to corporate emails via `https://api.resend.com/emails`.

## Project Structure

```text
atharva-estates/
├── api/
│   └── contact.mjs          # Serverless edge function handling Resend API integration
├── assets/                  # Centralized directories for Banners, Icons, Logos, etc.
├── FONTS/                   # Self-hosted typography (Juana, Helvetica Neue, Manrope)
├── scripts/                 # Page-specific ES6 scripts (e.g., home.js, contact.js)
├── styles/                  # Scoped stylesheets (e.g., common.css, leadership.css)
├── *.html                   # Core application views (index, contact, hospitality, etc.)
```

## Prerequisites

- **Node.js** (v18.x or newer) - For local dev server.
- **Resend API Key** - For testing the contact form pipeline locally.

## Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone git@github.com:Pras2005/atharva-estates.git
   cd atharva-estates
   ```

2. **Environment Variables:**
   Create a `.env` or `.env.local` file (depending on your serverless local emulator):
   ```env
   RESEND_API_KEY=your_resend_api_key_here
   CONTACT_FROM_EMAIL=no-reply@atharva-estates.com
   CONTACT_TO_EMAIL=leads@atharva-estates.com
   ```

## Usage / Running Locally

Since this project relies on static files + a serverless API, you can run the static assets using any basic HTTP server, but to test the API route, you should use a serverless CLI like Vercel:

1. **Install Vercel CLI (Optional but recommended):**
   ```bash
   npm i -g vercel
   ```

2. **Start the local emulator:**
   ```bash
   vercel dev
   ```
   *Alternatively, for just the frontend UI without the contact API functionality:*
   ```bash
   npx serve .
   ```

3. Open `http://localhost:3000` to browse the platform.

---
project: page-ui
stars: 1254
description: 📃 Landing page UI components for React & Next.js, built on top of TailwindCSS
url: https://github.com/danmindru/page-ui
---

Page UI 📃
==========

**Landing page components & templates that you can copy 📋 & paste 🍝**  
pageui.dev

A collection of **free templates**, components and examples to create beautiful, high-converting landing pages with React and Next.js. Open source & themeable with Tailwind CSS. Inspired by Shadcn UI.

Quick links:

-   📀 Installation
-   📄 Templates
-   👩‍💻 A ton of demos

Read more about Page UI.

🎨 Templates
------------

See all templates 👀  

💻 Installation (Next.js)
-------------------------

1️⃣ Start by creating a new Next.js app. You can use the following command:

npx create-next-app@latest my-app --typescript --tailwind --eslint

2️⃣ Run the Page UI CLI

npx @page-ui/wizard@latest init

3️⃣ Add the required dependencies to your Next.js app:

npm install @tailwindcss/forms @tailwindcss/typography tailwindcss-animate class-variance-authority clsx tailwind-merge lucide-react @radix-ui/react-accordion

4️⃣ Add the below to your `global.css` file.

**Show code ↕️**

@layer base {
  :root {
    \--hard-shadow: 0px 29px 52px 0px rgba(0, 0, 0, 0.4),
      22px 25px 16px 0px rgba(0, 0, 0, 0.2);
    \--hard-shadow-left: 0px 29px 52px 0px rgba(0, 0, 0, 0.4),
      \-22px 25px 16px 0px rgba(0, 0, 0, 0.2);
    /\* If you use Shadcn UI already, you should already have these variables defined \*/
    \--background: 0 0% 100%;
    \--foreground: 240 10% 3.9%;
    \--card: 0 0% 100%;
    \--card-foreground: 240 10% 3.9%;
    \--popover: 0 0% 100%;
    \--popover-foreground: 240 10% 3.9%;
    \--primary-foreground: 355.7 100% 97.3%;
    \--secondary: 240 4.8% 95.9%;
    \--secondary-foreground: 240 5.9% 10%;
    \--muted: 240 4.8% 95.9%;
    \--muted-foreground: 240 3.8% 46.1%;
    \--accent: 240 4.8% 95.9%;
    \--accent-foreground: 240 5.9% 10%;
    \--destructive: 0 84.2% 60.2%;
    \--destructive-foreground: 0 0% 98%;
    \--border: 240 5.9% 90%;
    \--input: 240 5.9% 90%;
    \--radius: 0.5rem;
  }

  .dark {
    /\* If you use Shadcn UI already, you can skip this block. \*/
    \--background: 20 14.3% 4.1%;
    \--foreground: 0 0% 95%;
    \--card: 24 9.8% 10%;
    \--card-foreground: 0 0% 95%;
    \--popover: 0 0% 9%;
    \--popover-foreground: 0 0% 95%;
    \--primary-foreground: 144.9 80.4% 10%;
    \--secondary: 240 3.7% 15.9%;
    \--secondary-foreground: 0 0% 98%;
    \--muted: 0 0% 15%;
    \--muted-foreground: 240 5% 64.9%;
    \--accent: 12 6.5% 15.1%;
    \--accent-foreground: 0 0% 98%;
    \--destructive: 0 62.8% 30.6%;
    \--destructive-foreground: 0 85.7% 97.3%;
    \--border: 240 3.7% 15.9%;
    \--input: 240 3.7% 15.9%;
  }

  \*,
  ::before,
  ::after {
    @apply border-gray-100 dark:border-neutral-800;
  }

  \* {
    @apply font-sans;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    @apply font-semibold font-display;
  }
}

@layer utilities {
  .text-balance {
    text-wrap: balance;
  }

  /\*\*
   \* Perspective (used for images etc.)
   \*/
  .perspective-none {
    transform: none;
  }

  .perspective-left {
    box-shadow: var(\--hard-shadow);
    transform: perspective(400em) rotateY(\-15deg) rotateX(6deg)
      skew(\-8deg, 4deg) translate3d(\-4%, \-2%, 0) scale(0.8);
  }

  .perspective-right {
    box-shadow: var(\--hard-shadow-left);
    transform: perspective(400em) rotateY(15deg) rotateX(6deg) skew(8deg, \-4deg)
      translate3d(4%, \-2%, 0) scale(0.8);
  }

  .perspective-bottom {
    box-shadow: var(\--hard-shadow);
    transform: translateY(\-4%) perspective(400em) rotateX(18deg) scale(0.9);
  }

  .perspective-bottom-lg {
    box-shadow: var(\--hard-shadow);
    transform: perspective(400em) translate3d(0, \-6%, 0) rotateX(34deg)
      scale(0.8);
  }

  .perspective-paper {
    box-shadow: var(\--hard-shadow);
    transform: rotateX(40deg) rotate(40deg) scale(0.8);
  }

  .perspective-paper-left {
    box-shadow: var(\--hard-shadow-left);
    transform: rotateX(40deg) rotate(\-40deg) scale(0.8);
  }

  /\*\*
   \* Custom shadows
   \*/
  .hard-shadow {
    box-shadow: var(\--hard-shadow);
  }

  .hard-shadow-left {
    box-shadow: var(\--hard-shadow-left);
  }

  /\*\*
   \* Container utilities
   \*/
  .container-narrow {
    @apply max-w-4xl;
  }

  .container-wide {
    @apply xl:max-w-6xl;
  }

  .container-ultrawide {
    @apply xl:max-w-7xl;
  }
}

  

For other frameworks, check out the installation guide.

> ✨ Skip the setup by bootstrapping your app with Shipixen.

🎨 Templates
------------

To copy and paste from the available templates, visit landing page templates.

💿 Demos
--------

To see the components in action, visit landing page component examples.

💪 Motivation
-------------

Designing and building landing pages that look good and convert well is hard business.  
Most UI libraries focus on application UI, so when you set up a starer or boilerplate you end up staring at a blank canvas.  
The time spent browsing through bloated templates, figuring out how to port them to your app and then customizing them is time you could spend on your product.

> Start from a blank canvas to create, start from Page UI to innovate.

📝 License
----------

Licensed under the MIT license

* * *

* * *

Save 10s of hours of work by using Shipixen to generate a customized codebases with your branding, pages and blog  
― then deploy it to Vercel with 1 click.

  
**Shipixen**  
Create a blog & landing page in minutes with **Shipixen**.  
Try the app on shipixen.com.

* * *

Apihustle is a collection of tools to test, improve and get to know your API inside and out.  
apihustle.com  

**Shipixen**

Create a personalized blog & landing page in minutes

shipixen.com

**Page UI**

Landing page UI components for React & Next.js

pageui.dev

**Clobbr**

Load test your API endpoints

clobbr.app

**Crontap**

Schedule API calls using cron syntax.

crontap.com

**CronTool**

Debug multiple cron expressions on a calendar.

tool.crontap.com

* * *

  
Page UI ❤️ Open Source

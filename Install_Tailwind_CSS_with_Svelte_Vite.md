# How to Install Tailwind CSS on Svelte with Vite

_Last Updated: July 07, 2024_

Tailwind CSS empowers rapid development of responsive user interfaces through its utility-first CSS framework. This guide walks you through integrating Tailwind CSS into your Svelte project using Vite as the build tool.

## Prerequisites

To begin, ensure you have Node.js and npm (Node Package Manager) installed on your system. You can verify their installation by running the following commands in your terminal:

Bash

```
node -v
npm -v

```

If these commands don't return versions, download and install Node.js from the official website ([https://nodejs.org/en](https://nodejs.org/en)) as it includes npm by default.

## Step 1: Setting Up Vite Project with Svelte Template

Let's create a new Svelte project using Vite's Svelte template. Open your terminal and execute:

Bash

```
npm init vite@latest my-svelte-tailwind-app --template svelte

```

This command generates a new project directory named `my-svelte-tailwind-app` with the necessary Svelte project structure.

## Step 2: Installing Dependencies

Navigate to your project directory using the following command:

Bash

```
cd my-svelte-tailwind-app

```

Now, install the required dependencies for Tailwind CSS functionality:

Bash

```
npm install tailwindcss postcss autoprefixer --save-dev

```

These packages enable Tailwind CSS usage, process styles with PostCSS, and ensure better browser compatibility through Autoprefixer integration.

## Step 3: Initializing Tailwind CSS Configuration

With Tailwind CSS installed, we need to initialize its configuration. Run the following command in your terminal:

Bash

```
npx tailwindcss init

```

This command creates a `tailwind.config.js` file at the project's root, which you can customize for specific needs.

## Step 4: Tailwind CSS Configuration (Optional)

Open the `tailwind.config.js` file for potential customization. The default configuration typically suffices for most projects initially.

## Step 5: Including Tailwind CSS Directives

Open the `src/app.css` file and replace its content with these Tailwind CSS directives:

CSS

```
@tailwind base;
@tailwind components;
@tailwind utilities;

```

These directives import all of Tailwind's utility classes, enabling their use within your Svelte components.

## Step 6: Importing app.css in src/main.js

To ensure styles are applied throughout your application, import `app.css` at the beginning of your `src/main.js` file:

JavaScript

```
import './app.css';

```

## Step 7: Running the Application

We're ready to see our Svelte app with Tailwind CSS in action! Start the development server using:

Bash

```
npm run dev

```

This command launches the development server, making your application accessible at `http://localhost:5173` in your web browser.

**Congratulations!** You've successfully integrated Tailwind CSS into your Svelte project with Vite. Leverage Tailwind's utility classes to efficiently style your Svelte components and create stunning user interfaces.

**Happy Coding!** 🎉

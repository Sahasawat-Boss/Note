# 🚀 Fix Tailwind IntelliSense Not Working in Vite + React for Tailwind V4.0

If Tailwind CSS IntelliSense is not working in your **Vite + React** project, follow these steps:
https://tailwindcss.com/docs/installation/using-vite

## 1. Manually Create `tailwind.config.js`
## 2. Use the Correct Configuration Based on Your Project
JavaScript (tailwind.config.js)
- If you are using JavaScript, paste the following inside tailwind.config.js:

```sh
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

TypeScript (tailwind.config.ts)
- If you are using TypeScript, create tailwind.config.ts and paste the following:

```sh
import type { Config } from 'tailwindcss'; 

const config: Config = { 
    content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"], 
    theme: { 
        extend: {}, 
    }, 
    plugins: [], 
}; 

export default config;
```

## 3. After making the changes, restart your development server
```sh
npm run dev
```
![image](https://github.com/user-attachments/assets/330f3327-a463-43d9-b3e9-6e9815160471)


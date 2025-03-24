## Default tailwind.config.js file for Next.js project

### For Project that is JS only and not support TS 

- If ``npx tailwindcss init -p`` not work
- Manual Create **tailwind.config.js** file
- And Copy this Default Config for tailwind.config.js


```sh
/** @type {import('tailwindcss').Config} */
const config = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
    "./app/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

module.exports = config;
```

So Tailwind CSS IntelliSense Work!!

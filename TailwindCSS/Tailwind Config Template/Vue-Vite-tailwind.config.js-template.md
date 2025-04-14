# 🚀 Fix Tailwind IntelliSense Not Working in Vite + Vue for Tailwind V4.0

If Tailwind CSS IntelliSense is not working in your **Vite + React** project, follow these steps:
https://tailwindcss.com/docs/installation/using-vite

## 1. Manually Create `tailwind.config.js`
## 2. Use the Correct Configuration Based on Your Project
JavaScript (tailwind.config.js)
- If you are using JavaScript, paste the following inside tailwind.config.js:

```sh
// tailwind.config.js
export default {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```


## 3. After making the changes, restart your development server
```sh
npm run dev
```
![image](https://github.com/user-attachments/assets/330f3327-a463-43d9-b3e9-6e9815160471)

-------------------
# New Update >> no need TW config
https://tailwindcss.com/docs/installation/using-vite

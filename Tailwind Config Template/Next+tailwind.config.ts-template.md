## Default tailwind.config.ts file for Next.js project

### Work on both TS and JS Project (If Project Support Both)

- If ``npx tailwindcss init -p`` not work
- Manual Create  tailwind.config.ts file
- And Copy this Default Config for tailwind.config.ts


```sh
import type { Config } from 'tailwindcss'

const config: Config = {
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

export default config
```

So Tailwind CSS IntelliSense Work!!

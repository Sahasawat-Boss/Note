# Tailwind Course

## Custom Property >> []
- text-[40px]

## Custom Breakpoint
https://tailwindcss.com/docs/responsive-design
```
@import "tailwindcss";

@theme {
  --breakpoint-xs: 30rem;
  --breakpoint-2xl: 100rem;
  --breakpoint-3xl: 120rem;
}
```

## Dark Mode
- dark: key word
```
@import "tailwindcss";
@custom-variant dark (&:where(.dark, .dark *));
```
## Theme Variables
Custom Theme Once
```
@import "tailwindcss";
@theme {
  --color-mint-500: oklch(0.72 0.11 178);
}
```

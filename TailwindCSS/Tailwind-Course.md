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
## Theme Custom Variables

Custom Theme Once
```
@import "tailwindcss";

@theme {
  --color-chestnut: #782f29;
  --color-mint: #4e7a5a;
}

```
# @layer
## @base/@component/@utilities

base
- apply style for all
- sample h1 p

component
- for reuse component like card

utilities
- Margin Padding Typography Color

--------
## @apply
- insert tailwind css to CSS

![image](https://github.com/user-attachments/assets/4c502c6a-9e11-4275-84c7-11479b76e203)

![image](https://github.com/user-attachments/assets/71bd7ee3-a5b5-4f57-aa8b-e91413c75ec6)

![image](https://github.com/user-attachments/assets/18db001d-2d50-49bd-9aed-5cec481058b1)





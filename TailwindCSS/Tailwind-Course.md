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


-----

# Tip and Trick
-  Special Util

## Accent
- class="accent-color-..."
![image](https://github.com/user-attachments/assets/cd5d0585-167b-43aa-b95c-7f323a8072b4)
```
<input type="checkbox" class="accent-pink-500" checked />
```
## Fluid Texts

no need >> class="sm:text-md md:text-lg"

use
```
<p class="text-[min(10vw, 70px)]">Fluid Text</p>
```
## specific font
## Selection
- เวลาคลุมดำ
![image](https://github.com/user-attachments/assets/f2d7fbf0-aac5-41f1-8ebc-494b26fbbef4)

![image](https://github.com/user-attachments/assets/7fd110a9-4a10-4912-ad71-adc13f93ca47)






















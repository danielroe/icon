![nuxt-icon](https://user-images.githubusercontent.com/904724/188514727-e252b825-be56-43bb-a044-5a97f9a3badc.png)

# Nuxt Icon

[![npm version][npm-version-src]][npm-version-href]
[![License][license-src]][license-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![Nuxt][nuxt-src]][nuxt-href]
<a href="https://volta.net/nuxt-modules/icon?utm_source=nuxt_icon_readme"><img src="https://user-images.githubusercontent.com/904724/209143798-32345f6c-3cf8-4e06-9659-f4ace4a6acde.svg" alt="Volta board"></a>

> Icon module for [Nuxt](https://v3.nuxtjs.org) with [100,000+ ready to use icons](https://icones.js.org) from Iconify.

- [✨ &nbsp;Release Notes](https://github.com/nuxt-modules/icon/releases)
- [🏀 &nbsp;Online playground](https://stackblitz.com/edit/nuxt-icon-playground?file=app.vue)

## Features ✨

- Nuxt 3 ready
- Support 100,000 open source vector icons via [Iconify](https://iconify.design)
- Emoji Support
- Custom SVG support (via Vue component)

## Setup ⛓️

Add `nuxt-icon` dependency to your project:

```bash
npm install --save-dev nuxt-icon

# Using yarn
yarn add --dev nuxt-icon
```

Add it to the `modules` array in your `nuxt.config.ts`:

```ts
import { defineNuxtConfig } from 'nuxt'

export default defineNuxtConfig({
  modules: ['nuxt-icon']
})
```

That's it, you can now use the `<Icon />` in your components!

✨ If you are using VS Code, you can use the [Iconify IntelliSense](https://marketplace.visualstudio.com/items?itemName=antfu.iconify) extension by [@antfu](https://github.com/antfu)

## Usage 👌

**Props:**
- `name` (required): icon name, emoji or global component name
- `size`: icon size (default: `1em`)

### Iconify dataset

You can use any name from the https://icones.js.org collection:

```html
<Icon name="uil:github" />
```

### Emoji

```html
<Icon name="🚀" />
```

### Vue component

```html
<Icon name="NuxtIcon" />
```

Note that `NuxtIcon` needs to be inside `components/global/` folder (see [example](./playground/components/global/NuxtIcon.vue)).

## Configuration ⚙️

To update the default size (`1em`) of the `<Icon />`, create an `app.config.ts` with the `nuxtIcon.size` property.

Update the default class (`.icon`) of the `<Icon />` with the `nuxtIcon.class` property, for a headless Icon, simply set `nuxtIcon.class: ''`.

You can also define aliases to make swapping out icons easier by leveraging the `nuxtIcon.aliases` property.

```ts
// app.config.ts
export default defineAppConfig({
  nuxtIcon: {
    size: '24px', // default <Icon> size applied
    class: 'icon', // default <Icon> class applied
    aliases: {
      'nuxt': 'logos:nuxt-icon',
    }
  }
})
```

The icons will have the default size of `24px` and the `nuxt` icon will be available:

```html
<Icon name="nuxt" />
```

## Render Function

You can use the `Icon` component in a render function (useful if you create a functional component), for this you can import it from `#components`:

```ts
import { Icon } from '#components'
```

See an example of a `<MyIcon>` component:

```vue
<script setup>
import { Icon } from '#components'

const MyIcon = h(Icon, { name: 'uil:twitter' })
</script>

<template>
  <p><MyIcon /></p>
</template>
```

## CSS Icons

This is currently experimental and may change in the future, this is a way to use CSS icons instead of SVG icons to reduce the DOM size and improve performance. It is leveraging the Mask combined with background color set to `currentColor`, useful to render monotone icons that use `currentColor` as icon color. Learn more on https://docs.iconify.design/icon-components/css.html

```vue
<template>
  <IconCSS name="uil:twitter" />
</template>
```

You can use aliases in `<IconCSS>` as well.

Note that CSS Masks have limited support, see https://caniuse.com/css-masks for more information.

Also, the icons won't be loaded on initial load and an HTTP request will be made to Iconify CDN to load them.


## Contributing 🙏

1. Clone this repository
2. Install dependencies using `pnpm install` (install `pnpm` with `corepack enable`, [learn more](https://pnpm.io/installation#using-corepack))
3. Run `npm run dev:prepare` to generate type stubs.
4. Use `npm run dev` to start [playground](./playground) in development mode.

## Credits 💌

- [@benjamincanac](https://github.com/benjamincanac) for the initial version
- [@cyberalien](https://github.com/cyberalien) for making [Iconify](https://github.com/iconify/iconify)

## License 📎

[MIT License](./LICENSE)

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/nuxt-icon/latest.svg?style=flat&colorA=18181B&colorB=28CF8D
[npm-version-href]: https://npmjs.com/package/nuxt-icon

[npm-downloads-src]: https://img.shields.io/npm/dt/nuxt-icon.svg?style=flat&colorA=18181B&colorB=28CF8D
[npm-downloads-href]: https://npmjs.com/package/nuxt-icon

[license-src]: https://img.shields.io/github/license/nuxt-modules/icon.svg?style=flat&colorA=18181B&colorB=28CF8D
[license-href]: https://github.com/nuxt-modules/icon/blob/main/LICENSE

[nuxt-src]: https://img.shields.io/badge/Nuxt-18181B?&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAD0AAAAoCAYAAABNefLBAAAAAXNSR0IArs4c6QAAA91JREFUaEPNWdtV20AQvSsVEDoIPoh8QwWBDkwFkApiCrCQ5QICFcSpIKQCoAL4DuJgOoAC2M0Zy8Y23pl9SEqyv9rH3J2rO3d3Fdpuv4s9JMkZgP586glSPUKvmLa9VOx8Knagddz9+ADKXFm+PSPV+/8L8PZAPxZbeE1uAWwzG3mNLD9sdZMjJ2sP9P2ogFJEa6GpI2TDy8hYWxvWDujHYhuvyaNHVNM5zZ89+nbWpR3QVUn/8YFXlMaMsHtWePXtqFNz0NW4D5ifQfGluuclarUwfgWwBWAKrS/wqbgLWsvSuRlot3hx8blFrSq/AzixTPAFWT5pArwZaFm8nuYZ+mAPUBA1mT2Ny188aJd4GXUI6ANB0e2i5sceN1OkGhJNE1m8fiHLa0dWleTEPlrXsYmaV+kDQJu6O7yOiT8u0y7xWhUq3qVRvOtUdbFnHeEUWd77i6BLqsl252XLXlVSRj4zAV4iy4/mrPAvfTQgsvyFZ9olXqneQ69YNx+uDM7+f4Dx7VIyo0QtDHQdPPlrqpu2CsjbTHmzFicwzre/AGCqAJZM8eR6GOiqJBOyODK+X+IGWc67slqVyVjYRY0P+Ala95HMNtveAkXNH7QsSICPy3IJoMQeF1MCRM0fdBUoXlxWZFHj2eNiSoCo+YGOES8OtEvUVse9Z09LTs0Nuol4ccB9DAiXOd/y18iRNREvPtsuUXuCrfTRfPUdXCNRkzPdhnjZgDdlTzU6BxQdOTebUnfYGe5L1UsG/TC+hTF7TJ24QHY28CyN692asqcWNart9tqtcIqd/JyLjQf9UA5g8I0Z+IJUb284L58daIs9VUlnbTpz2xo5NbqosF5L2UHXO0n+mnFeiD/It1X6CKooauoHsqHtEgJ20NV4AphjZhdl5yVlW1btcPZEitomaBf9tN6Puqfqij0RorYJujPx6og9EaK2DvpfiVcsexa/UqCoLUF3RT+aV6dXnZS+Vf0IELUl6K7Ei7/KpZDDxYu1tuzjYT1i5fhZg+5KvGTAtHJ86bOBlxP3doNagxZvNvl6x1ananQMlQx4Ss9Gxpc+bmGXqM03WUEWAYC8rDEhD24+b1pEa7pLsz/U1zFxPsHl+8g2c6Zq5tQUxBLlmj/6O09rt6BGLzobqHBKmTbNZgkeLf/H8n8ZvNjGAGNGBJp/gWi+xOoMdKM5EB/fXLayjXhmmfa5xWi+2A1SfeJ8ng15546LaaYlc/UWLWLc9FSDoS5hMPF6c3IJamwUy3EvMKpPsSzNCVFLKe5O239JpaYwauoFdHVWssDacKrrv76tZ6KekejJ4nz9B5NWGK+XC+AAAAAAAElFTkSuQmCC
[nuxt-href]: https://nuxt.com

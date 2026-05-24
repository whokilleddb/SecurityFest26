---
# try also 'default' to start simple
theme: default

# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
#background: ./imgs/background.png
# some information about your slides (markdown enabled)
title: From Code to Compromise
info: |
  ## Security Fest 2026 slides
  From Code to Compromise

# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade-out
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
# duration of the presentation
duration: 45min

fonts:
  sans: 'Fira Mono'
  serif: 'Fira Mono'
  mono: 'Fira Mono'
---

# From Code to Compromise: Turning IDEs into attack vectors
#### _DB (@whokilleddb)_

_Black Hills Information Security_

<img src="https://i.ytimg.com/vi/u0lzyDeU90Q/maxresdefault.jpg" class="absolute bottom-4 right-4 w-48" />

<!--
You guys are not supposed to see this - if you are, then I have seriously messed up the presentation part
-->

---
transition: fade-out
layout: two-cols
class: text-left
---

# @whoami

**DB (@whokilleddb)**

**Work Experience**

- Maldev @ BHIS
- Consultant @ Certus Cyber
- Researcher @ Payatu

**Socials**

<div class="flex gap-3 mt-2">
  <a href="https://x.com/whokilleddb"><img src="./imgs/x.png" class="w-10 h-10object-contain" /></a>
  <a href="https://www.linkedin.com/in/whokilleddb/"><img src="./imgs/linkedin.png" class="w-10 h-10object-contain" /></a>
  <a href="https://github.com/whokilleddb/"><img src="./imgs/github.png" class="w-10 h-10object-contain" /></a>
</div>

<br />

<div class="flex items-center gap-8">Cat Dad <img src="./imgs/car.jpg" class="w-30 h-30 object-contain" /></div>

::right::

**Off work DB**

<div class="grid grid-cols-2 gap-2 mt-2 mb-4">
  <img src="https://m.media-amazon.com/images/I/81zqVhvbHbL._SL1500_.jpg" class="w-full h-24 object-cover object-top rounded" />
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRnwpUzx-HpdEborrNpBJC8swy1u2TpvNqeew&s" class="w-full h-24 object-cover object-top rounded" />
  <img src="https://images.seeklogo.com/logo-png/33/1/anthony-bourdain-parts-unknown-logo-png_seeklogo-332957.png" class="w-full h-24 object-cover object-top rounded" />
  <img src="https://gaming-cdn.com/images/products/5661/orig/disco-elysium-pc-spel-gog-com-cover.jpg?v=1701269736" class="w-full h-24 object-cover object-top rounded" />
  <img src="https://assetsio.gnwcdn.com/cowboy-bebop-anime-characters.png?width=690&quality=85&format=jpg&dpr=3&auto=webp" class="w-full h-24 object-cover object-top rounded" />
  <img src="https://www.nintendo.com/eu/media/images/assets/nintendo_switch_2_games/eldenringtarnishededition/2x1_NSwitch2_EldenRing.jpg" class="w-full h-24 object-cover object-top rounded" />
</div>

<img src="https://i.ytimg.com/vi/u0lzyDeU90Q/maxresdefault.jpg" class="absolute bottom-4 right-4 w-48" />

<!--
You still should not be able to see this
-->

---
transition: fade-out
class: text-left
title: Spot the difference #1
---

### Spot the difference #1

**Windsurf**

<div class="flex flex-col gap-2 mt-2">
  <img src="./imgs/banter0.png" class="w-full max-h-72 object-contain object-left" />
  <img src="./imgs/banter1.png" class="w-full max-h-72 object-contain object-left" />
</div>

---
transition: fade-out
class: text-left
title: Spot the difference #2
---

### Spot the difference #2

**VSCode**

<div class="flex flex-col gap-2 mt-2">
  <img src="./imgs/banter2.png" class="w-full max-h-72 object-contain object-left" />
  <img src="./imgs/banter3.png" class="w-full max-h-72 object-contain object-left" />
</div>

---
layout: image-right
image: https://www.freecodecamp.org/news/content/images/size/w2000/2021/08/vscode.png
---

# VSCode

_"World's most popular IDE"_

<div class="text-sm">

- Built using **ELECTRON**

```json [package.json]
{
  "electron": "39.8.8",
}
```
- Has a dedicated market place
- Supports **EXTENSIONS** from multiple sources

- It separates different functionality into different processes 

```js [abstractExtensionService.ts] 
private _startExtensionHostsIfNecessary(isInitialStart: boolean, initialActivationEvents: string[])
```

</div>

---
layout: image-right
image: https://www.freecodecamp.org/news/content/images/size/w2000/2021/08/vscode.png
---

# Why target VSCode?

<div class="text-base">

- Developers often have sensitive secrets: API keys, saved logins, private keys, etc - making them a prime target.
- Cross platform - can make payloads for windows, mac and linux.
- Payloads are run by Code.exe (on Windows) - a Microsoft signed binary.
- <span class="text-red-500">*</span>Comparatively lesser known attack vector and EDR blindspot 
 
_<span class="text-red-500">*</span>I wrote this line two years ago, not quite sure of it now_
</div>

---
transition: fade-out
layout: image-right
image: https://exafunction.github.io/public/brand/windsurf-white-symbol.png
title: Rise of AI powered IDEs
---

# Rise of AI powered IDEs

<br/>

- 2024-2025 saw the rise of AI powered IDEs
- We Cursor, Windsurf and a bunch of IDEs
- \**Looks inside\** - Based out of VSCode
- So, they are vulnerable to the same attacks

---
layout: center
transition: fade-out
---

<img src="./imgs/uncben.png" class="w-full max-h-100 object-contain" />

---
transition: fade-out
layout: image-right
image: https://avatars.githubusercontent.com/u/61870837?v=4
---

# OpenVSX 

An Eclipse open-source project and alternative to the Visual Studio Marketplace

Due to legal nuances, alternative code editors built on the open-source VS Code project are barred from accessing the official Microsoft Visual Studio Marketplace 

This led to OpenVSX becoming really popular as an alternate extension store. However, it is not as extensively monitored as the VSCode Marketplace. It is very easy to spoof extensions, hijack search rankings, fake reviews - all of which has led to multiple security incidents over the last year.

---
transition: fade-out
---

# The extension file format: VSIX

<div class="text-sm" >

A `.vsix` file is a ZIP archive using the Open Packaging Conventions (OPC) format.

```{1|2|3-7}
[Content_Types].xml          ← OPC MIME type mappings
extension.vsixmanifest       ← VSCode metadata (XML)
extension/
├── package.json
├── out/
├── node_modules/
└── README.md
```

(Unzipped) VSIX Files are stored in `~/.vscode/extensions`. Each installed extension gets its own versioned subdirectory:

```{1|2|3-5}
~/.vscode/extensions/
├── extensions.json 
├── ms-python.python-2024.1.0/
├── esbenp.prettier-vscode-10.4.0/
└── attacker.malicious-ext-1.0.0/
```

The `extensions.json` file is our next target.  It is the extension profile manifest for the default user profile. VS Code uses it to track which extensions are installed — their identity, version, disk location, and metadata. 
</div>

---
transition: fade-out
layout: image-right
image: https://i.imgflip.com/askwvd.jpg
---

# Attacks in the Wild

- Solidity Extension Bonanza: _An extension which stole $500K_
- Malicious Corgi: _AI assisted coding agent which exfils data to China_
- TeamPCP github breach: _Because life hates me_
- Glassworm campaigns: _They stole my idea_ 

---
transition: fade-out
layout: two-cols
---

# Solidity Extension Bonanza

First, we have a legit extension:

- Legitimate extension from a verified publisher
- Has been around for 10 years on VSCode Marketplace and 5 years on OpenVSX
- Provides Syntax Highlighting, compilation features, etc
- 10.1M downloads, 1.78M installs

<div class="text-xs">

_Attackers love it - a lot._ 

_Here's a drinking game idea:_

_Take a shot everytime you see a malicious extension trying to impersonate this one_

</div>

::right::

<img src="./imgs/juanb.png" class="w-full max-h-50 object-cover object-left">
<img src="./imgs/solidity1.png" class="w-full max-h-50 object-cover object-left">
<img src="./imgs/solidity0.png" class="w-full max-h-50 object-cover object-left">

---
transition: fade-out
layout: two-cols
---

Extensions flagged by [SecureAnnex](https://secureannex.com/blog/sleepyduck-malware/) impersonating the legit Solidity extension:

<div class="text-xs">

|ID|Date|
|---|---|
|solidityai.solidity|2025-07-02|
|soliditysupport.solid|2025-07-02|
|juanbianco.solibidity|2025-07-08|
|ethereum.solidity-ethereum|2025-08-12|
|ethfoundry.solidityethereum|2025-08-12|
|juan-blanco.solidity|2025-08-13|
|nomicfdn.hardhat-solidity|2025-08-13|
|solidityai.solid|2025-08-15|
|chaindevtools.solidity-pro|2025-08-18|
|nomic-foundation.hardhat-solidity|2025-08-21|
|nomic-fdn.hardhat-solidity|2025-08-22|
|juan-blanco.vscode-solidity|2025-09-05|

</div>

::right::

<div class="text-xs mt-9">

|ID|Date|
|---|---|
|juanfblanco.solidity-ethereum-vsc|2025-09-05|
|kineticsquid.solidity-ethereum-vsc|2025-09-05|
|nomic-fdn.solidity-hardhat|2025-09-05|
|solidity-syntax.solidity-lang|2025-09-12|
|juanblonco.solidity|2025-09-14|
|soldevdesigne.pythonweb|2025-09-14|
|ethereum.solidity|2025-09-29|
|nethereum.solidity|2025-09-29|
|juanbianco.solidity-lang|2025-10-30|
|juanrblanco.solidity-lang|2025-10-30|
|juan-bianco.solidity-vlang|2025-10-31|

</div>


---
transition: fade-out
layout: center
---

<br />
<img src="./imgs/malicioussolidity.png">
<br />
<div class="text-center"><em>Extension which stole $500K from a Russian Crypto Dev</em></div>

<div class="absolute bottom-4 right-4 text-xs opacity-60"><a href="https://www.kaspersky.com/about/press-releases/kaspersky-uncovers-500k-crypto-heist-through-malicious-packages-targeting-cursor-developers">Source: Kaspersky GReAT Blog</a></div>

---
transition: fade-out
layout: image-right
image: https://content.kaspersky-labs.com/fm/press-releases/85/85d34dbd312fa53e3f41c0a5fc72d585/processed/search-results-for-the-query-solidity-q93.png
---


# Solidity Extension Bonanza
<br/>

- Attackers manipulated SEO to make the fake extension appear before the legit one

- At a glance, you might notice some differences - but remember that a user sees this in the Cursor UI - which makes it difficult to distinguish between the two.

<div class="absolute bottom-4 left-4 text-xs opacity-60"><a href="https://www.kaspersky.com/about/press-releases/kaspersky-uncovers-500k-crypto-heist-through-malicious-packages-targeting-cursor-developers">Source: Kaspersky GReAT Blog</a></div>

---
transition: fade-out
layout: center
---


# Taking a look at the code


---
transition: fade-out
layout: center
---

<div class="relative inline-block">
  <img src="./imgs/soliditysc.png" />
  <img src="https://i.redd.it/fwrxevbe9d2h1.jpeg" class="absolute inset-0 m-auto w-50 h-auto" />
</div>

---
transition: fade-out
layout: center
---

<div class="relative inline-block">
  <img src="./imgs/soliditysczoom.png" class="max-h-100" />
  <div class="absolute border-3 border-red-500" style="top: 30%; left: 10.2%; width: 17%; height: 21%;" />
  <div class="absolute border-3 border-red-500" style="top: 30%; left: 80%; width: 21%; height: 23%;" />
  <div class="absolute border-3 border-red-500" style="top: 49%; left: 4.9%; width: 10%; height: 20%;" />
</div>

---
level: 2
---

# Shiki Magic Move

Powered by [shiki-magic-move](https://shiki-magic-move.netlify.app/), Slidev supports animations across multiple code snippets.

Add multiple code blocks and wrap them with <code>````md magic-move</code> (four backticks) to enable the magic move. For example:

````md magic-move {lines: true}
```ts {*|2|*}
// step 1
const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})
```

```ts {*|1-2|3-4|3-4,8}
// step 2
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  }
}
```

```ts
// step 3
export default {
  data: () => ({
    author: {
      name: 'John Doe',
      books: [
        'Vue 2 - Advanced Guide',
        'Vue 3 - Basic Guide',
        'Vue 4 - The Mystery'
      ]
    }
  })
}
```

Non-code blocks are ignored.

```vue
<!-- step 4 -->
<script setup>
const author = {
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
}
</script>
```
````

---

# Components

<div grid="~ cols-2 gap-4">
<div>

You can use Vue components directly inside your slides.

We have provided a few built-in components like `<Tweet/>`, `<BlueSky/>`, and `<Youtube/>` that you can use directly. And adding your custom components is also super easy.

```html
<Counter :count="10" />
```

<!-- ./components/Counter.vue -->
<Counter :count="10" m="t-4" />

Check out [the guides](https://sli.dev/builtin/components.html) for more.

</div>
<div>

```html
<Tweet id="1390115482657726468" />
```

<Tweet id="1390115482657726468" scale="0.65" />

</div>
</div>

<!--
Presenter note with **bold**, *italic*, and ~~striked~~ text.

Also, HTML elements are valid:
<div class="flex w-full">
  <span style="flex-grow: 1;">Left content</span>
  <span>Right content</span>
</div>
-->

---
class: px-20
---

# Themes

Slidev comes with powerful theming support. Themes can provide styles, layouts, components, or even configurations for tools. Switching between themes by just **one edit** in your frontmatter:

<div grid="~ cols-2 gap-2" m="t-2">

```yaml
---
theme: default
---
```

```yaml
---
theme: seriph
---
```

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true" alt="">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-seriph/01.png?raw=true" alt="">

</div>

Read more about [How to use a theme](https://sli.dev/guide/theme-addon#use-theme) and
check out the [Awesome Themes Gallery](https://sli.dev/resources/theme-gallery).

---

# Clicks Animations

You can add `v-click` to elements to add a click animation.

<div v-click>

This shows up when you press <kbd>space</kbd> or <kbd>right</kbd>, or click outside the slide on the right.

```html
<div v-click>This shows up when you trigger a click animation.</div>
```

</div>

<p v-click>
You can also add modifiers to change the animation:
</p>

<div class="grid gap-3 mt-4 text-sm" style="grid-template-columns: repeat(3, 1fr) 1.5fr 1fr">
  <div v-after.up class="p-3 rounded border border-primary/20 bg-primary/10">
    <div class="font-mono text-xs opacity-60 mb-1">v-click.up</div>
    <div>Slide from bottom</div>
  </div>
  <div v-click.fade-in class="p-3 rounded border border-primary/30 bg-primary/15">
    <div class="font-mono text-xs opacity-60 mb-1">v-click.fade-in</div>
    <div>Fade in</div>
  </div>
  <div v-click.fade class="p-3 rounded border border-primary/40 bg-primary/20">
    <div class="font-mono text-xs opacity-60 mb-1">v-click.fade</div>
    <div>Dim (0.5 opacity)</div>
  </div>
  <div v-click.fade.right.scale class="p-3 rounded border border-primary/50 bg-primary/25">
    <div class="font-mono text-xs opacity-60 mb-1">v-click.fade.right.scale</div>
    <div>Composed</div>
  </div>
  <div v-click.none class="p-3 rounded border border-primary/60 bg-primary/30">
    <div class="font-mono text-xs opacity-60 mb-1">v-click.none</div>
    <div>No transition</div>
  </div>
</div>

<v-click>

The <span v-mark.red="7"><code>v-mark</code> directive</span>
also allows you to add
<span v-mark.circle.orange="8">inline marks</span>
, powered by [Rough Notation](https://roughnotation.com/):

```html
<span v-mark.underline.orange>inline markers</span>
```

</v-click>

<div v-click mt-12>

[Learn more](https://sli.dev/guide/animations#click-animation)

</div>

---

# Motions

Motion animations are powered by [@vueuse/motion](https://motion.vueuse.org/), triggered by `v-motion` directive.

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }"
  :click-3="{ x: 80 }"
  :leave="{ x: 1000 }"
>
  Slidev
</div>
```

<div class="w-60 relative">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-square.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-circle.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-triangle.png"
      alt=""
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 30, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn more](https://sli.dev/guide/animations.html#motion)

</div>

---

# $\LaTeX$

$\LaTeX$ is supported out-of-box. Powered by [$\KaTeX$](https://katex.org/).

<div h-3 />

Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$ {1|3|all}
\begin{aligned}
\nabla \cdot \vec{E} &= \frac{\rho}{\varepsilon_0} \\
\nabla \cdot \vec{B} &= 0 \\
\nabla \times \vec{E} &= -\frac{\partial\vec{B}}{\partial t} \\
\nabla \times \vec{B} &= \mu_0\vec{J} + \mu_0\varepsilon_0\frac{\partial\vec{E}}{\partial t}
\end{aligned}
$$

[Learn more](https://sli.dev/features/latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-4 gap-5 pt-4 -mb-6">

```mermaid {scale: 0.5, alt: 'A simple sequence diagram'}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectiveness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

```plantuml {scale: 0.7}
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}

database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}

[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```

</div>

Learn more: [Mermaid Diagrams](https://sli.dev/features/mermaid) and [PlantUML Diagrams](https://sli.dev/features/plantuml)

---
foo: bar
dragPos:
  square: 691,32,167,_,-16
---

# Draggable Elements

Double-click on the draggable elements to edit their positions.

<br>

###### Directive Usage

```md
<img v-drag="'square'" src="https://sli.dev/logo.png">
```

<br>

###### Component Usage

```md
<v-drag text-3xl>
  <div class="i-carbon:arrow-up" />
  Use the `v-drag` component to have a draggable container!
</v-drag>
```

<v-drag pos="663,206,261,_,-15">
  <div text-center text-3xl border border-main rounded>
    Double-click me!
  </div>
</v-drag>

<img v-drag="'square'" src="https://sli.dev/logo.png">

###### Draggable Arrow

```md
<v-drag-arrow two-way />
```

<v-drag-arrow pos="67,452,253,46" two-way op70 />

---
src: ./pages/imported-slides.md
hide: false
---

---

# Monaco Editor

Slidev provides built-in Monaco Editor support.

Add `{monaco}` to the code block to turn it into an editor:

```ts {monaco}
import { ref } from 'vue'
import { emptyArray } from './external'

const arr = ref(emptyArray(10))
```

Use `{monaco-run}` to create an editor that can execute the code directly in the slide:

```ts {monaco-run}
import { version } from 'vue'
import { emptyArray, sayHello } from './external'

sayHello()
console.log(`vue ${version}`)
console.log(emptyArray<number>(10).reduce(fib => [...fib, fib.at(-1)! + fib.at(-2)!], [1, 1]))
```

---
layout: center
class: text-center
---

# Learn More

[Documentation](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/resources/showcases)

<PoweredBySlidev mt-10 />

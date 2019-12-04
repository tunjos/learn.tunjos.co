---
layout: page
title: Install Tailwind
permalink: /tailwind/install/
---

{% include_relative /menu_tailwind.md install_tailwind="active" %}

## Install Tailwind

- [Installation - TailwindCSS](https://tailwindcss.com/docs/installation/){:target="_blank"}

___

### Installation

[1. Install Tailwind via npm]  
(Using npm)  
`npm install tailwindcss`

(Using Yarn)  
`yarn add tailwindcss`  

[2. Add Tailwind to your CSS]  
Use the **@tailwind** directive to inject Tailwind's **base**, **components**, and **utilities** styles into your CSS:  
Create **tailwind.css** or similarly named file and add the following:

```
@tailwind base;

@tailwind components;

@tailwind utilities;
```

(Tailwind will swap these directives out at build time with all of its generated CSS.)


[3. Create your Tailwind config file (optional)]  
`npx tailwind init`  

This will create a minimal **tailwind.config.js** file at the root of your project:

```
// tailwind.config.js
module.exports = {
  theme: {},
  variants: {},
  plugins: [],
}
```

[4. Process your CSS with Tailwind]  
[Using Tailwind CLI]  
For simple projects or just giving Tailwind a spin, you can use the Tailwind CLI tool to process your CSS:  
`npx tailwind build styles.css -o output.css`

Use the `npx tailwind help build` command to learn more about the various CLI options.


[Using Tailwind with PostCSS]  
For most projects, you'll want to add Tailwind as a PostCSS plugin in your build chain.
Generally this means adding Tailwind as a plugin in your **postcss.config.js** file:  

```
module.exports = {
  plugins: [
    // ...
    require('tailwindcss'),
    require('autoprefixer'),
    // ...
  ]
}
```

---
author: Zach Jensz
pubDatetime: 2023-06-27T11:00:00Z
title: Professional blog for $0 in 10 minutes beginner tutorial
postSlug: how-to-start-a-blog
featured: true
tags:
  - blog
  - webdev
  - guide
description: Setup a static generated blog with astro using the paper theme and deploy to cloudflare pages
---

## 1. Clone the _astro-paper_ theme.

If you have GitHub's CLI installed:

`gh repo clone satnaing/astro-paper`

If you have git installed:

`git clone https://github.com/satnaing/astro-paper.git`

Or download and extract the ZIP file:

`https://github.com/satnaing/astro-paper/archive/refs/heads/main.zip`

## 2. Install dependencies with [npm](https://nodejs.org/en/download)

Open the astro-paper folder in the terminal and run:

`npm i`

## 3. Run locally

`npm run start`

Click http://localhost:3000/ here or the link in the terminal to view the site during development.

## 4. Swap out all the details for your own

Make sure the dev page you have up reflects the changes as you go!

### 4.1 `src/content/blog` - stores all your blog posts.

Move all the example pages somewhere else and use them as a guide to write your own<br>
Add a basic page of your own now as you need at least one page here.

`1_first-page.md`

```md
---
author: Yoda
pubDatetime: 0000-00-00T00:00:00Z
title: A title is this
postSlug: a-title-is-this
featured: true
tags:
  - yoda
description: Description
---

## Page my first
```

### 4.2 Fill `src/config.ts` with global site info

### 4.3 Edit `src/pages/about.md` to be about you

### 4.4 Edit `src/pages/index.astro` as your homepage

## 5. Sign up for Cloudflare

https://dash.cloudflare.com/sign-up

## 6. Setup wrangler

Install Cloudflare's Wrangler CLI:

`npm i wrangler`

Link wrangler with the account you created:

`wrangler login`

## 7. Build and deploy

Turn all your code into static files:

`npm run build`

Send those static files to Cloudflare:

`npx wrangler pages deploy dist`

## 8. Done!

View and manage your site: Cloudflare Dashboard > Workers & Pages > Yoursite<br>
View your site live: [yoursitesname].pages.dev

From here you can keep adding blog articles inside of `src/content/blog` as simple markdown `.md` files.

I wrote a custom script in `package.json` for deploying to cloudflare:

```js
//
"scripts": {
    //
    "deploy": "npx wrangler pages deploy dist",
    //
}
//
```

Every time you want to redeploy just run `npm run build`, then double check the build with `npm run preview` unless you live life on the edge, and finally `npm run deploy`.

## 8. Bonus step - How to add a custom domain

Get your own domain i.e. mypersonalsite.com<br>
This optional step costs around ten dollars usually depending on your country. You can register a domain with any domain registrar but I suggest using cloudflare as they're cheap and you will want to use their nameservers anyway, which would add extra steps if you register elsewhere.

[Register a domain with cloudflare](https://www.cloudflare.com/products/registrar/)

On the _Cloudflare pages_ site you have setup in your Cloudflare dashboard, navigate to the _Custom Domains_ tab. Click _Set up a custom domain_, type in the domain you purchased and accept all the defaults. It might take a few minutes for the custom domain to point to your site.

## Bonus info - How does it work?

We essentially setup SSG with a CDN. But what does that even mean 🤔

CDN stands for Content Delivery Network. Think of it as an internet shipping company that has computer warehouses all over the planet that deliver our website to people. This is what Cloudflare does for us.

SSG stands for Static Site Generation. If our site were a cake, we baked it on our computer rather than something like sending the recipe to the warehouse which would be reffered to as SSR (Server Side Rendering). It's cheaper and easier this way for small cakes (websites) like our blog.

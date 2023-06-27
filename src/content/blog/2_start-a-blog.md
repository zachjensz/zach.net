---
author: Zach Jensz
pubDatetime: 2023-06-27T11:00:00Z
title: Start your own blog like mine in 10 minutes!
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

Open the astro theme folder and run the following command:

`npm i`

If you're on Windows, open the astro theme folder and:<br>
Go to the navigation bar (below the "Home Share View" tabs at the top of the window, and above the "Name Date modified" fields).<br>
Type in cmd and hit ENTER to open the command prompt in the folder you have open.<br>
Now you can run the command above in the terminal that opens!

## 3. Run locally

`npm run dev`

Click http://localhost:3000/ or similar in the terminal. You should see a working example blog site.

## 4. Swap out all the details for your own

Make sure the dev page you have up reflects the changes.

Move everything in `src/content/blog` somewhere else and use as a guide for your own pages.<br>
Edit `src/config.ts`, `src/pages/about.md` and `src/pages/index.astro` with your details, link the socials you want.<br>

## 5. Sign up for Cloudflare

https://dash.cloudflare.com/sign-up

## 6. Setup wrangler

Install Cloudflare's Wrangler CLI:

`npm i -g wrangler`

Login with the account you created:

`wrangler login`

## 7. Build and deploy

Turn all your code into static files:

`npm run build`

Send those static files to Cloudflare:

`npx wrangler pages deploy dist`

## 8. Done!

You can view and manage your site in the Cloudflare Dashboard > Workers & Pages > Yoursite<br>
You should be able to go to [yoursitesname].pages.dev and view your site live.<br>
Every time you want to deploy again just run steps 7 and 8 again. I wrote a custom script in `package.json`:

```js
//
"scripts": {
    //
    "deploy": "npx wrangler pages deploy dist",
    //
}
//
```

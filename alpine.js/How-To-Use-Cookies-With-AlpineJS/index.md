How to Use Cookies With AlpineJS
================================

Inspired by [TailwindUI's](https://tailwindui.com/) mentions I've started looking into [AlpineJS](https://github.com/alpinejs/alpine). It's minimalistic, comes without any long preparation steps directly as a CDN link in your header and, similar to [TailwindCSS](https://tailwindcss.com/), just gets added to your HTML tags.

As I liked what I saw, I've made the call to use it for the website of my new project [PageExplorer](https://pageexplorer.net). For context, PageExplorer a [browser extension](https://browserextension.dev) to analyse your Google Search ranks with the goal to grow your search traffic. As part of the website, I'd like to highlight new features and promotions. TailwindUI comes with handy banners for this purpose:

![](https://lh6.googleusercontent.com/Lt5IQyKyrUw9S4aLPIqDk7xttGN8Qwlz_dxozbjfhcmPRacUMfS2Wp_PtS8o2OMGPQkkagHEyZ86p1jNEbfP6yKjf3WJAb-Uv4EW00404z7LENsxFEBCafYA4esBJJjfDIS8lmBv)

To hide the banner on closing, I've opted for a simple cookie 🍪️ During my research I stumbled on this article on how to work with [cookies in VanillaJS](https://gomakethings.com/working-with-cookies-in-vanilla-js/). It mentioned [cookies.js](https://github.com/madmurphy/cookies.js) to manage the cookies. You can either:

- add a CDN link to the [minified version](https://github.com/madmurphy/cookies.js/blob/master/cookies.min.js) or,
- install it using yarn/npm (```yarn add --dev  madmurphy/cookies.js```), or
- simply add the minified version in your application JavaScript (not recommended).

All lead to the same result. After the installation, you can use it as described in the docs. For my Alpine-based promo banner, it looks like this:

```html
<div
  class="bottom-0 inset-x-0 pb-2 sm:pb-5"
  x-data="{ hide_banner: true }"
  x-init="hide_banner = docCookies.hasItem('hide_banner') ? (docCookies.getItem('hide_banner') == 'true') : false;"
  x-bind:class="{ 'hidden': hide_banner, 'fixed': !hide_banner }"
>
```

The key points are:

-   x-data sets the variable and defines the default as hidden
-   x-init loads the cookie (if available) or sets a default of false to display it
-   x-bind changes the visibility depending on the data.

For the closing of the banner, we just set a cookie for a week:

```html
<button
  type="button"
  @click="hide_banner = true; docCookies.setItem('hide_banner', true, (7*24*60*60));"
  class="-mr-1 flex p-2 rounded-md hover:bg-indigo-500 focus:outline-none focus:bg-indigo-500 transition ease-in-out duration-150"
  aria-label="Dismiss"
>
```

I've opted to omit the whole source code of the banner, as TailwindUI is a commercial product and you need to purchase a license for yourself. This supports the continued development of the open source library.

Making Sure the Banner Shows up Again After Changes
---------------------------------------------------

Currently, the implementation of the banner has some limitations. Mostly these are:

-   It would show up again after one week
-   If changed, it shouldn't show up again within one week

That's rather sub-optimal. So we need to tweak it a bit more to enforce re-displaying. Here we customize the cookie name using a settings-value coming from Laravel:

```html
<div
  class="bottom-0 inset-x-0 pb-2 sm:pb-5"
  x-data="{ hide_banner: true, cookie_name: 'c{{ md5(settings()->get('banner_short_text')) }}' }"
  x-init="hide_banner = docCookies.hasItem(cookie_name) ? (docCookies.getItem(cookie_name) == 'true') : false;"
  x-bind:class="{ 'hidden': hide_banner, 'fixed': !hide_banner }"
>
```

The ```cookie_name``` changes with changes of the banner text automatically. Using this, we can extend the cookie lifetime to 60 days:

```html
<button
  type="button"
  @click="hide_banner = true; docCookies.setItem(cookie_name, true, (60*24*60*60));"
  class="-mr-1 flex p-2 rounded-md hover:bg-indigo-500 focus:outline-none focus:bg-indigo-500 transition ease-in-out duration-150"
  aria-label="Dismiss"
>
```

Now our solution is more practical and works across various situations and use-cases.

## More?

If you are interested in being a beta tester for PageExplorer and learning how to improve your website rankings, sign up now. I'm also writing about dev now and then - mostly on my [Hashnode blog](https://releasecandidate.dev) 💪️ Mainly because I think [building alone doesn't work anymore](https://roadmap.sh/guides/why-build-it-and-they-will-come-wont-work-anymore). On my Hashnode blog you can also sign up for a newsletter 📬️ alerting you when I solve another problem!

# Minimal 11ty Starter

[![Screenshot of the Demo Website](https://github.com/tomreinert/minimal-11ty-tailwind-starter/assets/3286735/87949d5e-dc9a-4f12-bab0-b854f7e78dd0)](https://11ty-tailwind-starter.netlify.app)

A *very* minimal [eleventy](https://11ty.io/) starter using [Tailwind CSS](https://tailwindcss.com/) for styling.

It features a smart navigation component that sets active states automatically.

For beginners and/or when you need a simple static site and don't want to duplicate your navigation header and set active states for the nth time.

## Features
🦴 As minimal as possible  
⚡️ Active states in the navigation are automatically set based on the current url.  
🌗 Dark/Light Mode Toggle  
💨 Add a couple of lines to any page and it will appear in the navigation. (Check how to below)  
🗓 A very simple blog structure because why not  
🍪 Example for including json data on contact page  
💜 Tailwind 4


### [Live Demo](https://11ty-tailwind-starter.netlify.app)  

---

## Getting Started


#### 1. Clone this repo

```
git clone git@github.com:tomreinert/minimal-11ty-tailwind-starter.git mysite
```
#### 2. Change into the working directory

```
cd mysite
```

#### 3. Install dependencies

```
npm install
```

#### 4. Work locally
Watches for changes and serves locally on http://localhost:8080

```
npm run serve
```

#### 5. Create a production build

```
npm run build
```



## How To: Navigation

The top navigation is the only *feature* in this starter and lives in `/src/_includes/components/navigation.njk`.  

It looks for the eleventyNavigation object in pages and adds them to the navigation bar. It also checks whether the site's url is in the currently opened url and highlights the navigation item accordingly. This even works for subpages. So if you're on `/blog/post/` the **Blog** nav item will still be active.


### Adding links to the navigation
Add the `eleventyNavigation` object to any page and it will appear in the navigation. Optionally set the order of your items.
Check the [11ty docs](https://www.11ty.dev/docs/plugins/navigation/) for more information about the navigation plugin.

```
---
eleventyNavigation:
  key: Your Page Name
  order: 1
---
```


### Changing the navigation item styles
The script in `/_includes/components/navigation.njk` checks if a navigation item is active and styles it accordingly.
Let's dissect the code:

```
<a
  href="{{ entry.url }}"

  // Base styles for all navigation items
  class="uppercase text-sm py-1 px-2 rounded inline-block
  
  // Active navigation items
  {% if (entry.url in page.url and entry.url != '/') or (page.url == '/' and entry.url == '/')  %}
    bg-black text-white
  
  // Default navigation items
  {% else %}
    text-zinc-700 dark:text-zinc-200 hover:bg-zinc-100 dark:hover:bg-zinc-700
  {% endif %}">
  {{ entry.title }}
</a>
```

## How to: Dark mode

As someone with limited development skills, it was harder than expected to implement a dark-light-mode toggle. So I dug into it and built it into the template.
You can easily remove it if you don't need it.

Per default, the site takes the user's operating system preference.

Once the user toggles the mode manually, it is saved to local storage and will override system preference. 

You can add a button that forgets the manually selected mode. See line 50 in `navigation.njk`:

```
<button id="forgetPref" onclick="forgetPref()">Forget</button>
```

If you don't need the dark mode toggle, do this:
1. Remove the entire `<script>...</script>` from the head of `base.njk`
2. Remove the entire `<button>...</button>` from `navigation.njk`
3. Remove any classes that start with `dark:`from `base.njk` and `navigation.njk`



## How To: Blog

Add a page in `_src/blog/posts` and it will appear in the post list.

## Images

Put your images into `_src/img` and add them to your markup like so:
```
<img src="/img/example-image.jpg">
```



## Credits

[Bryan L. Robinson](https://bryanlrobinson.com/blog/using-nunjucks-if-expressions-to-create-an-active-navigation-state-in-11ty/) for explaining how to create the active navigation state

https://11ty.io/

https://tailwindcss.com

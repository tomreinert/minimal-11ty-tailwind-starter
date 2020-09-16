# Minimal 11ty Starter



A *very* minimal starter using tailwind for styling and a smart navigation component.

For beginners and/or when you need a simple static site and don't want to duplicate your navigation header and set active states for the nth time.

**Features**
- Active states in the navigation are automatically set based on the current page.
  - This even works for subpages! So if you're on `/blog/post/` the **Blog** nav item will still be active
- Add a couple of lines to any page and it will appear in the navigation. (Check how to below)
- A very simple blog structure
- Example for including json data on contact page
- Tailwind CSS


---

## Getting Started


#### 1. Clone this repo

```
git clone git@github.com:tomreinert/XXXXXXX.git mysite
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

---

## How To: Navigation


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

 // Base styles for navigation items
 class="py-1 px-2 rounded mr-4 inline-block

 // Styles for the active navigation item
 {{'bg-white text-black' if entry.url in page.url

 // Styles for default navigation item
 else 'text-gray-400 hover:text-gray-100'}}">
 {{ entry.title }}
</a>
```

---

## Project structure

```
├───_site         -> Your build goes here
├───src           -> Source files, you work here
  ├───data        -> Data to use in your site (e.g. contact data)
  └───includes    -> Your build goes here
      ├───components  -> Components to include in your site (e.g. navigation)
      └───layouts     -> Layouts
  └───blog        -> Blog posts
  └───pages       -> Main pages of your website
  └───scripts     -> Custom scripts go here
  └───styles      -> CSS, currently only importing tailwind
  └───index.njk   -> Your home page

```

---

## Credits

[Bryan L. Robinson](https://bryanlrobinson.com/blog/using-nunjucks-if-expressions-to-create-an-active-navigation-state-in-11ty/)

 https://statickit.com/guides/eleventy-tailwind

 https://11ty.io/

 https://tailwindcss.com/

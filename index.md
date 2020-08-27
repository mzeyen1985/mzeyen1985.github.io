---
permalink: /
---

# GitHub Pages Test

This is a test page for experimenting with GitHub Pages.

## Useful Links

* [Supported Themes](https://pages.github.com/themes/)
* [Customizing Themes](https://docs.github.com/en/github/working-with-github-pages/adding-a-theme-to-your-github-pages-site-using-jekyll#customizing-your-jekyll-themes-html-layout)

## Initial Setup

1. Create a new repo `<username | organization>.github.io` adding an initial `README.md`
2. On the new repo's GitHub page go to `Settings` and scroll down to the `GitHub Pages` section
3. Click on the "Change Theme" button and select a theme
4. Navigate in the browser to `https://<username | organization>.github.io` to verify the setup worked correctly (it might take a little for the page to generate).

## Configure the Page

1. On the repo's GitHub page click on the generated `_config.yml` file and edit it.
   Add the following entries:
   
   ```yml
   title: <pages-title>
   description: <pages-description-aka-subtitle>
   baseurl: /
   ```
2. The `README.md` can now be renamed (e.g. `index.md`) and should have the following added at the very top of it:
   ```
   ---
   permalink: /
   ---
   ```
   
## Customizing the Page

The default theme selected can be modified with local copies of the files that require modifications.
The default theme source codes are listed here: [Supported Themes](https://pages.github.com/themes/)

### Example: Navigation Bar

1. Copy the `_layouts/default.html` file of the theme into the pages repo with the same path and name.
2. Add the following line to the `default.html` file:
   <pre>
     &lt;header&gt;
       &lt;div class=&quot;inner&quot;&gt;
         &lt;a href=&quot;{{ '/' | absolute_url }}&quot;&gt;
           &lt;h1&gt;{{ site.title | default: site.github.repository_name }}&lt;/h1&gt;
         &lt;/a&gt;
         &lt;h2&gt;{{ site.description | default: site.github.project_tagline }}&lt;/h2&gt;
         {% if site.github.is_project_page %}
           &lt;a href=&quot;{{ site.github.repository_url }}&quot; class=&quot;button&quot;&gt;&lt;small&gt;View project on&lt;/small&gt; GitHub&lt;/a&gt;
         {% endif %}
         {% if site.github.is_user_page %}
           &lt;a href=&quot;{{ site.github.owner_url }}&quot; class=&quot;button&quot;&gt;&lt;small&gt;Follow me on&lt;/small&gt; GitHub&lt;/a&gt;
         {% endif %}
         <b><i>{% include nav.html %}</i></b>
       &lt;/div&gt;
     &lt;/header&gt;
   </pre>
3. In the repo root create a new file in `_includes/nav.html` with the following code:
   ```html
   <p style="text-align: center; background-color: white;">
     <a href="{{site.baseurl}}/">Home</a> |
     <a href="{{site.baseurl}}/news/">News</a>
   </p>
   ```
4. Create a file for the `News` entry in `news/<filename>.md` under the repo's root with the following lines at the very top:
   ```
   ---
   permalink: /news/
   ---
   ```
   The name of the file doesn't matter as only the `permalink` entry is required for the correct link.

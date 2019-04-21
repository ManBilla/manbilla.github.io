---
title: Setting up my website
author: Manoj Billa
date: '2018-12-11'
slug: setting-up-my-new-website
categories:
  - Website
tags:
  - R Markdown
  - Markdown
  - HTML
description: ''
---
FInally, after much deliberation, I finished building my new website. I Initially had a [basic google sites website](https://www.manojbilla.com) showcasing my projects, experience, etc. Then after experimenting with [Jekyll](https://jekyllrb.com/), [Ghost](https://github.com/TryGhost/Ghost), [Hugo](https://gohugo.io/), etc., I finally settled upon Hugo :smile:. Then I discovered [blogdown](https://github.com/rstudio/blogdown) and moved my website into that. Yihui has written a pretty comprehensive [book](https://bookdown.org/yihui/blogdown/) on blogdown which is available for free online and you should read that book if you want in-depth understanding of blogdown and hugo.

# Basic instructions:
1. Choose a theme among the available themes showcased <a href="https://themes.gohugo.io/" target="_blank">here!</a>. Be wary that not all themes have been tested to work with blogdown. Yihui recommends certain [themes](https://bookdown.org/yihui/blogdown/other-themes.html) in his book. I chose the ghostwriter theme because of its simplicity and support in community.
2. Install hugo, if you are using standalone hugo. Install blogdown package if you are using blogdown. You can do this by using `install.packages('blogdown')` after installing RStudio. Installing blogdown also installs hugo.
3. Edit the `config.toml` file to personalize your website. You can, for example, add menu options, change social media links, embed google analytics, disqus comments, etc.
4. Create a new project in a directory of your choice. With this as your working directory, use `blogdown::new_site()` to create a new site. If you don't want to use the default theme, use `theme = "your chosen theme github path"` argument to use a different one.
5. You can create a new post using 'New post' addin or using `blogdown::new_post()` function with the Title, Author, etc as arguments. You can also edit your existing files in `content/post` folder. These files can be plain markdown or Rmarkdown (the graphics, etc will be rendered) or html. These files in the `content` folder render into HTML pages which will be in your `public` folder, along with .css, .js, image assets needed to publish your website.
6. After creating your post, use the function `blogdown::serve_site()` to serve the site. You can see the website in "Viewer" section of RStudio. the function also gives you a local web address (for example: http://127.0.0.1:4321) where you can see your website in the browser. Do not knit the markdown file. If you do, just use serve_site() again after deleting the knitted html files from the content & public folders.
![rstudio](/img/RStudio.PNG)
(If you are using standalone hugo instead of blogdown, then use `hugo server -D` to serve site and open `http://localhost:1313` to see your site)

After setting up a basic website, you can experiment before deploying to web server. Hugo has livereload functionality, by which you can see your changes updated in the locally hosted webpage instantaneously. :rocket:

# Personalizing your theme

As described earlier, config.toml can be used to make most of the possible personalizations. Each theme has different levels and kinds of customization. For example, some themes let you change page colors, number of most recent posts, etc while some do not. You can also edit your css/js in `themes/static` folder.

# Deploying
After finishing your changes, you can deploy your site either in Netlify (recommended), github pages, gitlab pages, etc for free. I chose netlify for now but might change to github pages later just because of the .github.io domain and the flexibility to use project pages from different repositories in my website. For doing any of these, you need to install git and push your files to a github repository. After this, create an account in netlify and follow the steps and after 2 minutes, your site will be live!
After deploying, netlify assigns your site a random domain. You can customize the subdomain to something of your liking. Your CSS, JS files may fail to load initially. You need to update your new site link in the `baseurl` within `config.toml` document. If you want a free rbind domain, create an issue here: https://github.com/rbind/support/issues

# Testing how different objects embed
---
#### Tables & quotes


| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | `centered`      |   $12 |
| zebra stripes | _are neat_      | **$1** |

> This line is being quoted from **somewhere**


---

#### Code Blocks
```
#Hello world
  if hello = True:
    print "World"
```
In some other themes in Hugo, I observed that we can specify the language name and the syntax is highlighted accordingly. In this them that doesn't seem to be the case.

---

#### Images
Images can also be embedded using html tag where you can specify custom width, height, etc. 
![Here's a kitten](/post/2018-12-11-setting-up-my-new-website-files/kitten.png)

---

#### Tweets

{{< tweet 1027260993800261633 >}} 

---

#### Iframe


You can use the below html code as reference to embed a Tableau viz
```
<iframe 
src = "https://public.tableau.com/shared/BPZ8QJP25?:showVizHome=no&:embed=true" width="100%" height="100%" style="border: 0px;" scrolling="no">
</iframe>
```
<iframe 
src = "https://public.tableau.com/shared/BPZ8QJP25?:showVizHome=no&:embed=true" width="1500" height="790" style="border: 0px;" scrolling="no">
</iframe>




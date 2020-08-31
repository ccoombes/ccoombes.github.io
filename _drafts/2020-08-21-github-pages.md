---
title: "GitHub Pages basics and why I choose it as the platform for this website"
header:
    image: /assets/images/posts/github-pages.jpg
    teaser: /assets/images/posts/github-pages-th.jpg
toc: true
toc_label: "Contents"
toc_icon: "book"  
categories:
  - blog
tags:
  - Git
  - GitHub
  - Windows
  - Chocolatey
  - MacOS
  - HomeBrew
  - MarkDown
---
As evident from the tag line of this site "Journey to the clouds" and the themes highlighted in my initial post, the criteria for setting up this site was documenting my discovery of modern infrastructure and the practices that enables it. One such practise considered to be a key enabler of modern infrastructure is the concept of Infrastructure as Code, which as the name would indicate offers the ability to describe the desired state of your infrastructure as code. While the concept in theory is sound, through its ability to create immutable repeatable infrastructure, it introduces a new challenge of managing and sharing the source files used in the process.  

Thankfully there are plenty of tools already available to manage source files, both opensource and commercial offerings. The use of source control has traditionally only been within the developer community, its use is quickly becoming more prevalent across the full range of IT roles. The most common of these tools is the opensource offering Git.

!["GitHub sign up"](https://git-scm.com/images/logos/2color-lightbg@2x.png "https://git-scm.com/images/logos/2color-lightbg@2x.png")

>Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows.
>Wikipedia

When selecting a blogging platform I wanted something that integrated the learnings of a source control system and as the most widely used system being Git this seemed like a logical choice. While technically any project that contains source files can be managed by Git, I wanted something that easy is to use and that wouldn't interfere with the content creation process.

GitHub Pages meets this brief perfectly. GitHub Pages is a free static website hosting service from GitHub that takes source files from a cloud repository managed via Git and publishes them as a website. It’s a no-brainer! Why should we install security updates, manage plugins and tune the performance of a website so our pages load fast? Blogging should be all about the writing!

With Jekyll you don’t need to worry about all of that. Jekyll has no admin interface, only source files that you can build using a CLI (command line interface) to create a static website. Simply write your blog posts in Markdown and if you choose to host your website using GitHub Pages, you can use Git to commit and push your changes to publish new posts or pages.

Before moving on it is worth noting that while all these technologies all have Git in there name they offer very different functionality and can cause confusion when getting started. Git and GitHub  I will provide a brief summary below;
- Git: Tool for working with source files
- GitHub: A cloud-based repository to store source files
- GitHub Pages: Renders source files to be displayed as a website

The rest of this post will cover off the steps for getting started with GitHub pages.

# Basic Setup
The first step with getting started with GitHub pages, if you don't already have one, is creating a GitHub account. This is a simple as heading to GitHub.com entering a few personal details and you are good to go.

!["GitHub sign up"](/assets/images/posts/github-pages/gh-signup.png "Creating a GitHub Account")

## Creating a Repository
After you have signed up the next step is creating a Repository to host your source files. 

For any standard project you can name this whatever you like, for a repository to be detected by GitHub pages it needs to formatted as 'githubusername.github.io'. 

The username for my demo account in 'gac-cloud-demo' so I will name my repository 'gac-cloud-demo.github.io'. 

!["Creating repository"](/assets/images/posts/github-pages/gh-repo.png "Creating your GitHub pages repository")

# Installing Git
Now that we have a GitHub repository ready to host source files we need to install Git on our local computer and create the content to be published.
Git is a free open source distribytion avalibale on Windows, Mac and Linux.

In this psot i wil cover the installation method I use for Windows and Mac only, for installtio struction for the Linux distribution of you choice please visit;

https://git-scm.com/download/

## Windows
Install Chocolatey

https://chocolatey.org/install
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```
Install Git chocolatey package
```
choco install Git
```

## MacOS
Install Home brew 

https://brew.sh/
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
install git homebrew package
```
brew install git
```
Your computer is now setup and ready to us Git on your local computer and push content to a GitHib repository.

## Git Commands
Cover a few basic commands 

https://git-scm.com/docs

# GitHub Pages source files

GitHub Pages publishes any static files that you push to your repository. You can create your own static files or use a static site generator to build your site for you. You can also customize your own build process locally or on another server. We recommend Jekyll, a static site generator with built-in support for GitHub Pages and a simplified build process. For more information, see "About GitHub Pages and Jekyll."

GitHub Pages will use Jekyll to build your site by default. If you want to use a static site generator other than Jekyll, disable the Jekyll build process by creating an empty file called .nojekyll in the root of your publishing source, then follow your static site generator's instructions to build your site locally.

https://docs.github.com/en/github/working-with-github-pages

I will cover 2 types of static files, simple HTML and markdown files renders using Jekyll.

## Basic HTML
Create directory and content
```
mkdir gac-cloud-demo
cd gac-cloud-demo
echo "<h1>Hello GitHub Pages</h1>" >> index.html
```
Intialise Git, add files to be versioned then commit the changes to your local Git repostory 
```
git init
git add index.html
git commit -m "first commit"
```
Connect your local Git repository to the remote GitHub repostory to was crated earlier.
Discuss credential manager complexities.
```
git remote add origin https://github.com/gac-cloud-demo/gac-cloud-demo.github.io.git
git remote add origin https://gac-cloud-demo@github.com/gac-cloud-demo/gac-cloud-demo.github.io.git
```
Push the commit files to the remote Git hub repostory.
```
git push -u origin master
```
test githb url
Log into you GitHub accoutnt and confirm the Github pages settings
!["Creating repository"](/assets/images/posts/github-pages/gh-ghp-settings.png "Creating your GitHub pages repository")

Now visit your GitHub pages URL and should see the render HTML code
!["Creating repository"](/assets/images/posts/github-pages/ghp-html-render.png "Creating your GitHub pages repository")


## Basic MarkDown
the github jekyll integration
what is markdown as why is it used
what is static site generation

https://jekyllrb.com/docs/

```
echo "# Hello GitHub Pages" >> index.md
```
```
git rm index.html
```
```
git add index.md
git commit -m "markdown commit"
git push
```

Now visit your GitHub pages URL and should see the render HTML code
!["Creating repository"](/assets/images/posts/github-pages/ghp-md-render-basic.png "Creating your GitHub pages repository")

enable a github jekyll theme
With Jekyll integration, Gihub pages offers a varitye of template you can use to format you r content.
!["Creating repository"](/assets/images/posts/github-pages/ghp-themes.png "Creating your GitHub pages repository")

With Jekyll integration, Gihub pages offers a varitye of template you can use to format you r content.
!["Creating repository"](/assets/images/posts/github-pages/ghp-md-render-template.png "Creating your GitHub pages repository")


# What's Next 
The next pot will cover using a custom theme and some of the tweaks i have used creating ChrisCoombes.com 

If you found this article useful, please let me know at @ccoombes83 or email me at ccoombes@outlook.com. I look forward to reading your new Jekyll blog!
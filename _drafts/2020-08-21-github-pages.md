---
title: "Introduction to GitHub Pages and why its the chosen platform for this blog"
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
As the tag line of this site and the themes highlighted in my initial post would indicate, the primary driver for setting up this site was to document my learnings of the practices that enable and power the modern cloud technologies. To gain the full operational benefit of these practises relies on automating all aspects of the environment, including the ability to rapidly provision and manage infrastructure. The concept of Infrastructure as Code (IaC) introduces an infrastructure deployment process which describes in text files the desired state of the systems. While the theory is sound, through the ability to create immutable repeatable infrastructure, it introduces a new challenge of managing and sharing the source files used in the process. 

In a large environment, this will consist of hundreds if not thousands of files, including multiple versions. These files all need to be created and maintained by several people across the organisation. Keeping these files organised can quickly become a management burden. Source control or version control is the practice of tracking and managing changes to code. Source control management (SCM) is the classification given to the tools that operate this process. SCM is a system which provides a running history of code development and helps to resolve conflicts when merging contributions from multiple sources.

There are several SCM tools available with the most common and widely used of these tools is Git. The use of Git or SCM systems, in general, has traditionally been associated with the developer community. This observation is no longer valid, with its adoption rapidly increasing across the full range of IT roles. Familiarity with SCM tools is quickly becoming a must-have skill for developers and systems administrators alike.

!["GitHub sign up"](https://git-scm.com/images/logos/2color-lightbg@2x.png "https://git-scm.com/images/logos/2color-lightbg@2x.png")

> Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows.

> Wikipedia

When selecting a blogging platform, I wanted something that integrated the learnings of an SCM and with Git being the logical choice. While technically any project containing any source files can be managed by Git, I wanted something that is to easy to use and had content creation as its core.

GitHub Pages meets this brief perfectly. GitHub Pages is a free static website hosting service from GitHub that renders files from a Git managed cloud repository and publishes them as a website. In addition to the learning opportunities, the use of a static hosting service has many advantages. There are no databases to maintain, no plugins to manage, no security updates to install and with the removal of these overheads page load speed are greatly enhanced. 

You might think with the removal of all these features that the functionality and flexibility would be reduced, this where static site generators (SSG) applications come in. SSG's are a software application that you run on your workstation that creates HTML files based on templates you specify and formats them for publishing to the web. There are several SSG available the one that will be the focus of this post is Jekyll as it natively supported by GitHub Pages.

!["GitHub sign up"](https://upload.wikimedia.org/wikipedia/commons/4/42/Jekyll_%28software%29_Logo.png "https://upload.wikimedia.org/wikipedia/commons/4/42/Jekyll_%28software%29_Logo.png")

> Jekyll does what you tell it to do — no more, no less. It doesn’t try to outsmart users by making bold assumptions, nor does it burden them with needless complexity and configuration. Put simply, Jekyll gets out of your way and allows you to concentrate on what truly matters: your content.

> Jekyll README.md


In summary, while all the technologies mentioned above have a direct connection Git they offer very different functionality and can confuse a beginner or even a seasoned professional when getting started;
- Git: Tool for working with source files
- GitHub: A cloud-based repository to store Git managed source files
- GitHub Pages: Renders source files to be displayed as a website
- Jekyll: Tool used to generate HTML pages which can be pushed GitHub and rendered as a website

The rest of this post will cover off the steps for getting started with GitHub pages.

# Basic Setup
The first step with getting started with GitHub pages, if you don't already have one, is to a GitHub account. This is a simple as heading to GitHub.com entering a few personal details and you are good to go.

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

# GitHub Pages

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
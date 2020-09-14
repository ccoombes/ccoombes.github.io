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
  - GitHub Pages
  - Jekyll
  - MarkDown
  - Tutorial
---
As the tag line of this site and the themes highlighted in my initial [post](/blog/welcome-to-my-blog/) would indicate, the primary driver for setting up this site was to document my learnings of the practices that enable and power the modern cloud technologies. To gain the full operational benefit of these practises relies on automating all aspects of the environment, including the ability to rapidly provision and manage infrastructure. The concept of Infrastructure as Code introduces an infrastructure deployment process which describes in text files the desired state of the systems. While the theory is sound, through the ability to create immutable repeatable infrastructure, it introduces a new challenge of managing and sharing the source files used in the process. 

In a large environment, this will consist of hundreds if not thousands of files, including multiple versions. These files all need to be created and maintained by several people across the organisation. Keeping these files organised can quickly become a management burden. Source control or version control is the practice of tracking and managing changes to code. Source control management (SCM) is the classification given to the tools that operate this process. SCM is a system which provides a running history of code development and helps to resolve conflicts when merging contributions from multiple sources.

There are several SCM tools available with the most common and widely used of these tools is Git. The use of Git or SCM systems, in general, has traditionally been associated with the developer community. This observation is no longer valid, with its adoption rapidly increasing across the full range of IT roles. Familiarity with SCM tools is quickly becoming a must-have skill for developers and systems administrators alike.

!["GitHub sign up"](https://git-scm.com/images/logos/2color-lightbg@2x.png "https://git-scm.com/images/logos/2color-lightbg@2x.png")

> Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows.

> [Wikipedia](https://en.wikipedia.org/wiki/Git)

When selecting a blogging platform, I wanted something that integrated a content management system while learning the basics of Git. While technically any project containing source files can be managed by Git, I was looking for a platform that is easy to use and had content creation as its core.

GitHub Pages meets this brief perfectly. GitHub Pages is a free static website hosting service from GitHub that renders files from a Git managed cloud repository and publishes them as a website. In addition to the learning opportunities, the use of a static hosting service has many advantages. There are no databases to maintain, no plugins to manage, no security updates to install and with the removal of these overheads page load speed are greatly enhanced. 

When comparing against a traditional blogging platform, you might think with the removal of all these features that using a static website functionality would be reduced. While this may be true when thinking about a hosting service like GitHub Pages in isolation, this is where the use of static site generator (SSG) applications come in. SSG is a software package that you run on your workstation that creates HTML files based on templates you specify and formats them for publishing to the web. There are several SSG's available the one that will be the focus of this post is Jekyll as it's natively supported by GitHub Pages.

!["Jekyll Logo"](https://upload.wikimedia.org/wikipedia/commons/4/42/Jekyll_%28software%29_Logo.png "https://upload.wikimedia.org/wikipedia/commons/4/42/Jekyll_%28software%29_Logo.png")

> Jekyll does what you tell it to do — no more, no less. It doesn’t try to outsmart users by making bold assumptions, nor does it burden them with needless complexity and configuration. Put simply, Jekyll gets out of your way and allows you to concentrate on what truly matters: your content.

> [Jekyll README.md](https://github.com/jekyll/jekyll/blob/master/README.markdown)


In summary, while all the technologies mentioned above have a direct connection with Git they offer very different functionality and can confuse a beginner or even a seasoned professional when getting started;
- Git: Tool for working with source files
- GitHub: A cloud-based repository to store Git managed source files
- GitHub Pages: Renders source files to be displayed as a website
- Jekyll: Tool used to generate HTML pages which can be pushed GitHub and rendered as a website

The rest of this post will cover off the steps for getting started with GitHub pages.

# Basic Setup
The first step to getting started with GitHub pages is to create a GitHub account. Head to the [GitHub.com](https://github.com/join?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home) sign up page to create an account.

!["GitHub sign up"](/assets/images/posts/github-pages/gh-signup.png "Creating a GitHub Account")

## Creating a Repository
Now that you have a GitHub account, the next step is creating a cloud repository to host your source files that are to be rendered as a webpage. 

Select New from the top left corner of GitHub dashboard.

!["GitHub New Repo"](/assets/images/posts/github-pages/gh-new-repo.png "GitHub New Repository")

Typically when naming a repository you can name it whatever you like as long as it is unique for GitHub account. GitHub pages have a unique requirement in that it needs to be named 'username.github.io' to properly render the files the repository contains as a website. 

The username for my demo account in **'gac-cloud-demo'** so I will name my repository **'gac-cloud-demo.github.io'**. 

Make sure your repository is set to public so the content is visible to all, then select create a repository.

!["Creating repository"](/assets/images/posts/github-pages/gh-repo.png "Creating your GitHub pages repository")

Take note of the HTTPS URL we will need this later.

![GitHubURL](/assets/images/posts/github-pages/gh-url.png "GitHub Repository URL")

# Installing Git
Now we need to install Git on our local computer to create a local Git repository that will be eventually be synced with the GitHub repository we just created.

Git is available on Windows, Mac and Linux. In this post I will cover the installation methods I use for Windows and Mac only, for installation instruction for the Linux distribution of your choice please visit;

<https://git-scm.com/download/>

## Windows

I will be using the Chocolatey package manager to install Git on Windows which is my preferred method for managing application installations, for more detail on Chocolatey please visit;

[![Chocolatey](/assets/images/posts/github-pages/chocolatey-logo.png "Chocolatey Logo")](https://chocolatey.org)

### Install Chocolatey
To install Chocolatey first open PowerShell as an Administrator
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```
Close Powershell window
### Install Git package
Open PowerShell as an Administrator
```
choco install Git
```
Close and reopen Git as a standard user.  
To confirm Git has been successfully installed.
```
git --version
```
At the time of writing, this would return
```
git version 2.28.0.windows.1
```
Your PC is now set up and ready to use Git on your local computer and push content to a GitHub repository.

## macOS
There are several options available for installing Git on macOS. If you already have the XCode Command Line Tools installed it's likely that Git will already be available. There is a standalone macOS installer, like Windows my preferred method for managing packages is to use a package manager. The package manager for macOS is HomeBrew, for more details please visit;

[![HomeBrew](/assets/images/posts/github-pages/Homebrew-mac-logo.jpg "HomeBrew Logo")](https://brew.sh)

### Install Homebrew 
Open a new Terminal window.
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
Close and reopen Terminal

### Install Git package
```
brew install git
```
Close and reopen Terminal  
To confirm Git has been successfully installed
```
git --version
```
At the time of writing, this would return
```
git version 2.28.0
```
Your Mac is now set up and ready to use Git on your local computer and push content to a GitHub repository.

# GitHub Pages

Now that we have a GitHub account and a functioning installation of Git on our Windows PC or Mac, the next steps are to create some content to be used by GitHub pages and commit it to a Git repository. 

I will cover the basics of using two content types with GitHub pages, HTML and Markdown and highlight the differences between the two. For an in-depth look at GitHub pages please visit;

<https://docs.github.com/en/github/working-with-github-pages>

## Basic HTML
Open your console of choice (PowerShell / Terminal)  
First, let's create a directory for our files
```
mkdir gac-cloud-demo
cd gac-cloud-demo
```
Create the HTML file
```
echo "<h1>Hello GitHub Pages</h1>" >> index.html
```
Now it time to start working with Git  
Lets first initialise our local Git repository
```
git init
```
Next, we add files to be tracked by version control to our local Git repository 
```
git add index.html
```
Commit the changes
```
git commit -m "first commit"
```
We now have our first files being tracked by version control

To enable the content we have just created to be uploaded to GitHub we need to link our local Git repository with the Cloud-hosted GitHub repository we created earlier.

First, we need to copy the HTTPS URL for our GitHub pages repository

![GitHubURL](/assets/images/posts/github-pages/gh-url.png "GitHub Repository URL")

Using this URL we then need issue the command to link our repositories

```
git remote add origin https://github.com/gac-cloud-demo/gac-cloud-demo.github.io.git
```

Now that the repositories are linked we need to push the committed files in our local Git repository to our cloud repository. 

As this is the first time we are pushing files we need to tell Git which branch to push our changes. The default branch is master which exists on every repository. 
```
git push -u origin master
```
Now that the files have been uploaded we can check in on our website. First, let's check our GitHub pages settings if we named our repository 'username.github.io' these should be configured by default.

Log into your GitHub account and confirm the Github pages settings  

!["Confirm GitHub pages settings"](/assets/images/posts/github-pages/gh-ghp-settings.png "Confirm GitHub pages settings")

Now open your preferred web browser and visit your GitHub pages URL and you will see the rendered HTML.

NOTE: If this is the first time browsing it can take a few minutes for GitHub to populate the content.

For me this is;

<http://gac-cloud-demo.github.io>

!["GitHub pages rendered HTML"](/assets/images/posts/github-pages/ghp-html-render.png "GitHub pages rendered HTML")


## Basic MarkDown
Markdown is a lightweight markup language with a plain-text-formatting syntax, removing the requirement to add complex tags to format documents. The primary use case for this is HTML, taking a simple human-readable text file and having it converted to structurally correct HTML ready to be displayed on the web.

GitHub Pages allows us to use markdown files to create content through the built-in integration with Jekyll.  By default, every file saved in a GitHub pages repository will be rendered by Jekyll. Through the use of a template, we can take these simple text files and have them displayed to the web in a visually pleasing way.

In the same local directory we were working in before, let's create a new markdown file.
```
echo "# Hello GitHub Pages" >> index.md
```
As we are replacing our HTML files with Markdown we need to exclude these file from being tracked version control.
```
git rm index.html
```
Add the new markdown file to be tracked
```
git add index.md
git commit -m "markdown commit"
```
As we linked our local and remote repositories earlier, we can simply run a Git push.
```
git push
```

Now visit your GitHub pages URL and should see the render Markdown file.  

!["GitHub pages rendered Markdown"](/assets/images/posts/github-pages/ghp-md-render-basic.png "GitHub pages rendered Markdown")

You will notice the formatting is slightly different. This is Jekyll formatting the content using the default template.

GitHub pages offer a variety of templates you can use to format your content.

!["Jekyll templates"](/assets/images/posts/github-pages/ghp-themes.png "Jekyll templates")

Select a new template, for this demo, we will be using 'Slate'. 

Browse to your URL again and you will see the new formatting.

!["New Jekyll Template"](/assets/images/posts/github-pages/ghp-md-render-template.png "New Jekyll template")

This is the power of writing in Markdown. Removing all the complex formatting tags and focusing purely on creating the content.

For example, please visit my [GitHub](https://raw.githubusercontent.com/ccoombes/ccoombes.github.io/master/_drafts/2020-08-21-github-pages.md) profile and review the markdown file for this post.


# What's Next 
The next post will cover using a custom theme and some of the Jekyll tweaks I have used creating [ChrisCoombes.com](https://chriscoombes.com) 

If you found this article useful, please let me know at [@ccoombes83](https://www.twitter.com/ccoombes83) or email me at [ccoombes@outlook.com](mailto:ccoombes@outlook.com).
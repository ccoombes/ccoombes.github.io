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

When comparing against a traditional blogging platform, you might think with the removal of all these features that using a static website functionality would be reduced. While this may be true when thinking about a hosting service like GitHub Pages in isolation, this is where the use of static site generator (SSG) applications come in. SSG is a software package that you run on your workstation that creates HTML files based on templates you specify and formats them for publishing to the web. There are several SSG available the one that will be the focus of this post is Jekyll as it natively supported by GitHub Pages.

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
The first step with getting started with GitHub pages, if you don't already have one, is to create a GitHub account. This is a simple as heading to GitHub.com selecting a username and you are good to go.

!["GitHub sign up"](/assets/images/posts/github-pages/gh-signup.png "Creating a GitHub Account")

## Creating a Repository
After you have signed up the next step is creating a repository to host your source files. 

For any standard project you can name this whatever you like, for a repository to be detected by GitHub pages it needs to formatted as 'username.github.io'. The username for my demo account in 'gac-cloud-demo' so I will name my repository 'gac-cloud-demo.github.io'. 

Make sure your repository is set to public so the content is visible to all.

!["Creating repository"](/assets/images/posts/github-pages/gh-repo.png "Creating your GitHub pages repository")

# Installing Git
Now that we have a GitHub repository ready to host our source files we need to install Git on our local computer and create the content to be published.

Git is available on Windows, Mac and Linux. In this post I wil cover the installation methods I use for Windows and Mac only, for installation instruction for the Linux distribution of your choice please visit;

<https://git-scm.com/download/>

## Windows

There are standard installation packages available for installation on Windows, but my preferred method for managing packages on Windows is using the Chocolatey package manager.

For more detail on Chocolatey please visit;

![Chocolatey](https://blog.ipswitch.com/hs-fs/hubfs/Featured%20Images/chocolatey-logo-1.png?width=640&name=chocolatey-logo-1.png "Chocolatey Logo")
<https://chocolatey.org>

### Install Chocolatey
Open PowerShell as an Administrator
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
At the time of writing this would return
```
git version 2.28.0.windows.1
```
Your PC is now setup and ready to use Git on your local computer and push content to a GitHib repository.

## MacOS
There are several options available for installing Git on MacOS. If you already have the XCode Command Line Tools installed its likely that Git will already have Git available, there is a standalone MacOS installer, ut like Windows my prefer method for managing packages is ot use a package manager. The package manager for MacOS is HomeBrew, for for details  check out the following;

![HomeBrew](https://ioshacker.com/wp-content/uploads/2017/08/Homebrew-mac-logo.jpg "HomeBrew Logo")
<https://brew.sh>

### Install Home brew 
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
To confirm Git has been successfully installed.
```
git --version
```
At the time of writing this would return
```
git version 2.28.0.windows.1
```
Your Mac is now setup and ready to use Git on your local computer and push content to a GitHib repository.

# GitHub Pages

Now that we have a functioning installation of Git on our workstation, the next steps is to create some content and push it to cloud repository to be served by GitHub pages. 

I will cover the basics below, by creating two files, HTML and Markdown and highlight the differences between the two. For an in depth look at GitHub pages please visit;

<https://docs.github.com/en/github/working-with-github-pages>

## Basic HTML
HTML is the language of the web and the format that most will be familiar with.  

Open your console of choice (PowerShell / Terminal)  
First lets create directory for our files
```
mkdir gac-cloud-demo
cd gac-cloud-demo
```
Create a basics HTML file
```
echo "<h1>Hello GitHub Pages</h1>" >> index.html
```
Now it time to start working with Git  
Lets first initialise our local Git repositoryIntialise Git, add files to be versioned then commit the changes to your local Git repostory 
```
git init
```
add the conntent you want tracked by version control
```
git add index.html
```
commit the changes
```
git commit -m "first commit"
```
We now have our first file being tracked by version control

To enable the content we have jsut created to be uploaded to GitHub pages we need to link our local Git repostory with the Cloud hosted GitHub repostory we vreated earlier.

```
git remote add origin https://github.com/gac-cloud-demo/gac-cloud-demo.github.io.git
```
Side note, if you have multiple GitHub accounts
```
git remote add origin https://gac-cloud-demo@github.com/gac-cloud-demo/gac-cloud-demo.github.io.git
```

Now that the repositiories are linked we need to push the commited files in our local Git repostory to our cloud repository. As the this is the first time we are pushing file we need tell Git 
```
git push -u origin master
```
Now that the files have been uploaded we can check in on our website. First lets check the setting on our GitHub pages settings, as we name our repo 'username.github.io' these should be configured by default.
Log into you GitHub accoutnt and confirm the Github pages settings  

!["Creating repository"](/assets/images/posts/github-pages/gh-ghp-settings.png "Creating your GitHub pages repository")

Now open your preffered web browser visit your GitHub pages URL and should see the render HTML .

For me this is;

<http://gac-cloud-demo.github.io>

!["Creating repository"](/assets/images/posts/github-pages/ghp-html-render.png "Creating your GitHub pages repository")


## Basic MarkDown
By default a file GitHub pages files are rendered via Jekyll, this enabled us to use Markdown.

Markdown is a text editor that was developed to make factors such as readability of plain text documents and conversion to HTML easier. Markdown removes the requiremtn to add complex tags to format documents and relies on a simple text based structure. 

Jekyll takes these simple texts files and renders in a more visually pleaseing wau to be present to the web.

Lets create our first markdown file.  

In the same local directory we where working in before, let create a new markdown file.
```
echo "# Hello GitHub Pages" >> index.md
```
Exclude the exisiting HTML file we create earlier from being tracked version control.
```
git rm index.html
```
Add the the new markdown file to be tracked
```
git add index.md
git commit -m "markdown commit"
```
As we linked our local and remote repostiories ealier and specific the destiantion for our files, we can simple run a Git push.
```
git push
```

Now visit your GitHub pages URL and should see the render HTML code  

!["Creating repository"](/assets/images/posts/github-pages/ghp-md-render-basic.png "Creating your GitHub pages repository")

You will noticed some slightly improved format for which you wrote no code for. This is becuase Jekyll is doing the formating for you.

Gihub pages offers a varitye of template you can use to format you r content.

!["Creating repository"](/assets/images/posts/github-pages/ghp-themes.png "Creating your GitHub pages repository")

With Jekyll integration, Gihub pages offers a varitye of template you can use to format you r content. Select a new template, for this demo we will be using 'Slate'. Browse to your URL agin and you will notice some new formating.

!["Creating repository"](/assets/images/posts/github-pages/ghp-md-render-template.png "Creating your GitHub pages repository")

This is the power of writing in Markdown by removing all formatting and having a Static Site Generator like Jekyll render the content for you.


# What's Next 
The next post will cover using a custom theme and some of the tweaks i have used creating [ChrisCoombes.com](https://chriscoombes.com) 

If you found this article useful, please let me know at [@ccoombes83](https://www.twitter.com/ccoombes83) or email me at [ccoombes@outlook.com](mailto:ccoombes@outlook.com). 
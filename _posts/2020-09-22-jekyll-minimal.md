---
title: "GitHub Pages, advance setup with Jekyll and Minimal Mistakes"
header:
    image: /assets/images/posts/jekyll-mm/jekyll-mm.jpg
    teaser: /assets/images/posts/jekyll-mm/jekyll-mm-th.jpg
toc: true
toc_label: "Contents"
toc_icon: "book"  
categories:
  - blog
tags:
  - GitHub
  - Jekyll
  - Minimal Mistakes
  - Ruby
  - Windows
  - MacOS
---
Following on from my previous post on [Getting Start with GitHub Pages](/blog/github-pages/) this post takes you through getting up and running with the static site generator Jekyll, creating content and publishing the content toGitHub. I will also cover off using custom themes, including some of the tweaks I implemented in setting up this site, adding your own domain, implementing post comments and enabling SSL. 

So lets get started,

# Installing Jekyll
Firstly, what is Jekyll? It is obviously a static site generator (SSG), but more than that is and so the following makes more sense, Jekyll is a Ruby application bundling several packages / plugins called Gems to into a single command line interface to build your site. If you are interesting in learning more about Ruby, please visit the following; 

[Ruby 101](https://jekyllrb.com/docs/ruby-101/)

As Jekyll is a Ruby application the first step is installing Ruby;

## Jekyll on Windows
I will be using Chocolatey for this, further details at [Installing Chocolatey](/blog/github-pages/#install-chocolatey)

Launch aa PowerShell window as **Admin**
```
choco install ruby --version=2.6.5.1 -y
choco install msys2 -y
Set-ExecutionPolicy Unrestricted
`````
Close powershell window

Launch a Standard user PowerShell window
``` 
#install Ruby dev environment
ridk install
- Just hit enter
- hit enter again after the install
ridk enable

#installing jekyll and creating site
gem install bundler jekyll

#confim versions
jekyll -v
```
```
jekyll new myblog

cd .\myblog\

jekyll serve
```
## Jekyll on MacOS
I will be using HomBrew for this, further details at [Installing HomeBrew](/blog/github-pages/#install-homebrew)

```powershell
#install ruby
brew install ruby

#set terminal path
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.zshrc

#install bundler and jekyll - what is bundler?
#bundler tracks and installs the required gems and version for each project https://bundler.io/ 

gem install bundler jekyll

#confirm Jekyll has been installed
$ jekyll -v                                                                
jekyll 3.8.5

#this will likely fail as by default as the Gem path is not included in the profile

#get the location of the Jeykll Gem
$ gem which jekyll                
/usr/local/lib/ruby/gems/2.6.0/gems/jekyll-3.8.5/lib/jekyll.rb

#Try to replace /gems/jekyll-3.8.5/lib/jekyll.rb with /bin. Jekyll should be inside /usr/local/lib/ruby/gems/2.6.0/bin. Use ls to make sure jekyll is there.
#Add that path to your shell config:

echo 'export PATH="/usr/local/lib/ruby/gems/2.6.0/bin:$PATH"' >> ~/.zshrc
```

## Minimal Mistakes Theme
Git is required for this, instructions on installing Git at [Installing Git](/blog/github-pages/#install-homebrew)

Install MM 

https://github.com/mmistakes/mm-github-pages-starter
```powershell
'ADMIN' 

choco install Git
-Close powershell

'Standard'
git clone https://github.com/mmistakes/mm-github-pages-starter.git

cd mm-github-pages-starter

# gem install --user-install jekyll bundle
bundle install # --path vendor/bundle
budle exec jekyll serve
```
## Creating a post with Jekyll
- creating a markdown file
- general markdown concepts
- serve locally
- push to github
- draft posts

## Customising your site with Jekyll
- config file
- bio details
- custom css

## Push you site to GitHub 
- push to github using command line
git init
git add .
git commit -m "first minimal mistakes commit"
git remote set-url origin https://github.com/gac-cloud-demo/gac-cloud-demo.github.io.git
git push -u origin master

## Extra's
### custom domains
### comments / analytics 
### other options
- other jekyll themes
- static site generators compatible with github

If you found this article useful, please let me know at [@ccoombes83](https://www.twitter.com/ccoombes83) or email me at [ccoombes@outlook.com](mailto:ccoombes@outlook.com).
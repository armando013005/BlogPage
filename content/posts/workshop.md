+++
title = 'Workshop'
date = 2025-11-07T16:20:41-08:00
draft = true
+++
# Portfolio website workshop
This guide is centered on creating a website that displays your abilities as a coder, engineer, artist, etc. It uses Hugo as a static website framework. This guide does not require code or any knowledge of it. You'll have to use your computer terminal, but do not let it intimidate you. If you ever forget how to save your work or any step from the process, this guide is made so it is easy to look back and copy the command.


## Getting started
Creating a static website is easy. The first step is installing the prerequisites.

#### `Windows`
This workshop uses [winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/#install-winget) a package manager. winget should be installed in systems with Windows 10 and later.


#### `macOS`
This workshop uses [homebrew](https://docs.brew.sh/Installation), another package manager. To install Homebrew, run the next text in your terminal shell. 
~~~bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
~~~

### Installing git 
[Git](https://git-scm.com/) a free and open-source version control system. We are going to use this as a tool to get our templates from the internet.

#### ``Windows``
Run the following command in the terminal.
~~~bash
winget install --id Git.Git -e --source winget
~~~
#### `MacOS`
Run the following command line:
~~~bash
brew install git
~~~

#### ``Linux``
If you are using Linux, look for the command line that matches your distribution in the [documentation.](https://git-scm.com/install/linux)

### Installing HUGO 

#### ``Windows``
Run the following command in the terminal.
~~~bash
winget install Hugo.Hugo.Extended
~~~

#### ``macOS``
Run the following command line:
~~~bash
brew install hugo
~~~

#### ``Linux``
If you are using Linux, look for the command line that matches your distribution at the [repository packages.](https://gohugo.io/installation/linux/#repository-packages)
### misc 
Related to the theme we are using in this guide, if you are using another theme, you can skip to the next section.

#### npm
- Windows ``winget install OpenJS.NodeJS.LTS`` 
- macOS ``brew install node``
- Linux: You can just install npm as is in your distribution package manager.

#### Tailwind CLI 
Install the Tailwind CSS CLI v4.0 or later:
~~~bash
npm install --save-dev tailwindcss @tailwindcss/cli
~~~

## Selecting your starting theme 
To select the theme of your website. The theme used as an example is [aafu](https://themes.gohugo.io/themes/aafu/). Get the GitHub repository link by clicking ***download.***

> It is important to note that almost every theme, has its own instructions. If you decide to use another theme, you will have to look at the repository instructions. If you are a beginer, or have no knowledge, chatGPT its a good friend.

## Set-up
To set up the files of our website, we can create a new website by running
~~~bash
hugo new site myNewSite
cd myNewSite
git init 
git submodule add https://github.com/darshanbaral/aafu.git themes/aafu
echo "theme = 'aafu'" >> hugo.toml
~~~

### Config files 
A general step to modify the themes is to copy the configs file into your root directory. In this step, we will copy more than just the config file; we will also copy some other dependencies.

- inside the themes/aafu folder. Copy the following to your root directory:
~~~bash
    assets/
    static/
    config.yaml
    package.json
    tailwind.config.js
~~~
or run:
~~~bash
cp themes/aafu/assets/ themes/aafu/static/ themes/aafu/config.yaml themes/aafu/package.json themes/aafu/tailwind.config.js ./
~~~

> if you are using windows, use ``copy`` instead of ``cp``

- Rename your config.yaml to hugo.yaml, and delete hugo.toml
- Inside your config.yaml, make sure that: 
~~~yaml
theme: aafu
~~~

- Test the website
~~~bash
hugo server
~~~
This should display the default information that the theme has.

## Making it yours !
To personalize it with your own information, we will modify the hugo.yaml we just copied.

Inside that file, the names of the different sections of the file are easy to see.
~~~yaml
title: #title of your site
theme: aafu #the theme you are using, remember to uncomment this 

#Inside params you will find the sections
params:
  profile:
  social:
~~~
To modify with your information, just change the information inside those parameters.

### Your image 
This file reads images from the static folder we copied. To change the default image, just replace it with your image and the same name. 
This also works for the page webpage icon

### Other files
To share other files like resume PDFs or project images, the files should be placed in the static folder; from there you can call them from the config file.

## Deploy
This guide uses github pages to deploy the website.

### Create an account
Go to github.com and create your account

### Create repository
To be able to deploy a website with github pages, you will etiher need a domain, or use github's free domain. 

- create a repos using the following name: ``yourUsername.github.io``
- Create a new directory called .github/workflows/hugo.yaml
and paste the content from this [file](/files/workshop/hugo.txt).
- Push your source code by running:
~~~bash
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/portfolio-site.git
git push -u origin main
~~~
- Visit your site at https://yourUsername.github.io 

### Update the content
To update the content that everybody can see, you will run these commands:
~~~bash
git pull
git add .
git commit -m "update"
git push
~~~


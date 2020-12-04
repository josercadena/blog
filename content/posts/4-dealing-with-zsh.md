---
title: "📌 Friendly reminder when dealing with zshrc.sh"
summary: Friendly reminder to myself
date: 2020-10-12T11:30:03+00:00
weight: 
aliases: ["/friendly-reminder-on-zshrc"]
tags: ["zsh", "debug", "personal notes"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: false
TocOpen: false
draft: false
hidemeta: false
disableShare: false
cover:
    image: ""
    alt: "<alt text>"
    caption: "<text>"
    relative: true
comments: true
---

<h1>Friendly reminder when dealing with zshrc.sh</h1>

This one is a quick note on zsh. I have recently decided to download [this awesome tool](https://ohmyz.sh/) to make my terminal look great (and get some useful plugins as well). I mean, together with the Dracula theme, it's just 👌👌👌 

![zsh](/images/4/zsh.png)


So, when I was getting this error on my screen, things were not so appealing to me... 

- ```bash
    [oh-my-zsh] Insecure completion-dependent directories detected:
    (...)

    [oh-my-zsh] For safety, we will not load completions from these directories until
    [oh-my-zsh] you fix their permissions and ownership and restart zsh.
    [oh-my-zsh] See the above list for directories with group or other writability.

    [oh-my-zsh] If the above didn't help or you want to skip the verification of 
    [oh-my-zsh] insecure directories you can set the variable ZSH_DISABLE_COMPFIX to 
    [oh-my-zsh] "true" before oh-my-zsh is sourced in your zshrc file.
    ```
Naturally, I googled this error and tried every highest rated answer crossing my way. But none worked!

So. Let's change the approach, let's do what the message says. Add a line before sourcing zsh...
- ```bash
    ZSH_DISABLE_COMPFIX ="true"

    source $ZSH/oh-my-zsh.sh

    ...
    ```

Well, that didn't work. Do you know **why**? 🤔 

This one did the trick though...

- ```bash
    ZSH_DISABLE_COMPFIX="true"

    source $ZSH/oh-my-zsh.sh

    ...
    ```

Can you spot the difference? A whitespace after the ZSH_DISABLE_COMPFIX keyword! A **whitespace**! 🤦

**Kids, don't forget whitespaces are important in bash.**
# Gridea - Build a Static Blog by Github Pages


I have been wanting to build a blog a long time ago, and I even applied for a domain and VPS. But I am lazy, to be honest, and don't want to spend too much time in building a blog. So I googled and found some methods to build a blog via GitHub Pages. Such as Hexo, Jekyll, and Gridea. Among them, Gridea is the easiest for me, as I feel more comfortable with a desktop app. So here we go! 
 
<!-- more -->

## Instal Gridea 
 
Go to the [Gridea](https://gridea.dev/) website. 
Scroll down to the bottom, download and install the desktop app (Mac OS / Windows / Linux)
My version is Ver. 0.9.2


## Create a GitHub Pages Repository

- Create a GitHub Repository, name it like “xyzabc.github.io”
- Settings -> GitHub Pages -> Choose any theme

## Create a token

- Log in GitHub account
- Click this [link](https://github.com/settings/tokens/new) to create a new token. 
- Check all repo authorization. 
- Click Generate new token
- Copy the token, note this token won’t show anywhere else, so you should keep it in somewhere. 

## Gridea Setup

- Click Settings in the Left Bottom corner, choose English, and choose the Site source file path. The default folder is fine with me. Restart Gridea. 
- Click Server in the sidebar, Basic Setting: 
-- Domain:xyzabc.github.io, 
-- Repository Name: xyzabc.github.io
-- Branch: master
-- Branch Username: your GitHub account, like “xyzabc”
-- Email: your email registered in GitHub
-- Token: the token created just now
-- Test Connection, and Save
- Comment Setting
-- Choose Gitalk
-- Turn on "Show comments"
-- Create a GitHub OAuth Applicatio. Click [here](https://github.com/settings/applications/new)
-- Write the Application name you like, such as Gitalk
-- Hompage URL: https://xyzabc.github.io
-- Authorization callback URL: https://xyzabc.github.io
-- Click Register application
-- Copy and keep the Client ID and Client Secret
-- Paste Client ID and Client Secret to Comment Setting
-- Repository name: xyzabc.github.io
-- Owner: your GitHub account name



## How to Use

Write articles with markdown, you can save and preview the blog first, then Sync Website to Github. You can refresh the blog if there is no update. 

## Some Chinese to English Converting

Due to it is too simple, the English translation is not completed yet. You can search Chinese characters with VS Code and replace them. 

There are two folders to be reviewed: program folder and local site source file path. Keywords are as below in case you don't know Chinese. 

Chinese|English
-|-
首页|Index
归档|Archives
标签|Tags
关于|About
微博|LinkedIn
Weibo|linkedin
下一页|Next Page
上一页|Previous Page
下一篇|Next
上一篇|Previous

## Add Mermaid Support

For now, only theme “fly” can support mermaid by some modification. Please refer to my [previous artical](https://zhiqiwang.github.io/post/adding-mermaid-support-in-gridea/) for more detail. 

## Some Known Issues

1. Time Zone is UTC/GMT+08:00 by default, and there is no way to change it. Every time when you save, the time would be convert to GMT+8 and shift a little if it's not set on purpose . I am looking for a solution. 
2. Some Theme Settings are written in Chinese, need to be replaced manually if English is needed. 
3. Floating TOC is not supported in theme fly. `@[TOC]` can be used anyway. 
4. Search is not support in most themes, if you want search function, please try gridea-theme-next, gridea-theme-pure, bitcron-pro. Just Copy files to `local site source file path\Themes\`
---

## Summary

Gridea is a great tool to build a blog via GitHub Pages, fast and simple. The English version is not polished perfectly, but I believe you can enjoy it with some modifications I mentioned above. Hope you have fun!


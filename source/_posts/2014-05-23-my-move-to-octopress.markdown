---
layout: post
title: "My Move to Octopress"
date: 2014-05-25 14:00:00 +0100
comments: true
categories: [octopress, windows]
---

So, a friend of mine was talking about this thing called Octopress and how he was moving his blogspot content across to it. I toiled for a while thinking that it wasn't something I needed to do right now, but in the end I gave in and spent an evening moving my own blog across (I only had 2 posts before this so I assumed it would be quick - and I was right). There are plenty of blogs describing the process of setting up an Octopress site using GitHub pages, so rather than regurgitate others material I'll talk about the bits that I got stuck with. But first... 

<!-- more -->

### Why did I move?
It's not hard to notice that I've only got two other posts on this blog. There's a couple reasons for that. The main reason is I don't like to repeat content that's already out on the net. I've had a few things to talk about previously but after having a look about it's already been done before, so why copy what's out there? Secondly, the sort of posts that I would like to write (like my De-Ice guide) would be in depth. Whilst I do enjoy blogging, using blogspot was a pain to use. Making everything look pretty using the formatting in blogspot was tedious and slow making me reluctant/too lazy to write big blog posts. 

Not so long ago I had been updating my README.md files in[ my GitHub repositories](https://github.com/NullMode) using a tool called [MarkdownPad2](http://markdownpad.com/). In the git fashion, I was writing the markdown locally, seeing the output of the markdown in MarkdownPad before pushing. After finding out how Octopress works the way I could push blog posts out was more appealing: I could create pages offline, work on them offline and see the preview of the generated output offline all before pushing it GitHub and using a very glorified notepad-ish tool. All along with simple and to the point formatting. Hazzah. 

###What is Octopress anyway?
For those who don't know what Octopress is, here's a small run down. Octopress is a Ruby on Rails application that is essentially a framework for Jekyll: a static website generator. This generated content can then be pushed up to a repository on GitHub, and then you can use GitHub pages to host it. Visiting the [Octopress](http://octopress.org/ "Octopress") site will give you some more information about Octopress.


### So what is markdown?
Markdown is language created for the sole purpose allowing people [“to write using an easy-to-read, easy-to-write plain text format, and optionally convert it to structurally valid XHTML (or HTML)”.](http://daringfireball.net/projects/markdown/ "John Gruber on Markdown") The [syntax](http://daringfireball.net/projects/markdown/syntax "Syntax") is so basic that makes knocking up a simple page (such as readme files for GitHub repositories) trivial. 


### Windows installation
The main bulk of my installation came from following the two guides below. This includes setting up: titles, a custom theme, adding posts and adding pages:

1. http://octopress.org/docs/blogging/
2. http://paulsturgess.co.uk/blog/2013/04/24/hello-octopress-and-github-pages/

Since I had ruby mostly installed on my system all I needed was to download and install the DevKit which is required for Octopress. The download for DevKit can be found on [Ruby Installer](http://rubyinstaller.org/downloads "Ruby downloads") website (make sure you get the correct version for your Ruby install).

### Bundle exec
On my shell in windows I was getting an error because the wrong version of rake was installed. Anyone who knows what they're going with Ruby knows that they can run the required version by using bundle exec (I had to look this up because I don't normally work with Ruby):

	> rake new_post["My move to Octopress"]
	You have already activated rake 10.1.0, but your Gemfile requires rake 0.9.2.2.
	Using bundle exec may solve this.

Simply prepend your commands within the application with "bundle exec", like so:
	
	> bundle exec rake new_post["My move to Octopress"]

### Adding a twitter recent tweet box
After being disappointed that a twitter box didn't appear after filling in my details in the configuration file I was pointed to [Jmac's](http://blog.jmac.org/blog/2013/03/30/putting-twitter-back-into-octopress/ "Jmac - Putting Twitter Back Into Octopress") post on how to put twitter back into Octopress. The guide was pretty easy to follow, although I removed the following line from the twitter.html page as it wasn't required for my theme:

```<h1>Twitter</h1>
```

### Custom favicon in Octopress
I wanted to use my old blog's favicon on my Octopress site. Presumably it would be a copy and paste win, however Octopress likes to have the favicon as a png file (yes you could edit some html to include the ico, but the following was faster for my lazy brain somehow). The main solution was found at the end of this [post](https://brianbuccola.github.io/blog/2012-11-29-how-to-change-the-favicon-in-octopress.html "How to Change the Favicon in Octopress"). Firstly I went to my old site (before the CNAME part below if you skipped ahead) and downloaded the favicon: http://blog.nullmode.com/favicon.ico. I then needed to convert my .ico to a .png file. Since I couldn't be bothered to use some fancy image library for converting the .ico which had been mentioned in a few guides, I simply went to [http://converticon.com/](http://converticon.com/ "Convert your ico files") for the conversion. With this new favicon.png in hand, I added it to my sources/ folder and ran `bundle exec rake generate` which added the favicon to my generated code.

### Pointing a custom domain to your GitHub Pages site
Most people want to have a custom domain pointing to their blog. The steps for this are really simple, [GangMax](http://gangmax.me/blog/2012/07/02/add-cname-for-my-octopress-github-pages/ "Add CNAME for My Octopress Github Pages") and [GitHub](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages "Setting up a custom domain with GitHub Pages") are both good guides on how to do this. However, remember how I said I was on windows? On my command line (PowerShell by default) I ran the following:

	> echo blog.nullmode.com > sources/CNAME	

That should be okay? Right? Well no. When I deployed my site with the new CNAME file I got an e-mail from GitHub:

	The page build completed successfully, but returned the following warning:
	
	Bad CNAME format: ÿþb l o g . n u l l m o d e . c o m

Weird right? Well, it turns out that when piping into a file with PowerShell it uses the encoding `UCS 2 Little Endian` (checking with Notepad++ on the encoding tab). To fix this I done the following using Notepad++: open said file, clicking `Encoding`, then selecting `Convert to UTF-8 without BOM` and saving. It turns out that using the old fashioned Command Prompt for piping the CNAME into the CNAME file uses the correct encoding. Committing and redeploying after the changing the encoding fixed this error.


### List of links

- [http://markdownpad.com/](http://markdownpad.com/)
- [http://daringfireball.net/projects/markdown/](http://octopress.org/docs/blogging/)
- [http://daringfireball.net/projects/markdown/syntax](http://daringfireball.net/projects/markdown/syntax)
- [http://octopress.org/docs/blogging/](http://octopress.org/docs/blogging/)
- [http://paulsturgess.co.uk/blog/2013/04/24/hello-octopress-and-github-pages/](http://paulsturgess.co.uk/blog/2013/04/24/hello-octopress-and-github-pages/)
- [http://rubyinstaller.org/downloads](http://rubyinstaller.org/downloads)
- [http://blog.jmac.org/blog/2013/03/30/putting-twitter-back-into-octopress/](http://blog.jmac.org/blog/2013/03/30/putting-twitter-back-into-octopress/)
- [https://brianbuccola.github.io/blog/2012-11-29-how-to-change-the-favicon-in-octopress.html](https://brianbuccola.github.io/blog/2012-11-29-how-to-change-the-favicon-in-octopress.html)
- [http://converticon.com/](http://converticon.com/ ) 
- [http://gangmax.me/blog/2012/07/02/add-cname-for-my-octopress-github-pages/](http://gangmax.me/blog/2012/07/02/add-cname-for-my-octopress-github-pages/)
- [https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages)
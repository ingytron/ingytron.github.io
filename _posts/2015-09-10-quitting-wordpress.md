---
layout: post
title:  "WordPress: I quit. Hello, Jekyll"
date:   2015-09-11 22:47:40
categories: coding
---

WordPress and I have been friends for about eight years. I'd been a fan of using Drupal (before deciding that it was overkill for those "one website please" requests) and used Magento on a few projects. WordPress edged out the competition as time went by, because they were constantly improving their user interface, things became easier and slicker, and they brought out integrations that made it so that you didn't have to use anything else (the content management, the WooCommerce integration and so forth). All of this was great.

However, in practice, I found that I was generally spending time on maintaining the sites rather than creating content and coding. There were always updates that needed to be done. Spam was mitigated with Akismet but my very low-traffic servers were always being pummelled by fraudulent login attempts (there are ways to get around this but it was still annoying). I have cleaned up a fair few hacked servers, of my own and clients, and to make life easier, I ended up having to buy security plugins. The WYSIWYG system sometimes created crazy code, and in my WP multisite network I had at least 30 plugins installed for various reasons. Crazy. I wanted to have a simpler life in which I don't wrangle with dozens of plugins and themes and updates. 

I came across the article <a href="http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html">Blogging like a hacker</a> and was intrigued from the start as I'd felt the same pains with WordPress. I decided to check out <a href="http://jekyllrb.com/">Jekyll</a> as it sounded very promising, plus you can use it with GitHub Pages and get free hosting, and you can use a custom domain. Most of my efforts these days are on GitHub so this was a perfect option. I like that my blog will now have version control and be easily updated from my own text editor (or using GitHub's online editor) and not need to go through the logging in, doing updates, etc, WordPress blogging process.	 

<h3>Getting Started</h3>

The first thing I did was look at my old blog, which I seldom updated (I'm not much of a blogger, really) and decided that my old posts weren't really in line with my current efforts, so I'm not importing the old blog content. I did export my WordPress blog just in case I decide to use it later, however. 

I downloaded <a href="http://jekyllrb.com/">Jekyll</a> and installed it as per the documentation. I added Bootstrap by adding it to the head.html file which comes with Jekyll (I've seen other people do this in various ways, but it worked for me) and I added FontAwesome and jQuery also. Jekyll is neat and simple, built with Ruby and very lightweight.


<h4>Resolving Build Errors</h4>

I had a bit of an issue with my initial repo, because I created a README.md file and so I was getting conflicts when I tried to do a git push to the repo, and doing a pull wasn't resolving it either. So I deleted and recreated the repo, this time without a README.md file and then added the remote repository through the command line. 

I created a Gemfile and added the following to enable GitHub Pages support:
<code>
source 'https://rubygems.org'
gem 'github-pages'
</code>

Everything should work after that, right? Unfortunately not. I was able to git push now but I was getting a build error and accessing the page was giving a 404 error. I got an e-mail from GitHub that said

<code>The submodule `voodoobettie.github.io` was not properly initialized with a `.gitmodules` file. For more information, see https://help.github.com/articles/page-build-failed-missing-submodule.
</code>
This was weird because I hadn't created any submodules at all, yet the build would consistently fail. I tried to switch to a ghost branch and back but to no avail. Eventually, after re-examining my files on the repo, I noticed that I had a folder with my repo name in it (voodoobettie.github.io/voodoobettie.github.io), so I deleted that and did a <code>git add --all</code> and that resolved it. 


<h4>Redirecting my domain</h4>

I created a CNAME file in my GitHub repo, and created an A name record at my provider. Easy peasy, literally you just create a file in your repo called CNAME and then put your domain name in it, save and done. 

<h4>Making things better</h4>

I felt that there was some functionality still missing from the new site so I did a bit of googling and found some useful tutorials on extending the functionality of Jekyll. 

<a href="http://joshualande.com/jekyll-github-pages-poole/">Adding a Twitter sharing link</a>


<h4>Next steps</h4>

I'm still in the process of getting this site to the way I want it set up. I will add bootstrap via the Gemfile soon (now that I have one) and do some more configuration, but overall I really liked the way that this site was fairly straightforward to set up with Jekyll.

{% include twitter_share.html %} 

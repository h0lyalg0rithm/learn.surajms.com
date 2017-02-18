---
layout: post
title: Setting up this blog in less than a minute
---
Jekyll ❤️️ Github

I decided to host this blog through github as it took care of both the version control and hosting of the website.

To my amazement the blog took less than a minute to setup.

I had the local version the blog running on my machine for a day now.Here is how I set it up.
- I add a CNAME file to the root directory of the blog.In my case since the url for the blog was learn.surajms.com. I wrote it on the file.
- Push to Github
- Go to the repository settings in github and change the branch in the Github Pages to the master branch.Thats it your website is hosted by github.
- Visit the your domain/dns provider and I create an A record which points to Github's ip (192.30.252.154).

Thats it folks

The website should now be accessible by anyone.
 

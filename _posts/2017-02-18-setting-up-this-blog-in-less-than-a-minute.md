---
layout: post
title: Setting up this blog in less than a minute
---
### Jekyll ❤️️ Github ###

I decided to host this blog through github as it took care of both the version control and hosting of the website.

To my amazement the blog took less than a minute to setup.

I had the local version the blog running on my machine for a day now.

This is how I set it up.

- Add a CNAME file to the root directory of the blog with the url of the blog.In my case since the url was learn.surajms.com.
- Push to Github.
- Go to the repository settings in github and change the branch in the Github Pages to the master branch.Thats all there is.The website is now hosted by github.
- Visit your Domain/DNS provider and create an A record which points to Github's ip (192.30.252.154).

Thats it folks.

The website should now be accessible by anyone.

---
layout: post
title: Lets pretend to be the internet! 
---

I was recently approached about using Selenium or some other software to write a macro to handle a repetitive business process. While I've never worked with technologies like that I think it will be a fun challenge to work with both datafiles and an external site. 

During my research I saw something promising called Nokogiri and I hope that is as simple to use as it seems. I can't wait to get into the weeds and see just what kind of aneurysm doing this will cause me.

My plan for this project is to first reliably parse the datafile, and then separately get a function working that can work with the remote site. Ideally each part can be built modularly so that connecting to the site will be one issue, searching on it will be another, and verifying the results would be a third. By breaking it up like that I can wrap that entire section in a single function that takes in the account number and simply returns a boolean reflecting the status of the account. This project strikes me as one where it would behoove me to have as few moving parts as possible.

Maybe I'm wrong. Hopefully I'm wrong. This should be fun

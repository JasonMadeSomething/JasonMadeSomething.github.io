---
layout: post
title: Who does the thinking?
---

#### When does the human get involved?

I've been working on a simple script for tracking barcodes and it has gone through a few iterations since I started. At first I had to scan everything directly into the input for the program (yuck) but then I had the clever(?) idea to just scan everything into a text document and have the program read that. This cuts down on weird scans or having to start over from scratch if a particular ID can't be found because I haven't updated the directory right. So as it stood things went swimmingly where I would just scan things in, a new CSV would be generated, and I would file things away from there.


But then I went and made the mistake of thinking some more. I realized that I could just make my script file the files away like I would manually which would save some time, but I also worry that in case something weird does happen I would have a lot more back tracking to do in order to clean up after the failed execution.


So as I wrestle with this does anyone know of a better way to handle this? Maybe using a try block that cleans up whatever I made in case of failure, though that is an area I'm weak in. 


So for now my scanner stays as it was, but given some time I'll make it smarter yet!

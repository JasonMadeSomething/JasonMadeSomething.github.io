---
layout: post
title: Everything is always broken forever

---

### Just a few months

I was always told to include comments in my code, and today I am really starting to see why. Although I'm in the middle of trying to tease out an issue heroku is having with my 6 month old app, I'm noticing that I'll still be sorely lacking in documentation even when I do get it working.

Though this also raises the question of where information like "forgot to push updated databse to heroku" goes. I assume it would go somewhere in the Readme, but information like that seems like it can either be useful down the line, or wind up only being needed once. This seems like an area I should look more into so I can get some clarity on where I should be taking notes. (that being said my commenting is atrocious, so that'll just have to be where I start).

Reverse engineering my old projects to figure out what I was trying to do is proving to be quite the frustrating exercise. "Documentation Documentation Documentation" needs to be my new motto. What's been making this even more interesting is that even though each app appears to be failing the same way on heroku, but on closer inspection they aren't working for totally different reasons. 

My [Bloccit](https://rocky-gorge-8621.herokuapp.com/) app seemed to be fixed by allowing the user to see full error messages (which feels far too hacky to be the real answer), while my [Blocitoff](https://arcane-fjord-2494.herokuapp.com/) app appeared to stop working entirely whenever it needed to send an email. 

Initially I was drawn to the `ApplicationController` because the development server was reporting that the parameter sanatizer had been depreciated. After I changed this the app worked in development mode, but still wouldn't in production. Because the error Rails was reporting appeared to point to the SMTP settings, I decided to check my mail initializer. I then realized that all of the sensitive smtp information was stored in environment variables and after a quick check of the figaro docs I realized that because `application.rb` was not being uploaded by git, only the development and test environments had access to the mail API. I was able to quickly fix this with instructions from the figaro docs detailing how to get environment variables into the heroku environment.

I think the most surprising part about all of this is how months ago I thought this project worked, and while one update did change something in it, it seems like it should have never worked in the first place.
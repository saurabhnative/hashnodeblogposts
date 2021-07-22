## Learnings from daily dev job - Part 1

Hello everyone, so today I'm starting a new series in which I'm going to share a few programming tips which I learn from my day to day job on my own and with my colleagues. So let's begin with the first tip...

### Which side to choose when a bug can be fixed from both backend and frontend?

When a bug can be fixed from let's say backend as well as the front end side then which side should we choose from?

The first thing which we can consider in this case is whether our application is cross-platform and whether a back end fix will fix the bug both on the website as well as a mobile application. In that case, it makes sense to fix the bug from the backend.

The other scenario is when the bug is specific to a single platform like let's say web or mobile and backend fix might not fix it for both platforms at once. In that case, it makes sense for the frontend developers to take initiative to fix the bug from his/her own side instead of waiting for the backend developer to take the initiative and fix it from their end. 
If it is not fixable from our own end at all or if it is easier to fix it from the other end then picking up the other side for a bug fix makes sense.

### Smaller PRs makes life easier for reviewers as well as future project maintainers
Let's just say you have a big feature in which you need to make a lot of changes in your code. In that case my advice is to break that feature into smaller modules and create pull request in smaller chunks, because the thing that happens is, if your commit is huge with lots of files into your committed code for a particular pull request, then the person who is going to review your pull request might feel like it's a headache for him/her to review all those file changes at once. 
That is why it is advisable to break down your changes into smaller modules and create smaller PRs. Then send them to your reviewer, so that he or she is able to review them properly and tell you where the actual issues or corrections might be required. 

There is a popular saying he goes by if your PR is 500 lines of code there won't be any single review comment and if you have committed just 10 lines of code, you might have 5 to 10 corrections in that:-

![CodeReview.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626943340934/3P2h1uOcR.png)

That's actually true because larger files or code changes, tend to get ignored and smaller ones are easy to review. So my tip for the day is to make sure to divide your entire module of code changes into smaller chunks and get smaller PRs reviewed daily so that the code reviewers don't have to review through a large quantity of code at once missing useful fixes and bugs. It is generally good practice for us to create smaller PRs also because future maintainers of the project are able to see changelog or history easily and make sense of what happened in the project when a particular pull request was merged into the project. I have personally made the mistake of committing huge chunks of code in a single PR a lot of times in the past. But currently, I try my best to make sure there are not a lot of code changes in a single PR for review.

That's it from for this article. If you found this article useful hit the like button and follow me to learn more about such small but useful tips in future. Also if you have any different opinions on the topic than my own then feel free to share them in the comments. I am not a subject expert in these things and would love to learn from your opinions, perspectives or points as well.  

Have a nice day ahead 👋🏽
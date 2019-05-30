# Technical Interviewing General Advice

How to present yourself as a hire-able candidate

note: today we're going to talk about how you can make yourself more desirable as a candidate
---

## What are employers looking for?

![beer-test](http://www.cheatsheet.com/wp-content/uploads/2015/08/Coworkers-at-bar.jpg)

Note: ok so let's talk about what employers are looking for
---

## What are employers looking for?

Passing a technical interview is about knowing the right stuff and communicating that you know it

Note:
It really boils down to just a few things
* Ability to work through a difficult problem and utilize different tools
* Good design decision making -- clean, readable, maintainable code
* Familiarity with a variety of “basics” that all software developers should know
* Good communication skills & fit with team members  

---

## The application pipeline

* Phone Screen (20-45 minutes)
* Coding challenge or project (2-8 hours)
* Technical phone or video screen (45-60 minutes)
* Onsite (3-6 hours)

Note: The typical application pipeline consists of a phone screen followed by a coding challenge or take-home project followed by a technical screen followed by an onsite.  You may see some variations in this pattern but usually this is the process.

---

## General advice for phone screens

* Don’t rush
* If it’s technical, have something to write on- “Writing things down helps me keep track of my thoughts, would it be cool if I jotted things along the way as I explain?”
* If it’s behavioral, have your PAR chart in front of you!

Note:
Make sure you take your time!  For technical screens it's essential that you have a pad and pen to work through problems and take notes.  For behavioral screens you should not only have your PAR sheet in front of you, but also your resume, and project githubs open for reference as well.
---

## General advice for coding challenges

* Coding style and presentation
* Efficiency and modularity
* Good documentation
* Write tests!! (new workshop for this on W13)

Note:
Pay attention to your code style!  Lines shouldn't extend past 80 chars.  Use classes where appropriate.  Helper functions are your friend!  Remember great code should read like English.  If theres a part of your implementation that's hard to read you should ask yourself if this can be abstracted into a cleverly named helper function.  Remember each function should do one thing.  Same for classes and files.  Be sure to document your project and write tests if there's time!!

---

## General advice for onsites

* Ask clarifying questions
* Communicate your approach
* Communicate throughout
* Write examples
* Clean coding style and presentation
* Be mindful of time and space complexity
* Provide alternatives
  * Efficiency
  * Modularity
* Be persistent - NEVER GIVE UP!

Note:
Ok let's dive into the technique for solving whiteboarding questions in an onsite. Generally you should start by clarifying the problem and testing I/O as well as edge cases.  Then you're going to formulate your approaches.  After you've gotten a few approaches worked out you'll pick the best one and pseudocode it - very high level almost english explanation of what you're about to do.  Important to write it down.  Then you'll implement it, walk the interviewer through an example input, and finally provide the Big O analysis of the algorithm you wrote.  If there's any time remaining you should spend it attempting to further optimize your implementation.

---

END VIDEO 1

---

## Knowledge and Trivia Topics

* JavaScript
* Rails
* Ruby
* SQL
* HTML/CSS
* React/Redux
* Web Architecture/Scaling

Note:
“Why are they asking you these questions? It's to find out: Do you have a baseline understanding of various important subjects in web development and can you communicate your understanding well?”

---

## Examples

* What is the event loop? How does it work?
* What happens when you type in ‘www.google.com’ and hit enter?
* Talk about the 4 types of positions in CSS

Note:
* What's your favorite thing about your favorite language?
* What is a load balancer?
* What does it mean for a web page to be responsive?
* What is a hashmap? How is it different from a hash table?
* What are the differences between XSS and CSRF?

---

## Succeeding at trivia

* Take a couple of moments to think
* Structure your responses
* Make a thesis statement
* Use an example to illustrate the idea
    * Example should be small and show benefits of tool/concept

Note:
Think before you speak then try and give a high level overview or thesis statement of how the tool/technology works. Then use an example to demonstrate it.

Example:
What is the event loop?

Thesis statement: “The event loop is essentially a queue of callback functions. To fully explain the event loop, we have to understand how the JavaScript call stack works, how async functions are executing, and then finally how the event loop handles those callback functions.”

You should already be familiar with the event loop from the JavaScript lectures so I won't expound on it further in this video.

---

## Practical Coding Challenges

* Build Something
* Make calls to an API
* Debug
* Refactor

Note:
Go ahead and note the topics that are likely to come up in practical coding challenges.
These types of coding challenges can be either take home or done live in a shared coding document
---

## Project Examples

* Build tic-tac-toe in React
* Build a digital clock using only vanilla JS, HTML, and CSS
* Here’s some broken code - fix it

Note:
* Write a debounce function
* Make a simple todos CRUD app in a tech stack of your choice
---

## Live Coding Tips

* Waste as little time as possible on setup
* Practice effective communication
* Remember to test
* Analyze along the way

Note:
Here's some tips for when you have to perform live.
You should practice writing boilerplate code so that your setup is fast. Boilerplate includes your react component framework, your script tag for JQuery, html and css structure, backend scaffolding etc.

Try to channel your pair programming experience!
and don’t wait until you’ve coded up the entire problem before testing to see that it works!


---

## Succeeding at practical challenges


* Keep coding - don’t let your skills get stale
* Spend 2.5 hours working on projects or practical coding challenges per day
* Focus on deepening your understanding as you code
* Hackathons

Note:

* Success or failure of these challenges will be determined by the amount of time and effort you put into your daily practice leading up to them - Similar to a sporting event or musical performance. Pay attention to the task at hand and don't just copy and paste things from around the internet without understanding them.  Finally hackathons are a great way to get good technical practice in if you're fresh out of new project ideas.

---

END VIDEO 2

---

## Architecture and system design

* Typically big, vague, broad questions  
* Often times more pseudocode and high level discussion than actual coding
* Practice good judgement and thoughtfulness in design
* Be aware of what’s out there

Note:
Architecture and System Design can sometimes be the most intimidating due to their vagueness, with that said though the implementation is usually far easier as it's often just a high level discussion and maybe some pseudocode.

---

## Examples

* How would you design a URL shortener?
* Design Twitter
* How does a website scale?

Note:
Can also be non digital, for example - let's design a parking lot.

---

## Succeeding at Architecture Questions

* Start with making sure you understand the end goal
* Make it conversational
* Diagrams and visuals (use whiteboard or paper)

Note:
As an aside if your tasked with building something like twitter or Uber or a project management app or something similar, your main focus should be the user and crafting things in a way that make sense if someone were actually going to use this app.
---

## Preparing for Architecture Questions

* Read 1 High Scalability article per day to get acquainted with the different tools available and their strengths/weaknesses.
* Be ready for the frequently asked questions
* Practice doing this with your everyday websites

Note:
(Pay attention to the Web Architecture section when you get to it)
For example, what is a NoSQL database, why use one? What are its strengths and weaknesses?  (as you read, research the topics you’re not familiar with, make flashcards out of them)

---

## After the Interview

* Always do a debrief
    * What questions did you struggle with and why?
    * What topics came up?
    * Go one level deeper
* Interview DB
* Get feedback if you can
* Follow up with your interviewer
* Don’t take rejection personally; learn from it and push forward
* Keep studying!

Note:
Debrief can be by yourself or with your coach (spoiler: it should be both).  Don't neglect interview DB!!!!  It helps us all learn.  Don't take it personally:  This might be the hardest part, but it's also the most important for your mental health.  There's millions of reasons outside of our control why we do or do not move on to the next step or get the job.  Every phonescreen, onsite, etc is a learning opportunity, and practice IS perfect.

---

End Video 3

---

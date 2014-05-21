---
layout: post
title: "Penetration Testing With Backtrack - OSCP"
date: 2013-05-11 12:00:00 +0100
comments: true
categories: OSCP
---


### The course
The Penetration Testing with BackTrack (PWB) course is one which covers a lot of topics and genres, will push you to your limits, and make you forget what sleep is. The remote lab covers multiple networks, each with machines varying in difficulty and types of vulnerabilities. I cannot go into too much detail due to the non-disclosure agreement students make with Offensive Security. The best insight as to what is covered in the course can be viewed here in the [course syllabus](http://www.offensive-security.com/documentation/penetration-testing-with-backtrack.pdf) (this is what got me initially interested in the course). Be aware that the lab book will go through a large selection of topics, but independent research will be required. Expect to be surprised in the labs.

To start with a few quick notes to people that might be reading this.

### Le background
Before I start rambling on about my experiences and information about the course, it is worth noting my past experience. Before taking the course my main programming strengths were PHP and Java (guys don't shoot me). I had some basic web app exploitation knowledge and a some Linux experience.

I was advised to tackle some free systems that have built-in vulnerabilities (listed at the bottom of this post). All of these applications were Linux based, they were fun to do and gave me deeper insight into service enumeration, web-based attacks and kernel exploitation. I am glad I decided to do these boxes as it gave me a bit of a starting knowledge. However, if you are new to this game as I was (and still am) the offsec course will throw a hell of a lot more at you than these machines will. 

**If you're new penetration testing** and have similar experience to me then this course may not be for you. I encourage you to read this post as I will attempt to put things into perspective about the time it takes, and the factors that helped me succeed in the time I did. Believe me when I say that if you're new, it's gonna hurt, it's going to take time but it's gonna be fun. 

**If you're not new to penetration testing** this course may be great as a "refresher" or something to do to get some additional practice. It may even be a case of doing it to get the cert for your resume. If you're a fully-fledged pen tester you will probably (and hopefully) fly through the course.

### Many thanks
I am very lucky to have and made a few good friends that have guided me and supported me throughout this course. Without them, I would not have learnt and grasped as much, and would certainly have not popped as many machines as I did. If you're one of the people that helped me in this course (and you will know who you are) thank you for teaching me how to fish. 

### The adventure
I booked the 60 day option for the course, knowing that I would at least need this amount of time to get to grips with the materiel and make a good start on the labs. I made a point of downloading and looking at the course syllabus to see what I was letting myself in for. Well, to me it looked fun. The course covered a wide range of topics which tickled my fancy.

I took 2 weeks off my job at the time to work through all of the material. I took notes, screenshotted everything and completed near enough all of the exercises. For me, this is the only way for stuff to sink in (plus I wanted to get my money's worth). I had half hoped I could get through the PDFs and videos quickly, however I found that even after my 2 weeks off work I still had some stuff to do. I put this down to my overly-keen documentation, but I don't regret this at all. I now have a massive KeepNote file I can reference in the future.

I moved into the lab environment and quickly got to grips with a few of the tools described in the lab book. I started off by looking for the "Low Hanging Fruit". See port X open, exploit with Y. I soon broke into a few machines using some of the basic exploits and vulnerabilities described in the material. After about a week I had a small collection of machines under my belt, and a lot of information collected.

It was at this point I felt I was tackling the course the wrong way. I started brute forcing my way into servers. I'm not going to let on exactly what I was doing because I don't want to ruin the course for others. Long story short: I ended up taking "the easy route". After chatting with a friend I could sense he was either face palming or shaking his head. After a small discussion I took it upon myself to break into the remaining machines (and the ones I had brute forced) through their intended vulnerabilities. 

Now I know for a fact that in an actual penetration test, some of the techniques I used to pop boxes so quickly are vital (as time is usually of the essence). However, I did not want to go down this route as, for me at least,  more knowledge was to be gained by breaking into machine the hard way. After I cleared my conscience I started popping through boxes again, I found that I was getting a lot more satisfaction and "awwww yeah!" moments when getting system/root on servers. 

I extended the course by another 30 days so I could attempt to break into all the boxes. I really started picking up the pace at this point. I was popping at least a machine a day. The course material had finally sunk in better after some initial exposure to the labs; things were falling into place where they hadn't before. I started to find myself thinking more logically about the problems I was facing with a tough box, thinking back to basics, and finding out stuff I had missed. I popped the majority of the machines when my lab time ran out. I also took the time to break into everything again, save commands used, their outputs and save the screen shots. I did this more for myself so I had something to look back on after the course. It took me a good couple of days to do this, but I don't regret this at all.
  
### Exam
I booked my exam around about a month after my lab time had finished. I relished the time to relax a bit and not have to spend endless hours on the course. Looking back, I think that a month was too long to wait for the exam. I would say two weeks would have sufficed, giving me time to finish writing the lab report and preparing for the exam. In fact, I think the exam would have gone a bit easier as the course material would have been fresh in my head.

The exam lasts for 24 hours, I decided to opt for a afternoon start and prepared myself with a bit of a lay in. It was probably one of the most intense 24 hours of my life but it was certainly worth it. Within 72 hours of submitting my lab and exam reports I got this in my mail box:

**We are happy to inform you that you have successfully completed your Certification Challenge and obtained your OSCP certification.**

### Summary
Overall I really enjoyed the course. From starting with quite a small amount of knowledge I managed to gain a great understanding of the basics. Being thrown in the deep end is a great tool for learning, it makes you look up things that may not work, but at least you learn why it doesn't work and gain additional knowledge from doing so. New or Professional, there is something in this course for everyone. Learn the basics, hone your skills, or get a certification for your resume. 

Help and guidance
The [#offsec](irc://irc.freenode.net/offsec "#offsec") IRC channel on freenode is always active, and there should always be an admin around. You can get some "hints" with a specific machine you can !machinename in their IRC channel (some troll messages too). The forums are also a treasure trove of past posts that can be helpful if you're stuck or if you're having a problem with a particular box or lab module.

Course advice
If you get stuck on a box try to think back to basics. Enumeration is the key! Look back on the techniques you learnt from the material to finger print, banner grab and enumerate services/web applications. Google is your friend! Try to solve things yourself before asking others, especially when the question is one you find the answer for in a 10 second google search. Finding the solution yourself will also give you a better feeling then if you're just given the answers. Remember, in the real world, if you're stuck trying to break into a machine whilst on a pen test, who is going to spoon feed you then? Don't be too scared/lazy to read things! Try and do things the hard way if possible, the feeling you get will be great, and the amount of knowledge to be gained is worth it's weight in gold.

Before taking the course
Check out VulnHub (linked below) or similar sites to get a feel for what the course is going to offer. The machines I played with before starting the course:

- Kioptrix Level 1
- Kioptrix Level2
- De-Ice Disk 1
- De-Ice Disk 1.1
- De-Ice Disk 2.1
- DVWA (Damn Vulnerable Web App)

I would also suggest the following machines:

- Metasploitable
- Metasploitable 2

There are plenty of other free resources on the web, to list a few:

-  http://www.hackthissite.org
-  https://www.corelan.be
-  https://www.hacking-lab.com

### Links
- [http://vulnhub.com](http://vulnhub.com) 
- [http://www.offensive-security.com/information-security-training/penetration-testing-with-backtrack](http://www.offensive-security.com/information-security-training/penetration-testing-with-backtrack)
- [http://www.offensive-security.com/documentation/penetration-testing-with-backtrack.pdf](http://www.offensive-security.com/documentation/penetration-testing-with-backtrack.pdf)
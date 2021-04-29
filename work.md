---
layout: page
title: Sample Work
permalink: /work
---

### carbonOS

carbonOS is a Linux-based operating system and software platform I created and
maintain. Its main goal is to bring mobile-quality user experience to the desktop.
I do this by modernizing the software stack and by replacing certain assumptions
about traditional OS design with careful UX-driven consideration.

For example, Linux is all about packages. A traditional Linux OS will distribute
itself as a collection of packages that get assembled and maintained by a package
manager. System updates are simply package updates, and the package manager gives
users a broad range of software they can choose to use. Package managers are both
an amazing technical feat and the downfall of the Linux user experience. Users
do not care about packages; users care about their work and the apps they use to
get it done. carbonOS does not have a package manager. The OS does not rely on
packages; instead, the entire OS is a single collection of files that are protected
via various mechanisms. This technical decision heavily impacts user experience.
User’s cant go and modify any system components anymore without acknowleding that
they’re about to do so and that they will break things, ensuring consistency between
copies of carbonOS. Packages are replaced by apps and an app store. The OS can
update itself completely silently in the background, only occasionally asking
for a reboot. The OS can even undo botched updates if something goes wrong. The
very core design decisions of carbonOS ensure that, to a user, it’s a piece of
software that just always works and that they can rely on and trust to run their
apps.

Working on carbonOS has given me huge amounts of computer science experience. I
learned about OS design, about orchastrating large software stacks, and about
low-level programming languages. I learned how to debug software through multiple
layers in an OS and how to trace through code in low-level software. I learned
about the firmware, the boot process, and about the bootstraping an OS has to go
through to get itself running. I learned about maintaining and updating large
software systems. I learned a lot about the various layers of the Linux graphical
UI stack. Working on carbonOS has been equally as challanging as it has been
rewarding.

![carbonOS's Graphical Environment](/assets/gde.png)

[Project Website](https://carbon.sh)

---

### FTC Robotics

The FIRST Tech Challange is an engineering robotics competition I participated in
in high school. I worked on a team of about 20 people, and we designed, documented,
programmed, and tested a robot to perform pre-defined tasks, both autonomously and
via remote control. I was both the team’s programmer and the team captain: I’d
often have to make decisions that contradicted my interests as the programmer
but led directly to a better product. 

This project was real engineering experience, and it taught me how to not only
participate in a team of engineers but how to run one. It also taught me how to
use code to control mechanical devices such as motors, and I had to learn how to 
implement comptuer vision so that the autonomous mode could make decisions based
on its environment. Here, the focus on quality was essential, because without it
the robot would not only get penalized points-wise but it could also be a safety
risk to itself and to the people around it. My team received the Excellence in
Control Award for my software work on this project.

<p style="margin-bottom: 0px;">Project websites:</p>
- [2018-2019 Season](https://github.com/us-robotics/RoverRuckus)
- [2019-2020 Season](https://github.com/us-robotics/SkyStone)

---

### GEM

GEM was a music player app that I developed in response to a new design language
created by Google in 2014 called Material Design. At their demo, Google showcased
a music player that many people, including myself, fell in love with on sight.
Google later confirmed that it was just concept art and that they were not working
on building a music player that looked like that. So, at the age of 13 and with no
experience in Java or Android, I decided to take up the mantle.

The project was a stunning success. I taught myself Java and Android entirely
through this project, and it directly led to the creation of two Android libraries
that other music players used back then. I taught myself GUI development principals
that I use to this day. GEM was my first open source project. I managed to implement
Google’s concept UI in its entirety, and I published the app to the Google Play
store to relatively large reception. I had 550 monthly active users, and I received
emails from a Chinese app store asking me if they could translate my app into Mandarin
because they have a few hundred people using it in China. GEM taught me a lot about
comprehensive UX: I started out with many bad decisions that led to rewrites. Overall,
GEM was a great learning experience for me.

[Project website](https://github.com/SubstanceMobile/GEM)

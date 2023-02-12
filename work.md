---
layout: page
title: Sample Work
permalink: /work
---

### carbonOS (2018-present)

carbonOS is a Linux-based operating system that I created and maintain. It's
primary goal is to bring a mobile/Chromebook level of stability, security, and
UX to the Linux desktop. I do this by modernizing the software stack and
replacing certain assumptions made by traditional Linux distributions.

Part of carbonOS's philosophy comes from my interest in the intersection between
complex software stacks (like an OS) and UX. I believe that apps cannot provide
users with great experiences if the platform they are running on is not designed
from the ground up to focus on UX. Analogously, a platform cannot provide a good
UX unless its architecture is built on a foundation of usability and robustness.  

For example: traditional Linux distributions are all about packages. Such an OS
will distribute itself as a collection of programs that get assembled together
and maintained by a package manager on the client system. System updates are
simply a collection of package updates, and the package manager is the primary
way for the user to install the software they need to use.

I posit that most users don't actually care about packages or Linux tradition.
Users care about being able to do their work, by using the apps they need to use.
Package managers are not necessarily productive to that end, and often they
end up inhibiting users' understanding of their systems: packages blur the line
between OS and App, which can lead to user confusion. Packages also make systems
fragile, because they allow users to take apart their systems in ways that leave
them *somewhat* functional. A catastrophic example of all these forces working
together against users is the instance when Linus from LTT accidentally
uninstalled his desktop environment while trying to install Steam
([video](https://www.youtube.com/watch?v=0506yDSgU7M))

carbonOS replaces a package manager with two separate subsystems: an image-based
OS updater, and an app store. This allows carbonOS to protect the operating
system's files through various mechanisms, while users can continue installing
whatever apps they want. This system allows carbonOS to silently update itself in
the background, and it can even undo failed system updates! This model provides
the robustness necessary to build a great UX on top of it: users don't ever have
to open the terminal, since things that are dangerous on a traditional
package-based system are now perfectly safe to do automatically in carbonOS. 

Currently, I have work ongoing to implement secure-boot and TPM-backed data
encryption into carbonOS. This means that, on startup, carbonOS will cryptographically
verify the integrity of every bit of OS code, and the system will boot and decrypt
user data only if the system hasn't been tampered with.

Working on carbonOS has given me huge amounts of computer science experience. I
learned about OS design, about putting together large software stacks, and about
low-level programming languages. I learned how to chase bugs through multiple
layers in an OS and how to trace through code in low-level software. I learned
about the firmware, the boot process, and about the bootstrapping an OS has to go
through to get itself running. I learned about maintaining and updating large
software systems. I learned a lot about the various layers of the Linux graphical
UI stack. And through carbonOS I am learning more about OS development every day.

[Project Website](https://carbon.sh)

---

### Caesar Creek Software (Summer 2022)

For [CC-SW](https://www.cc-sw.com/) I built a tool that automates creation
and management of Wireguard VPNs on public clouds (DigitalOcean, Google Cloud,
and Vultr). 

Basically it worked like this: you can create tunnel by listing a cloud + datacenter
to route through: `tunnel create --hop digitalocean:nyc1 tunName`. This creates
a VPS in the datacenter and configures it to be Wireguard VPN. Once the tunnel
is up, you can use it by running software in it: `tunnel run tunName command`.
Whatever you run in a tunnel will only have access to the internet through the
tunnel. When you're done using it, you can clean up by destroying the VPS:
`tunnel destroy tunName`.

---

### Graphite Desktop Environment (2018-2022)

The Graphite Desktop Environment (GDE) was the GUI of carbonOS from 2018
through 2022 (it was replaced with GNOME shell in October 2023). It ran on top
of the [Wayfire](https://wayfire.org/) Wayland compositor, and used GTK to
implement the essential components of a Linux desktop. Here's a screenshot
of what it looked like:

![carbonOS's Graphical Environment](/assets/gde.png)

GDE development has exposed me to a comprehensive list of technologies that
power the GNOME desktop stack, and has given me experience working with and
developing for them. I have the experience that gives me an intricate
understanding of how GNOME and GNOME-like desktops function: what components
provide what functionality, how the session is started, etc.

[Project Archive](https://gitlab.com/groups/carbonOS/gde/-/archived)

---

### Upstream Contributions (ongoing)

As part of my work with carbonOS and related projects, I've contributed code
to various upstream projects. Here are some of my contributions to notable
upstream projects (some of which are still being reviewed):

- systemd [#21570](https://github.com/systemd/systemd/pull/21570): Added
  functionality to the systemd-boot stub (part of systemd's
  [UKI](https://uapi-group.org/specifications/specs/unified_kernel_image/)
  framework), to load [credentials](https://systemd.io/CREDENTIALS/) from
  a system-wide location in the ESP. This allows multiple UKI images to share
  credentials on a given system.
- find-debuginfo [patch](https://sourceware.org/pipermail/debugedit/2022-June/000155.html):
  `find-debuginfo` used to be part of RPM, and was used to separate debuginfo
  from ELF binaries as part of a package build. It has since been upstreamed into
  the [debugedit](https://sourceware.org/debugedit/) project. My patch further
  decouples `find-debuginfo` from the RPM build environment, while maintaining
  backwards compatibility
- mutter [!2653](https://gitlab.gnome.org/GNOME/mutter/-/merge_requests/2653):
  Researched the default UI scale of various HiDPI devices sold today. Used the
  data I collected to replace Mutter's scale-factor selection code with an 
  algorithm that picks much more appropriate scale factors.
- gnome-shell [!2507](https://gitlab.gnome.org/GNOME/gnome-shell/-/merge_requests/2507):
  Implemented a new mode for GNOME that temporarily inhibits the system's
  auto-suspend, for situations where auto-suspend would get in the way of a
  user's work.

---

### FTC Robotics (2018-2020)

The FIRST Tech Challenge is an engineering robotics competition I participated in
through high school. I worked on a team of about 20 people, and we designed, documented,
programmed, and tested a robot to perform predefined tasks both autonomously and
via remote control. I was both the team’s programmer and the team captain: I’d
often have to make decisions that contradicted my interests as the programmer
but led to a better outcome.

This project was real engineering experience, and it taught me how to not only
participate in a team of engineers but how to run one. It also taught me how to
use code to control mechanical devices such as motors, and I had to learn how to 
implement computer vision so that the autonomous mode could make decisions based
on its environment. Here, the focus on quality was essential, because without it
the robot would not only get penalized points-wise but it could also be a safety
risk to itself and to the people around it. My team received the Excellence in
Control Award for my software work on this project.

<p style="margin-bottom: 0px;">Project websites:</p>
- [2018-2019 Season](https://github.com/us-robotics/RoverRuckus)
- [2019-2020 Season](https://github.com/us-robotics/SkyStone)

---

### Substance SDK & KIDE (2016-2017)

The Substance SDK was an effort to build a unified buildsystem and set of
tools/libraries that would allow one set of Kotlin code (with very minimal,
if any, platform-specific code) for different platforms, including
Android, the JVM, Native CPU instructions, and iOS. I got as far as a Gradle
plug-in that managed project structure and implemented building for
JVM, Native, and (partially) Android targets. Complete Android support would
have required me to start work on the SDK's standard library, which would
implement many of the platform-specific APIs apps would be using.

KIDE was supposed to be the official IDE for the Substance SDK. It was a fork
of the Atom text editor and related plugins. It was nearly feature-complete,
with good Git integration, project management, UI tweaks and usability improvements,
and complete support for Gradle and specifically the Substance SDK plugin.

Unfortunately, a comindation of schoolwork and burn-out killed this project.

It's hard to give a single link to a "project website" because it's scattered
across a bunch of git repos [here](https://github.com/SubstanceMobile)

---

### GEM (2014-2017)

GEM was a music player app that I developed in response to a design language
created by Google in 2014 called Material Design. At their demo, Google showcased
a music player that many people, including myself, fell in love with on sight.
Google later confirmed that their demo was just concept art and that they were
not working on building a music player that looked like that. So, with no
experience in Java or Android, I decided to take up the challenge of building
such an app myself.

The project was a stunning success. I managed to implement Google’s concept UI in
its entirety, and I published the app to the Google Play store to relatively
popular reception. Google reported that I had 550 monthly active users, and I
received emails from a Chinese app store asking me if they could translate my
app into Mandarin because they have a few hundred people using it in China.

I taught myself Java and Android entirely through this project, and it directly
led to the creation of two Android libraries that other apps used back then. I
taught myself GUI development skills that I use to this day in my OS development
projects. GEM was my first open source project. It also taught me a lot
about the relationship between code and UX: I started out with many bad code and
structure decisions that damaged the UX of the app and required rewrites to fix.
Overall, GEM was a great and early learning experience for me.

[Project website](https://github.com/SubstanceMobile/GEM)

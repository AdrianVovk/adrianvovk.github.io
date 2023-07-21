---
layout: page
title: Sample Work
permalink: /work
---

### carbonOS (2018-present)

carbonOS is a Linux-based operating system that I created and maintain. It's
primary goal is to bring a mobile/ChromeBook level of stability, security, and
UX to the Linux desktop. I do this by modernizing the software stack and
replacing certain assumptions made by traditional Linux distributions.

Unlike a traditional distro, carbonOS does not have a package manager. Instead, it
replaces all the necessary functionality of a package manager with three separate
components:

- An image-based A/B OS updater, like on an embedded device or a ChromeBook
- An app store, using [Flatpak](https://flatpak.org)
- Container runtimes (i.e. [Podman](https://podman.io)), to run traditional
  Linux environments for the purposes of development

This layout allows carbonOS to protect the operating system's files via various
mechanisms (including strong cryptographic hashing!), while users can continue
installing whatever apps they want. This system also allows carbonOS to silently
update itself in the background, and even rollback failed system updates. This
makes actions that are dangerous on a traditional package-based system (i.e.
installing updates) perfectly safe to do automatically in carbonOS.

This model provides the robustness necessary to build a great UX: users shouldn't
ever have to think about the OS, let alone open a terminal to maintain it. 

Working on carbonOS has taught me many useful skills:

- Packaging software for Linux distros
- Quickly reading through and understanding existing code bases
- Tracking down bugs in multiple layers of a software stack
- Tracking down bugs in hard-to-debug environments (i.e. initramfs in a Linux system)
- Writing systems-level software

[Project Website](https://carbon.sh)

---

### Upstream Contributions (ongoing)

As part of my work with carbonOS and related projects, I've contributed code
to various upstream projects. Here are some of my contributions to notable
upstream projects (some of which are still being reviewed):

- systemd [#28134](https://github.com/systemd/systemd/pull/28134): Designed, implemented, and
  documented a new dbus service, `systemd-sysupdated`, which allows unprivilaged users to update
  various components of the system. The service can update the host system, systemd-sysexts,
  systemd-confexts, systemd portable services, and potentially any other resource on the system,
  all in parallel. Also implemented a companion CLI app: `updatectl`. (NOT MERGED YET)
- mutter [!2653](https://gitlab.gnome.org/GNOME/mutter/-/merge_requests/2653):
  Researched the default UI scale factors of various HiDPI devices on the market
  today. Used the data I collected to replace Mutter's scale-factor selection code
  with an algorithm that picks much better scale factors. This enables mutter to
  be much more usable on HiDPI laptops and phones especially.
- debugedit [patch](https://sourceware.org/pipermail/debugedit/2022-June/000155.html):
  `find-debuginfo` used to be part of RPM, and was used to separate debuginfo
  from ELF binaries as part of a package build. It has since been upstreamed into
  the [debugedit](https://sourceware.org/debugedit/) project. My patch further
  decouples `find-debuginfo` from the RPM build environment, while maintaining
  backwards compatibility. (NOT MERGED YET)
- gnome-shell [!2507](https://gitlab.gnome.org/GNOME/gnome-shell/-/merge_requests/2507):
  Implemented a new mode for GNOME that temporarily inhibits the system's
  auto-suspend, for situations where auto-suspend would get in the way of a
  user's work. (NOT MERGED YET)
- systemd [#27792](https://github.com/systemd/systemd/pull/27792):
  Implement systemd-installer-generator, which allows a single OS disk image to both be an installer
  (like a LiveOS ISO in a traditional distro) and an installed "normal" OS. The image can differentiate
  its behavior either explicitly (via a Linux kernel command line option) or automatically (by detecting
  if it's booting off of removable storage). (NOT MERGED YET)
- libarchive [#1873](https://github.com/libarchive/libarchive/pull/1873): Port over FreeBSD's
  `unzip` utility, which allows libarchive to act as a drop-in replacement for Info-ZIP's `unzip`
  command. This allows distributions to drop the poorly-maintained Info-ZIP package and instead
  rely on `libarchive`'s robust and actively-maintained implementation.
- systemd [#28061](https://github.com/systemd/systemd/pull/28061): Added a new `systemd-empty` token
  type to `cryptsetup`. This allows an empty key to be enrolled into an ecrypted volume to disable
  encryption without actually decrypting the data on disk. `systemd-cryptsetup` can then automatically
  unlock the volume without the performance hit of `try-empty-password`.
- And some more minor patches:
  - systemd [#18522](https://github.com/systemd/systemd/pull/18522): Let systemd-tmpfiles
    create Btrfs subvolumes on systems using libostree
  - systemd [#21570](https://github.com/systemd/systemd/pull/21570): Let the systemd-boot stub
    load [credentials](https://systemd.io/CREDENTIALS/) from a system-wide location in the
    ESP, which allows multiple [UKI](https://uapi-group.org/specifications/specs/unified_kernel_image/)s
    to share credentials
  - systemd [#26643](https://github.com/systemd/systemd/pull/26643): Fixed bug where the gpt-auto
    generator mounted the ESP to /boot instead of /efi on systems where `root=tmpfs`
  - systemd [#26645](https://github.com/systemd/systemd/pull/26645): Let systemd automatically create
    a /lib64 -> /usr/lib symlink, for systems that make use of Arch-style multilib (like carbonOS)
  - plymouth [!131](https://gitlab.freedesktop.org/plymouth/plymouth/-/merge_requests/131): Fixed
    bug where Plymouth failed to render a fallback logo when
    [BGRT](https://learn.microsoft.com/en-us/windows-hardware/drivers/bringup/boot-screen-components)
    is unavailable.
  - systemd [#27794](https://github.com/systemd/systemd/pull/27794): Added a way for systemd-sysupdate
    to put files (such as updated kernels) into the $BOOT partition, as defined by the
    [Boot Loader Specification](https://uapi-group.org/specifications/specs/boot_loader_specification/)

I've also committed to working on some more major contributions:

- AccountsService ([link](https://gitlab.freedesktop.org/accountsservice/accountsservice/-/issues/89#note_1766514)):
  Implementing a systemd-homed backend
- systemd ([link](https://lists.freedesktop.org/archives/systemd-devel/2023-March/048862.html)):
  Adding pluggable download backends for systemd-sysupdate

Finally I have some contributions I'd like to make and hopefully will get to one day:

- Upstreaming a systemd service for cups-pk-helper
- Integrate gnome-software tightly with gnome-shell: [idea](https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/4752#note_1615197)

---

### Caesar Creek Software (Summer 2022)

For [CC-SW](https://www.cc-sw.com/) I built a tool that automates creation
and management of Wireguard VPNs on public clouds (DigitalOcean, Google Cloud,
and Vultr). 

Basically it worked like this: you can create tunnel by listing a cloud + datacenter
to route through: `tunnel create --hop digitalocean:nyc1 tunName`. This creates
a VPS in the specified datacenter and configures it to be Wireguard VPN. Once
the tunnel is up, you can use it by running software in it: `tunnel run tunName command`.
Whatever you run in a tunnel will only have access to the internet through the
tunnel. When you're done using the tunnel (`tunnel destroy tunName`) the VPS
is destroyed.

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

Unfortunately, a combination of schoolwork and burn-out killed this project.

It's hard to give a single link to a "project website" because it's scattered
across a bunch of git repos [here](https://github.com/SubstanceMobile)

---

### GEM (2014-2017)

GEM ("Google Experience Music") was a music player app that I developed in
response to a design language created by Google in 2014 called Material Design.
At their demo, Google showcased a music player that many people, including myself,
fell in love with on sight. Google later confirmed that their demo was just
concept art and that they were not working on building a music player that looked
like that. So, with no experience in Java or Android, I decided to take up the
challenge of building such an app myself.

The project was a stunning success. I managed to implement Google’s concept UI in
its entirety, and I published the app to the Google Play store to relatively
popular reception. Google reported that I had 550 monthly active users, and I
received emails from a Chinese app store asking me if they could translate my
app into Mandarin because they have a few hundred people using it in China.

GEM also became part of the Substance Project, which was an effort to replace
AOSP's aging and abandoned built-in apps with material design alternatives. Google
had abandoned these apps in favor of proprietary alternatives: Camera (Google's 
Pixel camera app), SMS (Google Messages, the RCS client), Music Player
(Google Play Music, then YouTube Music), and many more. So, Android ROMs needed
something new to fill the space.

I taught myself Java and Android entirely through this project, and it directly
led to the creation of two Android libraries that other apps used back then. I
taught myself GUI development skills that I use to this day in my OS development
projects. GEM was my first open source project. It also taught me a lot
about the relationship between code and UX: I started out with many bad code and
structure decisions that damaged the UX of the app and required rewrites to fix.
Overall, GEM was a great and early learning experience for me.

[Project website](https://github.com/SubstanceMobile/GEM)

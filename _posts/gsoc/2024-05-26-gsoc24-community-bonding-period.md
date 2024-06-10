---
title: GSoC'24 | Community Bonding Period
author: swastik
date: 2024-05-28 09:55:00 +0800
categories: [python, package, summary]
tags: [gsoc]
image:
  path: /assets/images/cbp-gsoc.jpeg
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt:
---

With the announcement of the **Google Summer of Code (GSoC) results on May 1, 2024**, my excitement was so overwhelming that I didn't even study for my University End Semester Exam. I can still recall the subject: "Power System Analysis." This summer, I'll be collaborating with the [**AboutCode organization**](https://aboutcode.org/) on the project **"Compute summary for all the detected packages."** The most crucial phase of my **GSoC 2024 journey** started before writing any code: the **Community Bonding Period**. Our organization holds weekly meetings every **Monday at 9:30 IST**. Here is the project description:



## Project Description

Today the summary and license clarity scores are computed for the whole scan. Instead, we should compute them for EACH package (and their files). This is possible now that we are returning which file belongs to a package.

- Add license clarity scores to package models, so every package can have these
- Store references to license detection objects for clarity scores
- Compute summary and package attributes from their key files or other files:
  - Primary and other licenses
  - Copyrights and notices
  - License clarity score (extra field in the package model)
  - Authors and other miscellaneous info
- Make sure the attributes are collected properly for all package ecosystems (like copyrights)

This will ensure all package attributes are properly computed and populated from their respective package files, instead of only having a codebase-level summary.

## Weekly Meet on 6th May 2024

### Discussion

The mentors began the meeting by congratulating the mentees and then proceeded with the agenda as usual. During the discussion, the mentors requested all participants to prepare a presentation for the following week, focusing on the detailed description of their respective projects. It was mentioned that the organization had selected four projects for GSoC.

| Sr.no | Name | Project | Contributor | Mentors |
|-------|------|---------|-------------|---------|
| 1     | Add more data sources: Vulnerablecode | Vulnerablecode | Ambuj Kulshreshtha | Tushar Goel, Ziad Hany, Keshav Priyadarshi |
| 2     | VulnerableCode/Vulntotal: Browser Extension | Vulntotal | Michael Ehab Mikhail | Keshav Priyadarshi, Ziad Hany, Omkar Phansopkar |
| 3     | Enrich SBOM data based on OSSF Security Score Card | ScanCode.io | Pranay Das | Thomas Druez, Tushar Goel, Ayan Sinha Mahapatra, Jay Kumar |
| 4     | Compute summary for all detected packages | scancode-toolkit | Swastik Sharma | Jono Yang, Ayan Sinha Mahapatra, Jay Kumar, Avishrant Sharma |

### Attendees

- [Ayan Sinha Mahapatra](https://github.com/AyanSinhaMahapatra)
- [Jono Yang](https://github.com/JonoYang)
- [Omkar Phansopkar](https://github.com/OmkarPh)
- [Ziad Hany](https://github.com/ziadhany)
- [Michael Ehab](https://github.com/michaelehab)
- [Pranay Das](https://github.com/404-geek)
- [Ambuj Kulshreshtha](https://github.com/ambuj-1211)
- [Swastik Sharma](https://github.com/swastkk)

## Weekly Meet on 13th May 2024

### Discussion

The meeting commenced with an agenda review, followed by GSoC mentees being tasked with presenting their projects to all the mentors. I was the first to present my project, and the presentation was recorded, reflecting the organization's cultural practice.

[Presentation Link](https://docs.google.com/presentation/d/1kuqFp2czs3H0i_NJE4hAKX4jw3C2LQp3Rys86olEHis/edit?usp=sharing)
![image](/assets/images/ppt-image.png)

The organization stored recordings of all the mentees' presentations.
![image](/assets/images/drive-ppts.png)

### Attendees

- [Ayan Sinha Mahapatra](https://github.com/AyanSinhaMahapatra)
- [Jono Yang](https://github.com/JonoYang)
- [Jay Kumar](https://github.com/35C4n0r)
- [Keshav Priyadarshi](https://github.com/keshav-space)
- [Ziad Hany](https://github.com/ziadhany)
- [Pranay Das](https://github.com/404-geek)
- [Ambuj Kulshreshtha](https://github.com/ambuj-1211)
- [Swastik Sharma](https://github.com/swastkk)

## Weekly Meet on 20th May 2024

### Discussion

The meeting commenced with an orientation session for this year's GSoC, led by Ayan Sinha Mahapatra. This session included an introduction to Communication Channels, where all project-related discussions would occur, as well as details about the weekly status meetings scheduled for 16:00 UTC every Monday at [https://meet.jit.si/AboutCode](https://meet.jit.si/AboutCode). Additionally, specific calls with mentors were made available if needed.

### Deadlines and Extensions

- Standard: 12-week project ([timeline](https://developers.google.com/open-source/gsoc/timeline))
  - **July 8 – 12**: Contributor and Mentor Midterm Evaluations
  - **August 19 – 26**: Contributor Final Submission
  - **August 26 – September 2**: Mentor Final Evaluation

- Extensions are allowed under GSoC rules, but only in special cases if required, after discussion and agreement with specific project mentors (if the contributor requests this due to some unavoidable circumstances, 14-22 weeks).

- GSoC [Project dates](https://developers.google.com/open-source/gsoc/help/project-dates) for more info on dates/extensions

![gsoc-kickoff-image](/assets/images/gsoc-kickoff.png)

### Expectations

- Write good commit messages [Link](https://cbea.ms/git-commit/)
- Keep changes in modular issues, commits, PRs
- Issue-specific discussions should happen in specific GitHub issues and Pull requests
- Avoid using DMs as much as possible
- After the creation of Project Boards on GitHub, collaborator access will be given to all the Mentees.

### Attendees

- [Ayan Sinha Mahapatra](https://github.com/AyanSinhaMahapatra)
- [Philippe Ombredanne](https://github.com/pombredanne)
- [Jono Yang](https://github.com/JonoYang)
- [Keshav Priyadarshi](https://github.com/keshav-space)
- [Hritik Vijay](https://github.com/Hritik14)
- [Omkar Phansopkar](https://github.com/OmkarPh)
- [Ziad Hany](https://github.com/ziadhany)
- [Michael Ehab](https://github.com/michaelehab)
- [Pranay Das](https://github.com/404-geek)
- [Ambuj Kulshreshtha](https://github.com/ambuj-1211)
- [Swastik Sharma](https://github.com/swastkk)
- Steven

### Important Links

- [Timeline](https://developers.google.com/open-source/gsoc/timeline)
- [Contributor Guides](https://google.github.io/gsocguides/student/)
- [Contributor Responsibilities](https://developers.google.com/open-source/gsoc/help/responsibilities#gsoc_contributor_responsibilities)
- [Mentor Responsibilities](https://developers.google.com/open-source/gsoc/help/responsibilities#mentor_responsibilities)

# Conclusion & Further Plans

During the community bonding period, my mentor(s) and I had several in-depth discussions about the project. These conversations were incredibly productive and provided me with a clear understanding of the project’s scope and objectives. We revisited the initial project plan and identified areas that needed more detailed planning.

---
title: Coding Period Week 1
author: swastik
date: 2024-06-02 09:55:00 +0800
categories: [python, package, summary]
tags: [gsoc]
image:
  path: /assets/gifs/cw-1.gif
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt:
---

# Week 1 Progress (May 27 - June 2)

In [scancode-toolkit](https://github.com/nexb/scancode-toolkit), we previously computed the summary and license clarity scores for the whole scan. Now, we need to implement this for each package and its related files. With the ability to identify which files are associated with a package, this is now achievable.

There are two levels of reporting license detections:
- File/package level License Detections
- Codebase level unique License Detections (summarized from the file/package level detections)

## What is the License Clarity Score?

License Clarity is a set of criteria that indicate how clearly, comprehensively, and accurately a software project has defined and communicated the licensing that applies to the project software. Note that this is not an indication of the license clarity of any software dependencies.

### License Clarity Scoring

**Score Range: 0-100**

Calculated by combining weighted values of the following elements:

1. **Declared License (40)**
   - Indicates if the license is documented in key files like the package manifest, NOTICE, LICENSE, COPYING, or README.

2. **Identification Precision (40)**
   - Measures how well the license statement matches known licenses with precise identifiers from sources like ScanCode LicenseDB, SPDX, OSI, or a specific URL.

3. **License Texts (10)**
   - Confirms if license texts supporting the declared license are provided in key files.

4. **Declared Copyright (10)**
   - Indicates if the copyright is documented in key files.

5. **Ambiguous Compound Licensing (-10)**
   - Flags if the license declaration is unclear due to poorly defined multiple licenses.

6. **Conflicting License Categories (-20)**
   - Detects conflicts where a declared permissive license is contradicted by other licenses in the code (e.g., copyleft, proprietary).

For deeper insights, refer to [Providing Clarity on License Clarity Scoring in ScanCode](https://nexb.com/scancode-license-clarity-scoring/#:~:text=The%20license%20clarity%20score%20is,licensing%2C%20and%20Conflicting%20license%20categories.).

To add this to each package instance, changes need to be made in the Package Models. Below is the addition in the Top-Level Package Instance in `packagedcode/models.py`:

```python
license_clarity = List(
        item_type=dict,
        label='License Clarity Information',
        help='List containing the license clarity score and related elements.'
    )
```

## Discussions
I discussed with the mentors regarding the Package Assembly, which plays an important role in generating the Codebase Summary and the License Clarity Scores. During file-by-file level scanning, we create a package data object from each package manifest and store it in the file.

For codebase-level scanning, we combine several package manifests and extract package data details from them.

Available Package Parsers
Alpine packages, BUCK files, ABOUT files, Android apps, Autotools, Bazel, JavaScript Bower, Java Axis, MS Cab, Rust Cargo, Cocoapods, Chef, Chrome apps, PHP Composer and composer.lock, Conda, CPAN, Debian, Apple dmg, Java EAR, WAR, JAR, FreeBSD packages, Rubygems gemspec, Gemfile and Gemfile.lock, Go modules, Haxe packages, InstallShield installers, iOS apps, ISO images, Apache IVY, JBoss Sar, R CRAN, Apache Maven, Meteor, Mozilla extensions, MSI installers, JavaScript npm packages, package-lock.json, yarn.lock, NSIS Installers, NugGet, OPam, Cocoapods, Python PyPI setup.py, setup.cfg, semi-structured README files like README.android, README.chromium, README.facebook, README.google, README.thirdparty, RPMs, Shell Archives, Squashfs images, Java WAR, Windows executables, and the Windows registry.

Refer the link below for available package parsers and more details.

[https://scancode-toolkit.readthedocs.io/en/stable/reference/available_package_parsers.html](https://scancode-toolkit.readthedocs.io/en/stable/reference/available_package_parsers.html)

I explored many package ecosystems like `python whl`, `java mavens`, and others. During discussions on this [issue](https://github.com/nexB/scancode-toolkit/issues/3707), the package file *beartype 0.18.5* had the output as [beartype-py3-none-any-whl.json](https://github.com/nexB/scancode-toolkit/files/14720145/beartype-0.17.2.json) with many **unknown-license-references** detected because each Python file in the package had the following header:

```python
#!/usr/bin/env python3
# --------------------( LICENSE                            )--------------------
# Copyright (c) 2014-2024 Beartype authors.
# See "LICENSE" for further details.
```

The mentioned LICENSE file was not located at the root of the scanned directory, so it was missed as we only look at sibling files and files at the root.

```shell
.
├── beartype
└── beartype-0.17.2.dist-info
    ├── LICENSE
    ├── METADATA
    ├── RECORD
    ├── WHEEL
    └── top_level.txt
```
## Conclusion and Further Plans

We plan to implement the Plugin part first and then complete the implementation of the Package Assembly. This is because the package summary computation depends on the package ecosystem.

## Attendees

- [Ayan Sinha Mahapatra](https://github.com/AyanSinhaMahapatra)
- [Jono Yang](https://github.com/JonoYang)
- [Omkar Phansopkar](https://github.com/OmkarPh)
- [Ziad Hany](https://github.com/ziadhany)
- [Jay Kumar](https://github.com/35C4n0r)
- [Keshav Priyadarshi](https://github.com/keshav-space)
- [Michael Ehab](https://github.com/michaelehab)
- [Pranay Das](https://github.com/404-geek)
- [Ambuj Kulshreshtha](https://github.com/ambuj-1211)
- [Swastik Sharma](https://github.com/swastkk)

<div style="text-align: center;">
  <p style="margin-bottom: 1px;">Visitor Count</p>
  <img src="https://profile-counter.glitch.me/swastkk-cw-1/count.svg" alt="visitor count" />
</div>
---
title: Coding Period Week 2
author: swastik
date: 2024-06-09 09:55:00 +0800
categories: [python, package, summary]
tags: [gsoc]
image:
  path: /assets/images/cw-2.webp
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt:
---

# Week 2 Progress (June 3 - June 9)
This week was completely focused on integrating the post-scan plugin `--package-summary` for the computation of package-level summaries. These plugins primarily handle data processing, summarization, and reporting, relying on results from all scan plugins. They introduce new attributes at the codebase or file level, and may also remove or modify data as needed for consolidation or summarization. The base plugin class to be extended is `PostScanPlugin`, located at [/src/plugincode/post_scan.py](https://github.com/nexB/plugincode/src/plugincode/post_scan.py).

Previously, the scancode-toolkit had `--summary` as the post-scan plugin for summarizing the entire codebase. The available post-scan options in scancode-toolkit include:

- **`--license-clarity-score`**: Computes a summary license clarity score at the codebase level. This is a sub-option of `--classify`.
- **`--summary`**: Summarizes scans by providing declared origin information and other detected information at the codebase attribute level.
When `--summary` plugin is applied, the JSON file is structured as below-
```json
{
  "headers": [...],
  "summary": {
    "declared_license_expression": null,
    "license_clarity_score": {...},
    "declared_holder": "",
    "primary_language": "C",
    "other_license_expressions": [...],
    "other_holders": [...]
    "other_languages": [...]
  },
  "files": [...]
}
```

The ScanCode toolkit utilizes the plugincode for its pluggable functionality, including Click plugins. This plugincode is built upon the pluggy package. To incorporate a post-scan plugin:

1. Begin by creating a new file named `package_summary.py` in the `src/summarycode` directory, which will contain all necessary components.


2. Import required modules:

    ```python
    from plugincode.post_scan import PostScanPlugin
    from plugincode.post_scan import post_scan_impl
    from scancode import CommandLineOption
    from scancode import POST_SCAN_GROUP
    ```
3. Construct a `PostScanPlugin` class:

   - The PostScanPlugin class [PostScanPlugin](https://github.com/nexB/plugincode/blob/main/src/plugincode/post_scan.py) inherits from the [CodebasePlugin](https://github.com/nexB/plugincode/blob/main/src/plugincode/__init__.py) class, which itself inherits from [BasePlugin](https://github.com/nexB/plugincode/blob/main/src/plugincode/__init__.py).

    ```python
    @post_scan_impl
    class PackageSummary(PostScanPlugin):
        """
        Summary at the Package Level.
        """

        options = [
            PluggableCommandLineOption(('--package-summary',),
            is_flag=True, default=False,
            help='Generate Package Level summary',
            help_group=POST_SCAN_GROUP)
        ]

        def is_enabled(self, package_summary, **kwargs):
            return package_summary

        def process_codebase(self, codebase, package_summary, **kwargs):
            """
            Process the codebase.
            """
            if not self.is_enabled(package_summary):
                return
    ```

4. Add the entry point `package_summary` in the setup.cfg file:
  ```python
    scancode_post_scan =
        package_summary = summarycode.package_summary:PackageSummary
        summary = summarycode.summarizer:ScanSummary
        tallies = summarycode.tallies:Tallies
        tallies-with-details = summarycode.tallies:TalliesWithDetails
    ```
   - here, `package_summary` refers to the name of the command flag.
   - `summarycode` denotes the directory containing the plugin file.
   - the `package_summary` is the name of the Python file housing the plugin.
   - `PackageSummary` is the name of the PostScanPlugin created.  

5. Loaded the Plugin

   - After running the command
  ```shell
  pip install .
  ```
    - This ensures that the plugin is successfully installed.
    
# Discussions
During the Weekly Status Call, we discussed with the mentors about adding small unit tests for the Post Scan Plugin. Additionally, there was a discussion about the Pull Request that needs to be updated with the failing tests regenerated to ensure all tests pass successfully.

[Philippe](https://github.com/pombredanne) also provided insights into various examples of monorepos and scenarios where a package contains more than one package within it. He emphasized the importance of developing appropriate populating methods to handle such cases effectively.

# Conclusion and Further Plans
Now that we have the plugin, we discussed further plans to develop methods for populating the License Clarity Field and other fields for Package Level scanning.
# Attendees

- [Philippe Ombredanne](https://github.com/pombredanne)
- [Ayan Sinha Mahapatra](https://github.com/AyanSinhaMahapatra)
- [Jono Yang](https://github.com/JonoYang)
- [Omkar Phansopkar](https://github.com/OmkarPh)
- [Ziad Hany](https://github.com/ziadhany)
- [Keshav Priyadarshi](https://github.com/keshav-space)
- [Michael Ehab](https://github.com/michaelehab)
- [Pranay Das](https://github.com/404-geek)
- [Ambuj Kulshreshtha](https://github.com/ambuj-1211)
- [Swastik Sharma](https://github.com/swastkk)



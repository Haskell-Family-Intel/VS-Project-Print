Overview

VS Project Print is a Windows GUI tool (single executable) that scans a Visual Studio project directory for C++/C# sources and recent build logs, then exports a consolidated report as Markdown (ProjectExport.md) or plaintext (ProjectExport.txt). The tool performs all operations locally and does not transmit data.

Quick Start (Recommended)

Place the tool: Copy VS_Project_Print.exe into the root of the Visual Studio project you want to scan (the same folder you open in VS, typically containing your .sln or top-level project files). The tool treats its current folder as the project root.

Run the GUI: Double‑click VS_Project_Print.exe.

Select files: In the Files tab, use the checkboxes to include/exclude files for export.

Export: Click Export Selected. Your report (ProjectExport.md by default) is written to the same folder.

Tip: You can also drop the executable next to your project’s built .exe (e.g., within a solution’s top-level directory) so it scans that subtree. The tool always uses the folder it runs from as the project directory.

What the Tool Scans

Languages: C++ (.cpp sources + common headers .h, .hpp, .hxx) and C# (.cs).

Build Logs: Searches recursively for common Visual Studio/MSBuild logs and picks the most recently modified one:

buildlog.txt, build.log, msbuild.log

Files matching *error*.txt, output.txt

Any *.log under bin/ or obj/

Export Contents

Exports are written to ProjectExport.md or ProjectExport.txt in the project folder and include:

Selected Header Files — listed as relative paths.

Selected Source Files — full contents embedded in code fences (language‑tagged when possible).

Build Information — a parsed summary of the latest build log:

Log path + last modified time

Build summary (when detected)

Up to 10 errors and 10 warnings (with codes, messages, and file:line:col when present)

A note if there are additional findings beyond the first 10

If no logs are found, the report states that explicitly

The GUI at a Glance

Files tab

Tree view of discovered headers and sources

ReScan: Re‑crawl the current directory

Select All / Deselect All: Bulk selection controls

Export Selected: Generate the report

Log tab

Displays the local tool log (vs_project_print.log) in real‑time (auto‑refresh)

About tab

Tool name, version, and authorship

License tab

Displays the license terms shipped with this tool

Logs (Local Only)

A tool log named vs_project_print.log is created in the project directory.

It records major actions (start, scanning, export results, errors encountered).

The Log tab tails this file so you can monitor progress.

No data is sent externally; all logging stays on your machine.

Command Line (Optional)

The executable supports the same flags as the Python script.

# Run in the current project folder and export Markdown (default)

./VS_Project_Print.exe

# Run headless (no GUI) and export plaintext

./VS_Project_Print.exe --no_gui --output_format txt

# Specify a different project directory (rare; normally run from the project root)

./VS_Project_Print.exe "C:\\Path\\To\\Project" --output_format md

Arguments

project_dir (positional, optional): Project root to scan; defaults to the current directory.

--output_format md|txt (default: md): Report format.

--no_gui: Run headless; exports all discovered headers/sources automatically.

Privacy & Security

No IP leakage: The tool does not upload files, send telemetry, or contact any external service.

All outputs (ProjectExport.* and vs_project_print.log) are written locally to the project folder.

Troubleshooting

No files found: Make sure VS_Project_Print.exe is inside the project’s root directory.

No build information: Ensure a recent build was run so a supported log exists (see list above).

GUI won’t launch: Try running from a standard, writable folder (not from a protected system path). You can also use --no_gui.

Large projects: Use the GUI to selectively export only the relevant files.

License

🛡️📜 Copyright © 2025 Haskell Family Intel. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to use the Software subject to the following conditions:

Personal, Non-Commercial Use Only The Software may be used solely for personal, non-commercial purposes, including single-player GTA V modding and development activities. Any commercial use, including but not limited to selling, licensing, or incorporating the Software into products for profit, is strictly prohibited without prior written permission from Haskell Family Intel.

No Redistribution or Derivative Works You may not redistribute, republish, modify, merge, sublicense, sell, or otherwise distribute the Software or any derivative works based upon the Software in any form without prior written permission from Haskell Family Intel. This includes sharing the Software on public repositories, forums, or other platforms.

Enforcement Unauthorized modifications or distributions may result in DMCA takedown notices, legal action, or other enforcement measures as deemed appropriate by Haskell Family Intel. You acknowledge that Haskell Family Intel retains the right to seek damages and injunctive relief in the event of a breach. ⚖️

No Warranty The Software is provided "AS IS," without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall Haskell Family Intel or the author be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the Software or the use or other dealings in the Software. ❗

Governing Law This agreement shall be governed and construed in accordance with the laws of the State of [REDACTED], United States, without regard to conflict of law principles. All disputes shall be subject to the exclusive jurisdiction of the courts of [REDACTED] County, [REDACTED] State. 🏛️

For permissions or inquiries, contact Haskell Family Intel at HaskellFamilyIntel@protonmail.com. By using the Software, you agree to these terms. ✉️

Last Updated: January 15, 2025 Version: 1.0© 2025 Haskell Family Intel. All Rights Reserved. 📆🖋️📜

Contact

For permissions or inquiries: HaskellFamilyIntel@protonmail.com

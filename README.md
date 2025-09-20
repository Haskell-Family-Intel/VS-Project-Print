# VS Project Print 🚀

[![Windows](https://img.shields.io/badge/Platform-Windows-blue?style=flat-square&logo=windows)](https://github.com/topics/windows) [![C++](https://img.shields.io/badge/Language-C%2B%2B-brightgreen?style=flat-square&logo=c%2B%2B&logoColor=white)](https://github.com/topics/c%2B%2B) [![C#](https://img.shields.io/badge/Language-C%23-purple?style=flat-square&logo=csharp&logoColor=white)](https://github.com/topics/csharp) [![Markdown](https://img.shields.io/badge/Output-Markdown-orange?style=flat-square&logo=markdown&logoColor=white)](https://github.com/topics/markdown)

## Overview 📋

**VS Project Print** is a Windows GUI tool (single executable) that scans a Visual Studio project directory for C++/C# sources and recent build logs, then exports a consolidated report as Markdown (`ProjectExport.md`). The tool performs all operations locally and does not transmit data. 🔒

This tool is perfect for developers who need a quick, offline way to bundle project code and build insights for documentation, sharing, or backups—without the hassle of manual copying.

## Quick Start (Recommended) ⚡

1. **Place the tool**: Copy `VS_Project_Print.exe` into the root of the Visual Studio project you want to scan (the same folder you open in VS, typically containing your `.sln` or top-level project files). The tool treats its current folder as the project root. 📁
   
2. **Run the GUI**: Double-click `VS_Project_Print.exe`. 🖱️

3. **Select files**: In the **Files** tab, use the checkboxes to include/exclude files for export. ✅

4. **Export**: Click **Export Selected**. Your report (`ProjectExport.md` by default) is written to the same folder. 📤

> 💡 **Tip**: You can also drop the executable next to your project’s built `.exe` (e.g., within a solution’s top-level directory) so it scans that subtree. The tool always uses the folder it runs from as the project directory.

## What the Tool Scans 🔍

- **Languages**: 
  - C++ (`.cpp` sources + common headers `.h`, `.hpp`, `.hxx`) 
  - C# (`.cs`)

- **Build Logs**: Searches recursively for common Visual Studio/MSBuild logs and picks the most recently modified one:
  - `buildlog.txt`, `build.log`, `msbuild.log`
  - Files matching `error.txt`, `output.txt`
  - Any `*.log` under `bin/` or `obj/`

## Export Contents 📄

Exports are written to `ProjectExport.md` or `ProjectExport.txt` in the project folder and include:

- **Selected Header Files** — listed as relative paths. 📄
- **Selected Source Files** — full contents embedded in code fences (language-tagged when possible). 💻
- **Build Information** — a parsed summary of the latest build log:
  - Log path + last modified time ⏰
  - Build summary (when detected) 📊
  - Up to 10 errors and 10 warnings (with codes, messages, and `file:line:col` when present) ❌⚠️
  - A note if there are additional findings beyond the first 10 🔍
- If no logs are found, the report states that explicitly. ℹ️

Example Markdown snippet:
```markdown
## Errors
- **C2039**: 'identifier' is not a member of 'class' in `src/main.cpp:42:5`  
- **C2664**: 'function' : cannot convert argument 1 from 'type1' to 'type2' in `src/utils.cpp:17:12`
```

## The GUI at a Glance 🖥️

### Files Tab 📁
- Tree view of discovered headers and sources
- **ReScan**: Re-crawl the current directory 🔄
- **Select All / Deselect All**: Bulk selection controls ✅❌
- **Export Selected**: Generate the report 📤

### Log Tab 📝
- Displays the local tool log (`vs_project_print.log`) in real-time (auto-refresh) 🔄

### About Tab ℹ️
- Tool name, version, and authorship

### License Tab 📜
- Displays the license terms shipped with this tool

## Logs (Local Only) 🗒️

A tool log named `vs_project_print.log` is created in the project directory.  
It records major actions (start, scanning, export results, errors encountered).  

The **Log** tab tails this file so you can monitor progress.  
No data is sent externally; all logging stays on your machine. 🔒

## Command Line (Optional) 💻

The executable supports the same flags as the Python script.

- **Run in the current project folder and export Markdown (default)**:
  ```
  ./VS_Project_Print.exe
  ```

- **Run headless (no GUI) and export plaintext**:
  ```
  ./VS_Project_Print.exe --no_gui --output_format txt
  ```

- **Specify a different project directory (rare; normally run from the project root)**:
  ```
  ./VS_Project_Print.exe "C:\Path\To\Project" --output_format md
  ```

### Arguments
- `project_dir` (positional, optional): Project root to scan; defaults to the current directory. 📁
- `--output_format md|txt` (default: `md`): Report format. 📄
- `--no_gui`: Run headless; exports all discovered headers/sources automatically. 🤖

## Privacy & Security 🔒

- **No IP leakage**: The tool does not upload files, send telemetry, or contact any external service.
- All outputs (`ProjectExport.*` and `vs_project_print.log`) are written locally to the project folder.

Your project stays private—100% offline. 🌐❌

## Troubleshooting 🛠️

- **No files found**: Make sure `VS_Project_Print.exe` is inside the project’s root directory. 📁
- **No build information**: Ensure a recent build was run so a supported log exists (see list above). 🔨
- **GUI won’t launch**: Try running from a standard, writable folder (not from a protected system path). You can also use `--no_gui`. 🖥️
- **Large projects**: Use the GUI to selectively export only the relevant files. 📊

For permissions or inquiries, contact Haskell Family Intel at [HaskellFamilyIntel@protonmail.com](mailto:HaskellFamilyIntel@protonmail.com). By using the Software, you agree to these terms. ✉️
  
**Version**: 1.2  
**© 2025 Haskell Family Intel. All Rights Reserved.** 📆🖋️📜

## Contact 📧

For permissions or inquiries: [HaskellFamilyIntel@protonmail.com](mailto:HaskellFamilyIntel@protonmail.com)

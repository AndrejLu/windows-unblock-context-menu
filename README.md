# Windows Unblock Context Menu

Adds an **"Unblock files in this folder"** option to the Windows Explorer context menu.

This removes the Windows `Zone.Identifier` alternate data stream from files in the selected folder and its subfolders using PowerShell `Unblock-File`.

This can help when Windows blocks document previews or marks downloaded files as originating from another computer.

## Installation

1. Download `install.reg`.
2. Double-click it.
3. Accept the Windows Registry prompt.

After installation, right-click:

- a folder, or
- the empty background inside a folder

and select:

**Unblock files in this folder**

On Windows 11, the option may appear under:

**Show more options**

## Removal

Run:

`uninstall.reg`

## What it does

The context menu runs:

```powershell
Get-ChildItem -LiteralPath "<folder>" -Recurse -File -ErrorAction SilentlyContinue | Unblock-File
```

This recursively removes the Windows downloaded-file blocking marker from files.

## Warning

Only use this on files you trust.

Unblocking a file removes Windows' indication that the file originated from the Internet or another potentially untrusted source.

## Requirements

- Windows 10 or Windows 11
- Windows PowerShell

## License

MIT

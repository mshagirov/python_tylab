# Getting Started
---
> Following installation steps assume that we will use Anaconda python distribution (individual edition, Python 3.7 or later).

## 1. Installing Anaconda Python Distribution
Install Anaconda individual edition.
- Review your system requirements and follow steps in [anaconda website](https://docs.anaconda.com/anaconda/install/#).
- \[Suggested\] Use default installation/destination directory when installing anaconda.
- \[Suggested\] When asked, select "add Anaconda to your PATH" option.

## 2. Set `PATH` environment variable:
**If you already added `anaconda` to the path variable, skip to the next step "Check your installation"**.

### Windows
([source](https://docs.microsoft.com/en-us/previous-versions/office/developer/sharepoint-2010/ee537574(v=office.14))):

1. On the `Start` menu
  - \[Older than Win10\] right-click `Computer`.
  - \[Win10\] Click the `Settings` button (gear icon), or type "this pc" and right-click `This PC` app.
1. Go to `Properties` (old Windows OS), or `Settings` (Win10)
  - \[Older than Win10\] `Properties`-->`System`-->`Advanced system settings`-->`Advanced` tab-->`System Properties`-->`Environment Variables`
  - \[Win10\] On the panel located on the right hand side find and open `Advanced system settings`, then click on `Environment Variables`.
1. On the `Environment Variables` dialog box, go to `System Variables` box.
1. Click `Path` variable and then press `Edit`.
  - \[Older than Win10\] In `System Variable` dialog box, scroll to the end of the string in the `Variable value` box and add a semicolon (`;`).
  - \[Older than Win10\] Append the new path (location of Anaconda binary files, `anaconda3\bin\`) after the semicolon, e.g.:
  - \[Win10\] Click `New` and type in the anaconda binaries path.
1. Save the environment variable.

### Mac OS
Starting with Catalina, macOS uses [zsh as the default shell](https://support.apple.com/en-us/HT208050).

- \[Suggested\] Edit `~/.zshrc`
    1. Open terminal, in terminal type the following and press enter.
    ```
    open -a TextEdit ~/.zshrc
    ```
    1. Find the last line starting with `export PATH=` (tip: use `Cmd+F`; if there is none, just use the last line of the file).
    1. Append following lines after the line you found in the previous step, *replace* the `/Users/USER/anaconda3/bin` *part with the correct location of Anaconda binary files* (line starting with `#` is a comment line):
    ```
    # Anaconda path
    export PATH="/Users/USER/anaconda3/bin:$PATH"
    ```
    1. Save `.zshrc` file.
- For other way to add path variables, e.g. using `/etc/paths.d` directory see "method 2" section of this [blog post](https://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/).

## Check your anaconda installation.
- Windows
  - In Cmd
- Mac os
  - In terminal.

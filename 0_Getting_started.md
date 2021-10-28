Getting Started
---
> Following installation steps assume that we will use Anaconda python distribution (individual edition, Python 3.7 or later).

# Installing Anaconda Python Distribution
1. Install Anaconda individual edition.
    - Review your system requirements and follow steps in [anaconda website](https://docs.anaconda.com/anaconda/install/#).
    - \[Suggested\] Use default installation/destination directory when installing anaconda.
    - \[Suggested\] When asked, select "add Anaconda to your PATH" option.
1. Set `PATH` environment variable:
    - **If you already added `anaconda` to the path variable, skip to the next step "Check your installation"**.
    - Windows ([source](https://docs.microsoft.com/en-us/previous-versions/office/developer/sharepoint-2010/ee537574(v=office.14))):
      - On the `Start` menu, right-click `Computer`.
      - Go to `Properties`-->`System`-->`Advanced system settings`-->`Advanced` tab-->`System Properties`-->`Environment Variables`
      - On the `Environment Variables` dialog box, go to `System Variables` box.
      - Select `Path` variable and then press `Edit`.
      - Edit System Variable dialog box, scroll to the end of the string in the Variable value box and add a semicolon (`;`).
      - Append the new path (location of Anaconda binary files, `anaconda3\bin\`) after the semicolon. Save it.
    - Mac OS (starting with Catalina, macOS uses [zsh as the default shell](https://support.apple.com/en-us/HT208050)).
      - \[Suggested\] Edit `~/.zshrc`
        1. Open terminal, in terminal type the following and press enter.
        ```
        open -a TextEdit ~/.zshrc
        ```
        1. Find the last line starting with `export PATH=` (tip: use `Cmd+F`; if there is none, just use the last line of the file).
        2. Append following lines after the line you found in the previous step, *replace* the `/Users/USER/anaconda3/bin` *part with the correct location of Anaconda binary files* (line starting with `#` is a comment line):
        ```
        # Anaconda path
        export PATH="/Users/USER/anaconda3/bin:$PATH"
        ```
        3. Save `.zshrc` file.
    - For other way to add path variables using `/etc/paths.d` directory see "method 2" section of this [blog post](https://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/).
1. Check your anaconda installation.

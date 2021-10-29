# Getting Started
---
> Following installation steps assume that we will use Anaconda python distribution (individual edition, Python 3.7 or later).

Please follow these four steps to install and start using jupyter notebook.

## 1. Anaconda Python Distribution
Install Anaconda individual edition.
- Review your system requirements and follow steps in [anaconda website](https://docs.anaconda.com/anaconda/install/#).
- \[Suggested\] Use default installation/destination directory when installing anaconda.
- \[Suggested\] When asked, select "add Anaconda to your PATH" option.

## 2. `Path` environment variable
**If you already added `anaconda` to the path variable, skip to the next step ["Check your installation"](#3-check-your-anaconda-installation)**.
- [Windows instructions](#setting-path-variables-on-windows).
- [Mac OS instructions](#setting-path-variables-on-mac-os).

### Setting Path Variables on Windows
1. On the `Start` menu
  - \[Before Win10\] right-click `Computer` then click `Properties`.
  - \[Win10\] Click the `Settings` button (gear icon, or type "this pc" and right-click `This PC` app then click `Properties`).
1. Go to
  - \[Before Win10\] `Properties`-->`System`-->`Advanced system settings`-->`Advanced` tab-->`System Properties`-->`Environment Variables`
  - \[Win10\] `Settings`-->`System`-->`About` (on the left-bottom)-->`Advanced system settings` (panel on the right)-->`Environment Variables`.
1. On the `Environment Variables` dialog box, go to `System Variables` box.
1. Click `Path` variable and then press `Edit`.
  - \[Before Win10\] In `System Variable` dialog box, scroll to the end of the string in the `Variable value` box and add a semicolon (`;`). Append the new path (location of Anaconda binary files) after the semicolon (`;`).
  - \[Win10\] Click `New` and type in the anaconda binaries path.
  > \[Default paths\] Add following `C:\Users\USER\anaconda3\`, `C:\Users\USER\anaconda3\Scripts\` where `USER` is your user name.

1. Save the environment variable.

### Setting Path Variables on Mac OS
Starting with Catalina, macOS uses [zsh as the default shell](https://support.apple.com/en-us/HT208050).

- \[Suggested\] Edit `~/.zshrc`
    1. Open terminal (press <kbd>Cmd</kbd> + <kbd>space</kbd>, then type "terminal"). In terminal, type the following and press enter.
    ```
    open -a TextEdit ~/.zshrc
    ```
    2. Find the last line starting with `export PATH=` (tip: use `Cmd+F`; if there is none, just use the last line of the file).
    3. Append following lines after the line you found in the previous step, *replace* the `/Users/USER/anaconda3/bin` *part with the correct location of Anaconda binary files* (line starting with `#` is a comment line, and `USER` is your user name):
    ```
    # Anaconda path
    export PATH="/Users/USER/anaconda3/bin:$PATH"
    ```
    4. Save `.zshrc` file.
- For other ways to add path variables, e.g. using `/etc/paths.d` directory see "method 2" section of this [blog post](https://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/).

## 3. Check your anaconda installation.
- [Windows](#checking-your-installation-on-windows)
- [Mac OS](#checking-your-installation-on-mac-os)
### Checking Your Installation on Windows

  1. Press **windows logo key** <kbd>![Windows Key][winlogo]</kbd>+ <kbd>R</kbd> to open `cmd`. Alternatively use windows terminal app (with cmd, git bash etc.).
  1. Type following (and press enter for each):
  ```
  where conda
  ```
  this should print out the location of `conda.exe`, next type
  ```
  where python
  ```
  same for `python.exe`, and
  ```
  where jupyter
  ```
  should print location of `jupyter.exe`

### Checking Your Installation on Mac OS
  1. Press <kbd>Cmd</kbd> + <kbd>space</kbd>, then type "terminal" and press enter to open  terminal.
  1. Entering following,
  ```
  which conda
  ```
  should print out locations for conda, and 
  ```
  which python
  ```
  location for the new installation of python in `anaconda3` directory, e.g. for python it should print `/Users/USER/anaconda3/bin/python` where `USER` is your user name. You can check your user name by entering `echo $USER` in terminal. If you set up your `path` variable correctly, but still facing errors (e.g. `which` or `where` can not locate your `conda`/`python`):
- \[Mac OS\] Try installing `xcode`, then close and re-open your terminal and try checking again (this should install command line tools for Mac OS)
- \[Windows\] Probably your `path` is not set up properly, instead you can use `Anaconda prompt`. You can find it on start menu by typing "anaconda" in the search bar.

## 4. Run Python and Jupyter Notebook. 
In terminal (or `cmd` command shell on Windows), enter one of these
```
python
```
or
```
ipython
```
this should start `python`/`ipython` interpreter. To exit use `exit()` command or press <kbd>Ctrl</kbd> + <kbd>D</kbd>. Next, to check jupyter enter
```
jupyter notebook
```
this starts the jupyter notebook server at `http://localhost:8888` and opens it using your default browser (if the port 8888 is being used by another application jupyter will automatically serve the notebook site using another port, you can see the address/link in the terminal after a line with `The Jupyter Notebook is running at:`). If evrything is working you can shut down jupyter (<kbd>Ctrl</kbd> + <kbd>C</kbd>) and go to the [next session](./1_python.md).

[winlogo]: ./images/winlogo.png


# Introduction

## Choosing Julia

- **Why Julia?**: Julia gets as close to writing whiteboard mathematics directly in code as any language has yet to achieved.  Moreover, the code has the possibility to be almost as as fast (or faster in the longrun) than typical code using compiled lanugages like Fortran or C/C++.
- **Why not Python?**: Python is a general-purpose language, and very useful for things like screen-scraping, manipulating data files, gluing together code, cookbook datascience, etc.  But it is not ideal for implementing mathematical models and scientific computing, and incapable of high-performance by its very design.  The development environment is more mature than Julia, but in 2+ years that will likely not be true.  On the other hand, Python may remain a better language for cookie-cutter datascience and machine learning tasks in the near future.
- **Is Julia Ready?** The language: Yes.  The environment: Almost.  The general "development environment" of Julia is rough around the edges, but will get better.  If you are thinking a few years into the future, then now is the time to invest in learning the language (even if it is sometimes painful).  The current version of Julia (1.0) is now stable and with [backwards compatible release cycles](https://semver.org/), so while the ecosystem and environment will evolve, the code will now work.
- **Will it succeed?** It is too good to fail!  The community is large enough, and the packages available are dense enough, to support specialist users in certain fields already.  Whether it displaces Matlab in the medium-run is a tougher quetsion, but it isn't necessary.
- **It feels slow!**:  Yes, the environment does.  Many tasks run slowly the first time you execute them.  Keep in mind that Julia is often closer to a compiled language (like Fortran and C++) than a dynamic language (like Matlab or Python).  But there is hope!  The perceived speed usually has to do with code being compiled the first time you use it.  Luckily, once the compiling has happened it should feel lightning fast.  Plotting is another area where (first-plot) performance is often slow, but that should become better in the next few years.

# Getting Started with Julia

You can: (1) run as Jupyter notebooks on a web server; (2) install and use Jupyter on a desktop; (3) or use julia files directly on the desktop with an IDE or a REPL.

Unlike working with files directly, a Jupyter notebook contains both code and results.  To see some of the key features, look at https://lectures.quantecon.org/jl/getting_started.html#notebook-basics

For more details on accessing tutorials, see [Julia Tutorials](julia/tutorials.md)

## Using Julia Online with Jupyter

[JuliaBox](https://next.juliabox.com/)  is the easiest method to get started using Julia, as it requires no installation
- Login with a github account (which will  make it easy to connect to github)
	 - The most important rule is: **never install packages directly** on JuliaBox
	 - i.e. don't use `Pkg.add()` on https://next.juliabox.com/ notebooks
     - Instead, form the main page, click on `Packages` at the top, choose `Yours`, then add to the dialog that says `Enter the package...`.  After installing packages, hit `Start` to rebuild.
- From JuliaBox, a great place to start are the pre-installed tutorial files.  You can walk through them with a [Youtube Tutorial](https://www.youtube.com/watch?v=4igzy3bGVkQ)

## Installing Julia on your Desktop

To install Julia locally, see the QuantEcon [first steps](https://lectures.quantecon.org/jl/getting_started.html#first-steps).  Alternatively, for the impatient the summary of links to download and install is:

1. [Git](https://git-scm.com/downloads). 
	- This is the "version control system" that Julia uses to manage packages, and that coders use to manage software. 
	- If on Windows, afterwards we recommend running
```
git config --global core.eol lf
git config --global core.autocrlf false
```
2. [Anaconda](https://www.anaconda.com/download/)
    - May not be necessary if you already have a complete installation of Python and its package managers
    - Choose the Anaconda with Python 3.6
3. Install [Julia](https://julialang.org/downloads/)
4. Follow the setup steps on the front of this repository. 
5. To Install Jupyter
    - If you followed the included steps it will install it for you
    - Otherwise, you will need to go to a Julia consol and type `using Pkg; Pkg.add("IJulia")`
    - After installation, you can run jupyter with `jupyter notebook` or to use the latest interface (which is a major step forward) `jupyter lab`
    - Depending on how you installed Anaconda, this may require adding a directory to the PATH.  The location depends on the installation location, but it will be something like `/bin/Anaconda3/Scripts`
6. To change Jupyter start-up directory
   - For Windows: if Anaconda was installed in C:/bin, then created a shortcut with
        - Target = `C:\bin\Anaconda3\Scripts\jupyter.exe notebook`
        - Or to use Jupyter Lab, `Target = C:\bin\Anaconda3\Scripts\jupyter.exe lab`
        - Next, to have it start in a particular folder, change the "Start In" to = `c:\working` or wherever you want.

   - For OS X: you have to launch Jupyter from the directory that you want to work in. One way to do this is
        - Type `terminal` to launch the OS X Terminal
        - Next, to have it start in a particular folder, enter the command: `cd/folder_name`
        - After that, type `jupyter notebook` to launch Jupyter
        - If you don't want to enter the command `cd/folder_name` each time, you could set up a bash alias command. See this [tutorial](https://davidwalsh.name/alias-bash).

## Julia 1.0 with Atom + Juno

Note: This guide is a minimal example to get up-and-running with Julia 1.0 and [Atom](https://atom.io), extended with [Juno](http://junolab.org). For a more comprehensive overview of the Atom IDE, see the [Atom Tutorial](atom.md). 

### Choosing Atom + Juno 

* **Why these technologies?** Currently, the Juno environment is the richest IDE for Julia, with native support for things like plots, documentation, progress statistics, autocompletion, and namespaces. Juno is built on Atom, an open-soure and "hackable" (read: extendable, modular, etc.) text-editor. 

* **What are the drawbacks?** The main one is performance; Atom is a bit slower than VS Code. But this isn't too noticeble, and we think the extra features + interoperability with the rest of the Julia community is worth it. 

### Installation and Setup

1. Install Atom, by downloading it from the [Atom website](https://atom.io).

2. Go to the `Install` menu, either by clicking the appropriate button on the welcome screen, or navigating to it after opening the settings pane (`Cntrl,` on Windows, and `⌘,` on macOS).

3. Type `uber-juno` into the search box and hit enter. Click install on the package that appears. This will typically take a while, as Juno installs dependencies. When it asks you whether or not to use the standard layout, click `yes`.

4. Sometimes, Juno will fail to find the Julia executable (say, if it's installed somewhere nonstandard, or you have multiple). To do this, go back to preferences, click on `Packages`, type in `julia-client`. You'll then see a setting called `Julia path`. Fill it with the result of running `Sys.BINDIR` in the REPL, with an addiional `/julia` at the end. For example, in my REPL running that command yields:

    `/Applications/Julia-1.0.app/Contents/Resources/julia/bin`
    
    So I would type in `/Applications/Julia-1.0.app/Contents/Resources/julia/bin/julia` (no quotes).

5. You can test this setup by restarting Atom, opening the command palette (`Shift-Cntrl-P` on Windows, and `Shift-⌘-P` on a Mac, and selecting `Julia: Standard Layout`. :warning: Sometimes, you may encounter an error mesage, say because Atom was confused by the switch in versions. Restarting the program should resolve this. 

6. To change a few Atom settings, with `Shift-Ctrl-P` go to ` Atom > Open Your Config` to get your `config.cson` add,
- `softWrap: true` in the `editor:` section
- And
```
  "line-ending-selector":
    defaultLineEnding: "LF"
```    
If you do not want to mess with the `config.cson` directly, you can go `Ctrl-,` to get the settings and then go 
- `Packages` and choose `line-ending-selector` and change the setting to `LF`.
- `Editor` and change the soft wrap.

## Advanced Configuration for your Desktop: The Revise Workflow
It is much easier to edit sourcecode in an editor with [Revise.jl](https://github.com/timholy/Revise.jl).  See [configuration](https://timholy.github.io/Revise.jl/latest/config.html#Using-Revise-by-default-1) instructions for details, or
1. Find the `.` files are for your account.  For example, it is usually at `cd ~/.julia/` on linux/osx/windows with bash, or in a directory such as `C:\Users\USERNAME\.julia\`
2. Create a directory called `config` as required, so that `.julia/config/` exists
2. Copy [startup.jl](etc/startup.jl) to that directory, so that you have `.julia/config/startup.jl`

### Usage

* Define a variable in the REPL and navigate to the workspace tab (near documentation), and that variable (along with a MATLAB-style binding, `ans`) should appear. 

* Make a plot using 

```
    using Plots 
    x = 0.0:0.01:10.0 
    y = sin.(x)
    plot(x, y)
```

If you don't have `Plots.jl` installed, see our earlier configuration instructions. (You will quickly feel one of the major current issues with Julia environment right now: (time required to plot the first time, which they are working on).

* Create a new `.jl` file, or open the `example.jl` in this repository
  - To run a line of code in the editor, use `shift-enter`
  - To run the entire file, you can use the tools on the left hand bar, or `shift-control-enter` (with the usual proviso for Mac users).

* Use the `Documentation` pane to search up Julia objects (say, the function `getindex`).

### Additional Notes 

* [Juno Installation](http://docs.junolab.org/latest/man/installation.html)
* [Juno Usage Guide](http://docs.junolab.org/latest/man/basic_usage.html)

# Setting up Python the right way 🤞

Setting up Python on your computer is hard because there are many ways to do it. 

<img src="https://imgs.xkcd.com/comics/python_environment_2x.png" width=500>

Off the top of my head, the popular ones are:

1. Use the Python that comes pre-installed with macOS—bad idea because you don't want to pollute this
1. Download and install directly from python.org—bad idea because it messes up your path
1. Install it using a package manager, like brew—ok'ish idea, but you have no control of versions
1. **Install using a Python installation manager, like pyenv—better idea, (but linux and macOS only)** 👈 we'll use this

# But first, what is your `PATH`, and how does it work?

When you open your terminal and run `python` like so:

<img src="https://user-images.githubusercontent.com/1169974/78176391-662e9a00-742a-11ea-8de1-a618fa6d2aa1.png" width=600>

...your computer needs to know where to find `python`. You may have many `python`s installed on your computer, so how do you know _which_ one your OS is running? Simple, use `which`:

```bash
which python
/usr/bin/python
```

My OS is telling me that when I run `python`, it's using the `python` interpreter located in `/usr/bin/`.

Your terminal has access to a variable called `PATH` which is a _list_ of folders (seperated by `:`s) that are searched for any program you invoke. Here's what my PATH looks like:

```bash
echo $PATH
/usr/bin:/usr/local/bin:/bin:/usr/sbin:/sbin
```

So when I run `python` in my terminal, the following folders will be searched for a `python` executable:

1. `/usr/bin`
1. `/usr/local/bin`
1. `/bin`
1. `/usr/sbin`
1. `/sbin`

and the first result will be the one executed.

This has implications for installing Python as it may be installed in a less prioritized folder and so will never be run. So it's crucial to understand how to modify your `PATH` if you run into trouble. 

Your shell (the program your terminal runs when it starts) usually runs a script when you open it. Using a fresh installation of macOS? Then you're likely using `bash`, which runs the file `/Users/dvf/.bash_profile` when it starts. You can place any code in here if you want it to run when your terminal loads, including any `PATH` modifications:

For example, if you want to prepend `/some/new/path/to/python` at the beginning of your `PATH`, you can do:
```bash
export PATH="/some/new/path/to/python:$PATH"
```

As you'll see later, tools like Virtual Environments or `pyenv` are actually just modifying your `PATH` to point to different versions of Python.d

# Installing `pyenv`





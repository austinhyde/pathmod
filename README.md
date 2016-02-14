# pathmod

A very simple utility for modifying your POSIX `PATH` variable.

I like to edit my `~/.bashrc` frequently, and I got tired of my PATH additions like

```
export PATH="$HOME/.composer/vendor/bin:$PATH"
```

piling up:

```
/Users/austin/.phpbrew/php/php-5.6.17/bin:/Users/austin/.phpbrew/bin:/Users/austin/.composer/vendor/bin:/usr/local/sbin:/Users/austin/.composer/vendor/bin:/usr/local/sbin:/Users/austin/.composer/vendor/bin:/usr/local/sbin:/Users/austin/.composer/vendor/bin:/usr/local/sbin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/X11/bin
```

So I made `pathmod` to fix this problem.

This has been tested exclusively on Mac OS X. I'd like it to work everywhere, so if you try it on something else and it doesn't work, open an issue.

# Installation

Either:

* Clone this repo somewhere
* Download the raw `pathmod`

Then copy/symlink `pathmod` to somewhere in your path. `/usr/local/bin` or `$HOME/bin` are typically good choices.


# Usage

```
Usage: pathmod [-aehr] [-p pathstring] [paths...]
Adds or removes entries from your PATH environment variable
Default behavior is to echo the new PATH value with the given paths prepended, with duplicate entries removed
Note that this cannot set the PATH variable directly
  -a            Append the path entry rather than prepend it
  -e            Echo an eval-able statement for easier use.
                For example: eval $(pathmod -e foo)
  -h            Print this help message
  -r            Remove the given paths from the PATH.
  -p pathstring Use pathstring instead of the current PATH value

Examples:
  Add composer binaries to the beginning of PATH:
    $ eval $(pathmod -e $HOME/.composer/vendor/bin)
  Remove /usr/local/bin from the path
    $ eval $(pathmod -er /usr/local/bin)
  Print the current PATH
    $ pathmod
```

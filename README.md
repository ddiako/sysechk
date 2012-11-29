# System Security Checker [![Build Status](https://secure.travis-ci.org/infertux/sysechk.png)](http://travis-ci.org/#!/infertux/sysechk)

<pre>
        _           _             _
       / /\        / /\         /\ \
      / /  \      / /  \       /  \ \
     / / /\ \__  / / /\ \__   / /\ \ \
    / / /\ \___\/ / /\ \___\ / / /\ \ \
    \ \ \ \/___/\ \ \ \/___// / /  \ \_\
     \ \ \       \ \ \     / / /    \/_/
 _    \ \ \  _    \ \ \   / / /
/_/\__/ / / /_/\__/ / /  / / /________
\ \/___/ /  \ \/___/ /  / / /_________\
 \_____\/    \_____\/   \/____________/
</pre>

_System Security Checker_ is a bundle of small shell scripts to assess your
computer security.

All scripts run in read-only mode and will never modify any file on your system.
They rather print actions that should be done to improve system security.
You always have the last word (see [Disclaimer](#disclaimer) below).

Test scripts come from various sources:

  - [Common Configuration Enumeration](https://cce.mitre.org/lists/cce_list.html) (CCE&trade;):
    files named CCE-&lt;ID&gt;.sh (&lt;ID&gt; is the official CCE's ID)

  - [Guide to the Secure Configuration of Red Hat Enterprise Linux 5](https://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf):
    files named NSA-&lt;ID&gt;.sh (&lt;ID&gt; is the section number in the PDF)

  - other common best practices from here and there (custom tests):
    files named SSC-&lt;ID&gt;.sh (&lt;ID&gt; is an incremental counter)

__WARNING: This is a beta release still under development!__

![screenshot](https://imageshack.us/a/img89/8939/sysechk.png "Example output")


# Compatibility

The primarily targeted OS are Fedora, CentOS & Debian.
Other distributions might have fewer tests.
Since CentOS is fully compatible, RHEL should be too (not tested though).
Tests should be applicable to all variants (Desktop & Server) of each OS.


# Disclaimer

Do not attempt to implement any of the recommendations without first testing in
a non-production environment.

This software containing recommended security settings. It is not meant to
replace well-structured policy or sound judgment. Furthermore this software does
not address site-specific configuration concerns.


# Usage

1. Clone the latest version of SSC.

    ```
    git clone https://github.com/infertux/sysechk.git
    cd sysechk
    ```

1. Alternatively if you have already cloned it before, update it.

    ```
    cd sysechk
    git pull
    ```

1. Finally, run all tests.

    ```
    ./sysechk.sh
    ```

1. You can also run each test individually.

    ```
    ./tests/<test>.sh
    ```

## Flags

You can pass flags to `sysechk.sh` and to individual tests:

```
$ ./sysechk.sh -h
Usage: sysechk.sh [options]
  -h  Display this help
  -s  Skip all tests where root privileges are required (overrides -e)
  -e  Execute all tests where root privileges are required
  -f  Force the program to run even with root privileges
  -v  Be verbose
  -x <test>  Test to exclude (can be repeated, e.g. -x CCE-3561-8 -x NSA-2-1-2-3-1)
  -o <file>  Write the list of failed tests into an output file
  -m (trivial|minor|major|critical) Minimal severity to report

$ ./tests/NSA-2-1-2-3-1.sh -h
Usage: NSA-2-1-2-3-1.sh [options]
  -h  Display this help
  -s  Skip all tests where root privileges are required (overrides -e)
  -e  Execute all tests where root privileges are required
  -f  Force the program to run even with root privileges
  -v  Be verbose
  -x <test>  Test to exclude (can be repeated, e.g. -x CCE-3561-8 -x NSA-2-1-2-3-1)
  -o <file>  Write the list of failed tests into an output file
  -m (trivial|minor|major|critical) Minimal severity to report
```


# Bugs

Writing test scripts is probably the most boring part of this application but
it is also a challenging one to write quick and pretty shell scripts.
Every script does one test but does it well (UNIX way ;)).

I am not a Bash guru! There are probably bugs or optimizations that can be done
in test scripts. Any patches are welcome! :)


# License

AGPLv3


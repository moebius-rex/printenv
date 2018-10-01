# Environment Variable Print Command
A python script that pretty-prints operating system environment variable names and values in name order on Windows, Linux and MacOS X systems.


## Features
* Name-sorted, pretty-printed version of the Unix `printenv` or `env` and Windows `set` command outputs.
* When available, ANSI color codes are used to highlight names and values.
* Command line options provide a convenient, formatted alternative to piping output to `grep`-like commands.
* Variables containing multiple values may be printed on multiple lines, one per value, by providing the value separator string as a command line option.
* Unformatted output option mimics OS-native environment variable vieiwing commands.


## Supported Operating Systems
This script should run on all devices that support Python 2.7 or 3.x interpreters. It has been tested on Windows, Linux and MacOS X systems.


## Installation and Prerequisites
You will need a supported [Python](https://www.python.org/downloads/) interpreter installed on your target device before running this script.

Installing the script is as simple as downloading a copy of the
[printenv.py](https://raw.githubusercontent.com/moebius-rex/printenv/master/printenv.py) Python script and making sure that it is executable. Unix users can do this using `curl` and `chmod` for example, for example:

<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>curl https://raw.githubusercontent.com/moebius-rex/printenv/master/printenv.py > printenv.py
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  6940  100  6940    0     0  11875      0 --:--:-- --:--:-- --:--:-- 11863
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>chmod +x printenv.py
</pre>

Windows users may be best served by simply copying and pasting the [raw file contents](https://raw.githubusercontent.com/moebius-rex/printenv/master/printenv.py). Windows scripts are executable by default.

## Testing
The software has had some testing on Windows, Linux and MacOS X devices. There are no unit tests but they could be furnished upon request.


## Usage Examples
All usage examples below show ANSI color terminal output. For the sake of brevity, all output is simulated. 

### Pretty-print all environment variables:
<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>./printenv.py
<span class="name">    DISPLAY</span> <span style="color:#21D18B">:0</span>
<span class="name">       LANG</span> <span style="color:#21D18B">en_US.UTF-8</span>
<span class="name">   LANGUAGE</span> <span style="color:#21D18B">en_US</span>
<span class="name"><span style="color:#3B8EEA;">       PATH</span> <span style="color:#26B8D8">/home/user/bin:/usr/local/bin:/usr/bin:/bin</span>
<span class="name">        PWD</span> <span style="color:#26B8D8">/home/user</span>
<span class="name">      SHELL</span> <span style="color:#26B8D8">/bin/bash</span>
<span class="name">      SHLVL</span> <span style="color:#FFFFFF">1</span>
<span class="name"">       TERM</span> <span style="color:#21D18B">xterm-256color</span>
<span class="name">       USER</span> <span style="color:#21D18B">user</span>
<span class="name">VTE_VERSION</span> <span style="color:#FFFFFF">4205</span>
<span class="name">       _</span> <span style="color:#21D18B">./printenv.py</span>
</pre>

### Pretty-print variables containing multiple values separated by a semicolon on multiple lines, variable name on all lines:
<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>./printenv.py -s
<span style="color:#3B8EEA;">    DISPLAY</span> <span style="color:#21D18B">:0</span>
<span style="color:#3B8EEA;">       LANG</span> <span style="color:#21D18B">en_US.UTF-8</span>
<span style="color:#3B8EEA;">   LANGUAGE</span> <span style="color:#21D18B">en_US</span>
<span style="color:#3B8EEA;"><span style="color:#3B8EEA;">       PATH</span> <span style="color:#26B8D8">/home/user/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">       PATH</span> <span style="color:#26B8D8">/usr/local/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">       PATH</span> <span style="color:#26B8D8">/usr/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">       PATH</span> <span style="color:#26B8D8">/bin</span>
<span style="color:#3B8EEA;">        PWD</span> <span style="color:#26B8D8">/home/user</span>
<span style="color:#3B8EEA;">      SHELL</span> <span style="color:#26B8D8">/bin/bash</span>
<span style="color:#3B8EEA;">      SHLVL</span> <span style="color:#FFFFFF">1</span>
<span style="color:#3B8EEA;">       TERM</span> <span style="color:#21D18B">xterm-256color</span>
<span style="color:#3B8EEA;">       USER</span> <span style="color:#21D18B">user</span>
<span style="color:#3B8EEA;">VTE_VERSION</span> <span style="color:#FFFFFF">4205</span>
<span style="color:#3B8EEA;">       _</span> <span style="color:#21D18B">./printenv.py</span>
</pre>

### Pretty-print variables containing multiple values separated by a semicolon on multiple lines, variable name on first line only:
<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>./printenv.py -ns
<span style="color:#3B8EEA;">    DISPLAY</span> <span style="color:#21D18B">:0</span>
<span style="color:#3B8EEA;">       LANG</span> <span style="color:#21D18B">en_US.UTF-8</span>
<span style="color:#3B8EEA;">   LANGUAGE</span> <span style="color:#21D18B">en_US</span>
<span style="color:#3B8EEA;"><span style="color:#3B8EEA;">       PATH</span> <span style="color:#26B8D8">/home/user/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">           </span> <span style="color:#26B8D8">/usr/local/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">           </span> <span style="color:#26B8D8">/usr/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">           </span> <span style="color:#26B8D8">/bin</span>
<span style="color:#3B8EEA;">        PWD</span> <span style="color:#26B8D8">/home/user</span>
<span style="color:#3B8EEA;">      SHELL</span> <span style="color:#26B8D8">/bin/bash</span>
<span style="color:#3B8EEA;">      SHLVL</span> <span style="color:#FFFFFF">1</span>
<span style="color:#3B8EEA;">       TERM</span> <span style="color:#21D18B">xterm-256color</span>
<span style="color:#3B8EEA;">       USER</span> <span style="color:#21D18B">user</span>
<span style="color:#3B8EEA;">VTE_VERSION</span> <span style="color:#FFFFFF">4205</span>
<span style="color:#3B8EEA;">       _</span> <span style="color:#21D18B">./printenv.py</span>
</pre>

### Pretty-print only variables whose name or value contains a user-defined character sequence:
<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>./printenv.py PATH -s
<span style="color:#3B8EEA;"><span style="color:#3B8EEA;">PATH</span> <span style="color:#26B8D8">/home/user/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">PATH</span> <span style="color:#26B8D8">/usr/local/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">PATH</span> <span style="color:#26B8D8">/usr/bin</span>
<span style="color:#3B8EEA;"><span style="color:#2272C2;">PATH</span> <span style="color:#26B8D8">/bin</span>
</pre>

Use with the `-i` option to ignore the case of the supplied character sequence.

Character sequences may contain regular expression metacharacters, for example:
<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>./printenv.py U.*8 -s
<span style="color:#3B8EEA;">LANG</span> <span style="color:#21D18B">en_US.UTF-8</span>
</pre>

On Unix systems, similar results can be achieved by piping the results to commands like `grep` and `awk`. 

### Print help:
Use the `-h` or `--help` option to print instructions for using the command:

<pre>
<span style="color:#21D18B; font-weight:bold">user@host </span><span style="color:#3B8EEA; font-weight:bold">~ $ </span>./printenv.py -h
usage: printenv.py [-h] [-c] [-e] [-i] [-n] [-r] [-s [sep]] [-u] [-w]
                   [char-sequence]

description:

  Display environment variable names and values in name order.

  Features:
    * Name-sorted, colorized (Unix only) version of Unix 'env'/'printenv'
      and Windows 'set' commands.
    * Command line options provide convenient, formatted alternative to
      piping output to grep-like commands.
    * Variables containing multiple values may be printed on multiple
      lines, one per value, by providing the value separator string as
      a command line option.

positional arguments:
  char-sequence         print only those variable names/values that contain
                        this character sequence

optional arguments:
  -h, --help            show this help message and exit
  -c, --clear           clear terminal before printing
  -e, --exact-match     print only those variable names/values that exactly
                        match the character sequence provided
  -i, --ignore          ignore case in character sequence if supplied
  -n, --no-name-repeat  when used with -s option, suppress printing of
                        variable name on all but first line of multiple value
                        variables
  -r, --reset           reset terminal before printing
  -s [sep], --split [sep]
                        split multiple value variables by supplied 'sep'
                        (separator, default ':') string and print one value
                        per line
  -u, --unformatted     sort by name but disable all output formatting to
                        produce output similar to that of native operating
                        system commands
  -w, --wait            prompt user to exit script (useful when launching a
                        terminal window to run this command)
</pre>


## Authors
* [Shay Gordon](https://www.linkedin.com/in/shaygordon/) &mdash; Initial implementation


## Licensing and distribution
This project is licensed under the MIT License &mdash; see [LICENSE](LICENSE) for details.


## Acknowledgments
* [Bill Joy](https://en.wikipedia.org/wiki/Bill_Joy) for his original 1979 implementation of `printenv` for [BSD](https://en.wikipedia.org/wiki/Berkeley_Software_Distribution)
* Tracy and Paul for their unwavering support

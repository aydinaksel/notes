# Description

The `time` command is used to determine how long a given command takes to run. It is useful for testing the performance of your scripts and commands. The following is an example:

```bash
time <command>
time wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.19.9.tar.xz
```

The output is dependent on the version of the `time` command, as seen with the following:

```bash
# Bash
real	0m33.961s
user	0m0.340s
sys	  0m0.940s

# Zsh
0.34s user 0.94s system 4% cpu 33.961 total

# GNU time (sh)
0.34user 0.94system 0:33.96elapsed 4%CPU (0avgtext+0avgdata 6060maxresident)k
0inputs+201456outputs (0major+315minor)pagefaults 0swaps
```

The output from `Bash` can be described with the following:
- real or total or elapsed (wall clock time) is the time from start to finish of the call
- user - amount of CPU time spent in user mode.
- system or sys - amount of CPU time spent in kernel mode.

# Time Command Versions

You can use the `type` command to determine whether `time` is a binary or a built-in keyword.

```bash
type time
```

```bash
# Bash
time is a shell keyword

# Zsh
time is a reserved word

# GNU time (sh)
time is /usr/bin/time
```

To use the GNU `time` command, which has additional features, you need to specify the full path to the time binary, usually `/usr/bin/time`. For example, you can output to a file in append mode with the following:

```bash
/usr/bin/time -o <file-name> -a <command>
```

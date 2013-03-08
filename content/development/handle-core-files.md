Title: How to handle .core files
Date: 2013-03-07
Category: Development
Tags: linux, unix, admin
Summary: A way to handle .core files

When I develop or debug C++ program, I often have to deal with `.core` files that arise from crashes.

While everyone knows about:

    ::::bash
    ulimit -c unlimited

That enables the generation of such core files, it it also very useful to know about the `/proc/sys/kernel/core_pattern` file that controls where and how the `.core` files will be generated.

Here is the content of mine:

    /core/core-%e-pid-%p-sig-%s-time-%t

One can configure it for the current session doing, **as `root`**:

    ::::bash
    echo "/core/core-%e-pid-%p-sig-%s-time-%t" >> /proc/sys/kernel/core_pattern

It can also be configured permanently by adding the following line in `/etc/sysctl.conf`:

    kernel.core_pattern=/core/core-%e-pid-%p-sig-%s-time-%t

For the sake of completeness, here is the list of all the available special sequences:

    %p: pid
    %: '%' is dropped
    %%: output one '%'
    %u: uid
    %g: gid
    %s: signal number
    %t: UNIX time of dump
    %h: hostname
    %e: executable filename
    %: both are dropped

Happy debugging !

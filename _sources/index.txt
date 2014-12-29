
.. Unix & Git for Everyone slides file, created by
   hieroglyph-quickstart on Fri Nov 14 11:41:40 2014.

***********************
Unix & Git for Everyone
***********************

Getting comfortable with the command line and mastering basic git versioning
workflow.

.. slide:: Unix & Git for Everyone
    :level: 3

    *Goals*:

    .. rst-class:: build

    * Comfort and agility at the command line
    * Mastery of basic versioning workflow with git

.. slide:: Today's Agenda
    :level: 3

    .. rst-class:: build

    * Find/Install your command line
    * Get accustomed to finding your way around
    * Create a journal to record what you learn
    * Put your journal into version control with basic git workflow
    * Learn some more advanced shell commands
    * Learn some more advanced git commands

    .. rst-class:: build

    .. container::

        Along the way, you'll get a chance to learn more about the history of
        unix.

        And you'll gain a deeper understanding of what exactly git does when
        you use it.

.. slide:: By The End Of Today
    :level: 3

    Using only your browser, your text editor and your command line, you'll be
    able to

    .. rst-class:: build

    * move around and manipulate files with confidence
    * learn about common unix commands
    * run programs from your command line
    * control access to your filesystem
    * create a git repository from scratch
    * add, edit and remove items from a repository
    * connect a repository to the larger world with GitHub

Unix
====

A bit of history and context

History
-------

.. slide:: Unix Commands
    :level: 1

    A bit of history and context

.. slide:: What is Unix?
    :level: 3

    .. rst-class:: build

    * Multiuser Multitasking Operating System
    * Unix can be a lot of things

      .. rst-class:: build

      * A desktop
      * A server
      * A super computer
      * A phone
      * An embedded system

.. slide:: History
    :level: 3

    .. rst-class:: build


     * Created at AT&T's Bell labs by Ken Thompson and Dennis Ritchie

     * In 1983 Richard Stallman began the creation of GNU Project (Gnu's not
       Unix) with the intention of creating an open source version of Unix

     * In 1991, a student at Helsinki name Linus Torvalds created a small unix
       kernel for his 80386 PC

.. slide:: Announcing Linux
    :level: 3

    Hello everybody out there using minix -

    I'm doing a (free) operating system (just a hobby, won't be big and
    professional like gnu) for 386(486) AT clones. This has been brewing
    since april, and is starting to get ready. I'd like any feedback on
    things people like/dislike in minix, as my OS resembles it somewhat
    (same physical layout of the file-system (due to practical reasons)
    among other things).

    I've currently ported bash(1.08) and gcc(1.40), and things seem to work.
    This implies that I'll get something practical within a few months, and I'd
    like to know what features most people would want. Any suggestions are
    welcome, but I won't promise I'll implement them :-)

    Linus (torvalds@kruuna.helsinki.fi)

    PS. Yes it's free of any minix code, and it has a multi-threaded fs. It
    is NOT portable (uses 386 task switching etc), and it probably never will
    support anything other than AT-harddisks, as that's all I have :-(.

    Linus Torvalds

.. slide:: History
    :level: 3

    Linux is now the largest software project that has ever existed in the
    history of computing,

    Why?

    .. rst-class:: build

    * open source
    * anyone can work on it.



.. slide:: Current State of Unix on the Desktop
    :level: 3

    .. rst-class:: build

    * Linux
    * BSD (Berkeley Software Distribution)
    * Mac OSX (Darwin)

Philosophy
----------

.. slide:: Philosophy
    :level: 3

    .. rst-class:: build

    * Everything is a file

      .. rst-class:: build

      * Including pieces of the Kernel and hardware
      * Linux exposes these interfaces in /proc and /sys
      * OSX does not directly expose these interfaces to the user, instead use
        sysctl

    * "Do one thing and do it well"
    * "Every output can become the input of another program"

Architecture
------------

.. slide:: Two Major Unix Components
    :level: 3

    .. rst-class:: build

    * Kernel

      .. rst-class:: build

      * Is the absolute core of the OS
      * Determines what runs on the CPU
      * Interacts directly with the hardware

    * The shell

      .. rst-class:: build

      * How the user interacts with the operating system

    * Represent two different execution environments on a Unix

      .. rst-class:: build

      * Kernel space
      * User space

.. slide:: Kernel Space
    :level: 3

    .. rst-class:: build

    * Represents the "admin" user space
    * Directly affects the hardware, filesystem and how the system itself runs
    * You need elevated access in order to manipulate anything here
    * At the same time, users need to be able to access things like hardware
      and the filesystem
    * The kernel provides "system calls" that check permissions and allow or
      disallow certain actions

.. slide:: User Space
    :level: 3

    .. rst-class:: build

    * All the actions that aren't in Kernel Space
    * Has to use system calls in order access the hardware
    * Manifests as a "shell" run in a terminal program

    .. rst-class:: build

    .. container::

        This is where we will spend our time today

        (and for the for the forseeable future)

.. slide:: Next Up
    :level: 2

    `Travelling the Filesystem <./travelling.html>`_

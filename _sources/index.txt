
.. Git & Unix for Everyone slides file, created by
   hieroglyph-quickstart on Fri Nov 14 11:41:40 2014.

***********************
Git & Unix for Everyone
***********************

Getting comfortable with the command line and mastering basic git versioning
workflow.

.. slide:: Git & Unix for Everyone
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
    * learn about commands
    * run programs
    * control access to your filesystem
    * create a git repository from scratch
    * fork someone else's repository
    * clone a repository to your laptop
    * add, edit and remove items from a repository
    * interact with the owners of other repositories using github

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


Working on the Command Line
===========================

In which we get to know the basic commands for finding our way around in a
terminal.

.. slide:: Working on the Command Line
    :level: 1

    Getting to know your way around

.. slide:: Your First Terminal Session
    :level: 3

    Locate and open your terminal

    .. rst-class:: build

    * Linux Users

      * Use the keyboard shortcut ``Ctrl-Alt-T``

    * OSX Users

      * launch ``Finder``
      * go to ``Applications`` > ``Utilities``
      * click on ``Terminal``
      * right-click on dock icon, click ``Options`` > ``Keep In Dock``

    * Windows Users

      * you'll use ``git-bash`` instead of the windows command prompt
      * right-click on desktop
      * select ``Git Bash``
      * if not already set, right-click taskbar icon and select 'pin this
        program to the taskbar'

.. slide:: Reading the Prompt
    :level: 3

    The first stuff you see in your terminal is called *the prompt*.

    .. rst-class:: build

    .. container::

        It will include your username, where you are, and what machine this
        terminal is on.

        By default:

        .. rst-class:: build

        * OSX:

        .. code-block:: bash

            machine_name:current_directory username$

        * Linux:

        .. code-block:: bash

            username@machine_name:current_path$


        * Windows (git-bash):

        .. code-block:: bash

            username@machine_name current_path
            $

.. slide:: Home Is Where Your Stuff Is
    :level: 3

    In general, most systems will open a terminal in your *home directory*

    .. rst-class:: build

    .. container::

        This is a folder on the computer filesystem that belongs to you.

        You put your work here, configure settings for many programs and so on.

        You can see where you are using the shell command ``pwd``

        Type that command into your terminal now


.. slide:: COMMAND: ``pwd``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``pwd`` command shows the *present working directory*

        OSX

        .. code-block:: bash

            $ pwd
            /Users/cewing/projects

        Linux

        .. code-block:: bash

            $ pwd
            /home/cewing/projects

        Windows (git-bash)

        .. code-block:: bash

            $ pwd
            /c/Users/Cris Ewing/projects

.. slide:: CONCEPT: The Path
    :level: 2

    .. rst-class:: left
    .. container::

        In any computer system, a **path** represents a location in the
        filesystem.

        .. rst-class:: build

        .. container::

            Paths are like addresses, listing a location from the general to the
            specific.

            A bit like addressing an envelope backwards:

            | USA
            | Seattle, WA 98105
            | 123 Somestreet
            | Cris Ewing
            |

            vs.

            | /home/cewing/projects/someproject
            |

            A path is *absolute* when it starts with ``/``

            A path is *relative* when it does not

.. slide:: QUESTION
    :level: 2

    Is the **path** returned by the ``pwd`` command *absolute* or *relative*?

.. slide:: Moving Around
    :level: 3

    Movement is basic to life.

    .. rst-class:: build

    .. container::

        All operating systems distribute resources among many *directories*

        To be a power user of the command line, you must be able to move
        around.

        The command for moving from one directory to another is called ``cd``

        You can supply a *path* to tell the terminal the address where you want
        to go

        This path can be *absolute* **or** *relative*.

.. slide:: COMMAND: ``cd``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``cd`` command allows you to *change directories*

        It can take a *path* as an argument (*absolute* or *relative*)

.. slide:: QUESTION
    :level: 2

    What happens if you do not supply a *path* to indicate where you want to
    go?

.. slide:: To the Root
    :level: 3

    Before we begin, use ``pwd`` again to show the path to your *home
    directory*

    .. rst-class:: build

    .. container::

        Write this value down

        You'll use it in a moment to get back

        Now type the following command at your prompt:

        .. container::

            OSX/Linux:

            .. code-block:: bash

                $ cd /

            Windows:

            .. code-block:: bash

                $ cd /c

.. slide:: To the Root
    :level: 3

    You've just changed directories.

    .. rst-class:: build

    .. container::

        The address you supplied to the ``cd`` command was for the *root* of
        your computer

        (Windows users, this isn't *exactly* true, but it's true enough for
        today)

        This is the very topmost container in your filesystem

        Everything else is located inside this directory, or in a directory
        whose *path* starts here.

        **paths that start with the root are absolute because there can be no
        ambiguity about where to start looking**

.. slide:: CONCEPT: The Root
    :level: 2

    .. rst-class:: left
    .. container::

        The **root** is the topmost container of a computer filesystem

        Everything on the computer can be said to be contained in **the root** or
        in a container that is contained there

        Absolute paths always begin with **the root**, so that there is no doubt
        about where to begin moving through the filesystem

        **The root** is generally restricted to administrative users

        You should never delete anything located directly in **the root**

.. slide:: Looking Around
    :level: 3

    Now that you're here at **the root** of your computer filesystem, you might
    want to see what's here.

    .. rst-class:: build

    .. container::

        To list the contents of your *present working directory*, you'll use
        the ``ls`` command.

        Type this command at your prompt:

        .. code-block:: bash

            $ ls

.. slide:: Looking Around
    :level: 3

    You should see something like this:

    OSX:

    .. code-block:: bash

        Applications    Users       dev     net     tmp
        Library         Volumes     etc     opt     usr

    Linux:

    .. code-block:: bash

        bin   etc   lib    lost+found  opt   run      srv  usr
        boot  home  lib64  media       proc  sbin     sys  var

    Windows:

    .. code-block:: bash

        $Recycle.Bin  Documents and Settings  Recovery                   autoexec.bat
        BOOTSECT.BAK  PerfLogs                System Volume Information  bootmgr

.. slide:: Take a Closer Look
    :level: 3

    Like many unix-style shell command, the behavior of ``ls`` can be modified

    .. rst-class:: build

    .. container::

        By default, it shows the names of items in your *present working directory*
        in alphabetical order

        By providing the command with *flags*, we can modify that

        For example, the ``t`` flag changes the order of the listing so that
        the most recently modified items are first.

        .. container::

            You can supply a *flag* to a command with the ``-`` sign, like so:

            .. code-block:: bash

                $ ls -t

        Try it out now.

.. slide:: Prove it works
    :level: 3

    Clearly, the ordering changes, but is it really sorting by modification
    time?

    .. rst-class:: build

    .. container::

        The ``l`` *flag* changes the listing shown to *long* format

        .. container::

            This will display permission, ownership and modification
            information about each item in the directory:

            .. code-block:: bash

                $ ls -l
                drwxr-xr-x  2 root root  4096 Sep 23 12:08 bin
                drwxr-xr-x  3 root root  4096 Nov  5 15:25 boot
                ...

        You can combine flags by adding each to a single ``-``

        .. container::

            Try this:

            .. code-block:: bash

                $ ls -lt

.. slide:: Turn it Around
    :level: 3

    We have a command that lists items alphabetically

    .. rst-class:: build

    .. container::

        We can modify it to list them by modification date, with the most
        recent first.

        What if we want to reverse the ordering?

        The ``r`` flag (note that that is a lower-case r) does this.

        Try using that flag by itself

        Try combining it with the ``t`` flag

        Try combining it with ``l`` and ``t``

.. slide:: COMMAND: ``ls``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``ls`` command shows you a *listing* of the contents of your
        *present working directory*

        The behavior of this command can be altered by *flags*

        The ``l`` flag returns the listing in *long* format

        The ``t`` flag returns the listing ordered by modification *time*

        The ``r`` flag *reverses* the order of the listing

.. slide:: CONCEPT: flags
    :level: 2

    .. rst-class:: left
    .. container::

        Unix commands may be modified by providing *flags*

        Each *flag* changes the behavior of a command in a single, simple way

        The *flags* can be combined to produce more complex changes

        *Flags* are provided by using the ``-`` sign after the command

.. slide:: QUESTION
    :level: 2

    How can you know what *flags* may be used for a given command?

.. slide:: RTFM
    :level: 3

    Unix-like systems provide a system command called ``man`` (short for
    *manual*)

    .. rst-class:: build

    .. container::

        You provide this command the name of another command

        It will return a manual explaining how that command works and what options
        it provides

        .. container::

            Type the following command at your prompt:

            .. code-block:: bash

                $ man ls

        Windows users, this will not work for you

        Instead, use your web browser and type the same command into your
        search bar

        Teh Google will provide

.. slide:: COMMAND: ``man``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``man`` command provides access to the built-in *manual* for all
        unix commands

        Providing the command with the name of some other command will print
        detailed information about how that command may be used

        Often these *manual* pages include useful examples for common and
        advanced usage patterns

.. slide:: Test it out
    :level: 3

    Spend the next five to ten minutes trying out different *flags* to the
    ``ls`` command

    .. rst-class:: build
    .. container::

        For each flag you try, make a prediction about the effect it will have

        After trying it, review your prediction

        Were you right?

        If not, in what way were you wrong?

        What happened that surprised you?

        These sorts of surprises are the seeds of learning, treasure them

.. slide:: Going Home
    :level: 3

    Okay.  Enough poking about here at *the root*

    .. rst-class:: build
    .. container::

        Let's head back to our *home directory*

        You wrote down the *path* returned by the ``pwd`` command as we were
        leaving.

        Can you get back there now?

        .. code-block:: bash

            $ cd /Users/cewing

.. slide:: Trouble Spot
    :level: 3

    Some of you may have a bit of difficulty at this point

    .. rst-class:: build
    .. container::

        For example, Windows users may have a *path* for their *home directory*
        that looks like this:

        .. code-block:: bash

            /c/Users/Cris Ewing

        .. code-block:: bash

            $ cd /c/Users/Cris Ewing
            sh.exe": cd: /c/Users/Cris: No such file or directory

        The problem is the space between my first and last names

        The command line expects paths to be a single continuous string of
        characters

        Spaces are used to delimit one element of the command line from the next

        So how do we cope with this?

.. slide:: Escape from Space Mountain
    :level: 3

    The secret lies in tricking the command line into thinking that the space
    is just another character like any other letter or number

    .. rst-class:: build
    .. container::

        You can do this by *escaping* it with the ``\`` character

        Try typing this instead:

        .. code-block:: bash

            $ cd /c/Users/Cris\ Ewing

        How'd that work?

.. slide:: What's in a Name?
    :level: 3

    This brings up the idea of unix *naming conventions*

    .. rst-class:: build
    .. container::

        In general, unix power users tend not to use spaces in the names they
        give to things.

        Use dashes (``-``) or underscores (``_``) to separate words in names

        This will help as you start working with software systems that don't
        play nicely with spaces in path names.

        It gets easier to do this as you use the command line more

.. slide:: wHat'S IN a nAmE?
    :level: 3

    One other interesting issue to cover here is the question of *case
    sensitivity*

    .. rst-class:: build
    .. container::

        Linux is a *case sensitive* operating system

        This means that the names ``foo.jpg`` and ``FOO.JPG`` *are not* the
        same

        OSX and Windows are *case insensitive*, which means those two names
        *are* the same

        (however, in terminals, unix command names are case sensitive)

        Most unix power users tend to write **all** names in lower-case
        letters.

        (**bonus**: you don't have to use the shift key when you do)

.. slide:: CONCEPT: Naming Conventions
    :level: 2

    .. rst-class:: left
    .. container::

        Avoid spaces in the names you give to files and directories

        Use dashes and underscores to create visual separation between words in
        names

        Prefer lower-case letters in naming files and directories

.. slide:: Cutting Corners
    :level: 3

    So far, we've used ``cd`` to move to *the root* of our filesystem and back

    .. rst-class:: build
    .. container::

        Each time we've provided an *absolute path* as an address to where we'll go

        But we can also use *relative paths* as addresses

        When we do, they are considered to be *relative* to where we are now

        In other words, *relative paths* are always construed by the OS as
        beginning with the value of ``pwd``

.. slide:: Prove It Works
    :level: 3

    Use the ``ls`` command to see what you have here in your *home directory*

    .. rst-class:: build
    .. container::

        Use the ``l`` flag to get the *long* format

        Notice that some of the entries in the list start with a ``d`` and some
        begin with ``-``

        Those that begin with ``d`` are *directories*, pick one

        Use the ``cd`` command, providing the name of your chosen directory as a
        *relative path*

        Now, make a prediction about the *path* of your *present working directory*

        Finally, use the ``pwd`` command to confirm or reject your prediction

        Repeat the exercise, moving further down from your home

.. slide:: Going Up
    :level: 3

    You've now moved several levels down from your *home directory*, but how to
    get home?

    .. rst-class:: build
    .. container::

        You could provide the *absolute path* of your home directory, you've done
        that before

        But let's mix it up a bit

        In unix systems, the symbol ``..`` (two periods) stands for "one filesystem
        level above where I currently am"

        You can use this *relative path* with the ``cd`` command to move up one
        level

        .. container::

            Try it:

            .. code-block:: bash

                $ cd ..

.. slide:: Going Up
    :level: 3

    You can even chain them together, providing *relative paths* that
    go up more than one level:

    .. rst-class:: build
    .. container::

        .. code-block:: bash

            $ cd ../..

        .. container::

            And you can combine these with directory names to go back down into
            a different branch of your filesystem:

            .. code-block:: bash

                $ cd ../somewhere-else

.. slide:: Look Around You
    :level: 3

    Take the next five to ten minutes to explore your filesystem

    .. rst-class:: build
    .. container::

        Use the ``ls`` command to find *directories* in your *present working
        directory*

        Use the ``cd`` command to move down into and back up out of various
        directories

        Use *relative paths* and the ``..`` symbol

.. slide:: The Express Train Home
    :level: 3

    Finish when you are somewhere **not** in your *home directory*

    .. rst-class:: build
    .. container::

        Do you know the exact command to give to get home from wherever you
        are?

        Remember back a while, when you tried the ``cd`` command *without a
        path*?

        .. container::

            Try it again:

            .. code-block:: bash

                $ cd

        Where are you now?

        Is that what you thought it did before?

.. slide:: Home by Another Name
    :level: 3

    You've seen how ``..`` is interpreted by the command line to mean "one
    level up from here"

    .. rst-class:: build
    .. container::

        That's not the only symbol you have to work with

        Use ``cd``, ``ls`` and ``..`` to move away from your home directory
        again

        .. container::

            When you've moved away three or four steps, try this:

            .. code-block:: bash

                $ ls ~

        That squiggle after the ``ls`` command is a *tilde*

        You can find it in the upper left corner of your keyboard

        Your command line replaces that symbol with the *absolute path* of your
        *home directory*

.. slide:: Listing Somewhere Else
    :level: 3

    One other item of note in that last command

    You provided a *path* to the ``ls`` command, what was the result?

    In fact, the ``ls`` command can list places other than where you are now,
    if you provide a *path*

    Try listing **the root**: ``ls /``

    Try listing a *directory* located at the root

    Try combining a path with *flags* to the ``ls`` command

    Does the order in which you give the two make a difference?

.. slide:: Short For Here
    :level: 3

    In point of fact, if you don't give ``ls`` a path, it simply assumes you
    mean "right here"

    .. rst-class:: build
    .. container::

        You can make this explicit by using the ``.`` symbol (one period)

        Just as ``..`` means "one level up from here", ``.`` means "right here"

.. slide:: QUESTION
    :level: 2

    Does ``...`` mean "two levels up from here"?

.. slide:: CONCEPT: shortcuts
    :level: 3

    You can use the ``..`` symbol as an element in a *path* (absolute or
    relative) as a shortcut for "one level up"

    You can use the ``.`` symbol as an element in a *path* as a shortcut for
    "right here"

    You can use the ``~`` (tilde) as a shortcut for the *absolute path* of your
    *home directory*

    You can use the ``cd`` command without an argument to return to your *home
    directory* immediately from anywhere

.. slide:: Review
    :level: 1

    Take a moment to reflect

.. slide:: COMMANDS
    :level: 3

    You've learned and used the following commands:

    ======= =============================================================
    command purpose
    ======= =============================================================
    ``pwd`` obtain the *absolute path* of the *present working directory*
    ------- -------------------------------------------------------------
    ``cd``  change directories to the path provided (or home if none)
    ------- -------------------------------------------------------------
    ``ls``  list the contents of the provided path (or here if none)
    ------- -------------------------------------------------------------
    ``man`` get information about the options and usage for any command
    ======= =============================================================

.. slide:: CONCEPTS
    :level: 3

    You've also learned the following concepts:

    The Path
      An *address* for a filesystem location, either *absolute* or *relative*

    The Root
      The location at the top of the filesystem which contains everything else

    Flags
      Symbols provided at the command line to alter the behavior of commands.
      They may be combined to achieve complex changes

    Naming Conventions
      Common practices around the naming of things adopted by power users,
      usually in accomodation of some aspect of the command line

    Shortcuts
      Ways to provide potentially long values by using a much shorter symbolic
      representation

.. slide:: Take a Break
    :level: 1

    You've earned it












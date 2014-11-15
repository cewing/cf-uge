
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

        It takes a *path* as its one required argument

        This tells the terminal the address where you want to go

        This path can be *absolute* **or** *relative*.

.. slide:: COMMAND: ``cd``
    :level: 3

    The ``cd`` command allows you to *change directories*

    It takes a *path* as an argument (*absolute* or *relative*)



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

            .. code-block:: language
            
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

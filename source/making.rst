
.. Git & Unix for Everyone slides file, created by
   hieroglyph-quickstart on Fri Nov 14 11:41:40 2014.

***********************
Git & Unix for Everyone
***********************

Getting comfortable with the command line and mastering basic git versioning
workflow.

Manipulating the Filesystem
===========================

In which we learn to create, modify, move, and destroy things as well as how to
preserve a record of the actions we take.

.. slide:: Manipulating the Filesystem
    :level: 3

    Learn to make, move, and modify

.. slide:: Captured History
    :level: 3

    One way to help cement learning is to take notes

    .. rst-class:: build
    .. container::

        You've already spent quite some time learning today, but have yet to take
        any notes

        Or have you?

        As it turns out, your shell keeps track of what you do as you do it

        You can look over this record using the ``history`` command

        .. container::

            Try it out:

            .. code-block:: bash

                $ history

.. slide:: Reading History
    :level: 3

    You should see something like this:

    .. code-block:: bash

        ...
        432  ls
        433  ls -l
        434  cd projects/
        435  ls
        436  ls -l
        437  cd training/
        438  ls
        439  ls -l
        440  cd /
        441  cd
        442  cdcd
        443  cdcd
        444  cd /
        445  cd
        446  cd
        447  ls

.. slide:: COMMAND: ``history``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``history`` command allows you to review and revise the history of
        actions you've taken in a shell

        Providing a numeric argument will list the last *n* actions:

        .. code-block:: bash

            $ history 5
            443  cdcd
            444  cd /
            445  cd
            446  cd
            447  ls

.. slide:: Paging Through History
    :level: 3

    There's probably a lot more output from that command than fits in one
    screen of your terminal

    .. rst-class:: build
    .. container::

        Most of it scrolled by too fast to read

        You could read the last *n* actions

        .. container::

            Or you can review it all at your leisure by combining the ``history``
            command with another command ``less``:

            .. code-block:: bash

                $ history | less

        The *pipe* character (``|``) takes the output from the first command
        and uses it as input to the second

.. slide:: Chain of Commands
    :level: 3

    Remember the Unix Philosophy::

        Do one thing and do it well
        Every output can become the input of another program

    .. rst-class:: build
    .. container::

        Here, the text output by ``history`` is taken as input to the command
        ``less``

        That command allows you to control the rate of scrolling for longer files

        You can press **enter** to move one line forward at a time

        Or press **space** to move a full screen forward at once

        You can also move forward arbitrary numbers of lines, or backward!

        Try ``man less`` to learn more about this useful comand

.. slide:: COMMAND: ``less``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``less`` command allows the user to control movement through the
        reading of a file

        It provides controls for moving forward or backward through files at
        increments of an arbitrary number of lines or screens

        It does not read entire files before starting, and so is very fast

        It is particularly well suited to input *piped* from other commands
        that produce large amounts of text

.. slide:: CONCEPT: Piping
    :level: 2

    .. rst-class:: left
    .. container::

        The *pipe* (``|``) can be used to use the output of one command as the
        input to another

        This *chaining* of commands allows the savvy user to combine simple unix
        commands into complex processes with little effort and powerful results

.. slide:: Saving History
    :level: 3

    But there's more you can do with this history

    .. rst-class:: build
    .. container::

        Begin by making sure that you are in your *home directory* using ``pwd``,
        ``ls`` and ``cd``

        .. container::

            Next, you'll use the *redirection* operator (``>``) to take the output from
            ``history`` and write it to a file:

            .. code-block:: bash

                $ history > moving_around.txt

        You can use ``ls`` to verify that the new file "moving_around.txt" exists

        You can use the ``t`` flag to verify that it's the newest file in your home
        directory

        You can even use the ``less`` command to read it and verify that it
        contains your history.

.. slide:: CONCEPT: Redirection
    :level: 2

    .. rst-class:: left
    .. container::

        The *redirection* operator (``>``) sends the output of a command on the
        left side to a file named on the right

        If the named file does not exist, it is created

        If it does exist, it is overwritten

        If the operator is doubled (``>>``) then output is *added* to an existing
        file instead of replacing it

        You can do a *lot* more with redirection (try googling for *bash
        redirection*) but thats enough for today

.. slide:: Take Notes
    :level: 3

    Now that you have this file with your command history, open it in your
    editor:

    .. code-block:: bash

        $ subl moving_around.txt

    .. rst-class:: build
    .. container::

        Take the next 10 minutes or so to edit that history

        Add notes to lines after the commands you found particularly interesting or
        surprising

        Add information explaining the purpose of a command, and the result

        You can delete boring lines or even your embarassing mistakes

        Take this opportunity to ask your instructors questions, if you haven't
        already

        Make sure you understand everything you've done so far today

.. slide:: Keep It Safe
    :level: 3

    Come to think of it, it might be nice to keep these notes (and more you'll
    make today) safe

    .. rst-class:: build
    .. container::

        Let's begin by making a place to keep them

        .. container::

            Use the ``mkdir`` command to create a new directory here in your *home
            directory* to hold these notes:

            .. code-block:: bash

                $ mkdir gue_workshop

        Use ``ls`` to confirm that the new directory exists

        Use the ``l`` flag with ls to confirm that the new directory is a directory

.. slide:: Put Things in Their Place
    :level: 3

    Now that you have a directory to hold your notes, move them on in

    .. rst-class:: build
    .. container::

        You can use the ``mv`` command to move a file from one place to another

        This command is a bit different from others we've seen in that it requires
        *two* paths

        The first is the address of the thing you want to move

        The second is the address of where you want to put it

        .. code-block:: bash

            $ mv moving_around.txt ./gue_workshop/

.. slide:: Better Names
    :level: 3

    Actually, the filename "moving_around.txt" is not all that great

    We should rename it to something better, like "unix_notes.txt"

    .. container::

        You can use the ``mv`` command to do this, too:

        .. code-block:: bash

            $ mv ./gue_workshop/moving_around.txt ./gue_workshop/unix_notes.txt

    That's better

    Don't forget to add any notes you might want about ``mv`` to your newly
    renamed file

.. slide:: COMMAND: ``mv``
    :level: 2

    .. rst-class:: left
    .. container::

        The ``mv`` command allows *moving* files from place to place in a
        filesystem

        The command expects two paths: a thing to be moved and a place to move
        it

        The command can be used to move files and also to rename them

        *Flags* allow you to handle conditions like there being a file of the
        same name already in the destination in various ways

        Try ``man mv`` to learn more about this command

.. slide:: Saving Your Work
    :level: 3

    You've got all these great notes

    .. rst-class:: build
    .. container::

        It'd be terrible if something were to happen to them

        This is where having something like version control can come in handy

        It can allow you to keep a history of your work on a project like this
        safe

        And can also allow you to collaborate with others over time

        We'll start by creating a *repository* for our work from today

        We'll be using the ``git`` Distributed Version Control System

.. slide:: Install Git
    :level: 3

    If you haven't already done so, please download and install git now

        http://git-scm.com/downloads

    Windows users, please install git from here instead:

        http://msysgit.github.io/

.. slide:: Basic Configuration
    :level: 3

    You should also be sure to set up the basic configuration git requires

    .. rst-class:: build
    .. container::

        In order to make commits, git wants to know your name and email address

        .. container::

            We use the ``config`` git command to set these up:

            .. code-block:: bash

                $ git config --global user.name "Cris Ewing"
                $ git config --global user.email "cris@crisewing.com"

        This will allow git to record that you made changes, and to provide
        contact information for any who wish to consult with you


.. slide:: Your First Repository
    :level: 3

    Once git is installed and configured, creating your first repository is a
    snap

    Begin by changing directories into the one that holds the files you want to
    save

    In your case, that's the new ``gue_workshop`` directory you just created a
    moment ago

    Once there, use the ``init`` git command to create a new repository

    .. code-block:: bash

        $ git init
        Initialized empty Git repository in /home/cewing/gue_workshop/.git

.. slide:: What's Up, Git?
    :level: 3

    You can now check the status of your repository using ``status``:

    .. rst-class:: build
    .. container::

        .. code-block:: bash

            $ git status
            On branch master

            Initial commit

            Untracked files:
              (use "git add <file>..." to include in what will be committed)

                unix_notes.txt

            nothing added to commit but untracked files present (use "git add" to track)

        Notice that git is quite verbose in telling you what's going on

        You can see that you have one untracked file

        Git even tells you what to do next

.. slide:: Adding your first file
    :level: 3

    A repository is simply a collection of things you care about

    .. rst-class:: build
    .. container::

        In order for git to save anything, it must first be ``added`` to the
        repository

        .. container::

            Use the ``add`` command to add your ``unix_notes.txt`` file:

            .. code-block:: bash

                $ git add unix_notes.txt

        There should be no output here, but your file has now been added

.. slide:: QUESTION
    :level: 2

    How can you tell that the file has been added to the repository?

.. slide:: Always Check Status
    :level: 3

    Of course, you use ``status``

    .. rst-class:: build
    .. container::

        It's a good idea to develop the habit of checking the status of your
        repository regularly

        .. code-block:: bash

            $ git status
            On branch master

            Initial commit

            Changes to be committed:
              (use "git rm --cached <file>..." to unstage)

                new file:   unix_notes.txt

        You can now see that the notes file has been added and is ready to be
        *committed*

.. slide:: Commits Save Changes
    :level: 3

    Until you *commit* your chages nothing is permanent

    .. rst-class:: build
    .. container::

        As the previous slide showed, we could still *unstage* these changes,
        allowing our repository to forget this file exists

        But we don't want to do that

        .. container::

            So let's go ahead and use ``commit`` to save what we've done:

            .. code-block:: bash

                $ git commit -m "adding unix notes, first draft"
                [master (root-commit) 0bc447c] adding unix notes, first draft
                 1 file changed, 0 insertions(+), 0 deletions(-)
                 create mode 100644 unix_notes.txt

        .. container::

            And ``status`` shows the result:

            .. code-block:: bash

                $ git status
                On branch master
                nothing to commit, working directory clean

.. slide:: What Makes a Repository?
    :level: 3

    You have now created a repository and added a new file to it

    .. rst-class:: build
    .. container::

        You can even look at the history of your repository now (short though it
        may be)

        .. code-block:: bash

            $ git log
            commit 0bc447c0cfd0b7856cd19c705e8eefa0c64283de
            Author: cewing <cris@crisewing.com>
            Date:   Sat Nov 15 03:33:09 2014 -0800

                adding unix notes, first draft

        But how does this all happen?

        Where is the stuff that makes this work?

.. slide:: Peek Behind the Curtain
    :level: 3

    If you use the ``ls`` command inside your repository, all you'll see is
    your notes file

    .. rst-class:: build
    .. container::

        But there's more there than meets the eye

        .. container::

            Use the `a` flag to ``ls`` to see *all* items in the folder:

            .. code-block:: bash

                $ ls -la
                total 0
                drwxr-xr-x   4 cewing  staff  136 Nov 15 03:15 .
                drwxr-xr-x   6 cewing  staff  204 Nov 15 03:15 ..
                drwxr-xr-x  13 cewing  staff  442 Nov 15 03:33 .git
                -rw-r--r--   1 cewing  staff    0 Nov 15 03:15 unix_notes.txt

        That ``.git`` directory is the special secret sauce

        Everything that git knows about your repository is held in that folder

        If you delete it (don't), your repository becomes just another
        directory

.. slide:: CONCEPT: Hidden Files
    :level: 2

    .. rst-class:: left
    .. container::
    
        This ``.git`` directory is an example of a *hidden file*

        In Unix, any file whose name begins with ``.`` is, by default, not shown to
        the user unless specifically asked for

        This helps to keep the clutter associated with maintenance and
        configuration out of sight

        The ``.`` and ``..`` items in every directory on the filesystem are also
        examples of this type of file

        You know what they do, right?

        Add a note to your ``unix_notes.txt`` about *hidden files*

.. slide:: Tracking Changes
    :level: 3

    Now that your notes file has changed, you'll want to preserve that change

    .. rst-class:: build
    .. container::
    
        .. container::
        
            Start by viewing the ``status`` of your repository:

            .. code-block:: bash
            
                $ git status
                On branch master
                Changes not staged for commit:
                  (use "git add <file>..." to update what will be committed)
                  (use "git checkout -- <file>..." to discard changes in working directory)

                    modified:   unix_notes.txt

                no changes added to commit (use "git add" and/or "git commit -a")

        Notice that you have *two* choices, to ``add`` the file or to *discard* the
        changes

        Also notice that git offers you a choice to use ``git commit -a``

        **Do Not Do That**

.. slide:: Stage Your Changes
    :level: 3

    You have a file that has been changed, you must ``add`` the file to the
    stage so it can be committed

    .. rst-class:: build
    .. container::
    
        .. code-block:: bash
        
            $ git add unix_notes.txt
            $ git status
            On branch master
            Changes to be committed:
              (use "git reset HEAD <file>..." to unstage)

                modified:   unix_notes.txt

        Notice that this time, the file is marked as *modified* instead of *new*

        .. container::
        
            You can now commit it:

            .. code-block:: bash
            
                $ git commit -m "added note about hidden files"
                [master 4eca5ad] added note about hidden files
                 1 file changed, 1 insertion(+)

.. slide:: Simple Workflow
    :level: 3

    And that's the basics of git workflow

    .. rst-class:: build
    .. container::
    
        You create a repository **once**

        Then you ``add`` a file or files to it and you ``commit`` those changes

        Then you modify the files, ``add`` them to the stage and ``commit`` the
        changes

        Lather, rinse and repeat

.. slide:: Building History
    :level: 3
        
    Check your ``log`` to see the history of your changes unfold:

    .. code-block:: bash
    
        $ git log
        commit 4eca5ad05bb6e3bc92595a9703a3c5c8da410820
        Author: cewing <cris@crisewing.com>
        Date:   Sat Nov 15 04:11:17 2014 -0800

            added note about hidden files

        commit 0bc447c0cfd0b7856cd19c705e8eefa0c64283de
        Author: cewing <cris@crisewing.com>
        Date:   Sat Nov 15 03:33:09 2014 -0800

            adding unix notes, first draft

.. slide:: Stepping Back
    :level: 1

    In which we learn a bit about what's going on here

.. slide:: What is git?
    :level: 3

    .. rst-class:: build
    .. container::

        A "version control system"

        A history of everything you do to your files

        A graph of "states" in which your files has existed

        That last one is a bit tricky, so let's talk it over for a minute

.. slide:: A Picture of git
    :level: 3

    .. figure:: /_static/git_simple_timeline.png
        :width: 70%
        :class: centered

    .. rst-class:: build
    .. container::

        A git repository is a set of points in time, with history showing where
        you've been.

        Each point has a *name* (here *A*, *B*, *C*) that uniquely identifies it,
        called a *hash*

        The path from one point to the previous is represented by the *difference*
        between the two points.

.. slide:: A Picture of git
    :level: 3

    .. figure:: /_static/git_head.png
        :width: 65%
        :class: centered

    .. rst-class:: build
    .. container::

        Each point in time can also have a label that points to it.

        One of these is *HEAD*, which always points to the place in the timeline
        that you are currently looking at.

.. slide:: A Picture of git
    :level: 3

    .. figure:: /_static/git_master_branch.png
        :width: 65%
        :class: centered

    .. rst-class:: build
    .. container::

        You may also be familiar with the label "master".

        This is the name that git automatically gives to the first *branch* in a
        repository.

        A *branch* is actually just a label that points to a specific point in
        time.

.. slide:: A Picture of git
    :level: 3

    .. figure:: /_static/git_new_commit.png
        :width: 65%
        :class: centered

    .. rst-class:: build
    .. container::

        When you make a *commit* in git, you add a new point to the timeline.

        The HEAD label moves to this new point.

        So does the label for the *branch* you are on.

.. slide:: Making a Branch
    :level: 3

    .. figure:: /_static/git_new_branch.png
        :width: 65%
        :class: centered

    .. rst-class:: build
    .. container::

        You can make a new *branch* with the ``branch`` command.

        This adds a new label to the current commit.

        Notice that it *does not* check out that branch.

.. slide:: Try It Out
    :level: 3

    Go ahead and try this out yourself

    .. rst-class:: build
    .. container::
    
        Use the ``branch`` command to create a new *branch* for your repo called
        *git-notes*:

        .. code-block:: bash
        
            $ git branch git-notes

        You can see the new branch by using the ``branch`` command without a name:

        .. code-block:: bash
        
            $ git branch
              git-notes
            * master
        
        Notice that git tells you which branch you are on with an asterisk (``*`` )

.. slide:: Switching Branches
    :level: 3

    .. figure:: /_static/git_checkout_branch.png
        :width: 65%
        :class: centered

    .. rst-class:: build
    .. container::

        You can use the ``checkout`` command to switch to the new branch.

        This associates the HEAD label with the *session01* label.

.. slide:: Try It Out
    :level: 3

    Go ahead and try checking out your own new branch with ``checkout``

    .. rst-class:: build
    .. container::
    
        As you do so, visualize the changes that are happening

        .. code-block:: bash
        
            $ git checkout git-notes

        .. container::
        
            Use ``git branch`` to see which branch is *active*:

            .. code-block:: bash
            
                $ git branch
                * git-notes
                  master

.. slide:: Making a change
    :level: 3

    Now that you have the ``git-notes`` branch checked out, make some changes

    .. rst-class:: build
    .. container::
    
        First, add a new file to your repository called ``git_notes.txt``

        .. container::
        
            To do so, use the unix ``touch`` command:

            .. code-block:: bash
            
                $ touch git_notes.txt

        .. container::
        
            Then, open the new file in your editor:

            .. code-block:: bash
            
                $ subl git_notes.txt

        Take the next ten minutes to write down your notes on what you've
        learned about git so far

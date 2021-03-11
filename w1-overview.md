# Week 1

## EdX - Introduction to Linux

The [Introduction to Linux](https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-1)
video course is a great overview of some pretty important topics when using
Linux, and offers a wealth of context to things we will use and discuss in
this course. I recommend going through the entire series if you have the time,
but have also compiled a list of what I believe to be the most important parts
as they pertain to this course. Please cover at least these listed portions so
that you can be prepared for the rest of the course.

- Most important topics:
  - Chapter 2:
    - 'Linux Philosophy' + video
    - 'Linux Terminology' + video
    - 'Linux Distributions' + video
  - Chapter 3
  - Chapter 7
  - Chapter 8
  - Chapters 9-18:
    - Any topics that are unfamiliar (esp. in a Linux environment)

## Linux CLI Basics

Essentially all of our interaction with Linux systems in this course will be through
some form of command line interface (CLI) whether that is directly or via Ansible
on another machine. Because of this, familiarity with and comfort using basic commands
and CLI utilities is essential to your success. There are a varietly of resources
related to learning these commands (some will be listed below) but we're going
to establish a baseline with some of the most frequently used:

- `~` - shortcut to reference the path of your user's home directory
- `pwd` - command to get the path of the current directory
- `ls` - command to list contents of the current directory (or a named directory)
- `cd` - command to change the current directory to a named directory via relative
  or absolute path
- `.` - shortcut to reference the current directory
- `..` - shortcut to reference the parent of the current directory
- `cat` - command to output the contents of a file
- `cp` - command to copy a file or directory from one named location to another
- `mv` - command to move a file or directory from one named location to another
- `grep` - command to search/filter text based on regular expressions
- `man` - command to get the installed documentation for a command

For a more complete overview related to a variety of topics, [this page](https://gto76.github.io/linux-cheatsheet/)
offers a wealth of information. For more in-depth information on a specific command,
use the `man` pages or other documentation provided by the author/origin.

## Git

Version control offers an easy way to track changes to a given set of files or
documents over time, from one or multiple authors, on one or multiple streams of
development. It can exist in a variety of formats, but `git`, a form of distributed
version control, has become the most popular for a variety of reasons. In modern
technological workplaces, version control is one of the most integral pieces of
the software and system development landscape. Understanding how to interface with
these tools makes collaboration with other teams and individuals much more manageable,
especially in remote environments.

For this course:

1. Install [Git](https://git-scm.com/)
2. Configure your local `git` instance with identity and personal preferences
3. Create an account on GitHub, if you do not already have one
4. Clone this repository to have a current copy of your course materials
5. Create a repository for yourself to store your lab exercises
   - The exercises will be cumulative, and will treat your deployed lab resources
     as long-lived elements of a developing system. Using Ansible and git for this
     will allow you to add each exercise to your existing files and tag the point
     in their history that represents each assignment.

### Git - Recommended Reading

1. The official [Getting Started](https://www.git-scm.com/book/en/v2/Getting-Started-About-Version-Control#ch01-getting-started)
2. This much more concise [Git Guide](https://rogerdudler.github.io/git-guide/)

## Lab Setup - Part 1

In order to practice Linux skills, you'll need a Linux environment. To get started,
you will need any Linux machine (a local VM or WSL is likely easiest) on which to
install Ansible. We will discuss Ansible in more depth as the course continues.
In just a moment, we'll be using it to configure a more suitable test environment
for continued use, but for now anything to which you have access will do. The following
steps should be followed on this machine:

1. Install pre-requisites
   1. `git`
   2. `ansible`
2. Install the `azure-cli` [package](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux)
   1. You'll need to login with the CLI before using it
3. Fork the [exercises repository](https://github.com/draevin/csc395-linux-lab-exercises)
   on Github and clone your fork to your local Linux machine with `git`
4. Install the [Ansible Azure Collection](https://galaxy.ansible.com/azure/azcollection)
   1. Install the Azure dependencies as listed in the `README`
5. Configure an admin username and password for the VMs to be provisioned
   1. Add a file to the `azure-lab-provisioning\inventory\host_vars\az-workstation\`
      directory named `vault.yml`
   2. Begin the file with `---` and follow this with two variable declarations:
      1. `vault_admin_un: {vm admin username here}`
      2. `vault_admin_pw: {vm admin password here}`
   3. Encrypt this file with `ansible-vault` using a password you will remember
6. Use `ansible-playbook` to run `lab-provisioning.yml` which should create your
   Azure lab VMs
   1. You will need to specify the `inventory` directory and vault password here

Your lab should now be live in Azure with four Ubuntu VMs on which to complete the
rest of the exercises! Feel free to manually stop these or setup Auto Shutdown to
reduce cost/credit-drain when they are not in use. The rest of our Ansible exercises
will be completed from the controller VM (publicly accessible) and will configure
the host VMs (only accessible via the controller through the Azure VNet) to handle
a variety of tasks. Editing your Ansible playbooks for these exercises can be done
in any of a variety of ways, and I recommend VS Code for this job due to its ease
of use, availability, and support for YAML/Ansible documents. Consider the following
when deciding how to manage your files:

1. `git` offers you a dependable way to record changes and store your files and history
   in a remote location for later use, and...
2. Pushing to a `git` repo from your local workstation and pulling them on the
   VM means no manual copying between machines, or...
3. VS Code will allow you to edit files over SSH, if you prefer to cut out the
   intermediate `git` steps, or...
4. You can use a terminal text editor such as `vim`, `nano`, or (my favorite) `micro`
   to edit the files directly on the VM

### Lab Setup Pt. 1 - Recommended Reading

1. Apt-Get - [Complete Beginners Guide](https://itsfoss.com/apt-get-linux-guide/)
2. Azure CLI [Docs](https://docs.microsoft.com/en-us/cli/azure/)

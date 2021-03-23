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
and CLI utilities is essential to your success. There are a variety of resources
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
- `man` - command to get the installed documentation for a named command

For a more complete overview related to a variety of topics, [this page](https://gto76.github.io/linux-cheatsheet/)
offers a wealth of information. For more in-depth information on a specific command,
use the `man` pages or other documentation provided by the author/origin.

## Tools

### VS Code

[Visual Studio Code](https://code.visualstudio.com/) is a primarily open source
text editor by Microsoft that offers extensibility and configuration for the type
of work in this course. I recommend it for managing your playbooks and interacting
with Git and the CLI in these contexts.

### VS Code - Extensions

Extensions can be installed from the Extensions menu in the sidebar menu
(shortcut `Ctrl+Shift+X`) by searching for the desired extension. The full name
in parentheses is unique to the intended extension for ease of searching.

- GitLens (`eamodio.gitlens`) - Additional git support directly in your editor
- Markdown All-in-One (`yzhang.markdown-all-in-one`) - Better Markdown support for
  class materials/docs
- YAML Language (`redhat.vscode-yaml`) - Language server for YAML (for Ansible playbooks)

### Git

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
   1. `git config --global user.name 'Your Name'`
   2. `git config --global user.email 'YourGithubEmail@example.com'`
3. Create an account on [GitHub](https://github.com), if you have not already
4. Clone this repository to have a current copy of your course materials
   1. Whenever you use your local copy, be sure to `pull` the latest changes to
      avoid working from old materials

#### Git - Recommended Reading

1. The official [Getting Started](https://www.git-scm.com/book/en/v2/Getting-Started-About-Version-Control#ch01-getting-started)
2. This much more concise [Git Guide](https://rogerdudler.github.io/git-guide/)

## Lab Setup - Part 1

### Local Instance Setup

For users on an updated version of Windows 10, Windows Subsystem for Linux (WSL)
is typically the easiest method to set up a local Linux environment.

1. Follow the provided [Manual Installation Steps](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps)
   through Step 5
   1. You will need to follow all instructions, including reboots, to successfully
      configure WSL
2. Instead of using the Windows Store, use the direct installation packages [here](https://aka.ms/wslubuntu2004)
   to download Ubuntu 20.04
3. Launch the installed package to complete the installation
   1. When prompted, set a username and password for your Ubuntu user
   2. You may need to enable BIOS settings if you encounter errors `0x80070003` or
      `0x80070003` upon installation:
      > Please make sure that virtualization is enabled inside of your computer's
      > BIOS. The instructions on how to do this will vary from computer to computer,
      > and will most likely be under CPU related options.

### Azure Lab Provisioning

1. From PowerShell, launch your Ubuntu CLI using the `wsl` command
2. Use `apt-get install` to install pre-requisites (Hint: always `apt-get update`!)
   1. `git`
   2. `ansible`
   3. `python3-pip`
3. Install the `azure-cli` [package](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux)
   1. You'll need to login with the CLI before using it (`az login`)
4. Fork the [exercises repository](https://github.com/draevin/csc395-linux-lab-exercises)
   on Github
   1. If you're working in a team, you will only need one fork, but be sure to
      add your team members as collaborators
5. `git clone` your fork to a directory on your local machine
6. Install the [Ansible Azure Collection](https://galaxy.ansible.com/azure/azcollection)
   using `ansible-galaxy` as described in the docs
   1. Install the Azure dependencies using `pip` as listed in the `README` or `pip3`
      if `pip` is not available
7. In VS Code, configure an admin username and password for the VMs to be provisioned
   1. In the exercises repository, add a file to the `inventory/host_vars/az-workstation/`
      directory named `vault.yml`
   2. Begin the file with `---` and follow this with two variable declarations:
      1. `vault_admin_un: {vm admin username here}`
      2. `vault_admin_pw: {vm admin password here}`
   3. Encrypt this file with `ansible-vault` using a password you will remember
      1. `ansible-vault encrypt inventory/host_vars/az-workstation/vault.yml`
      2. Ensure that you and your team remember this password
8. In WSL, use `ansible-playbook` to run `provisioning.yml` which should create your
   Azure lab VMs
   1. You will need to specify the `inventory` and vault password here using the
      `-i inventory/inventory.yml` param and `--ask-vault-pass` switch

Your lab should now be live in Azure with four Ubuntu VMs on which to complete the
rest of the exercises! Feel free to manually stop these or setup Auto Shutdown to
reduce cost/credit-drain when they are not in use. The rest of our Ansible exercises
will be completed from the controller VM (publicly accessible) and will configure
the host VMs (only accessible via the controller through the Azure VNet) to handle
a variety of tasks. To verify access to your lab VMs:

1. Use `ssh` and specify your admin username and controller IP (`ssh username@W.X.Y.Z`)
   1. Hint: you can use `ansible-vault view` to display your credentials without
      fully decrypting the file
2. Enter your admin username when prompted
3. Your CLI prompt should change to indicate the username and hostname of your controller

Editing your Ansible playbooks for these exercises can be done
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

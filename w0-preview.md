# Week 0

## Weekly Overview Structure

This course is comprised of eight, weeklong modules that each focus around one primary
topic. Most of these topics are examples of general system administration skills.
An overview for each module is provided in this repository that contains the information
needed to complete the learning and exercises for that week.

### Topic Blocks

There are blocks in each overview that give some insight into the context and relevance
of the topics being discussed in that module. These are not comprehensive, and don't
provide a lot of technical detail, but simply serve to briefly introduce the topics.

### Recommended Reading

Topic blocks will often included a sub-section titled "Recommended Reading" with
links to articles, tutorials, documentation, or videos that might help you in understanding
the topic at hand or completing the exercise(s) for that week. These are not mandatory
and there are no notes due or quizzes on this material, but they can be incredibly
valuable when completing (or troubleshooting) your other work, in that week and beyond.

## Lab Exercises

The lab exercises are intended to simulate tasks that might actually be required
of you in a workplace environment. These typically include virtual machine management
and the installation and configuration of various packages and applications. These
exercises should all be completed using Ansible and checked in to your fork of the
[exercises repository](https://github.com/draevin/csc395-linux-lab-exercises) for
safekeeping. With a public fork, you can just send me the link so that I can view
the repository on Github as well. From there, the easiest way to turn in your assignments
is to simply use a `git` [tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
to indicate which week's exercise you have completed and then continue working.

If at **any** time you have trouble with one of the exercises, especially one that
relates to the tooling involved (Azure, Ansible, Git, etc.) that is preventing you
from completing the exercises, please reach out to me through any of the provided
channels (Moodle, email, etc.) for assistance. It also may be useful to record any
issues encountered as Issues on Github, so that we can practice some of our source
control and collaborative skills, as well as making information available to other
students in case they come across the same troubles.

### Lab Exercise Troubleshooting Guide

If you run into trouble on your labs, this is probably the list I would help you
work through initially to solve our way out of it:

- Are you in the right command line on the right machine?
  - If you're provisioning, are you on your local?
    - If your local is Windows, are you in WSL?
  - If you're configuring, are you on your controller?
  - If you're checking some files/configs/etc. are you on the right host?
- Do you have the latest version of your sources?
  - If you're working (with yourself or others) across multiple machines, git repositories
    can quickly get out of sync without a regular pull from the server
  - Realign yourself with a `pull`, `rebase`, or `reset` to the correct point
    - Ask a teammate or instructor for help if you're concerned about losing work
      due to git confusion! It happens to everyone, somewhere along the way
- Are you missing resources?
  - If you've used a third-party role or collection in your playbook, be sure that
    it's present and accessible on your current machine
- Is it a syntax error?
  - If your YAML file has syntax errors, that's an immediate blocker. These errors
    typically identify themselves pretty readily, either in your editor or when you
    attempt to run the playbook
  - Follow any remediation steps that those provide
- Is it a runtime error?
  - The root of errors during a step in your playbook may not be quite as obvious,
    but using `ansible-playbook -vvv` for verbose output can give us a much better
    idea of what's going wrong

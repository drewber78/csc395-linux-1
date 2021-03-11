# Week 2

## Principles of System Administration

The move towards DevOps culture in the world of technology has changed the role
of a classical SysAdmin, but the need for specialists the area of systems and network
management has not gone away, and likely won't in the near future. The principles,
values, and practices of DevOps can be applied readily to this sort of administration.
Even outside of a software development, these same elements can be applied in context
to improve quality of service and quality of life for all members of an organization.

### Concepts to Establish

- Inter-team communication
- Configuration/Infrastructure as Code
  - Versioning
  - Automation
  - Idempotence
- Security as a Default
  - Default deny
  - Least permissions
- Quality assurance
  - Iterative changes
  - Incremental testing
- Resilience
  - Reducing single points of failure (technical and biological)
  - Automating rollback and recovery scenarios
- Immutability
  - "Pets vs. Cattle" (or maybe a nicer metaphor)
  - Ties into "X as Code" tooling and processes

### Primary Activities

- Understanding
  - "What's in prod?"
  - Documenting
    - Dependencies
    - System components
    - Technical and human processes
- Installing & Configuring
  - Adding components
    - Adjusting existing rules/practices/etc. for additions
    - Ensuring new components meet existing standards
  - Automating
    - Reduce manual work
    - Reduce points of failure
  - Standardizing
    - Comes with "Documenting" and "Automating"
- Maintaining & Adapting
  - Monitoring
    - System health
    - Security posture
  - Troubleshooting
    - Comes with "Understanding"

## Ansible Automation Intro

[Ansible](https://docs.ansible.com/) is an Infrastructure/Configuration as Code
platform that uses declarative documents to apply configurations to a set of machines
(known as your inventory) in an idempotent fashion. It allows a great deal of flexibility
with regards to the types of platforms, hosts, networking, and software in the
target system, while reinforcing principles in line with modern best practices.
We will be using Ansible to orchestrate all of the changes in our exercises, and
your deliverables will primarily be the Ansible files (known as playbooks) that
you use to configure your hosts. The Azure lab setup we used last week is an example
of such a playbook, in which our inventory was simply our local Linux workstation
and our changes were orchestrated through the Azure `az` CLI tool. In a typical
playbook, the inventory would consist of your remote machines to be configured
and the changes will be orchestrated through any number of tools over the network.

### Recommended Reading

#### Ansible

1. DigitalOcean - [Ansible Cheatsheet](https://www.digitalocean.com/community/cheatsheets/how-to-use-ansible-cheat-sheet-guide)
2. Ansible Docs on...
   - [YAML](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)
   - [inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)
   - [variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)
   - [playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html#)
   - [Azure.AzCollection](https://docs.ansible.com/ansible/latest/collections/azure/azcollection/index.html)

#### Lab Exercise (SSH hardening)

1. Mozilla InfoSec - [OpenSSH Guidelines](https://infosec.mozilla.org/guidelines/openssh.html)

## Lab Exercise

For this lab exercise, use Ansible to configure the `sshd` on your lab hosts to increase
the security of your system. You will be creating a playbook to run against your
hosts to handle this, as opposed to manual or ad-hoc configuration. When you complete
your development, be sure it includes all necessary details and variables to recreate
your configuration identically on another system. This playbook will go on to include
the exercises from further weeks in order to form a comprehensive collection of your
lab configurations.

Some typical hardening processes might include:

- Disable:
  - root login
  - empty passwords
  - password logins (entirely)
    - **Be sure you have created and added your keys to the host or risk lockout!**
  - login banner
  - X11 forwarding (only used for graphical applications)

Since this is our first time completing an exercise like this, some general advice
regarding configuring system applications and services in this way:

- Look online and in the [Ansible documentation](https://docs.ansible.com/) for
  modules, roles, and collections that deal with the material in which you're interested
  - The Ansible Galaxy site holds a wealth of community-driven resources, and can
    be leveraged through the CLI natively
- Back up your configurations before modifying them
  - Can be done manually or automatically
  - Hint: See the `backup` property on the `builtin` modules
- Test your configurations at runtime
  - Many applications/services offer a command or flag to do this (e.g. `sshd -t`)
  - Hint: See the `validate` property on the `builtin` modules
- Ansible can tell when your configuration files change and allow you to restart
  your services appropriately
  - Hint: This will require a `handler`
- Build your solutions one piece at a time and iteratively expand/improve
  - Commit to your repository in these small chunks to track development
  - Small changes beget small bugs

Please feel free to ask further questions as needed, and I'll do my best to assist!

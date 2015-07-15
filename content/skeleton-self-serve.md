Title: Skeleton
Date: 2015-07-15 12:13
Modified: 2015-07-15 12:13
Category: Brain-Dump
Authors: Aaron Pederson, Nikki Martinez
Summary: How to use skeleton/self-serve

#Skeleton/Self-Serve

Description
-----------

A squence of shell scripts that create the file structure and commonalities of our ansible playbooks.

How to use
-----------
`ruby playbook_skeleton {project_name} {required_system} {required_system} ...`

What it does
------------
- Creates the main directory title 'playbook-{project_name}'
  - Populates main directory with 'playbook.yml', 'dependencies.yml' and 'vault.yml'
- Creates a sub directory titled 'hosts'
  - Populates directory with four files 'next, development, staging, production'
- Creates the sub directories titled {required_system}
  - Populates each {required system} directory with 'playbook.yml' and 'dependencies.yml'

All files are created blank, but will be updated (in the next iteration) to suite current ansible requirements for baser functionality.




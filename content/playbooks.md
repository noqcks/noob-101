Title: Playbooks
Date: 2015-07-15 12:20
Modified: 2015-07-15 12:20
Category: Brain-Dump
Authors: JScott, Aaron Pederson, Nikki Martinez
Summary: How to use playbooks

#Playbooks

Think of playbooks like config files that create config files. They provision infrastructure in the simplest across-the-board way.

Description
-----------

A playbook repo contains vault, dependencies, and infrastructure files.

- **vault file**: Contains AES encyrpted variables for us to use.
- **dependencies file**: Contains roles that are required for the playbook you want to run.
- **infrastucture file**: Takes care of provisioning infrastructure on AWS. `playbook-skeleton` can create a default for you.

Creating the playbook from scratch
----------------------------------

- Create a new repository
- Populate it with the [playbook-skeleton scripts](https://github.com/aaronpederson/playbook-skeleton)
- Make sure any vault files have your master vault password in the forge bucket

Using Playbooks
----------------

### Testing changes to roles

Telus digital is our master copy. We must not mess with this perfect state.
Git-ready should have forked playbook-uet to your repo.
Clone this fork locally. Make sure you are cloning from your repo so as not to subvert the whole process.
Test out your changes on next server. This is our sandbox to play in.
Edit `/tmp/playbook-*.yaml` on the server to use your test role instead of telusdigital's
Use `ansible-playbook` to rerun the playbook manually
Once you have edited accordingly, pull request to merge to telusdigital.
DO NOT MERGE YOUR OWN CODE!!!!

### Syncing playbooks to forge

- `pip install s3cmd`
- `s3cmd --configure`
- `s3cmd sync playbook-foo/ s3://telusdigital-forge/foo/`

### Rerun forge without reprovisioning

- SSH into the server
- Run `sudo reforge`

### Checking that everything ran properly

- `cat /var/log/cloud-init-output.log`

Troubleshooting
---------------

Q: `fatal: [localhost] => One or more undefined variables: 'domain' is undefined`

A: Add `domain: teluswebteam.com` to your infra playbook until we get it sorted out how this can be done better globally.
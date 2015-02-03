# pypdfocr Role

[![Build
Status](https://travis-ci.org/dbryant4/ansible-role-pypdfocr.svg)](https://travis-ci.org/dbryant4/ansible-role-pypdfocr)

## Description

This role manages the installation of [pypdfocr](https://pypi.python.org/pypi/pypdfocr)
on a Raspberry Pi, although it should be able to manage any other Debian based
system. Since this role must compile from source, it might take a while
to complete the first run. Please be patient.

## Provides

1. pypdfocr installed using pip
2. tesseract 3.03 compiled from source
3. tesseract english language data

## Requires

1. Ansible 1.6 or higher
2. Raspberry Pi (possibly other Debian based systems)
3. Internet connectivity to download tesseract source

## Variables

The variables below correlate directly with pypdfocr's configuration
file. See the [pypdfocr docs](https://pypi.python.org/pypi/pypdfocr)
for more information.

- pypdfocr_target_folder - path to the directory where to place OCR'd
  PDFs
- pypdfocr_default_folder - path to place PDF's which were not
  automatically filed
- pypdfocr_original_move_folder - path to story original PDFs
- pypdfocr_folders - dictionary/hash of directories and key words used
  for automatic filing
- pypdfocr_mail_smtp_server - SMTP server to use for sending emails
- pypdfocr_smtp_login - login for the SMTP server
- pypdfocr_smtp_password - password for the SMTP server
- pypdfocr_mail_from_addr - from address
- pypdfocr_mail_to_list - array of email addresses which will receive
  emails when a PDF has been OCR'd and filed

### Changing Variable Values

To Change the value of variables, create a file in `host_vars/` or `group_vars/` or define variables in the playbook.

There are other options for changing variable values. See [Ansible
Variable
Documentation](http://docs.ansible.com/playbooks_variables.html) for
more ideas.

## Usage

Include this role in your plays and set variables as desired.

```yaml
---
  hosts: pypdfocr-servers
  roles:
    - pypdfocr
```

## Tests
This role includes Travis CI tests and a Vagrantfile. To run tests
locally, run `vagrant up`

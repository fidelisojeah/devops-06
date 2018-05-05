## Configuration and change management 
Configuration management is the process of standardising resource configuration and enforcing their state across IT infrastructure in an automated yet agile manner. Configuration management solutions model infrastructure, continually monitor and enforce desired configurations and automatically remediate any unexpected changes or configuration drift.[puppet labs]

Examples of configuration management tools include ansible, puppet and chef 

### Ansible
Ansible is a simple but powerful open source tool for IT automation. It can be used for :

- Automation
- orchestration
- provision
- configuration management
- change management

The main parts of ansible are:

- inventory: 
- Modules
- Config
- Playbook

##### The use case
For this use case I use ansible for configuration management. I chose to use ansible for this demonstration use case due its simplicity. I find ansible an easy to use yet powerful tool. It is also well documented through the `ansible-doc` utility.
In most cases ansible is used to push changes and configure newly deployed instances. 
In my case I use ansible to manage configuration of packer instances during Image building.

#### Packer
Building machine images is a time consuming activity when done manually. Packer by Hashcorp automates the process of building machine images and supports the use of configuration tools like ansible to install and configure software within the packer-images.
packer has a large number of builders to support most of the available platforms, and it supports parallel builds. 

### The Demo
For the demo I build an image of a python flask api, I use ansible to configure the image.

There are two packer templates in the repo:

- packer.json : This packer templates uses scripts to configure the image. (not recommended)
- packer_ansible.json: This template uses anisble to configure the image. Reducing on the complexy of the process.(recommended)

The ansible folder contains the ansible playbooks:

**main-old.yml** Playbook does not make use of ansible roles.

**main.yml** Playbook makes use of ansible roles making the playbooks as granular as possible.

#### To build an image

```packer build <packer template>```

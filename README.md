# Playbooks to demonstrate Configuration as Code to an Automation Controller Instance
These playbooks make use of the roles in the collection [`redhat_cop.controller_configuration`](https://galaxy.ansible.com/redhat_cop/controller_configuration)

## Basic
1. `cac-01.yml` demonstrates connection to an AC instance and creation of a single user 
1. `cac-02.yml` extends creation to more than one user, creates a project and conditionally applies the roles.
1. `cac-03.yml` moves the whole controller structure to host_vars on localhost, adds many more objects

## Advanced
4. `cac-04.yml` creates a workflow template on the controller to allow self-configuration
4. `cac-05.yml` creates a webhook into Github so that any pushes to the main branch will trigger the configuration job template in the Automation Controller

## Usage

1. Install the awx.awx and the redhat_cop.controller_configuration collections
```sh
$ ansible galaxy collection install -r requirements.yml
```
2. Write the instance URL, username and password to connect into the extravars.yml file
```yaml
extra_aap_instance_url: https://myautomationcontroller.example.com
extra_aap_instance_username: admin
extra_aap_instance_password: verysecurepassword
```
3. Run the playbook(s)
```sh
$ ansible-playbook -e @extravars.yml cac-0x.yml
```



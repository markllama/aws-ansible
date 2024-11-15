# aws-ansible
A set of Ansible playbook examples for managing a network and instances on AWS

## Using Ansible To Manage AWS Resources

Ansible is a tool commonly used to configure the operating system and
and applications on computing hosts. It is also possible to use it to
configure Amazon AWS networks and resources to create running
instances that can then be configured in turn by Ansible.  While this
is not the best option for very large AWS configurations it can be
quite useful for prototyping or for small deployments that won't need
a lot of active updates.

There are two<sup>1</sup> sources of Ansible modules for AWS:

* [ansible.aws](https://galaxy.ansible.com/ui/repo/published/community/aws/) - Primary objects
* [community.aws](https://galaxy.ansible.com/ui/repo/published/amazon/aws/) - A few additional operations 

    ansible-galaxy collection install amazon.aws
    ansible-galaxy collection install community.aws

The ansible modules for AWS also require two additional Python
modules for general communication with the Amazon AWS API

* [boto3](https://github.com/boto/boto3) - AWS API bindings in Python 3
* [botocore](https://github.com/boto/botocore) - low level core functionality of boto3 and AWS CLI


# Footnotes

[1] There are a couple of other community modules for specialized operations

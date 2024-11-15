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

## Connection and Authentication

Ansible for AWS depends on the *aws cli* for authentication and, if you don't specify in the
Ansible parameters, the account and region for your objects.

The easiest way to control the account, auth and region is to log in with `aws sso login` and let
your AWS account auth method do it's job. Setting up AWS SSO
authentication and *AWS CLI* are out of scope and a little web
searching should find you what you need. 


The AWS SSO login process does like to use your browser to help you
enter an out-of-band code to confirm.  If you're running from a
machine without a browser handy, you can tell that to the auth command
and cut-n-paste the URL and code to your local browser to confirm.

    aws sso login --no-browser
	Browser will not be automatically opened.
	Please visit the following URL:

	https://device.sso.us-east-2.amazonaws.com/

	Then enter the code:

	XXXX-XXXX

	Alternatively, you may visit the following URL which will autofill the code upon loading:
	https://device.sso.us-east-2.amazonaws.com/?user_code=XXXX-XXXX

The authentication will use your default profile (or one you select
with a parameter) Then Boto and Ansible will use the cached
credentials until the session expires and you have to do it again.

## 

# Footnotes

[1] There are a couple of other community modules for specialized operations

    Title: PGD Cookbook
    Date: 2014-08-01T09:28:13
    Tags: osl, work, chef, code

When I mention, yum cookbook, recipes, and how to use knife, what comes to mind?
When first using [Chef](http://getchef.com) you begin to wonder what they were
thinking naming their product such a common thing.
Chef is a [configuration management](https://en.wikipedia.org/wiki/Software_configuration_management)(CI)
tool.  CI is a methodology for programmatically managing software and hardware.
There are many popular open source options including [Puppet](https://puppetlabs.com/),
[Ansible](http://www.ansible.com/home), [SaltStack](http://www.saltstack.com/),
 and [NixOS](http://nixos.org/) to name a few.  They differ in their language of
implementation, design goals, and range of popularity.

<!-- more -->

As an overview lets say you have a database server and web app. You are looking
to deploy a development instance of your web app but create it in such a way
that anyone can spin up a new instance and test against your various git
branches of the code base.  One way to do this is with [Vagrant](http://vagrantup.com).
You could then write a bash script to provision the machine and just run the 
commands verbatim from the script.  This is nice if you know exactly what you
want to do and an expert in bash. 

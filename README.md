# my-minions

A collection of ansible playbooks used to launch multiple EC2 instances, run the same benchmark across different CPU architectures, then collect results back locally. It's primarily designed to work with [ckb-vm-sysbench](https://github.com/xxuejie/ckb-vm-sysbench) but there might also be other use cases.

# Usage

First, ensure that AWS access credentials are defined via environment variables following instructions [here](https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_instance_module.html).

An example setup could be like following:

```
$ export AWS_ACCESS_KEY="<your access key>"
$ export AWS_SECRET_KEY="<your secret key>"
```

The API keys should have access to alter EC2 instances, security groups and keypairs.

Then use the following command to start the benchmark:

```
$ ansible-playbook run.yaml cleanup.yaml
```

When completed, there should be a local folder named `data` containing benchmark results.

In case of error states, you can use `cleanup` playbook alone to clean up resources created:

```
$ ansible-playbook cleanup.yaml
```

# Credits

A lot of the AWS-related code is borrowed from [ansible-real-life](https://github.com/ginigangadharan/ansible-real-life/tree/main/Ansible-AWS-Provisioning).

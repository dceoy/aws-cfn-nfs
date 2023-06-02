aws-cfn-nfs
===========

AWS CloudFormation stacks of NFS

[![Lint](https://github.com/dceoy/aws-cfn-nfs/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/aws-cfn-nfs/actions/workflows/lint.yml)

Installation
------------

1.  Check out the repository.

    ```sh
    $ git clone --recurse-submodules git@github.com:dceoy/aws-cfn-nfs.git
    $ cd aws-cfn-nfs
    ```

2.  Install [Rain](https://github.com/aws-cloudformation/rain) and set `~/.aws/config` and `~/.aws/credentials`.

3.  Set a Slack client on AWS Chatbot and get the Slack workspace ID. (optional)

4.  Deploy stacks for VPC.

    ```sh
    $ rain deploy \
        --params ProjectName=nfs-dev \
        aws-cfn-vpc-for-slc/vpc-private-subnets-with-gateway-endpoints.cfn.yml \
        nfs-dev-vpc-private-subnets-with-gateway-endpoints
    ```

5.  Deploy stacks for EFS.

    ```sh
    $ rain deploy \
        --params ProjectName=nfs-dev,VpcStackName=nfs-dev-vpc-private-subnets-with-gateway-endpoints \
        efs-with-access-point.cfn.yml nfs-dev-efs-with-access-point
    ```

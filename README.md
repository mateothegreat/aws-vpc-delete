# Delete AWS VPC

This role will delete an existing AWS VPC and it's components including:

* Peering Connection(s)
* Internet Gateway
* NAT Gateway(s)
* Route Table(s)
* Subnet(s)

## Requirements

```bash
pip install ansible boto3 boto
```
## Variables

```yaml
aws_vpc_delete:
  profile: "default"            # The aws credentials file profile name.
  name: "test-1"                # Name of the vpc you want to delete.
  region: "eu-central-1"        # AWS region.
  release_elastic_ip: "yes"     # Release elastic ip address(es) for any NAT gateway(s).
```

## Example Usage

Add the following to a file like `playbook.yaml`:

```yaml
- hosts: localhost
  roles:
    - role: "mateothegreat.aws_vpc_delete"
      vars:
        aws_vpc_delete:
          profile: "default"            # The aws credentials file profile name.
          name: "test-1"                # Name of the vpc you want to delete.
          region: "eu-central-1"        # AWS region.
          release_elastic_ip: "yes"     # Release elastic ip address(es) for any NAT gateway(s).
```

Run with `ansible-playbook -i <your inventory file> playbook.yaml`.

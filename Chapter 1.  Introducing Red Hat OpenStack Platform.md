# Topic 1 - OpenStack Personas
## Describe OpenStack Personas in cloud
Cloud Personas aresynthesized profiles of users, buyers or professionals who interact with cloud technology, designed to represent shared attributes, behaviors, motivations and goals.
They help orgs streamline workflows to different user groups instead of focusing on individual employees

Openstack Personas focuses on the roles (this stuff actually seems very wierdly complex, will come back to this later)
Edit: What I wrote below is literally what Openstack Personas are lmao.

## Personas
| Name and Role | Description | Good Day | Bad Day |
| :--- | :--- | :--- | :--- |
| **Alan**<br>App Developer | I consume the cloud by developing and deploying applications. I might not know much about the underlying infrastructure or the names of OpenStack projects | New application deploy to a cloud SUCCESSFULLY | Cloud environment is unreliable |
| **Pei**<br>Lead Developer/Project Owner (This course) | I manage my projects by adding or removing members. I am also the main interface with Cloud Ops. | Having enough quota to support my project | Running out of quota for my project and having to wait for the ops team to raise it |
| **Doug**<br>Domain Ops (This course) | I manage the relationship with the cloud provider for my company including quotas, users, policies and support tickets. | I can verify that the service provider is following the SLA | Yet another "unscheduled outage" When will it end? |
| **Carlos**<br>Cloud Ops | I make sure the cloud is up and running and, if it breaks, try to get things running again ASAP. | No new tickets from clients | Complexity and lack of skilled IT personnel |
| **Arnie**<br>Infra Architect | I am responsible for the strategy and roadmap for my company's cloud. | Identify reasons to compel the management to adopt openstack for production environment | Frequent instabilities and non-deterministic errors |

*Ref for above table: https://www.youtube.com/watch?v=2yDjvSebJHg*

## Describing the OpenStackClient

You generally have a file like this, that you can use to log in OpenStack

```
[stack@homelab ~]$ cat user-rhythm
export OS_USERNAME=rhythm
export OS_PASSWORD=redhat
export OS_PROJECT_NAME=homelab
export OS_PROJECT_DOMAIN_NAME=Default
export OS_USER_DOMAIN_NAME=Default
export OS_IDENTITY_API_VERSION=3
export OS_AUTH_URL=http://172.25.250.50:5000/v3
```

OpenStack uses these env variables to work in CLI, to make them work. Run this

```
[stack@homelab ~]$ source user-rhythm
```

You can now start running commands, for exampe

```
openstack server list -c Name -c Status
+-----------------+--------+
| Name            | Status |
+-----------------+--------+
| home-server2    | ACTIVE |
+-----------------+--------+
```

*Note "-c" is used when you want to print out specific columns of the table displayed*

OpenStack supports json and yaml as well, which can be used by adding "-f json" or "-f yaml"

```
[stack@homelab ~]$ openstack network list -f json
[
  {
    "ID": "3f7a92c1-5b6e-4d8f-a2b3-91c7e5f4a102",
    "Name": "alpha-net-xt9",
    "Subnets": [
      "a8d4c2e9-113b-4f6a-9c77-5e2d1b8f0c3a"
    ]
  },
  {
    "ID": "b6e1d3f4-9a27-41c8-b5e2-7d9f3a6c8e51",
    "Name": "core-provider-zone7",
    "Subnets": [
      "d2f9a7b1-6c4e-48e3-8f12-3a9b5c7d0e6f"
    ]
  }
]
```

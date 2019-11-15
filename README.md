# AWS Developer Associate

## IAM
- Provides multifactor authentication
- Provides temporary access for users
- **Users**: actual people
- **Groups**: groups of users with the same permissions
- **Roles**: defines a set of permissions - can then be assumed by users/groups/AWS services
- **Policies**: a JSON document that defines one or more permissions, can be attached to a user/group/role
- Setting up a new account - create IAM users for each person, add them to a relevant group, assign permissions on a group by group basis, according to their job function
- **Roles can be assumed by AWS services, policies are attached to groups and users**
- Access Type for a user:
  - programmatic access (CLI/SDK/etc)
  - management console access (UI)
- IAM is universal (not tied to a region)

## EC2
#### On Demand
- **pay a fixed rate by the hour/second with no commitment**
- good for short term applications, spiky or unpredictable workloads that cannot be interrupted as there is no upfront payment or long term commitment
- perfect for applications being tested or developed

#### Reserved
- **provides a capacity reservation, and offer significant discount on the hourly charge for an instance. 1 or 3 year term**
- good for applications with steady state or predictable usage, or that require reserved capacity
- standard RIs can save up to 75% vs on demand
- convertible RIs can save up to 54% vs on demand, and can modify the RIs as long as they are not scaled down
- scheduled RIs are available to launch within time window you reserve. Allows you to match your capacity to a predictable load

#### Spot
- **bid a price for instance capacity**
- good for applications that have flexible start and end times
- applications that are only feasible at very low compute prices
- good if you have an urgent need to large computing power
- example: scientific lab may use mega services at 5am on Sunday (when traffic is low) to use large instances for big simulations
- if the instance is terminated *by* EC2, you will not get partially charged for the usage. If *you* terminate the instace, then you will get charged the full hour

#### Dedicated hosts
- **Physical EC2 server dedicated for your use only**
- useful for regulatory requirements that may not support multi tenant virtualisation
- can be purchased on demand and as a RI 

#### Instance types
- `F` FPGA
- `I` IOPS
- `G` Graphics
- `H` High disk throughput
- `T` Cheap general purpose
- `D` Density
- `R` RAM
- `M` Main choice for general purpose
- `C` Compute
- `P` Graphics (pics)
- `X` Xtreme memory

### EBS (Elastic block storage)
- A virtual disk.
- Once attached to an EC2 instance, you create a filesystem ontop of it and have DBs, install applications, store files etc.
- Are placed in an availability zone, where they are automatically replicated from the failure of a single component.
- Types
  - **General purpose SSD (GP2)**, 3 IOPS per GB
  - **Provisioned IOPS SSD (IO1)**, designed for intensive applications such as large relational or NoSQL databases, use if you need more than 10,000 IOPS
  - **Throughput optimised HDD (ST1)**, big data, data warehouses, log processing, cannot be a boot volume (i.e. has to be an additional volume)
  - **Cold HDD (SC1)**, lowest cost for infrequently accessed workloads, such as a file server. Not bootable
  - **Magnetic (Standard)**, (legacy) lowest cost per GB of all bootable volumes

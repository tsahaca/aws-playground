# Compare high availability vs. fault tolerance in AWS

To achieve high availability and fault tolerance in AWS, IT admins must first understand the differences between the two models.


High availability and fault tolerance are closely related concepts. It's easy to conflate the two but highly available workloads are not the same as fault-tolerant ones.

AWS administrators can implement best practices and tools that minimize disruption. They must assess whether the financial and operational investments associated with high availability and fault tolerance are worth the benefits of sustained performance. In a perfect world, all AWS workloads would be both highly available and fault tolerant, by default -- but they rarely are.

## What is high availability?

High availability is the ability of a workload to remain operational, with minimal downtime, in the event of a disruption. Disruptions include hardware failure, networking problems or security events, such as DDoS attacks.

In a highly available system, workloads are spread across a cluster of servers. If one server fails, the workloads running on it automatically move to other servers.

Kubernetes is an example of a platform on which most workloads are considered highly available. As long as a Kubernetes cluster contains more than one worker node, containerized applications and application services in pods can automatically restart on a different node if the original node fails.

## What is fault tolerance?

Fault tolerance is the ability of a workload to remain operational with zero downtime or data loss in the event of a disruption.

In a fault-tolerant environment, instances of the same workload are typically hosted on two or more independent sets of servers. Admins keep the instances continuously in sync, so data and application state are identical across each instance. If one instance fails, another instance takes over. In this way, fault tolerance prevents user disruption and data loss -- assuming that at least one of the instances remains available.

As an example of fault tolerance, admins could configure an object storage bucket to replicate data automatically to a separate bucket. If the first bucket fails, the second bucket accommodates all requests.

## High availability vs. fault tolerance

Although high availability and fault tolerance both reduce the risk of service disruptions and downtime, they do so in different ways. Additionally, the two models tend to differ in terms of cost.

Level of disruption. With high availability, a workload usually experiences some level of disruption when a failure occurs. It may take seconds or minutes to migrate a workload from a failed server to a new one in a highly available cluster. Because the new server likely does not have identical copies of the failed server's data, there may be some permanent data loss. In contrast, a successful fault-tolerant environment provides zero downtime and no data loss because both instances maintain identical copies of the data.

Infrastructure requirements. Fault-tolerant environments require IT organizations to mirror workloads on dedicated infrastructure. As a result, these environments double an organization's infrastructure footprint, in the cloud or on premises. In either deployment scenario, expect twice the hosting costs of a non-fault tolerant workload. Highly available environments are not as demanding, but they do require some extra infrastructure capacity. This makes highly available environments less expensive to operate than fault-tolerant ones.

Management. Fault-tolerant workloads are more challenging to set up and administer. To ensure fault tolerance, admins must keep two or more workload instances in sync. This mean that changes in one instance are implemented in the other instance instantaneously. In contrast, high-availability workloads are less complex to set up and manage.

The main benefit of both high availability and fault tolerance is protection against hardware failure, not software issues. If a running instance in a highly available cluster fails because of a buggy application on it, the new instance of that workload that replaces it likely will also fail for the same reason. Likewise, in a fault-tolerant environment, an application bug is likely to cause both workload instances to fail.

## High availability in AWS

The way admins implement AWS high availability and fault tolerance depends on the type of workload, as well as which of the provider's cloud services they use to deploy it.

In some cases, AWS enables high availability by default. For example, if you use Elastic Container Service or Elastic Kubernetes Service to deploy containerized applications, the orchestrators in each respective service automatically attempt to restart on healthy nodes to maintain availability.

High availability is not built into all AWS products. Depending on which storage tier you choose, data in an Amazon S3 storage bucket may be stored, by default, in just one availability zone. Data will become unavailable if an S3 storage service disruption affects that availability zone.

## AWS fault tolerance with availability zones, regions

As with high availability, some AWS services offer a degree of fault tolerance, by default. Some S3 storage tiers automatically replicate data across multiple availability zones. If one availability zone is disrupted, data will remain available via the other availability zones, with no delays or loss of information.

If a workload is not fault-tolerant by default, use additional availability zones or additional regions, which encompass multiple availability zones. The use of multiple availability zones enables admins to replicate workloads across physical data centers within the same AWS region. The use of multiple regions spreads workloads across distinct geographical areas, such as different parts of the U.S., multiple European countries and more.

Depending on the workload, it can be difficult to configure deployment across multiple availability zones and regions to enhance fault tolerance. If the workload consists only of data, replicating that data across multiple zones or regions is straightforward. If the workload is an application, however, it requires networking and load balancing so that each availability zone or region can take over requests instantly if another zone or region becomes unavailable.

An alternative approach to fault tolerance in AWS is to maintain independent copies of the same workload running within the same availability zone or region. This approach doesn't protect against the risk of disruption to the whole location. But this approach does keep the workload operational if one instance fails due to a problem with the virtual host infrastructure. For example, Elastic IP addresses can reroute with a workload from one EC2 instance to another instantaneously to achieve EC2 fault tolerance.

AWS also offers Fault Injection Simulator, a service to assess workload resilience. Third-party chaos engineering tools, such as Gremlin or Chaos Monkey, also serve this purpose.

## Best practices to configure high availability and fault tolerance

Regardless of the specific AWS tools and services in use, the following best practices help IT admins achieve high availability and fault tolerance in cloud computing:

Consider the cost. Infrastructure costs will increase over those for an unfortified workload when you design for high availability or fault tolerance. Evaluate if the bill is worth the benefits.
Avoid lock-in. Try not to depend exclusively on high availability or fault-tolerance tools that work only on a specific cloud platform, as this poses vendor lock-in
Plan for software failures. As noted earlier, neither high availability nor fault tolerance protect against software issues. Observe software performance and formulate effective incident response plans to mitigate the risk of failure.
Back up data. High availability and fault tolerance are not substitutes for data backups. Data loss is a risk in either environment, due to issues such as data deletion or the failure of backup servers or application instances. Perform regular backups, even with high availability and fault-tolerance protections in place.

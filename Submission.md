Edit this page to describe your Submission.

## Which Categories Best Fit Your Submission and Why?
### Best New Feature
Being able to dynamically change instanceUrlSuffixes and use Curator service discovery for Turbine is an easy win for many organizations that already run Zookeeper but don't necessarily want to or need to run Eureka.

### Best Contribution to Operational Tools, Availability, and Manageability
* Allows Hystrix Metrics to be easily exported from any Zookeeper-enabled service.
* Opens up new possibilities for Turbine & service discovery

### Best Portability Enhancement
Not sure if this applies, but it certainly allows Turbine to work in more infrastructure environments 'out of the box'.

## Describe your Submission
I added the ability for Turbine to be a little more flexible in terms of Hystrix Event Stream URLs it can connect to. Instance discovery providers can set instance attributes such as server-port and have them replaced into the `instanceUrlSuffix` for situations such as multiple JVMs/machine.

The first instance discovery provider to take advantage of this is the ZookeeperInstanceDiscovery, I wrote this to work in concert with another piece of the puzzle, StormHystrix but will work with anything that uses Curator Service Discovery.

## Provide Links to Github Repo's for your Submission
https://github.com/Netflix/Turbine/pull/19 (instanceUrlSuffix placeholders)
https://github.com/Netflix/Turbine/pull/20 (ZookeeperInstanceDiscovery)

Edit this page to describe your Submission.

## Which Categories Best Fit Your Submission and Why?
### Best New Feature
Being able to dynamically change instanceUrlSuffixes and use Curator service discovery for Turbine is an easy win for many organizations that already run Zookeeper but don't necessarily want to or need to run Eureka. Additionally, StormHystrix is a decent feature for utilizing Hystrix inside Storm clusters.

### Best Contribution to Operational Tools, Availability, and Manageability
* Allows Hystrix Metrics to be easily exported from Storm
* Opens up new possibilities for Turbine & service discovery

### Best Portability Enhancement
Not sure if this applies, but it certainly allows Turbine to work in more infrastructure environments 'out of the box'.

## Describe your Submission
I added the ability for Turbine to be a little more flexible in terms of Hystrix Event Stream URLs it can connect to. Instance discovery providers can set instance attributes such as server-port and have them replaced into the `instanceUrlSuffix` for situations such as multiple JVMs/machine.

The first instance discovery provider to take advantage of this is the ZookeeperInstanceDiscovery, I wrote this to work in concert with another piece of the puzzle, StormHystrix but will work with anything that uses Curator Service Discovery.

For example, using my StormHystrix Storm module, it registers its self with Zookeeper and starts an embedded webserver on 9090, but if another worker on the same machine has an embedded webserver also running on 9090, it moves to 9091. This worker sets its port in ZK. The ZooKeeperInstanceDiscovery finds this entry and sets the server-port attribute accordingly. Turbine then replaces my instanceUrlSuffix `:{server-port}/hystrix.stream` and connects to `http://worker-ip:9091/hystrix.stream`

## Provide Links to Github Repo's for your Submission
https://github.com/Netflix/Turbine/pull/19 (instanceUrlSuffix placeholders)
https://github.com/Netflix/Turbine/pull/20 (ZookeeperInstanceDiscovery)
https://github.com/Xorlev/StormHystrix (not yet posted)

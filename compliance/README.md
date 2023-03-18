## Policy and Compliance in Red Hat cloud stack
### One capability and three perspectives!
Looks like there is still some debate about how to compare security, policy, and compliance in Red Hat different products, we are certainly talking about three products:
- Red Hat OpenShift - OCP
- Red Hat Advanced Cluster Management - RHACM
- Red Hat Advanced Cluster Security - RHACS

**We sometimes get similar feedback from existing OpenShift customers asking about differences, and similarities between OCP, RHACM, and RHACS in addition to best practices on how to use all together to manage security and compliance.**
![](rh-compliance-00.png)
##OpenShift Compliance Operator
Starting with Openshift, It comes with a built-in compliance operator that allows administrators to describe the desired compliance state of a cluster and provides them with an overview of gaps and ways to remediate them.

The assessment requires a continuous scanning for both API resources and nodes, this happens using OpenSCAP, a NIST-certified tool, to scan and enforce security policies provided by the compliance content/configuration.

The compliance content is grouped into compliance profiles. There are numerous predefined industry standard profiles like FISMA, CIS OCP benchmark, PCI-DSS, NERC-CIP, But you can also create your own profiles.

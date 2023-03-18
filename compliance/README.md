## Policy and Compliance in Red Hat cloud stack
### One capability and three perspectives!
Looks like there is still some debate about how to compare security, policy, and compliance in Red Hat different products, we are certainly talking about three products:
- Red Hat OpenShift - OCP
- Red Hat Advanced Cluster Management - RHACM
- Red Hat Advanced Cluster Security - RHACS

**We sometimes get similar feedback from existing OpenShift customers asking about differences, and similarities between OCP, RHACM, and RHACS in addition to best practices on how to use all together to manage security and compliance.**

### OpenShift Compliance Operator
Starting with Openshift, It comes with a built-in compliance operator that allows administrators to describe the desired compliance state of a cluster and provides them with an overview of gaps and ways to remediate them.

The assessment requires a continuous scanning for both API resources and nodes, this happens using OpenSCAP, a NIST-certified tool, to scan and enforce security policies provided by the compliance content/configuration.

The compliance content is grouped into compliance profiles. There are numerous predefined industry standard profiles like FISMA, CIS OCP benchmark, PCI-DSS, NERC-CIP, But you can also create your own profiles.
![](rh-compliance-00.png)
All the above mentioned features come with the OpenShift compliance operator, So OpenShift does not need any extra component to achieve this.
![](rh-compliance-01.png)

### Red Hat Advanced Cluster Management
While It is clear the role of compliance operator in OCP, the confusion starts when we add RHACM as a management layer that already comes with policy and compliance features and here is the explaination:

**RHACM** is responsible for **creating and managing policies**, It includes the policy framework that **supports policy creation and deployment to various managed clusters** in addition to taking remediation actions when policies are violated. At the managed clusters level, RHACM provides a policy controller to evaluate one or more policies on the managed cluster against the specified controls and generates Kubernetes events for violations. Violations are propagated to the hub cluster.

**Note**: When compliance is mentioned in the context of RHACM, it refers to RHACM’s ability to propagate policies, using the Policy Controller from the hub cluster that runs RHACM, to managed clusters so that the same API objects are placed across the managed clusters. In this context, RHACM can define a policy to **enforce the deployment of the OpenShift compliance operator on all managed clusters** while **compliance scanning is still taken care of by the compliance operator**. RHACM also comes with built-in controllers like K8s configuration, Certificate, IAM, and policy set controllers, they all work alongside Openshift compliance operator to support a long list of policies including but not limited to namespace, pod, memory usage, Role, Role Binding, ETCD encryption, and Image vulnerability policy in addition to support for Kyverno engine policies like add network policy, add quota policy, and sync secrets policy.

`So,`RHACM does NOT provide any scanning based on the OpenSCAP contents, but it guarantees the required configurations are loaded across the managed clusters to secure them.

![](rh-compliance-02.png)

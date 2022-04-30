# Application Security Lab Assignment 3

successful setup of the Lab environment in the Ubuntu Virtual machine provided with the lab material is demonstrated in the below screenshot.
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/setup.png)

## Part 1: Remediate Security Review Findings
### Control 1 - Minimize the admission of privileged containers

#### Validate findings

Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the value of *securityContext.privileged* set as **True**. This validates the issue of admission of privileged container. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control1validate.png)

#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.privileged* feild should be **omitted or set to False**. Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.privileged* feild is set to *True*, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.privileged* feild and set it to *False*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.

#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time no output is returned which satisfies the audit requirement as it is specifically mentioned in the CIS Benchmark that **either no output or false should be returned**. Hence the test is passed. Below screenshot signifies that issue of admission of privileged container is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal1.png)

### Control 2 - Minimize the admission of containers wishing to share the host process ID namespace

#### Validate findings

Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the value of *.spec.hostPID* set as **True**. This validates the issue of admission of containers wishing to share the host process ID namespace. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control2validate.png)


#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.hostPID* feild should be **omitted or set to False**. Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.hostPID* feild is set to *True*, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.hostPID* feild and set it to *False*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.


#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time no output is returned which satisfies the audit requirement as it is specifically mentioned in the CIS Benchmark that **either no output or false should be returned**. Hence the test is passed. Below screenshot signifies that issue of admission of containers wishing to share the host process ID namespace is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal2.png)

### Control 3 - Minimize the admission of containers wishing to share the host IPC namespace

#### Validate findings
Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the value of *.spec.hostIPC* set as **True**. This validates the issue of admission of containers wishing to share the host IPC namespace. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control3validate.png)

#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.hostIPC* feild should be **omitted or set to False**. Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.hostIPC* feild is set to *True*, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.hostIPC* feild and set it to *False*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.

#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time no output is returned which satisfies the audit requirement as it is specifically mentioned in the CIS Benchmark that **either no output or false should be returned**. Hence the test is passed. Below screenshot signifies that issue of admission of containers wishing to share the host IPC namespace is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal3.png)


### Control 4 - Minimize the admission of containers wishing to share the host network namespace

#### Validate findings
Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the value of *.spec.hostNetwork* set as **True**. This validates the issue admission of containers wishing to share the host network namespace. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control4validate.png)

#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.hostNetwork* feild should be **omitted or set to False**. Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.hostNetwork* feild is set to *True*, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.hostNetwork* feild and set it to *False*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.

#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time no output is returned which satisfies the audit requirement as it is specifically mentioned in the CIS Benchmark that **either no output or false should be returned**. Hence the test is passed. Below screenshot signifies that issue of admission of containers wishing to share the host network namespace is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal4.png)


### Control 5 - Minimize the admission of containers with allowPrivilegeEscalation

#### Validate findings

Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the value of *.spec.allowPrivilegeEscalation* set as **True**. This validates the issue admission of containers with allowPrivilegeEscalation. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control5validate.png)

#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.allowPrivilegeEscalation* feild should be **omitted or set to False**. Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.allowPrivilegeEscalation* feild is set to *True*, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.allowPrivilegeEscalation* feild and set it to *False*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.

#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time **False** is returned as output which satisfies the audit requirement as it is specifically mentioned in the CIS Benchmark that **either no output or false should be returned**. Hence the test is passed. Below screenshot signifies that issue of admission of containers with allowPrivilegeEscalation is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal5.png)


### Control 6 - Minimize the admission of root containers

#### Validate findings

Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the value of *.spec.runAsUser* set as **RunAsAny**. This validates the issue admission of root containers. The value RunAsAny allow root user in a container. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control6validate.png)

#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.runAsUser* feild should be **set to either MustRunAsNonRoot or MustRunAs with the range of UIDs not including 0** . Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.runAsUser* feild is set to *RunAsAny*, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.runAsUser* feild and set it to *MustRunAsNonRoot*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.

#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time **MustRunAsNonRoot** is returned as output which satisfies the audit requirement as it is specifically mentioned in the CIS Benchmark that **eeither MustRunAsNonRoot or MustRunAs should be returned**. Hence the test is passed. Below screenshot signifies that issue of admission of root containers is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal6.png)


### Control 7 - Minimize the admission of containers with the NET_RAW capability

#### Validate findings

Using the *kubectl get psp* command, I listed all the Pod Security Policies (PSPs). There is only one PSP by the name *unrestricted* and the no value was returned for *kubectl get psp unrestricted -o=jsonpath='{.spec.requiredDropCapabilities}'*. Hence we can say that there is no PSP which drops Net_RAW capabilities of a container. Thus, this validates the security flaw of admission of containers with the NET_RAW capability. Below is the screenshot demonstrating the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control7validate.png)

#### Remediate

As mentioned in the CIS benchmark for remidiation the Pod Security Policy (PSP) *.spec.requiredDropCapabilities* feild should be **set to include either NET_RAW or ALL** . Hence we surfed through the repository to find the PSP.yaml file which was found on the path */home/nyuappsec/AppSec3/GiftcardSite/k8* by the name *django-psp.yaml*.

As shown in the below screenshot *.spec.requiredDropCapabilities* feild is missing, which is the issue.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Old_PSP.png)

We now update the PSP *.spec.requiredDropCapabilities* feild and set it to *NET_RAW*

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/Updated_PSP.png)

Post updating the PSP we have rebuild the kubernetes cluster for the changes to take effect.

#### Verify finding resolution

After performing the fix to the issue in the pod security policy we run the validation step again to check the output. This time **["NET_RAW"]** is returned as output which satisfies the audit requirement. Hence the test is passed. Below screenshot signifies that issue of admission of root containers is removed from the cluster.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/RemVal7.png)


### Control 8

#### Validate findings


#### Remediate


#### Verify finding resolution

### Control 9

#### Validate findings

Using the *kubectl get namespaces* command we get default value of namespace which includes the following output:
1. default - The default namespace for objects with no other namespace
2. kube-system - The namespace for objects created by the Kubernetes system
3. kube-node-lease - Namespace used for node heartbeats
4. kube-public - Namespace used for public information in a cluster

This signifies that there is no namespace to isolate kubernetes objects. Please refer below screenshot for further proof.

![](control9validate.png)

#### Remediate


#### Verify finding resolution

### Control 10

#### Validate findings


#### Remediate


#### Verify finding resolution

### Control 11

#### Validate findings


#### Remediate


#### Verify finding resolution


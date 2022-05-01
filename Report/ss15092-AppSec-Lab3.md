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


### Control 8 - Prefer using secrets as files over secrets as environment variables

#### Validate findings

As mentioned in the audit report secret were littered all around the web application and we were also hinted that we need to look into **views.py and settings.py** files and identify that secrets were indeed present in the hardcode and there is no explicit file to handle and securely store the secrets.
As a first step we run the audit command provided in the CIS benchmark. Below is the output of the audit command.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v2.png)

The above output references to objects which use environment variables defined from secrets. Next step is to manually look into files to identify littered secret.

First, we open settings.py as hinted in the report, we find that secret key is hardcoded. Below is the screenshot for the confirmation.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v1.png)

There is no secret in views.py. But I thought to view all the files and identify other places where screts are littered. I found secrets littered in the following location:
1. **django-deploy.yaml** - MySQL admin password was hardcoded
    ![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v3.png)
2. **DB's Dockerfile** - MySQL root password was hardcoded
    ![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v4.png)
We also found that the file **django-admin-pass-secret.yaml** which should be containing all the secrets is not correctly built and a random user is existing hence this confirmed that issue of secrets being used as environment variables. Below is the screenshot as an evidence.
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v5.png)


#### Remediate

In order to mitigate the vulnerability I rewrite application code to read secrets from mounted secret files, rather than from environment variables. Below is the screenshot of the secret file where i have made edits to include MySQL password (base64 encoded, this is required as if we just enter normal text value the application will throw error while compiling) and secret key from settings.py. Please note that the reference field with which the secrets will acessed across all the web application is login-secrets. Also note that secret file is marked as opaque which hides the file by default.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r1.png)

As a next step we remove the secret in individual file and refer the secrets file instead:

1. **db-deployment.yaml** - As seen in the screenshot in the validate finding section MySQL password is hardcoded, I edit this file and instead of the password code refer the secrets file so that whenever required password will be called from the secrets file and not environment variable. Below is the screenshot for the same.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r2.png)

2. **django-deploy.yaml** - As seen in the screenshot in the validate finding section MySQL password and secret key is hardcoded, I edit this file and instead of the hardcoded secrets code refer the secrets file so that whenever secret is required it will be called from the secrets file and not environment variable. Below is the screenshot for the same.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r3.png)

3. **Dockerfile** - As seen in the screenshot in the validate finding section MySQL password is hardcoded,we just remove the environment variable. Below screenshot signifies the chages.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r4.png)

4. **settings.py** - As seen in the screenshot in the validate finding section secret key is hardcoded, I edit this file and instead of the hardcoded secret key, code refer the secrets file so that whenever secret is required it will be called from the secrets file and not environment variable. Below is the screenshot for the same.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r5.png)

#### Verify finding resolution

After making all the changes we restart the cluster and this is a test if we have done the refrencing corectly the web application will start perfectly otherwise the pods will not run. Below id the screenshot of pods running correctly after all the changes hence we have created the secret files correctly and referenced it perfectly for pods to fetch details from the secret file instead of the environment variables.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/rv1.png)

### Control 9 - Create administrative boundaries between resources using namespaces

#### Validate findings

Using the *kubectl get namespaces* command we get default value of namespace which includes the following output:
1. default - The default namespace for objects with no other namespace
2. kube-system - The namespace for objects created by the Kubernetes system
3. kube-node-lease - Namespace used for node heartbeats
4. kube-public - Namespace used for public information in a cluster

This signifies that there is no namespace to isolate kubernetes objects. Please refer below screenshot for further proof.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/9/v1.png)

#### Remediate

To remidiate this vulnerability we create a new namespace using *kubectl create namespace my-namespace* command. As seen in the below screenshot we can see that a new namespace is successfully created.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/9/r1.png)

Now to associate all the resources in the new namespace we just add my-namespace as value to the namespace feild in the metadata of all the yaml files in the application. For illustration please find below screenshot. Please note I have made changes to the namespace feild under metadata section in all the yaml file but showing the screenshot for all yaml file would be a waste of energy and space therefore only one screenshot was provided to signify correct understanding of the mitigation.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/9/all%20yaml%20same%20change.png)

#### Verify finding resolution

To verify if our pods/resources are running in the newly created namespace we run command *kubectl get pods* and the output is *no resource found in the default namespace* this was expected as we have migrated all our resources to a new namespace.

We now execute the same command as above but adding namespace flag *--namespace my-namespace* this should show all resources in new namespace, and successfully in the output we find all 3 pods in the new namespace. Hence out objective is achived and the audit finding is cleared.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/9/rv.png)

### Control 10 - Ensure that the seccomp profile is set to docker/default in your pod definitions

#### Validate findings

We check the deploy.yaml files in the web application code base, we found folowing 3 files which does not have seccomp profile in security context.
1. **django-eploy.yaml**
    ![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/v1.png)
2. **k8s/db-deployment.yaml**
    ![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/v2.png)
3. **k8/db-deployment.yaml**
    ![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/v3.png)

Hence confirming the issue of seccomp profile is set to docker/default in your pod definitions.

#### Remediate

We add the seccompProfile to the security context of all 3 files as shown in the below screenshots and restart the cluster for the changes to take effect.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/r1.png)
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/r2.png)
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/r3.png)


#### Verify finding resolution

So after restarting the cluster the pods will only run if the seccomp profile is placed corectly in the files. As shown in the below screenshot the pods are creates successfully and are running in perfect condition. Hence the vulerability is removed and the audit test case is passed.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/10/rv1.png)


### Control 11 - Ensure that a user for the container has been created

#### Validate findings

As mentioned in the CIS benchmark we first run the provided command *docker ps --quiet | xargs --max-args=1 -I{} docker exec {} cat /proc/1/status | grep '^Uid:' | awk '{print $3}'*. This command returns the effective UID for each container.
The below screenshot shows that the user in our container is running as root as the output to the command is 0. Hence the audit finding is validated

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/control11validate.png)

#### Remediate

To remediate the audit finding we fist create user **nginx** in our proxy docker file. Please find screenshot containing the updated dockerfile.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/11/r1.png)

In the main docker file we created a user *django-app* and uncommented adduser code statements already provided in the codebase and also using chmod we restrict permission for the new user.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/11/r2.png)

I have restarted the cluster for changes to take effect


#### Verify finding resolution

In order to validate and confirm if the my updates will come in effect and mitigate the vulnerability, I run the command mentioned in validate section again. Below is the screenshot as proof. As we can note that the output is not zero that means that the user is not root any more. Hence we can say that vulnerability is mitigated.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/11/rv1.png)

### Control 12 - Ensure that containers use only trusted base images

#### Validate findings

Please note for this finding it is mentioned that it is already cleared and no vulnetrability exist related to this point. But to verify we will check for fake docker images by runninng commands mentioned in the audit section of the CIS Benchmark. Below is the screenshot for the same.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/12/1.png)

#### Remediate

No remidiation is required as docker images are based on another established and trusted base image downloaded over a secure channel. This can be seen in the screenshot below.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/12/1.png)

#### Verify finding resolution

No remidiation was done and hence no verification of reolution is required as docker images are based on another established and trusted base image downloaded over a secure channel. This can be seen in the screenshot below.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/12/1.png)

## Control 13 - Ensure that unnecessary packages are not installed in the container

#### Validate findings

Post running the command *docker exec $INSTANCE_ID rpm -qa* we have compared packages called in the docker file. We found that packages like **openjdk11 , alpinelinux** were unnecesary packages in the cluster.
Below screenshot shows the docker file where unnecessary packages are called.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/13/v.png)

#### Remediate

In order to mitigate the vulnerability we just comment out all the code statements in dockerfile where unnecessary packages are being called. Below screenshot shows changes in the code base.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/13/r.png)

#### Verify finding resolution

We restart the cluster to ensure that the changes in the cluster are taken into effect. Our cluster starts perfectly thus signifing that the commented line of code calling unnecessary packages are indeed useless. Please see below screenshot signifying that the cluster works perfectly.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/13/rv.png)

## Control 14 - Ensure that COPY is used instead of ADD in Dockerfiles

#### Validate findings

As mentioned in the the CIS benchmark we look into all dockerfiles for ADD statements, we found sevreal ADD statements in dockerfiles. Hence confirming the presence of vulnerability. Below are the screenshot for proof

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/v1.png)
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/v2.png)
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/v3.png)

#### Remediate

To remediate we replace the ADD statement in dockerfiles with COPY instructions. Below is the screenshot for showing the changes we made to docker file

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/r1.png)
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/r2.png)
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/v3.png)

#### Verify finding resolution

After making changes to the code base we will restart the cluster and if cluster starts ok then it signifies that vulnerability is removed without impacting the application. Below is the screenshot showing that the cluster starts perfectly fine and hence the vulnerabiltiy is mitigated

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/14/rv.png)

## Control 15 - Ensure secrets are not stored in Dockerfiles

#### Validate findings

This finding is very simillar to control 8 and i have mitigated this vulnerability in control itself. I will use the data and instructions from there.

In **DB's Dockerfile** - MySQL root password was hardcoded
    ![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v4.png)
We also found that the file **django-admin-pass-secret.yaml** which should be containing all the secrets is not correctly built and a random user is existing hence this confirmed that issue of secrets being used as environment variables. Below is the screenshot as an evidence.
![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/v5.png)

#### Remediate

In order to mitigate the vulnerability I rewrite application code to read secrets from mounted secret files, rather than from environment variables. Below is the screenshot of the secret file where i have made edits to include MySQL password (base64 encoded, this is required as if we just enter normal text value the application will throw error while compiling) and secret key from settings.py. Please note that the reference field with which the secrets will acessed across all the web application is login-secrets. Also note that secret file is marked as opaque which hides the file by default.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r1.png)

As a next step we remove the secret in docker file and refer the secrets file instead:

**Dockerfile** - As seen in the screenshot in the validate finding section MySQL password is hardcoded,we just remove the environment variable. Below screenshot signifies the chages.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/r4.png)


#### Verify finding resolution

After making all the changes we restart the cluster and this is a test if we have done the refrencing corectly the web application will start perfectly otherwise the pods will not run. Below id the screenshot of pods running correctly after all the changes hence we have created the secret files correctly and referenced it perfectly for pods to fetch details from the secret file instead of the environment variables.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/8/rv1.png)

## Control 16 - Use Dedicated Least Privileged Account for MySQL Daemon/Service

#### Validate findings

To validate this finding we loginto the MySQL container and run the audit command *ps -ef | egrep "^mysql.*$"*. Below is the screenshot showing the output of the command. As we see mysql user is returned and it is specefically written in the benchmark that in order to make this control fail no output should be returned. Hence this is a pass as specified in the report.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/16/1.png)

#### Remediate

No remediation is required as the control is a pass.

To validate this finding we loginto the MySQL container and run the audit command *ps -ef | egrep "^mysql.*$"*. Below is the screenshot showing the output of the command. As we see mysql user is returned and it is specefically written in the benchmark that in order to make this control fail no output should be returned. Hence this is a pass as specified in the report.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/16/1.png)

#### Verify finding resolution

No remediation was implemented as the control is a pass.

To validate this finding we loginto the MySQL container and run the audit command *ps -ef | egrep "^mysql.*$"*. Below is the screenshot showing the output of the command. As we see mysql user is returned and it is specefically written in the benchmark that in order to make this control fail no output should be returned. Hence this is a pass as specified in the report.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/16/1.png)

## Control 17 - Dedicate the Machine Running MySQL

#### Validate findings

To validate the fining we run *kubectl get pods* command to identify that our MySQL database is running in a seperate pod which is equivalent to a different machine in virtual environment. Hence this control is a pass as mentioned in the report.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/17/1.png)

#### Remediate

No remediation required as the control is a pass.

To validate the fining we run *kubectl get pods* command to identify that our MySQL database is running in a seperate pod which is equivalent to a different machine in virtual environment. Hence this control is a pass as mentioned in the report.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/17/1.png)


#### Verify finding resolution

No remediation required as the control is a pass.

To validate the fining we run *kubectl get pods* command to identify that our MySQL database is running in a seperate pod which is equivalent to a different machine in virtual environment. Hence this control is a pass as mentioned in the report.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/17/1.png)

## Control 18 - Ensure 'password_lifetime' is Less Than or Equal to '365'

#### Validate findings

To validate the finding we loginto the MySQL pod as root user and execute the command given in CIS Benchmark *SELECT VARIABLE_NAME, VARIABLE_VALUE FROM performance_schema.global_variables where VARIABLE_NAME like 'default_password_lifetime';*. The output of the command is **0**. A value of 0 implies the password never expires. Hence the control failed. The screenshot below shows as a proof.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/18/v.png)

#### Remediate

In the same root session as loggid into for validating the control we set value of default_password_lifetime varialbe as 365 using the comamnd *set persist default_password_lifetime = 365;*. Query is executed successfully hence the changes are success.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/18/r.png)

#### Verify finding resolution

To verify the remediation we run the audit command *SELECT VARIABLE_NAME, VARIABLE_VALUE FROM performance_schema.global_variables where VARIABLE_NAME like 'default_password_lifetime';* again and the output shows that the variable default_password_lifetime varialbe is set to 365. Hence the vulnerability is removed and control is passed.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/18/rv.png)

## Control 19 - Ensure Password Resets Require Strong Passwords 

#### Validate findings

To validate the finding we loginto the MySQL pod as root user and execute the command given in CIS Benchmark *SELECT VARIABLE_NAME, VARIABLE_VALUE FROM performance_schema.global_variables where VARIABLE_NAME in ('password_history', 'password_reuse_interval');*. The output of the command is **0**. A value of 0 implies the password never expires. Hence the control failed. The screenshot below shows as a proof.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/19/v.png)

#### Remediate

In the same root session as loggid into for validating the control we set value of 'password_history', 'password_reuse_interval' varialbes as 5 and 365 respectively using the comamnd *set persist password_history = 5;*. Query is executed successfully hence the changes are success.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/19/r.png)


#### Verify finding resolution

To verify the remediation we run the audit command SELECT VARIABLE_NAME, VARIABLE_VALUE FROM performance_schema.global_variables where VARIABLE_NAME in ('password_history', 'password_reuse_interval');* again and the output shows that the variable default_password_lifetime varialbe is set to 5 and 365. Hence the vulnerability is removed and control is passed.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/19/rv.png)

## Control 20 - Ensure Example or Test Databases are Not Installed on Production Servers

#### Validate findings

To validate the finding we loginto the MySQL pod as root user and execute the command given in CIS Benchmark *SELECT * FROM information_schema.SCHEMATA where SCHEMA_NAME not in ('mysql','information_schema', 'sys', 'performance_schema');*.

The output shows that there is only one database base in the pod which is production database. Hence the control is a pass and it is wrongly mentioned as fail in the report.
Below screenshot is a proof that control is a pass.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/20/1.png)

#### Remediate

No Remidiation required as the control is a pass.

To validate the finding we loginto the MySQL pod as root user and execute the command given in CIS Benchmark *SELECT * FROM information_schema.SCHEMATA where SCHEMA_NAME not in ('mysql','information_schema', 'sys', 'performance_schema');*.

The output shows that there is only one database base in the pod which is production database. Hence the control is a pass and it is wrongly mentioned as fail in the report.
Below screenshot is a proof that control is a pass.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/20/1.png)

#### Verify finding resolution

No Remidiation required as the control is a pass.

To validate the finding we loginto the MySQL pod as root user and execute the command given in CIS Benchmark *SELECT * FROM information_schema.SCHEMATA where SCHEMA_NAME not in ('mysql','information_schema', 'sys', 'performance_schema');*.

The output shows that there is only one database base in the pod which is production database. Hence the control is a pass and it is wrongly mentioned as fail in the report.
Below screenshot is a proof that control is a pass.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/20/1.png)


## Part 2:

In oder to automate the Validation of security controls I have created a cron job which will run on hourly basis and put output of commands used in verifying the control in control 18 and 20.

Since both the control are MySQL related, my commands will run on the MySQL pod. Therefore using command *kubectl get services --namespace my-namespace* i list down all sevices and note down the IP and port of MySQL server for it to be specified in my cronjob code for execution of the queries. output to note **10.108.74.191    <none>        3306/TCP **. The below screenshot shows the steps followed for identifying the IP and port.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/p2/1.png)

My SQL validation commands are noted from the CIS benchmark for both the control:
1. **Control 18 - Ensure 'password_lifetime' is Less Than or Equal to '365'** - command is *SELECT VARIABLE_NAME, VARIABLE_VALUE FROM performance_schema.global_variables where VARIABLE_NAME like 'default_password_lifetime';*
2. **Control 20 - Ensure Example or Test Databases are Not Installed on Production Servers** - *SELECT * FROM information_schema.SCHEMATA where SCHEMA_NAME not in ('mysql','information_schema', 'sys', 'performance_schema');*

Now we create a cronjob stored as **job.yaml** in the repo at *AppSec3/db/k8*. We put the cronjob in the same namespace as our MySQL server so that it access the database pod for running querry. **schedule: "0 * * * *"** signifies that the job will run on an horly basis. 

We prepare a consolidated command on the basis of information gathered through steps mentioned above:

***mysql --host=10.108.74.191 --port=3306 --user=root --password=thisisatestthing. GiftcardSiteDB -e "SELECT VARIABLE_NAME, VARIABLE_VALUE FROM performance_schema.global_variables where VARIABLE_NAME like 'default_password_lifetime';" -e "SELECT * FROM information_schema.SCHEMATA where SCHEMA_NAME not in ('mysql','information_schema', 'sys', 'performance_schema');"***

Also we dont provide MySQL password in hardcode here but refer the secrets file created in this assignment.

The final **job.yaml** code can be seen in the below screenshot.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/p2/2.png)


Now we execute the cron job and restart the cluster and check if appears in our namespace using command *kubectl get cronjob part2-job --namespace my-namespace*. The output shows our job running by name part2-job scheduled hourly. We now know that our cronjob is running we wait for the next hour!

Now to see if our cronjob successfully executes SQL commands and output results in the logs we need to see the job pod in who's log out result will appear. Hence we run command *kubectl get pods --namespace my-namnespace* which give result of all pods in the namespace and not surprisingly we see 4 pods as compared to usual 3. Added pod is our cronjob pod.

To check logs on the cronjob pod we run the following command *kubectl logs part2-job-27519780 --namespace --my-namespace*. Hola! we can see the correct output of the MySQL query which is required to validate control 18 and 20.
Below screenshot proves successful execution of the cronjob query and output being stored in pod logs. Hence we have automated the validation step for control 18 and 20.

![](https://github.com/samaksh-singhal/ss15092-appsec3/blob/main/Report/Artifact/p2/Screenshot%202022-04-28%20at%2019.05.17.png)


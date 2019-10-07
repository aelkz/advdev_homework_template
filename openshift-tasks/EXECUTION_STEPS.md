1-Setup projects

```
./setup_projects.sh fee6 rabreu-redhat.com true
```

##### CONSOLE OUTPUT
```
to build a new example application in Ruby.
role "admin" added: "rabreu-redhat.com"
role "admin" added: "rabreu-redhat.com"
role "admin" added: "rabreu-redhat.com"
Error from server (Forbidden): namespaces "fee6-jenkins" is forbidden: User "rabreu-redhat.com" cannot patch namespaces in the namespace "fee6-jenkins": no RBAC policy matched
Error from server (Forbidden): namespaces "fee6-tasks-dev" is forbidden: User "rabreu-redhat.com" cannot patch namespaces in the namespace "fee6-tasks-dev": no RBAC policy matched
Error from server (Forbidden): namespaces "fee6-tasks-prod" is forbidden: User "rabreu-redhat.com" cannot patch namespaces in the namespace "fee6-tasks-prod": no RBAC policy matched
```

<p align="center">
<img src="https://raw.githubusercontent.com/aelkz/advdev_homework_template/master/openshift-tasks/_images/01.png" width="40%" height="40%" />
</p>

2-Create tasks dev app

```
./setup_dev.sh fee6
```

3-Create tasks prod app

```
./setup_prod.sh fee6
```

4-Setup homework jenkins

Validate your JenkinsFile at https://www.jdoodle.com/execute-groovy-online

```
./setup_jenkins.sh fee6 https://github.com/aelkz/advdev_homework_template.git na311.openshift.opentlc.com
```

http://jenkins-gpte-jenkins.apps.na311.openshift.opentlc.com/

5- Run Jenkins pipeline

Acces your own {GUID} jenkins instance. 
It will be something like:

{GUID} AdvDev Homework Jenkins

Build the pipeline, going to Builds -> Pipelines
and start a new pipeline.

6- Run grading script

Add the following permissions to jenkins GPTE user:

oc -n fee6-tasks-dev policy add-role-to-user edit system:serviceaccount:gpte-jenkins:jenkins
oc -n fee6-tasks-prod policy add-role-to-user edit system:serviceaccount:gpte-jenkins:jenkins
oc -n fee6-jenkins policy add-role-to-user edit system:serviceaccount:gpte-jenkins:jenkins

OBS. Where `fee6` is your GUID

Open https://jenkins-gpte-jenkins.apps.na311.openshift.opentlc.com and log in.
Click on "OpenShift Advanced Application Deployment Homework Grading" and start a new pipeline,
using the "Build with Parameters" link.

Enter the following:

GUID: fee6
USER: {your-email-goes-here}
REPO: https://github.com/{your-github-user}/advdev_homework_template.git
SETUP: unchecked
DELETE: checked

OBS. Where `fee6` is your GUID



###### TROUBLESHOOTING
If you get something like at the output after container starts, its because you're running 2 instances of the same application on PRD environment (namespace).
*** JBossAS wrapper process (1) received TERM signal ***

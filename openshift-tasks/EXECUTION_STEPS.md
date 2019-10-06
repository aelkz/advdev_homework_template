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

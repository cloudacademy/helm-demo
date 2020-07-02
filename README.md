# Helm Chart Demonstration Resources

The following instructions are used to demonstrate how to build, package, and install a Helm 3 custom chart.

:metal:

The custom ```cloudacademy-webapp``` Helm chart when installed creates the following cluster resources:

![CloudAcademyWebapp](./doc/HelmTemplate1.png)

# STEP 1:
Package the ```cloudacademy-webapp``` chart

```
helm package cloudacademy-webapp
```

# STEP 2:
Install the ```cloudacademy-webapp``` chart into Kubernetes cluster

```
helm install ca-demo1 cloudacademy-webapp-0.1.0.tgz
```

# STEP 3:
Examine newly created Helm chart release, and all cluster created resources

```
helm ls

kubectl get all
```

# STEP 4:
Perform an HTTP GET request, send it to the newly created cluster service

```
kubectl run --image=busybox bbox1 --rm -it --restart=Never \
-- /bin/sh -c "wget -qO- http://ca-demo1-cloudacademy-webapp"
```
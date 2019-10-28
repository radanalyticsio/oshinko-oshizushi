# Oshinko Oshizushi

An operator that encapsulates the source-to-image process for creating Apache
Spark based Deployments and Jobs within OpenShift.

## Quickstart

**Prerequisites**

1. A terminal shell with the OpenShift client tool (`oc`) installed.

1. An active login to OpenShift with `cluster-admin` role privileges.
   (this is required to install the custom resource definitions)

1. A copy of this repository.

**Procedure**

1. Install the custom resource definitions.
   ```
   oc apply -f deploy/crds
   ```

1. Install the operator.
   ```
   oc apply -f deploy
   ```

1. Create an application.
   ```
   oc apply -f examples/sparkpi-python27-application.yaml
   ```

You should now see the operator creating an ImageStream, Build, and Deployment
for the application. You will also see a Spark cluster being deployed.

**Validation**

To check that the application is working, you can run the following commands
to create and expose an external route and then access the application for an estimate
of the value for Pi. For a longer description of this application and its
functionality, please see [this tutorial](https://radanalytics.io/my-first-radanalytics-app.html).

1. Create a service
   ```
   oc create service clusterip sparkpi --tcp=8080
   ```

1. Expose the service
   ```
   oc expose svc/sparkpi
   ```

1. Curl the endpoint for a terrible estimate of Pi
   ```
   curl http://`oc get routes/sparkpi --template='{{.spec.host}}'`/sparkpi
   ```

If everything has worked you will see a message from the service returning
an estimate for the value of Pi.

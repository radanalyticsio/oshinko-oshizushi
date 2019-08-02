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
   oc apply -f examples/sparkpi-application.yaml
   ```

You should now see the operator creating an ImageStream, Build, and Deployment
for the application. You will also see a Spark cluster being deployed.

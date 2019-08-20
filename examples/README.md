# Oshizushi examples

The manifests contained in this directory demonstrate various features of the
oshinko-oshizushi operator.

* `sparkpi-application.yaml` - Deploys an HTTP service which will compute the
  value of Pi when requested. It will automatically spawn a Spark cluster for
  the service. For more information about how this service functions, see
  [this radanalytics.io tutorial](https://radanalytics.io/my-first-radanalytics-app.html).

* `sparkpi-job.yaml` - Deploys a Spark cluster and runs a kubernetes job to
  calculate the value of Pi. It will destroy the Spark cluster after a
  successful job completion. Examine the logs of the job pod to see the results.

* `sparkpi-job-override.yaml` - Runs the Pi calculation job using a pre-existing
  cluster. You must provide the Spark cluster to make this example function.

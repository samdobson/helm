# Streamlit Helm Chart

Deploy your Streamlit application to Kubernetes the simple way with Helm.

This is clearly very hacky, and not in any way suitable for a production deployment.

## Usage

No need to deal with containers!

### 1. Add the Helm Chart repo.

`helm repo add samdobson https://samdobson.github.io/helm`

### 2. Load your application code to a configmap.

Save your app code as `streamlit_app.py`, then create a configmap, with:

`kubectl create configmap streamlit-appcode --from-file=streamlit_app.py`

(to understand why this is managed outside of the chart, see [Issue #2](https://github.com/samdobson/helm/issues/2).

### 3. Install the chart.

`helm install my-streamlit-app samdobson/streamlit`

## Why?

Sometimes you just want an easy way of deploying an existing Streamlit application, without messing with Docker and container registries.

This helm chart deploys a Python 3.10 [Streamlit Docker Image](https://hub.docker.com/repository/docker/samdobson/streamlit), stores your application code as [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/), mounts it as a [volume](https://kubernetes.io/docs/concepts/storage/volumes/) and executes it.

### Limitations

This quick and dirty approach will only work if your Streamlit app:

* Has a single file only.
* Requires no additional libraries (you will need to build your own image, if this is the case).

Of course, this is absolutely *not* a secure / production-ready deployment method.

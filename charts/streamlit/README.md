# Streamlit Helm Chart

Deploy your Streamlit to Kubernetes in minutes. 

## Prerequisites

* [Helm](https://helm.sh/docs/intro/install/)

## Usage

`helm repo add samdobson https://samdobson.github.io/helm`
`helm install my-streamlit-app streamlit --set-file appCode=myapp.py`

## Why?

Sometimes you just want a quick route to deploying an existing Streamlit application, without worrying about containerisation.

This helm chart adds for, with your application code stored as a ConfigMap and mounted as a volume.

This deployment uses an unofficial Python 3.10 [Streamlit Docker Image](https://hub.docker.com/repository/docker/samdobson/streamlit).

# Limitations

This approach will only work for you if your Streamlit app:

* Has a single file only.
* Requires no additional libraries (you will need to build your own image, if this is the case).

Of course, this is absolutely *not* a secure / production-ready deployment method.

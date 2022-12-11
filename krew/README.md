# BiliBiliPro Kubectl Plugin

## Prerequisites

- Kubernetes >= v1.23.0.
- go >= v1.18
- kubectl installed on your local machine, configured to an existing healthy Kubernetes cluster.
- [krew](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) plugin installed

## Install Plugin

Command: `cd ./krew && make deploy`
The binary will be generated in cmd/ install it alonside the kubectl binary. 

For example: the kubectl is installed under `/usr/bin`, then put the bilibilipro plugin under `/usr/bin` too.

## Plugin Commands

### Deployment && Update

Command: `kubectl bilipro init --config config.yaml`

Creates Deployment with the needed environments. 


Optional Options:

- `--image=zai7lou/bilibili_tool_pro:0.2.1`
- `--namespace=bilipro`
- `--image-pull-secret=`

Required Options:

- `--config=<config.yaml>`

The content of <config.yaml> is a yaml array, please refer to the example config yaml under the krew directory.

For example
````yaml
- name: Ray_BiliBiliCookies__2
  value: "cookie"
  # DailyTrigger - required
- name: Ray_DailyTaskConfig__Cron
  value: "11 11 * * *"
````


Suggestions: Deploy this workload in namespace other than default or kube-* namespace, because the delete logic should be improved


### Deletion

Command: `kubectl bilipro delete [options]`

Deletes Deployment.
v
Optional Options:

- `--namespace=<deploy-namespace>`
- `--name=<deploy-name>`

### Version

Command: `kubectl bilipro version`

Output the plugin version.



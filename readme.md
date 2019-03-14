## Manifests - Guide

### Service Repos
[GCP-Source](https://github.com/knative-pdc-2019-ad/gcp-filesource-demo)

[Parser](https://github.com/knative-pdc-2019-ad/parser-demo)

[Resolver](https://github.com/knative-pdc-2019-ad/resolver-demo)



### Create Channels
```sh
$ kubectl apply -f channel-records.yaml

$ kubectl apply -f channel-parsed.yaml

$ kubectl apply -f channel-resolved.yaml
```


### Create services/subscriptions
```sh
# Message-dumper
$ kubectl apply -f message-dumper/subscription.yaml

# Resolver
$ kubectl apply -f resolver/subscription.yaml

# Parser
$ kubectl apply -f parser/subscription.yaml

# GCP - Source
$ kubectl apply -f gcp-source/subscription.yaml
```


### Commands
```sh
# View subscriptions
$ kubectl get subscription

# View services
$ kubectl get kvsc

# View manifest
$ kubectl get ksvc <ksvc_name> -oyaml

# View pods
$ kubectl get po -n default

# Istio namespace
$ kubectl get po -n isitio-system
$ kubectl get svc -n istio-system
```


### Stop and cleanup
```sh
# Services
$ kubectl delete containersource.sources.eventing.knative.dev/gcp-filesource
$ kubectl delete ksvc parser
$ kubectl delete ksvc resolver
$ kubectl delete ksvc message-dumper

# Subscriptions
$ kubectl delete subscription parser
$ kubectl delete subscription resolver
$ kubectl delete subscription logger

# Channels
$ kubectl delete channel records
$ kubectl delete channel parsed
$ kubectl delete channel resolved
```

<p align="center">
  <img alt="Raiders of the Lost Ark" src="docs/img/indiana.gif" height="140" />
  <h3 align="center">k8s-image-swapper</h3>
  <p align="center">Mirror images into your own registry and swap image references automatically.</p>
</p>

---

`k8s-image-swapper` is a mutating webhook for Kubernetes, downloading images into your own registry and pointing the images to that new location.
It is an alternative to a [docker pull-through proxy](docker-mirror).
The feature set was primarily designed with Amazon ECR in mind but may work with other registries.

[docker-mirror]: https://docs.docker.com/registry/recipes/mirror/

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Why?](#why)
- [Getting started](#getting-started)
  - [Helm](#helm)
  - [Kustomize](#kustomize)
- [Stargazers over time](#stargazers-over-time)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Why?

* Consolidate all images in a single registry
* Protection against:
  * external registry failure ([quay.io outage](quay-outage))
  * image pull rate limiting ([docker.io rate limits](docker-rate-limiting))
  * accidental image changes
  * removal of images
* Use in air-gaped environments without the need to change manifests
* Reduce NAT ingress traffic/cost

[quay-outage]: https://www.reddit.com/r/devops/comments/f9kiej/quayio_is_experiencing_an_outage/
[docker-rate-limiting]: https://www.docker.com/blog/scaling-docker-to-serve-millions-more-developers-network-egress/

## Getting started

### Helm

```
helm install
```

### Kustomize

```
kustomize build . | kubectl apply -f -
```

## Stargazers over time

[![Stargazers over time](https://starchart.cc/estahn/k8s-image-swapper.svg)](https://starchart.cc/estahn/k8s-image-swapper)

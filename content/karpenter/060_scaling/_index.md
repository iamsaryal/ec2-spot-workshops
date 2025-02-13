---
title: "Scaling App and Cluster"
chapter: true
weight: 60
---

# Implement AutoScaling with HPA and Karpenter

In this section, we will show patterns for scaling your worker nodes and applications deployments automatically. Automatic scaling in K8s comes in a few forms. In this section we will focus on the following three tasks

![Monte Carlo Pi Approximation](/images/karpenter/deploy/monte_carlo_pi.png)

* **Deploying a microservice application** To illustrate application scaling using [Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) (HPA) and cluster scaling using [Karpenter](https://github.com/awslabs/karpenter), we will deploy a microservice that generates CPU load. The microservice we will use is a trivial web service that uses a [Monte Carlo method to approximate pi](https://en.wikipedia.org/wiki/Monte_Carlo_integration).


* **Horizontal Pod Autoscaler (HPA)** scales the pods in a deployment or replica set. It is implemented as a K8s API resource and a controller. The controller manager queries the resource utilization against the metrics specified in each HorizontalPodAutoscaler definition. It obtains the metrics from either the resource metrics API (for per-pod resource metrics), or the custom metrics API (for all other metrics).

* **Karpenter** By now, I'm sure you don't need an introduction to Karpenter. You've seen it working and scaling it manually. In this section we will be showcasing how it works when in combination with HPA.
# Contour Example

## Install Contour 
`kubectl apply -f contour.yaml`

## Simple Ingress 

### Create Nginx and Httpd deployments and Services
```
kubectl create deploy nginx --image=nginx
kubectl expose deploy nginx --port=80
kubectl create deploy httpd --image=httpd
kubectl expose deploy httpd --port=80
```

### Apply simple ingress yaml
`kubectl apply -f simple-ingress.yaml`

## Named virtual host

### Using ingress 
`kubectl apply -f name-virtual-host-ingress.yaml`

### Using Httpproxy
Delte ingress based virtual host first
`kubectl delete -f name-virtual-host-ingress.yaml`

Now create httpproxy based virtual host
`kubectl apply -f httpproxy-virtual-host.yaml`


## Blue Green Deployment
`kubectl apply -f httpproxy-blue-green.yaml`

Goto http://bg.192.168.2.240.xip.io 

or 

 ```
 while true; http bg.192.168.2.240.xip.io | grep h1; sleep 1; done
 ```

## Weighted Routing

`kubectl apply -f httpproxy-weighted.yaml`

Goto http://wt.192.168.2.240.xip.io 

or 

 ```
 while true; http wt.192.168.2.240.xip.io | grep h1; sleep 1; done
 ```


## Rate Limiting

`kubectl apply -f httpproxy-rate-limiting.yaml`

Goto http://rt.192.168.2.240.xip.io 

or 

 ```
 while true; http rt.192.168.2.240.xip.io | grep h1; sleep 1; done
 ```
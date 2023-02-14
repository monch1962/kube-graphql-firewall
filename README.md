# kube-graphql-firewall

## Set up a Kubernetes cluster, if you don't already have one

You can follow the instructions at https://github.com/monch1962/kube-local-env to set up a local cluster

## Clone an existing GraphQL project

`$ git clone https://github.com/apollographql/federation-demo.git`

`$ cd federation-demo`

`$ npm i`

This application needs to be changed to run in a Kubernetes namespace. This involves changing URLs in the `gateway.js` file to ones that can be accessed via Kubernetes

`$ cat gateway.js | sed -r 's~http://localhost:([0-9]+)/([a-z]+)"~http://\2:\1"~g' > gateway.test.js && mv gateway.test.js gateway.js`

Now set up the GraphQL server in its own namespace

`$ kubectl create namespace graphql-server`
`$ cd manifests`
`$ kubectl apply -f . -n graphql-server`

Now keep running

`$ kubectl get all -n graphql-server`

until all the containers are running




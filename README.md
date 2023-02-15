# kube-graphql-firewall

## Set up a Kubernetes cluster, if you don't already have one

You can follow the instructions at https://github.com/monch1962/kube-local-env to set up a local cluster

We're going to hit an external GraphQL endpoint. You can check that it works by 

`$ curl 'https://countries.trevorblades.com/' -X POST -H 'Content-Type: application/json' -d '{ "query": "{ continents { code name } } " }'`


# example-voting-app-kubernetes
This is based on the original [example-voting-app](https://github.com/dockersamples/example-voting-app) repository from the [docker-examples](https://github.com/dockersamples) GitHub page as part of a [Kubernetes Course](https://www.udemy.com/share/1013LO3@YT9DZnL79ViZr0ccgyT7TulRwsFNIMuUNCZxHZ_dzbCm8BUwFoPf_JAdIcnPK5K2zw==/)


How to Run Deployment:
1. Deployed all apps as a Pod on a Kubernetes cluster

2. Enabled connectivity between the services
     - the redis db is accessed by the voting app and the worker app
     - the voting app saves the vote from the redis db
     - the worker app reads the vote from the redis db
     - postgres is accessed by the worker app to update the total count of votes
     - postgres is accessed by the result app to read the total count of votes to be displayed in the resulting web page
     - the voting app is accessed by external users
     - the result app is accessed by the external users to view the results
  
     - the voting app has a python web server that listens on port 80
     - the result app has a node.js based server that listens on port 80
     - the redis db has a service that listens on port 6379
     - the postgresSQL db has a service that listens on port 5432

       *the worker app is not being accessed by anyone
       *the worker app simply reads the counts of votes from the redis db and updates the total count of votes on the postgres db


  3. Exposed service for use to users for external users
     - created a service for the redis pod so it can be accessed by the voting app and worker app (redis-service) 
     - created a service for the postgresSQL pod so the postgresSQL db can be accessed by the worker app and result app (db) 
     - created service for voting-app and result-app (type: nodePorts)
    

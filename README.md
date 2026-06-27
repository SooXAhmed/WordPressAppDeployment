this project is a kubernetes deployment for a word press application

i used kind to create the cluster and the config file is in the repo its kind-config.yaml , i customized the cluster using the kind-config.yaml so i can map the cluster ports(the docker container that has the cluster ) to ports of vm that i am working on , so i can access it from the vm,my laptop browser 


and i then 
created two deployments
first : for database
i made one replica of the pod ,and used mysql database ,and passed the values needed for database creation as env vars but they are not stored plain they are inside kuberntes secret , i made a service for pods of this deployment with type clusterip ,the frontend will to talk to it using its dns (ofcourse they are in the same namespace)

second: for wordpress
i made one replica of the pod , and used the latest wordpress image , also i created a pv and attached it to this container so , the data uploaded on the website will presist recreation of the pod ,and i passed the database information needed for wordpress to start talking to the database in the env vars so that it doesn't ask for them when starting wordpress, i created a service for the pods of this deployment with type NodePort so thats accessible outside the kind cluster 




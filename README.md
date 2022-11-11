# CS3219-OTOT-D

## Instructions on how to run the Kafka Cluster :

- Install kafkacat by running `sudo apt-get install kafkacat` if you're using Linux/WSL
- Make sure the docker is running
- Clone the repo, go to the root directory and run `sudo docker-compose up -d`
- In the terminal, run `sudo vim /etc/hosts`, add `0.0.0.0 kafka-1 kafka-2 kafka-3`, and save the changes
- Run `kafkacat -L -b kafka-1:10092` to list all available brokers in the cluster
- Run `kafkacat -P -b kafka-1:10092 -t <topic-name>` to create a topic with topic-name, this is also the command to create a publisher, so you can immediately start sending messages here
- In a separate terminal, run `kafkacat -C -b kafka-3:30092 -t <topic-name>` to create the customer / subscriber, you’ll be able to see all the messages sent by the publisher

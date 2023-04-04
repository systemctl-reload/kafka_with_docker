# Install Docker



    sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg


    sudo mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg


    echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y


    sudo apt install docker-compose -y

# start kafka

    cd kafka_with_docker
    
    sudo docker-compose up -d
    
    sudo docker ps


# Producer & Consumer

    docker exec -it kafka1 bash

    kafka-console-producer.sh --bootstrap-server kafka1:9092 --producer.config /etc/kafka/secrets/client.properties --topic test

    kafka-console-consumer --bootstrap-server kafka1:9092 --consumer.config /etc/kafka/secrets/client.properties --topic test
    

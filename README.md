Login

    docker login


Build and Tag

    docker build -t  giddu/jenkins-inbound-agent:${tag} .

Push
    
    docker push giddu/jenkins-inbound-agent:${tag}


    buildah login docker.io
    buildah bud -t docker.io/giddu/jenkins-inbound-agent:dotnet-ecs-3.1 .
    buildah push docker.io/giddu/jenkins-inbound-agent:dotnet-ecs-3.1
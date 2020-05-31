# Build enviroment for wangle

Execute the following commands:

    docker build -t wangle .
    docker run -it -d --name wangle_builder wangle
    docker exec -it wangle_builder bash
    

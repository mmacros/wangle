# Build enviroment for wangle

Execute the following commands:

    docker build -t wangle ./Docker
    docker run -v C:\wangle\prj_src\:/prj_src -it -d --name wangle_builder wangle
    docker exec -it wangle_builder bash
    
If you need to compile inside the container use:

    g++ -std=c++14 server.cpp -o server -lwangle -lfizz -lfolly -lgflags -lglog -lpthread -ldl -lboost_context -lboost_program_options -lboost_thread -lboost_filesystem -lboost_system -lboost_regex -lboost_chrono -lssl -lcrypto -llzma -lz -lsnappy -llz4 -liberty -levent -ldouble-conversion -lsodium -lunwind


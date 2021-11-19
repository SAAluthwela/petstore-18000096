# PetStore API

## Introduction

This is Backend implementation for the Pet - Store web application.

## Packaging and running the application

If you want to build an _uber-jar_, execute the following command:

    ./gradlew build -Dquarkus.package.type=uber-jar

To run the application:

    java -jar build/petstore-runner.jar

The application can be also packaged using simple:

    ./gradlew build

It produces the `quarkus-run.jar` file in the `build/quarkus-app/` directory.
Be aware that it is not an _uber-jar_ as the dependencies are copied into the `build/quarkus-app/lib/` directory.

To launch the test page, open your browser at the following URL

    http://localhost:8080/index.html

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:

    ./gradlew quarkusDev

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Deploying the Application

If you want to create a Docker Image, execute the following command:

    ./gradlew build -Dquarkus.package.type=native -Dquarkus.native.container-build=true -Dquarkus.container-image.build=true

To deploy the application using docker-compose, navigate to the [./deploy](https://github.com/nandulaperera/petstore/tree/main/deploy) directory and execute the following command:

    docker-compose up -d
   
    
## Executing the Test Suite

To run the test suite, execute the following command:

    ./gradlew clean test

## Testing the API using curl
### Managing pets

- Get all pets

        curl -v http://localhost:8080/v1/pets

- Add a new pet

        curl -d '{"petId":4,"petName":"Tommy", "petType":"Dog", "petAge":5}' -H 'Content-Type: application/json' http://localhost:8080/v1/pets

- Update an existing pet

        curl -d '{"petId":4,"petName":"Tommy", "petType":"Dog", "petAge":7}' -H 'Content-Type: application/json' -X PUT http://localhost:8080/v1/pets/2

- Delete a pet

        curl -X DELETE http://localhost:8080/v1/pets/4

- Search pet by name
    
        curl -v http://localhost:8080/v1/pets/query/byName?Pet_Name="Tommy"

- Search pet by type

        curl -v http://localhost:8080/v1/pets/query/byType?Pet_Type="Dog"

- Search pet by age

        curl -v http://localhost:8080/v1/pets/query/byAge?Pet_Age=3




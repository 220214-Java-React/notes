# Microservices

* Compare the microservice and monolithic architectures. What are the advantages / disadvantages of each?
  * Monolith - all code deployed together in single, large application
    * Harder to scale, single point of failure
    * Easier to deploy
    * Code can get messy, complex, tightly coupled
  * Microservices - application composed of independently deployed services
    * Services governed by single responsibility principle
    * Enforces loose coupling of application
    * Complex to deploy and manage relative to monolith
    * Easier to scale
    * Teams can work independently on different services
* How do you solve the different problems inherent to microservices?
  * Use container orchestration tools for deployment
  * Use service discovery and API gateway
* What's the difference between a MSA and a SOA?
  * MSA (microservice architecture) is an extension of SOA to services within an application
* Can a Java microservice communicate with a Node.js microservice? Why or why not?
  * Yes, this is polyglot pattern and a benefit of microservices
  * Services communicate through requests sent to APIs, typically use JSON or XML data formats (language agnostic)
* What's the difference between horizontal and vertical scalability? Which way do monoliths and microservices typically scale?
  * Vertically scale - upgrade single server CPU, memory, storage, etc
  * Horizontal scale - replicate service on another server
  * Monoliths - typically vertically scale; harder / costly to scale horizontal
  * Microservices - typically scale horizontal; easier with smaller services
* What are some best practices for building microservices?
  * Keep services independent and minimize dependencies where possible
  * Have each service manage its own data store / database; other services access the data through its API
  * Use distributed logging, tracing, and monitoring tools
  * Implement circuit breaking pattern for fault tolerance
  * Containerize each service for rapid deployment and scaling of infrastructure
* How large should each service in a microservice be?
  * Follow single responsibility principle
  
# Docker

* What is a container? How is it different from a VM?
  * Containers are lightweight, they can share the underlying OS
  * Containers package only the app and the environment needed to run the app
  * Containers keep environments consistent for every deployment and isolate them from the rest of the system
* What is the Docker Daemon?
  * Underlying process that runs and manages the docker containers
* What is a Docker image? Container?
  * An image is like blueprint for a container
  * An image is readonly, like a file; container is the instantiation and contains the running application
* How is a Docker image different from a Docker container? How are the read/write layers different?
  * Docker containers are built in layers; each line in a Dockerfile adds a layer
  * A container adds a write layer
  * When an image needs to be rebuilt, only the layer that changed needs to be built
* List the steps to start Docker, create a Docker image, and spin up a container
  1. Write a Dockerfile
  2. Build the image `docker build <pathToDockerfile>`
  3. Spin up the container `docker run <imageName>`
* What is the relevance of the Dockerfile to this process? List some keywords in the Dockerfile.
  * Dockerfile is the configuration file for an image/container
  * Keywords: FROM, COPY, ADD, WORKDIR, ENV, CMD, RUN
* What is the benefit to an image being built in Layers?
  * Images can be composed from base images and keeps them lightweight / smaller size
* What are some other Docker commands?
  * `docker container ls`
  * `docker attach`
  * `docker kill`
  * `docker help`
  * `docker inspect`
* What is a container registry? How would you retrieve and upload images to DockerHub?
  * Holds images, either public or private
  * Use `docker pull` and `docker push` to upload/download images
* What is Docker compose and why is it useful?
  * Write a yml config file for spinning up multiple containers at once
* If you want to store state for a container, how does Docker recommend doing that?
  * Use a volume or connect to external state management service
  * Volumes are file systems mounted to a container and exist on the host independent of the container

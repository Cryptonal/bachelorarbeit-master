# Bachelor Thesis Topic: Embedded Software Architectures with Docker

![Python](https://img.shields.io/badge/Python-3-yellow)  ![React](https://img.shields.io/badge/React-18-blue) ![Docker](https://img.shields.io/badge/Docker-24-blue) 

## Introduction

A train communication system simulation is developed in my bachelor thesis. The system consists of five microservices. One client represent the screen and 4 flask web servers. The client sends messages to the web servers and getting response back using Rest-API protocol. The client can also do some actions on the screen. The whole system is running inside docker containers for scalability and portability because this system has to run at the end on the i.MX8-Quad core hardware. When system is containerized CPU,memory and throughput integration tests running inside every docker container. Hence the containers' performance.

## Project structure

1. All flask webservers are in Backend/webservers.
2. ./my-infotainment is the frontend screen GUI [the react app].
3. docker-compose.yml in the root is responsible for running the 5 micro services inside containers.
4. docker-compose.yml in Monitor tools is responsible for runnning the monitor tools containers.
4. dynamicRelocation in the root is responsible for dynamically relocate docker containers based on a cpu threshold value.



## Installation
1. nodejs
2. React
-- Go to dir ./my-infotainment and run `npm install`. This command will install all dependencies used for the client
3. Python3 
4. Flask

**Note:** If you want to run the system only inside containers, you need only to install docker, docker compose and python3. Docker images are going to install all other libraries and dependencies.

## Usage

To start the whole system and run the integration tests, you just need to run this command `sudo python3 startSystem.py`. 

## Integration Tests [CPU,Memory,Throughput]

In folder IntegrationTests, there are 3 directories CPU, Memory and Throughtput. Every directory has python script running some tests for these metrics.


cpu.py file in IntegrationTests/CPU dir is running the whole system on multiple distribution of docker containers on Quad core.

memory.py file in IntegrationTests/Memory is giving us exactly how much memory in megabytes and in bytes we need to run every container and getting out-of-memory error if allocating bytes are low.

throughput.py file in IntegrationTests/Throughput is used to know how megbytes per second can be transfered between client continaer [screen] and flask servers containers [control_center, emergency,passengers,train dispatcher] using iperf-package

## Result
Comparing all different distributions considering containers' metrics to know the best distribution, The best distribution is test case E.


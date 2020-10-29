# OpenVidu project

## Sprint 2

This project pull from <https://github.com/OpenVidu/openvidu-tutorials.git>.

1)To run this demo, You need to install node. For Windows, Download from <https://nodejs.org/en/> . For Linux /Max, install it using these lines:

```
sudo curl -sL https://deb.nodesource.com/setup_12.x | sudo bash -
sudo apt-get install -y nodejs
```

2) Then you need to install NPM dependencies

```
npm install
```


3) After that, execute server.js passing two arguments:

```
node server.js https://localhost:4443 MY_SECRET
```

4) You will also need to use Docker container to set up the OpenVidu Platform service.(The easiest way to setup)

```
docker run -p 4443:4443 --rm -e OPENVIDU_SECRET=MY_SECRET openvidu/openvidu-server-kms:2.15.0
```



## Sprint 3

- 10/21 
  - Choose Google Firebase as host to deploy our WebRTC project
  - Database schema draft 1.1
    - ![Database schema](C:\Users\Niantong Dong\Desktop\2020_Fall_BU\EC601-WebRTC-Security-Analysis\openvidu-js-node\Database schema.png)

- 10/28
  - Successfully deploy our website on https://www.ec601-openvidu-team1.com/
    - Chrome may encounters some unknown security issues to access this website. Use Firefox if Chrome doesn't work
  - AWS component
    - EC2 instance and Elastic IPs, CloudFormation, Route53
  - Some questions we will talk about during Sprint 3 presentation
    - How to bind Elastic IPs to instances ?
    - How to map domain to Elastic IPs ?
    - What is the problems we met when we created the stack ?



## Sprint 4


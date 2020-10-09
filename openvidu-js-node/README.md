### OpenVidu project

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
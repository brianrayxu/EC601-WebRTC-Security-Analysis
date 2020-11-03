<img src="Images/weblogo.png" alt="WebRTC" width="200"/>

EC601 Term Project- Analysis of OpenVidu and other WebRTC Applications
## Introduction

WebRTC is one of the most popular real-time communication protocol which can build on top of your browser. It is supported by every major browser and countless popular products utilize its versatility such as Facebook Messenger, Discord, and Google Hangouts.

One of the biggest challenges which these products prioritize is the security surrounding the communications and personal information of their users. Privacy is a necessity and even the smallest exposure of proprietary user data could have a significant effect on the product as well as the victims involved. In order to prevent any successful attacks on any WebRTC apps, we will do an analysis of WebRTC by creating our own sample system using the protocol and will attempt several tests and angles of analysis in order to further underestand the details of WebRTC and the security it offers and/or needs. 

Specifically, we are trying to create our own communication portal using Openvidu, an open source framework that supports real-time video and audio meeting app (using the WebRTC protocol). Initially, we will be implementing local examples of Openvidu and then move to online implementations using AWS to host our necessary servers.

<img src="Images/openvidulogo.png" alt="Openvidu" height="150" width="750"/>

From there, we will start our security analysis by using WireShark to monitor the data packet traffic to see if we can find a security weakness in our platform. In addition, we will also monitor the logs on our AWS instance to see if any logs that OpenVidu produces are exposing client info.

(INSERT FUTURE EXPERIMENTS HERE)

On a side note, we also want to examine the vulnerability of peer-to-peer communications with WebRTC but Openvido doesn't support it yet. So we will use another simple WebRTC example to see if we can build a peer-to-peer communication software and anaylze the vulnerability.

## MVP + User Story

The MVP for our product should be an instance o OpenVidu that is able to create a session and hold a virtual meeting with audio and video.

=======
## User-stories

As a academic user of WebRTC products such as Openvidu, ...

## Technical Approach - Brian
In this section, we will go in detail of our implementations and experiments.
### Local Implementations - Sprint 1 + 2
 Our first step is to just get a simple bare-bones instance up and running on a local machine. In order to achieve this, we followed the tutorials located on the 
 <a href="https://docs.openvidu.io/en/2.15.0/tutorials/" title="Openvidu Docs">Openvidu Documentation</a> 
 webpage. The specific tutorial we chose was the one called "openvidu-js-node" which includes 


<img src="Images/openvidunodejs.png" alt="openvidu system" width="800"/>

### AWS Implementation - Sprint 3
Once our local implementation was up and running without any issues, we deployed an instance on AWS in order to further mimic a standard use-case. We use the Openvidu Call Application S3 template in order to start off our deployment on the AWS Cloudformation Stack. From there, we supply our stack with an Elastic IP which is tied to the domain which we want to host our application at. 

The domain supplied needs to be a FQDN (Fully Qualified Domain Name) and not a website hosted at a static URL. This can all be done on Amazon Route 53 and here is a  <a href="https://aws.amazon.com/getting-started/hands-on/get-a-domain/#:~:text=Fully%20Qualified%20Domain%20Name%20(FQDN),-b.&text=b.-,Click%20the%20Create%20Record%20Set%20button.,resources%20that%20you%20have%20available." title="Domain Registration">link</a> to the walkthrough we used to create our FQDN.

Here is a general overview <a href="https://docs.openvidu.io/en/2.15.0/deployment/deploying-aws/" title="Deploying on AWS">link</a> to the tutorial we followed in order to deploy onto AWS.

For more details, check our code section README for a step by step walkthrough of how to deploy onto AWS.

During our deployment process, we were having issues creating our stack and getting our application to properly deploy at our domain but resolved the issues by 
![](Images/openviduexample.png)


### Security Analysis
In this section, we will talk about the experiments we did in order to evaluate security efforts from Openvidu.
#### Wireshark - Data Stream Security

#### 


## Conclusion

The MVP for our product should be able to hold a virtual meeting with audio and video.
Our user is anyone who need to hold meeting or attend meeting but unable to do so physically.
The user story is, for example, a professor in college do the lecture online and all of his/her students are attending this meeting at the same time with audio and video connection.

## References

<img src="Images/weblogo.png" alt="WebRTC" width="200"/>

# EC601 Term Project- Analysis of OpenVidu and other WebRTC Applications

WebRTC is one of the most popular real-time communication protocol which can build on top of your browser. It is supported by every major browser and countless popular products utilize its versatility such as Facebook Messenger, Discord, and Google Hangouts.

One of the biggest challenges which these products prioritize is the security surrounding the communications and personal information of their users. Privacy is a necessity and even the smallest exposure of proprietary user data could have a significant effect on the product as well as the victims involved. In order to prevent any successful attacks on any WebRTC apps, we will do an analysis of WebRTC by creating our own sample system using the protocol and will attempt several tests and angles of analysis in order to further underestand the details of WebRTC and the security it offers and/or needs. 

Specifically, we are trying to create our own communication portal using Openvidu, an open source framework that supports real-time video and audio meeting app (using the WebRTC protocol). Initially, we will be implementing local examples of Openvidu and then move to online implementations using AWS to host our necessary servers.

<img src="Images/openvidulogo.png" alt="Openvidu" height="150" width="750"/>

From there, we will start our security analysis by using WireShark to monitor the data packet traffic to see if we can find a security weakness in our platform. In addition, we will also monitor the logs on our AWS instance to see if any logs that OpenVidu produces are exposing client info.

The specific experiments we chose to accomplish are the following:
- Communications Layer Attack
- DoS Attack
- Signalling Layer Attack

On a side note, we also want to examine the vulnerability of peer-to-peer communications with WebRTC but Openvido doesn't support it yet. So we will use another simple WebRTC example to see if we can build a peer-to-peer communication software and anaylze the vulnerability.

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

### Security Analysis - Communication Layer - Sprint 4
After deploying our application onto AWS, we started our experiments by first looking at the most obvious angle attack, an attempt to eploit communications. 

### Security Analysis - DoS Attacks - Sprint 4 
Another popular angle attack is to do a Denial of Service attack (DoS). 


<img src="https://breakdev.org/content/images/size/w2000/2018/07/evilginx_blog_title2.jpg" alt="evilginx2" 
### Security Analysis - Signalling Layer - Sprint 5   width="200"/>
In our final sprint, we decided to deploy an attack onto the signalling layer of our application. This took the form of a Man in the Middle(MiTM) attack. MiTM attacks in our application could take place in two different places. They could either be a phishing attack between the server and client or in between two clients directly. We chose to take the approach of a phishing attack as these are more common and more practical for hackers to pull off. A phishing attack is when a third party acts as some trusted component of the application the attack is based on. Popular phishing attempts include pop-ups pretending to be Microsoft and saying your PC 'needs' attentiion or fake webpages asking for autentication in order to steal credentials off their victims. 

In order to pull off an attack, we use the open-source project evilginx2. Evilginx2 is a CLI application which makes the art of phising easy for anyone. Although the package seems to be a bad idea and promote malicious behavior, it is actually used as a research tool and to do exactly what we are doing, research ethods to defend against phishing attacks.

First, we create a custom phishlet, a webpage to 'act' as the legitimate service, from a copy of the html used in Openvidu's "Create a Room" web page:

<img src="Images/webpage.png" alt="openvidu system" width="800"/>

From here, we inspect what tag is used for the form where the user enters their unique session code in order to join or create a room. This tag is called "roomInput' and we specify in evilginx what tag we are looking to 'steal' from our victims on our copied webpage. Then, evilginx sets up our Let's encrypt certificates and hosts the fake webpage at a specificed domain with a secured connection. In order to simulate a victim falling for our phishing attack, we just access the URL of the fake webpage and input some unique code for our sesion. Evilginx2 takes the input data, saves it, and redirects the user to the legitimate site after inputting the data the user originally entered. This is so the user won't even be aware that they just got phished while the hackers run off with the stolen credentials. 


 





## Conclusion

The MVP for our product should be able to hold a virtual meeting with audio and video.
Our user is anyone who need to hold meeting or attend meeting but unable to do so physically.
The user story is, for example, a professor in college do the lecture online and all of his/her students are attending this meeting at the same time with audio and video connection.

## References

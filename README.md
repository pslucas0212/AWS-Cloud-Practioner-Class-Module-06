# Security

[AWS Cloud Practitioner Home](https://github.com/pslucas0212/AWS-Cloud-Practioner)

### Introduction

Shared responsiblity model 
- AWS controls datacenter and serives (AWS Foundational Services)
- Customer responsible for data applciaitons, etc.

### Transcript
Looks like we're getting deeper into our AWS account. Things are running well. And I want to let you in on the security measures we have in place. By this, I mean, we have to describe the various security mechanisms we offer on the AWS Cloud, like the shared responsibility model. 


With the shared responsibility model, AWS controls security of the cloud and customers control security in the cloud. We, as AWS, control the data centers, security of our services, and all the layers in this section. The next part are the workloads that AWS customers run in the cloud and those are the customer's responsibility to secure. It's something we share with customers to ensure security in the cloud. 


Let's take a look at the various other security services, mechanisms, and features that AWS has to offer in this module. Stay tuned.

### Shared Responsibility Model

Both AWS and the customer are responsible for security.

AWS is a set of parts that build upon each other.  THe Shared Responsiblilty model.

Example: EC2 - Datacenter, server, hypervisor, storage, network are secured by Amazon.  Customer 

AWS Responsiblities - 3rd party auditors have reviewed code for security
- Physical layer: Property, building
- Network Layer
- Hypervisor Layer

Customer Reponsibility
- Operating system in a VM
- OS Patching - AWS will alert you to security vulnerabilities, but AWS can't patch the OS
- Applications 
- Data

AWS responsible for security of the cloud.  The customer is responsible for what's in the cloud.

#### Transcript
When it comes to securing your business on AWS, it's important to ask the question: Who is ultimately responsible for the security? Is it A: You, the customer? or B: AWS? And the correct answer is: yes. Both. Both are ultimately responsible for making sure that you are secure. 


Now, if there's any security experts watching this right now you're probably shaking your head saying you can't have two different entities with the ultimate responsibility over a single object. That's not security, that's wishful thinking. At AWS, we agree completely. But for us, we don't look at your environment as a single object. Instead we see it as a collection of parts that build on each other. AWS is responsible for the security of some of the objects. Responsible 100% for those. The others, you are responsible 100% for their security. This is what's known as the shared responsibility model. 


It's no different than securing a house. The builder constructed the house with four walls and a door. It's their responsibility to make sure the walls are strong and the doors are solid. It's your responsibility, the homeowner, to close and lock the doors. 


It really is that simple on AWS as well. Take EC2, for instance. EC2 lives in a physical building, a data center that must be secured. It has a network and a hypervisor that supports your instances and their individual operating systems. On top of that operating system, you have your application, and that supports your data. So for EC2 and every service AWS offers, there's a similar stack of parts that build on top of each other. AWS is 100% responsible for some, you are responsible for the others. 


So, starting with the physical layer. This is iron and concrete and fences and security guards. Someone has to own the concrete. Someone has to staff the physical perimeter, 24/7. This is AWS. On top of the physical layer we have our network and our hypervisor. Now, I'm not gonna go into details on how this is all secured, but basically we have reinvented those technologies to make them faster, stronger, tamper-proof. 


But you don't have to just take our word for it. We have numerous third party auditors who have gone through the code and the way we build our infrastructure, and can provide the right documentation you need for your security compliance structures. Now, on top of all that, on EC2, you now get to pick what operating system you want to run. 


This is the magic dividing line that separates our responsibility. AWS' responsibility and your responsibility. This is your operating system. You're 100% in charge of this. AWS does not have any backdoor into your system here. You and you alone have the only encryption key to log onto the root of this OS or to create any user accounts there. I mean, no more than a construction company would keep copies of your front door key, AWS cannot enter your operating system. And here's a hint. If someone from AWS calls and asks you for your OS key, it is not AWS. 


Now that means your operations team is 100% responsible for keeping the operating system patched. If AWS discovers there are some new vulnerabilities in your version of Windows, let's say, we can certainly notify your account owner but we cannot deploy a patch. This is a really good thing for your security. This means no one can deploy anything that might break your system without your team being the ones that do it. Now, on top of that OS, you can run whatever applications you want. You own them. You maintain them. 


Which takes us to the most important part of the stack, your data. Data. This is always your domain to control. And sometimes you might want to have your data open for everyone to see, like pictures on a retail website. Other times like banking or healthcare, yeah, not so much, not so much. AWS provides everyone with the tool set they need for their data to open it up to some authorized individuals, to everyone, to just a single person under specific conditions, or even lock it down so no one can access it. Plus, the ability to have ubiquitous encryption. That way even if you accidentally left your front door open, all anyone would see is unreadable encrypted content. 


The AWS shared responsibility model is about making sure both sides understand exactly what tasks are ours. Basically, AWS is responsible for the security of the cloud and you are responsible for the security in the cloud. Together, you have an environment you can trust.


### User Permissions and Access

AWS Identity and Access Managemnet (IAM)

When you set up your AWS account, you become the root owner with root access to the account.  you have no restrictions on the AWS account.  When you first setup your account, turn on MFA (multi-factory authorization).

You control access and permissions with IAM
- First create IAM user.  The user has no permissions, you must explicity allow actions to be done by any user.
- Known as the least privelaged acces
- IAM policy is a JSON document that describes AWSA API call a user can or cannot make
- Policies can allow or deny, then list action and resource
- Create IAM groups that group users and attach a policy to that group instead of individaully adding polices to each user.


AWS IAM
- root user
- IAM user represents a person or application.  By default no permissions assigned initially to an IAM user
- IAM Groups - A collection of IAM users
- IAM Polices - permisions assigned to users or groups.  Follow the principle of least privelage
- IAM Role - You can create identities in AWS called roles that temporarily allow or deny particular permissions to users, applications or services.  To temporarily gain or grant access to a particular role.  When "receiving the role" the IAM user, app, or service abando all previous permissions under the previous role and assume permissions of the new role
- Federate users into IAM account....


#### Transcript
In the coffee shop, every employee has an identity. They come into work in the morning and they'd log into the system to clock in, use the registers and manage the systems, running the coffee shop, day to day. We have the cash registers, the computers helping run the whole operation. Each person has unique access to these systems based on who they are. 


If I have Rudy at the register taking orders and Blaine in the back, checking on the inventory levels on the computer, they have two different logins and two different sets of permissions. Rudy can run the cash register, but if he went to log into the inventory system, he wouldn't be allowed to do that. 


You will want to scope your users permissions in AWS in a similar way. When you create an AWS account, you are given what is called the root account user. This root user is the owner of the AWS account and has permission to do anything they want inside of that account. This is like being the owner of the coffee shop. 


In this situation, let's say I am the owner of the coffee shop. I can come into the shop, use my credentials to work the register, work the inventory system or any other system in the coffee shop. I cannot be restricted. With the AWS root user, you can access and control any resource in the account. You can spin up databases, EC2 instances, blockchain services, or literally whatever you want. Because that user is so powerful, we recommend that as soon as you create an AWS account and log in with your root user, you turn on multi-factor authentication, or MFA, to ensure that you need not only the email and password, but also a randomized token to log in. 


That is great. But even with MFA turned on, in reality you don't want to use the root user for everything. I, as the coffee shop owner, don't give my level of access to all employees. Rudy on the cash register cannot access the inventory system, remember? You control access in a granular way by using the AWS service, AWS Identity and Access Management, or IAM. 


In IAM, you can create IAM users. When you create an IAM user, by default, it has no permissions. The user can't even log into the AWS account at first, it has absolutely zero permissions. It can not launch an EC2 instance. It can not create an S3 bucket. Nothing. You have to explicitly give the user permission to do anything in that account. Remember, by default, all actions are denied. You have to explicitly allow any action done by any user. You give people access only to what they need and nothing else. This idea is called the least privilege principle. 


The way that you grant or deny permission is to associate what is called an IAM policy to an IAM user. An IAM policy is a JSON document that describes what API calls a user can or cannot make. Let's look at this quick example. In this example, you can see we have a permission statement that has the effect as Allow, the action as s3:ListBucket. And the resource is a unique ID for an S3 bucket. So if I attach this policy to a user and that user could view the bucket "coffee_shop_reports" but perform no other action in this account. There were only two potential options for the effect on any policy. Either allow or deny. For action, you can list any AWS API call and for resource, you would list what AWS resource that specific API call is for. Now, as a business person, you wouldn't need to write these policies, but they are used all over in your AWS accounts. 


One way to make it easier to manage your users and their permissions is to organize them into IAM groups. Groups are, well, they are groupings of users. You can attach a policy to a group and all of the users in that group will have those permissions. If you have a bunch of cashiers in the coffee shop, instead of individually granting them all access to the register. Instead, you can grant all cashiers access then just add each individual cashier to the group. Same idea with groups in IAM. 


All right, so far with IAM, you have the root user, they can do anything. You have users which can be organized into groups. And you also have policies which are documents that describe permissions that you can then attach to users or groups. There is one other major identity in IAM, and it's called a role. 


To understand the idea of roles, let's think about the coffee shop. As we know, Blaine works in the shop and depending on the staffing of the shop day to day, he might work the register or the inventory system or he might be the one cleaning up at the end of the day with access to no systems. I, as the owner, have the authority to assign these different roles to Blaine. His responsibilities and access are variable and change from day to day. Just because he worked on tracking inventory in the system yesterday, doesn't mean that he should be at any time. His role at work changes and is temporary in nature. The same type of idea exists in AWS. You can create identities in AWS that are called roles. 


Roles have associated permissions that allow or deny specific actions. And these roles can be assumed for temporary amounts of time. It is similar to a user, but has no username and password. Instead, it is an identity that you can assume to gain access to temporary permissions. You use roles to temporarily grant access to AWS resources, to users, external identities, applications, and even other AWS services. When an identity assumes a role, it abandons all of the previous permissions that it has and it assumes the permissions of that role.

You can actually avoid creating IAM users for every person in your organization by federating users into your account. This means that they could use their regular corporate credentials to log into AWS by mapping their corporate identities to IAM roles. AWS IAM authentication and authorization as a service.

### AWS Organization

Mostly like start with one AWS account.  Important to separate duites like development, procurment, etc.  AWS organizations allow you to manage multiple accounts controlling access, billing, etc.

AWS organizations
- Centralized managemnt of all accounts
- Consolidated billing for all member accounts.  Bulk discounts
- Hierachral groupsings of accounts for billing or security or access to particular resources.
- Contoral over AWS service and API that each account can access.  Use service control policies (SCPs) to control maximum resource access for each account

#### Transcript
With your first foray into the AWS Cloud, you most likely will start with one AWS account and have everything reside in there. Most people start this way, but as your company grows or even begins their cloud journey, it's important to have a separation of duties. For example, you want your developers to have access to development resources, have your accounting staff able to access billing information, or even have business units separate so that they can experiment with AWS services without effecting each other. So you start to add more cards for each person, whoever needs to onboard. And before you know it, you end up with a tangled bowl of AWS account spaghetti, not as tasty as you might imagine. 


For example, you'll then have to keep track of Account A, F, and G, or maybe Account B has the wrong permissions and Account C has billing and compliance info. One way to install order and to enforce who is allowed to perform certain functions in what account is to make use of an AWS service called AWS Organizations. 


The easiest way to think of Organizations is as a central location to manage multiple AWS accounts. You can manage billing control, access, compliance, security, and share resources across your AWS accounts. Let's outline some of the main features of AWS Organizations, shall we? 


The first is centralized management of all your AWS accounts. Think of all those AWS accounts, we had: A, B, C, F, G. Now you can combine them into an organization that enables us to manage the accounts centrally, and wow. Now we've found Accounts D and E in the process. Next up is consolidated billing for all member accounts. This means you can use the primary account of your organization to consolidate and pay for all member accounts. Another advantage of consolidated billing is bulk discounts. Cash money, indeed. 


The next feature is that you can implement hierarchical groupings of your accounts to meet security, compliance, or budgetary needs. This means you can group accounts into organizational units, or OUs, kind of like business units, or BUs. For example, if you have accounts that must access only the AWS services that meet certain regulatory requirements, you can put those accounts into one OU, or if you have accounts that fall under the developer OU, you can group them accordingly. 


One of the last main features we'll touch upon is that you have control over the AWS services and API actions that each account can access as an administrator of the primary account of an organization. You can use something called service control policies, or SCPs, to specify the maximum permissions for member accounts in the organization. In essence, with SCPs you can restrict which AWS services, resources, and individual API actions, the users and roles in each member account can access.

### Compliance

Every industry has particular standards that must be met (compliance checks and audits for example).  Tax Audits, Health inspections, etc.  GDRP, HIPPA, etc.  You will need to gather documentation for compliance.

You inherite all the best practices archictecture, security, etc. from AWS.  You AWS has a set of compliance mettrics that you have already met and focus on compliance related to your application. The customer owns their data in AWS per the AWS Shared Responsibility Model.

You can request from AWS for documentation secruity and compliance


AWS artificat - Provides you 3rd party reports on compliance.  See the AWS compliance center for documents.   

AWS Artifact Agreements
AWS Artifact Reports
Customer Compliance Center

#### Transcript
For every industry, there are specific standards that need to be upheld, and you will be audited or inspected to ensure that you have met those standards. For example, for a coffee shop, the health inspector will come by and check that everything is up to code and sanitary. Similarly, you could be audited for taxes to see that you have run the back office correctly and have followed the law. You rely on documentation, records and inspections to pass audits and compliance checks as they come along. 


You'll need to devise a similar way to meet compliance and auditing in AWS. Depending on what types of solutions you host on AWS, you will need to ensure that you are up to compliance for whatever standards and regulations your business is specifically held to. If you run software that deals with consumer data in the EU, you would need to make sure that you're in compliance with GDPR, or if you run healthcare applications in the US you will need to design your architectures to meet HIPAA compliance requirements. 


Whatever your compliance need is, you'll need some tools to be able to collect documents, records and inspect your AWS environment to check if you meet the compliance regulations that you're under. The first thing to note is, AWS has already built out data center infrastructure and networking following industry best practices for security, and as an AWS customer, you inherit all the best practices of AWS policies, architecture, and operational processes. 


AWS complies with a long list of assurance programs that you can find online. This means that segments of your compliance have already been completed, and you can focus on meeting compliance within your own architectures that you build on top of AWS. The next thing to know in regards to compliance and AWS, is that the Region you choose to operate out of, might help you meet compliance regulations. If you can only legally store data in the country that the data is from, you can choose a Region that makes sense for you and AWS will not automatically replicate data across Regions. 


You also should be very aware of the fact that you own your data in AWS. As shown in the AWS shared responsibility model, you have complete control over the data that you store in AWS. You can employ multiple different encryption mechanisms to keep your data safe, and that varies from service to service. So, if you need specific standards for data storage, you can devise a way to either reach those requirements by building it yourself on top of AWS or using the features that already exist in many services. For a lot of services, enabling data protection is a configuration setting on the resource. 


AWS also offers multiple whitepapers and documents that you can download and use for compliance reports. Since you aren't running the data center yourself, you can essentially request that AWS provides you with documentation proving that they are following best practices for security and compliance. 


One place you can access these documents is through a service called AWS Artifact. With AWS Artifact, you can gain access to compliance reports done by third parties who have validated a wide range of compliance standards. Check out the AWS Compliance Center in order to find compliance information all in one place. It will show you compliance enabling services as well as documentation like the AWS Risk and Security Whitepaper, which you should read to ensure that you understand security and compliance with AWS. 


To know if you are compliant in AWS, please remember that we follow a shared responsibility. The underlying platform is secure and AWS can provide documentation on what types of compliance requirements they meet, through services like AWS Artifact and whitepapers. But, beyond that, what you build on AWS is up to you. You control the architecture of your applications and the solutions you build, and they need to be built with compliance, security, and the shared responsibility model in mind.

### Denial of Service Attacks

DDOS - Distributed Denial of Service atttack.  DDOS objective is to shut down your system by overwhelming the system with requests.

Example attacks
- UDP Flood.  Requests info from the weather services and sends the results to your network.
- HTTP level attacks.  Send complicated product catalog request from an army zombie machines
- SLOWLORIS attack. - The attacker pretends to have a terribly slow connection so it takes a long time for the request to finish.
- Many other strategies

UDP Flood prevention - Security Groups - Not on the list, you don't get access to the system.  This is prevented at the network level and the EC2 instance level

SLOWLORIS attacs - ELB - ELB waits for the entire message to complete before it is sent to the EC2 instance.  ELB runs at the regional level and automatically scales.

AWS Shield with AWS WAF uses a web firewall and reconizes threats with AI/ML to identify attackers.

AWS Shield Standard protects all customers at no cost from common, fequently occuring DDOS attacks
AWS Shield Advanced is a pais service that provides detailed diagnositcs to protect agains DDOS attacks.  It integrates Amazon CloudFront, Amazon Route 53 and ELB.  It can also integrate wth AWS Shield with WAF so you can create customer rules to mitigate DDOS attacks.  





#### Transcript
D-D-o-S, DDoS, the distributed denial-of-service. It's an attack on your enterprise's infrastructure, and you've heard of it. Your security team might have written a plan for it, and you know that many businesses have been devastated by it. But what exactly is it, and more importantly, how can you defend against it? 


Now to be clear, this is a 14-hour discussion to really understand it all, but you need to at least know the fundamentals of how the attacks are carried out, and how AWS can automatically defend your infrastructure from these crippling assaults. Now we don't have a lot of time to cover all this, and the clock starts now. The objective of a DDoS attack is to shut down your application's ability to function by overwhelming the system to the point it can no longer operate. 


In normal operations, your application takes requests from customers and returns results. In a DDoS attack, the bad actor tries to overwhelm the capacity of your application, basically to deny anyone your services. But a single machine attacking your application has no hope of providing enough of an attack by itself, so the distributed part is that the attack leverages other machines around the internet to unknowingly attack your infrastructure. The bad actor creates an army of zombie bots, brainlessly assaulting your enterprise. The key to a good attack, and I call it that when I should call it powerful. I mean, it's definitely chaotic evil, but the key is to have the assault commander do the smallest amount of work needed, and have the targeted victim receive an unbearable load of resulting work they must process through. 


So let me cherry-pick a few specific attack examples that work really well. The UDP flood. It is based on the helpful parts of the internet, like the National Weather Service. Now anyone can send a small request to the Weather Service, and ask, "Give me weather," and in return, the Weather Service's fleet of machines will send back a massive amount of weather telemetry, forecasts, updates, lots of stuff. So the attack here is simple. The bad actor sends a simple request, give me weather. But it gives a fake return address on the request, your return address. So now the Weather Service very happily floods your server with megabytes of rain forecasts, and your system could be brought to a standstill, just sorting through the information it never wanted in the first place. Now that is one example of half a dozen low-level, brute force attacks, all designed to exhaust your network. 


Some attacks are much more sophisticated, like the HTTP level attacks, which look like normal customers asking for normal things like complicated product searches over and over and over, all coming from an army of zombified bot machines. They ask for so much attention that regular customers can't get in. 


They even try horrible tricks like the Slowloris attack. Mm-hmm. Imagine standing in line at the coffee shop, when someone in front of you takes seven minutes to order their whatever it is they're ordering, and you don't get to order until they finish and get out of your way. Well, Slowloris attack is the exact same thing. Instead of a normal connection, I would like to place an order, the attacker pretends to have a terribly slow connection. You get the picture. Meanwhile, your production servers are standing there waiting for the customer to finish their request so they can dash off and return the result. But until they get the entire packet, they can't move on to the next thread, the next customer. A few Slowloris attackers can exhaust the capacity of your entire front end with almost no effort at all. I could go on monologuing for hours just talking about the elegantly evil architecture of these attacks, but we are on the clock here, and it is time to stop these attacks cold. And here's the cool solution: You already know the solution. 


Everything we've been talking about over this entire course is not only good architecture, but it also helps solve almost all DDoS attack vectors with zero additional effort or cost. First attack, the low level network attacks like the UDP floods. Solution, security groups. The security groups only allow in proper request traffic. Things like weather reports use an entirely different protocol than the ones your customers use. Not on the list, you don't get to talk to the server. And what's more, security groups operate at the AWS network level, not at the EC2 instance level, like an operating system firewall might. 


So massive attacks like UDP floods or reflection attacks just get shrugged off by the scale of the entire AWS Regions capacity, not your individual EC2's capacity. This is a case where our size is a huge advantage in your protection. I won't say it's impossible to overwhelm AWS, but the scale it would take, it would be too expensive for these bad actors. Slowloris attacks? Look at our elastic load balancer. Because the ELB handles the http traffic request first, so it waits until the entire message, no matter how fast or slow, is complete before sending it over to the front end web server. I mean, sure, you can try to overwhelm it, but remember how the ELB is scalable and how it runs at the region level? 


To overwhelm ELB, you would once again have to overwhelm the entire AWS region. It's not theoretically impossible, but too massively expensive for anyone to pull off. For the sharpest, most sophisticated attacks, AWS also offers specialized defense tools called AWS Shield with AWS WAF. AWS WAF uses a web application firewall to filter incoming traffic for the signatures of bad actors. It has extensive machine learning capabilities, and can recognize new threats as they evolve and proactively help defend your system against an ever-growing list of destructive vectors. 


All right, that's it, the clock is almost up. The takeaway is a well-architected system is already defended against most attacks. And by using AWS Shield Advanced, you can turn AWS into your partner against DDoS attacks. Oh, oh.

### Additional Security Services

Securing Data at rest and in transit.  Encyrption at rest when data is sitting in storage.  DynamoDB automaticatlly is encrypted.  AWS Key management  Services (AWS KMS) is where you encryprtion kes are cread and managed.   Encryption in transit is enabled via SSL and key certfidates

AWS WAF aka AWS Web application firewall.  AWS WAF works with Amazon CloudFrotn and the Application Load Balancer. It uses a web access control lists (ACL) to protect web resrouces.


Amazon Inspector checks your systems for vulenrabilites and security best practices by running automated security assessments
- Network configuration
- Amazon Agent installed EC2
- Analysis service which identifies security issues and recommendations to remediat

Amazon Guardduty - analyze network and account activity for analyizing security threats.  It runs independtly of AWS services so does it affact performance or availability of your AWS service.  You can use AWS Lambda functions to automatically remediate security in response to GuardDuty's findings.

#### Transcript
With all the comings and goings on in your coffee shop, you'll want to increase security to your coffee beans, equipment, and even money in the till. For your beans, this could be when they're sitting in your store room, or even when you're transporting them between shops. After all, we don't want unwanted visitors with access to our coffee beans, or even running off with precious equipment. 


To start off, let's chat about how you can secure your coffee beans, or your data whether it's at rest, or in transit. For our beans, the simple way to do it would be to lock the door when we'd leave at night. That's the notion of encryption, which is securing a message or data in a way that can only be accessed by authorized parties. Non-authorized parties are therefore less likely to be able to access the message. Or not able to access it at all. Think of it as that key and door example. If you have the key, you can unlock the door. But if you don't, then you cannot unlock that door. 


At AWS, this comes in two variations. Encryption at rest and encryption in transit. By at rest, we mean when your data is idle. It's just being stored and not moving. For example, server-side encryption at rest is enabled on all DynamoDB table data. And that helps prevent unauthorized access. DynamoDB's encryption at rest also integrates with AWS KMS, or Key Management Service, for managing the encryption key that is used to encrypt your tables. That's the key for your door, remember? And without it, you won't be able to access your data. So make sure to keep it safe. 


Similarly, in-transit means that the data is traveling between, say A and B. Where A is the AWS service, and B could be a client accessing the service. Or even another AWS service itself. For example, let's say we have a Redshift instance running. And we want to connect it with a SQL client. We use secure sockets layer, or SSL connections to encrypt data, and we can use service certificates to validate, and authorize a client. This means that data is protected when passing between Redshift, and our client. And this functionality exists in numerous other AWS services such as SQS, S3, RDS, and many more. 


But speaking of other services, the next service we want to highlight is called Amazon Inspector. Inspector helps to improve security, and compliance of your AWS deployed applications by running an automated security assessment against your infrastructure. Specifically, it helps to check on deviations of security best practices, exposure of EC2 instances, vulnerabilities, and so forth. The service consists of three parts a network configuration reachability piece, an Amazon agent, which can be installed an EC2 instances, and a security assessment service that brings them all together. To use it, you configure Inspector options, run the service, out pops a list of potential security issues. The resulting findings are displayed in the Amazon Inspector console, and they are presented with a detailed description of the security issue, and a recommendation on how to fix it. Additionally, you can retrieve findings through an API. So as to go towards the best practice of performing remediation to fix issues. 


Another service dimension is our threat detection offering known as Amazon GuardDuty. It analyzes continuous streams of metadata generated from your account, and network activity found on AWS CloudTrail events, Amazon VPC Flow Logs, and DNS logs. It uses integrated threat intelligence such as known malicious IP addresses, anomaly detection, and machine learning to identify threats more accurately. The best part is that it runs independently from your other AWS services. So it won't affect performance or availability of your existing infrastructure, and workloads. 


They are so many other security services like Advanced Shield and Security Hub. So please check out the Resources section to learn more. Thanks for following along.


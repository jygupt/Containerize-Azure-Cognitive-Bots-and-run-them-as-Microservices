# Orchestrating multiple Intelligent AI Bots as one business with Azure Service Fabric

# Workshop
In this workshop, you will look at the process of designing multiple intelligent bots as one business that will illustrate the use of many Azure features to support scalability, performance, and intelligence based on Service Fabric and other cognitive services.

By the end of this workshop, you will be better able to design and deploy enterprise-ready bots based on Service Fabric and other related Azure services.

# Whiteboard Design Session
In this whiteboard design session, you will work in a group to design a solution that leverages aspects from microservices, bot framework, storage, and other cognitive services to help an online financial service provider to meet their customer demands quickly. You will handle the client's scaling and performance needs through microservices built on top of Service Fabric and apply cognitive services to put intelligence in the bot solution.

## Step 1: Review the customer case study

Step 1: Review the customer case study with all the participants in the group

Timeframe: 15 minutes

## Customer situation

OneBank is a global financial service provider which offers various online banking services to its customers across many countries. The current OneBank solution consists of a collection of websites and web APIs hosted on Azure service fabric with 100s of VMs running. The company has dedicated DevOps experts for maintaining and monitoring the service fabric based applications. Recently, OneBank has experienced tremendous growth trends in its regular online banking and insurance sector. In order for OneBank to meet their customer demands better, the company wants to invest in deploying bots in their existing architecture. To start with, they want to have two separate dedicated bots; one for standard banking services and another for providing insurance services.

**Standard Banking Services Bot Features**
1) Check account balance
2) Transfer money
3) Download statements

**Insurance Service Bot Features** 
1) Buy a new policy
2) Renew policy
3) Check policy details

The company wants to build a solution that is both scalable, fast and extensible so that they can introduce more business specific bots in the near future. In conjunction with this, they are also looking for some common services across all their bots as shown below:-

**Common services across all bots**
1) Human hand off aka Talk to human
2) Capturing all the incoming messages for analytics
3) Fraud detection
4) Answer frequently asked questions

## Customer needs

1. OneBank would like to deploy these bots in their existing Azure service fabric cluster.
2. Bot solution needs to be scalable to support high demand over the weekdays. Scaling a bot up or down should not impact other bots.
3. Automatically respond to frequently asked questions regardless of whether it is related to standard banking services, insurance or anything else.
4. The chat solution must provide support for sentiment analysis and contextual understanding.
2. Bots can be accessed from multiple channels like web chat and facebook.
4. All the incoming messages must be stored in the cloud for further processing. The solution should obfuscate any sensitive data present in      the messages such as credit card numbers, phone numbers and pin codes before putting it into the storage. 
5. One of the major common services across their bots is Human hand-off. They would like to initiate a chat session with the human if the user    demands it or if the sentiment score of the conversation is negative. Before beginning the session, the solution must gather last 15           minutes conversation with the user, summarize it by extracting the useful key phrases, so that the agent doesn't have to go through with the      entire conversation and could find the intent based on the key phrases easily.  
6. Due to security and performance reasons, they want to store the bot state inside the Azure service fabric.
7. The customer is looking for separate language understanding models for each of their bots.
10. Detect anomalies such as fraud detection.

## Customer considerations
1. How bot-to-bot communication will happen? What could be the challenges we might face? Any overheads of this approach?
2. In which of our requirements AI solutions can be leveraged?
3. We have heard about Actor programming model. Does it fit somewhere in our Architecture?
4. We are concerned about where to store all the incoming messages and scope for further processing
5. We are also concerned about how to obfuscate the sensitive information before storing the incoming messages. Can "AI" solutions help   here?
6. Where should we ingest our technical logs and what is the best way to visualize it?
7. We know that both pre-built AI and custom AI options available. We are confused as to when to choose one over the other.

## Step 2: Design a proof of concept solution

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

Directions: With all participants at your table, answer the following questions and list the answers on a flip chart:

Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

What customer business needs do you need to address with your solution?

**High-level architecture**

Without getting into the details (the following sections will address the particular details), diagram your initial vision for handling the top-level requirements for the solution.

_Bots_

1. How would you recognize if a user wants to talk about standard banking services and insurance services? What if a user changes the context from buying a new policy to checking the account balance? Can this be achieved without mixing the language understanding models?

2. Do we need another bot to fulfill the common services across bots like human hand-off, ingesting incoming messages and fraud detection?

3. What would be the best approach to forwarding requests from one bot to another?

_Summarizing chat text_
1. Which AI solution is better to summarize the conversation? Is it enough to extract just the key phrases to recognize the intent? Can we use any other open source library in the future to make this procedure more accurate?

_Bot state_
1. How stateful actors can be leveraged to store the bot states within the cluster. Is it reliable? What happens to the state during upgrade roll-outs? What would be the best strategy to manage the state from a performance perspective?

_Sentiment Analysis_
1. How would you recommend OneBank to identify the sentiment in the incoming messages? Would this require you to build a custom AI model? Is there a pre-built AI service you could use?

_Fraud detection_
1. Does Azure Machine Learning have any pre-built models to recognize frauds? If no, what would be the plan for this?


## Step 3: Present the solution

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 30 minutes

**Presentation**

Directions:

Pair with another table.

1. One table is the Microsoft team and the other table is the customer.

2. The Microsoft team presents their proposed solution to the customer.

3. The customer makes one of the objections from the list of objections.

4. The Microsoft team responds to the objection.

5. The customer team gives feedback to the Microsoft team.

6. Tables switch roles and repeat Steps 2-6.

**Wrap-up**

Timeframe: 15 minutes

Directions: Share the preferred solution for the case study.

## Additional references

| Description   | Links  |
| ------------- | ----- |
| Service Fabric| <https://azure.microsoft.com/en-in/services/service-fabric/> |
| Bot framework | <https://docs.microsoft.com/en-us/azure/bot-service/> |
| LUIS          | <https://azure.microsoft.com/en-in/services/cognitive-services/language-understanding-intelligent-service/> |
| QnAMaker      | <https://docs.microsoft.com/en-us/azure/cognitive-services/qnamaker/> |
| Cognitive services | <https://azure.microsoft.com/en-in/services/cognitive-services/> |
| Azure machine learning | <https://azure.microsoft.com/en-in/services/machine-learning-studio/> |
| Azure storage | <https://docs.microsoft.com/en-us/azure/storage/> |
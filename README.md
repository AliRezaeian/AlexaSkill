## Introduction:

Build the Alexa Interaction Model (the front-end) and point it to the back-end lambda function.

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/alexaarchitecture.png?raw=true)

## Before you Begin
You will need an account with [developer.amazon.com](http://developer.amazon.com/).

Go to [developer.amazon.com](http://developer.amazon.com/) and sign in with the same email address that you’ve registered your Amazon Echo with.

## Create a New Skill

1. Go to [developer.amazon.com/alexa](https://developer.amazon.com/alexa).
2. Click **Your Alexa Consoles** and then click **Skills**. This opens the developer console and displays any skills you have already created.
3. Click **Create Skill**.
4. Enter the **Skill name** "MyTravelSkill".
   * **Skill name**: This is the name customers will see when you publish the skill. You can edit this name later on the Distribution page.
   * **Default language**: You can add additional languages to the skill later.
5. Click the **Custom** model. [Click here](https://github.com/AliRezaeian/AlexaSkill/wiki/Interaction-Models) for more details about different models.
6. Select **Alexa-Hosted(Beta)** to host your backend code to the AWS. 
6. Click **Create skill**.

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill1.png?raw=true)

You should be landed to the Build page.

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill2.png?raw=true)

## Add Intents, Slots, and Utterances
An intent represents an action that fulfills a user's spoken request. 
Intents can optionally have arguments called Slots.
The utterances specify the words and phrases users can say to invoke your intents. 

1. From the checklist, click the second bullet **Intents, Samples, and Slots**
2. Enter the name of the new intent **PlanMyTrip** and click **Create custom intent**. This adds a new intent and opens its detail page, displaying the intent's sample utterances and slots.
3. Click **Create custom intent**

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill3.png?raw=true)

4. In the Intents Slots section, create below slots.

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill4.png?raw=true)

5. Enter below sample utterances:
 
* _i am going on a trip on friday_
* _i want to visit portland_
* _i want to travel from seattle to portland next friday_

Once you have written a few utterances, note the words or phrases that represent variable information. These will become the intent's slots. For example, in the utterances identified above, the variables that are highlighted next friday, seattle, and portland.

6. In an utterance, highlight the word or phrase representing the slot value.
7. In the drop-down that appears, select the slot. This will replace the original value in the utterance with the slot name in curly brackets ({ }).

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill5.png?raw=true)

8. Click **Save Model**

9. Click **Build Model**.

By creating this intent, if user says: "_Alexa, ask Plan My Trip i want to travel from seattle to portland next friday._"

The Alexa service sends the Plan My Trip service a PlanMyTrip intent with the value "Seattle" in the fromCity slot, "Portland" in the toCity slot and the date for the next upcoming Friday travelDate slot. The service can then save this information and send back text to convert to speech.

Slots are defined with different types. The travelDate slot in the above example uses Amazon's built-in AMAZON.DATE type to convert words that indicate dates (such as "today" and "next friday") into a date format, while both fromCity and toCity use the built-in AMAZON.US_CITY slot.

## Develop/Deploy Alexa's AWS Lambda code:

1. Click **Code** on the top menu.
2. Open **index.js** file.
3. Replace all code with the code [here](https://github.com/AliRezaeian/AlexaSkill/blob/master/index.js). 
4. Click **Save**.
5. Click **Deploy**.

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill6.png?raw=true)

## Test you skill

Use the simulator provided on the Test page in the developer console. This gives you access to most Alexa Skills Kit features without a device. You can interact with Alexa using either voice or text.

1. Click **Test** from top menu
2. You might get below pop-up. Click **Allow** to be able to use your microphone. 

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill7.png?raw=true)

3. Select **Development** from dropdown on top of the page
4. In the Alexa Simulator tab, you can type or hold the mic icon to talk. 
5. Say below sentences and see the response from Alexa,

* _ask MyTravelSkill i am going on a trip on friday_
* _ask MyTravelSkill i want to visit portland_
* _ask MyTravelSkill i want to travel from seattle to portland next friday_

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill8.png?raw=true)

## Endpoint

The Interaction Model is connected to a Lambda Function via Endpoints. Depending on the Intent detected, Lambda Function running on AWS executes a task (</code>) and the result is returned to the Interaction Model.

The Endpoint will receive POST requests when a user interacts with your Alexa Skill. You can link your Skill with Lambda (Recommended) or you can host your endpoint using an HTTPS web service that you manage.

![](https://github.com/AliRezaeian/alexaskill/blob/master/images/createskill9.png?raw=true)


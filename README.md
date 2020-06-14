# CarrotCake-Santori_Fit_20_SCDFXIBM

# Background of our team: Carrot Cake

The reason we chose the name carrot cake is because its taste reminds us home and home is a place that we want to protect. Carrot cake comes in two different colour versions, white and black. Similarly, in the context of an innovation challenge, there is no right or wrong answer, what matters is the creativity and the way contestants present their solutions. Coming into the competition with poor programming knowledge, we strive to do our best with our creativity and skills we possess to do what we can for this hackathon.

## Team Members

1. Yiap Zao Chuan - Year 1 Chemistry and Biological Chemistry Student @ NTU
2. Heng Hao Kiat - Year 1 Information Systems: Smart-City Technology and Management Major @ SMU
3. Lua Keng Koon - Final Year Marketing Student @ TP 
4. Neo Chuan Yang - Final Year Biotechnology Student @ TP

# Topic: Climate Change

## Problem we are tackling:

Following the death (https://www.todayonline.com/singapore/nsf-guardsman-19-dies-after-being-warded-heat-injury-mindef?cid=h3_referral_inarticlelinks_03092019_todayonline) of Corporal First Class Dave Lee on 30 April 2018 due to a heat injury, we have seen the swift response of the Singapore Armed Forces (SAF) in conducting more frequent cooling measures on soldiers such as the use of purpose-built cooling pads and the dipping of both arms into a bucket of ice water (https://www.todayonline.com/singapore/saf-makes-2-heat-injury-measures-mandatory-after-cfc-dave-lees-death). The case of Dave Lee has signalled to my team a strong message that such incidents proved to be fatal and it can be avoided if preventive measures are carried out efficiently. 

Given that SCDF personnel train and operate in harsh and humid conditions, their risk of obtaining a heat injury will be significantly higher than servicemen from the SAF. With that frame in mind, our team decided to leverage on a smart watch to predict the risk of a possible heat injury on the wearer. The wearable vibrates and alerts the user when he is at a high risk of obtaining a heat injury if he carries on with the training or operation. This would signal to the user that he should halt his training regime and cool his body down. Therefore, this technology helps to mitigate the risk of heat injury occurring to the SCDF servicemen. 

A further development of our solution include an application for the commanders conducting the training/operation. The application can give commanders an overview of the statuses of the wearables on all their trainees and servicemen. With this, commanders can react swiftly to a vibrating wearable, signaling that the trainee and serviceman is at high risk of a heat injury if he carries on with the training/operation.

# Video Pitch

Pitch (2 minutes): https://www.youtube.com/watch?v=RC3cXzU0c_0&feature=youtu.be
Product Video (1 minute): https://www.youtube.com/watch?v=GONFYP9a8Ek&feature=youtu.be 

# The architecture of our proposed solution

https://drive.google.com/file/d/1FGyGCXFbce2xf3eY5eFUIyPCnT_skNvs/view?usp=sharing


## 1. 

Band collects and stores data coming from the sensors and transfers it to IBM Watson IoT. IBM Watson IoT will determine if the user is at risk of heat injury. If there’s risk of heat injury(parameter out of reference range), the user will be alerted. (IBM Watson will send an alert to the operation band)

## 2 and 3. 

The data collected by IBM watson will be sent to IBM Cloudant for storage and IBM Watson Studio for analysis.

## 4 and 5.

The data and their analysis will be displayed on a webpage, if a heat injury case has occurred and the system was unable to alert the user beforehand. The users can help to calibrate the reference range by indicating that a heat injury has occurred via the web page. This information will then be sent to Watson Studio, allowing it to calibrate the reference range.


# Detailed solution

Wearable technology: Santorio Fit 20

We will be introducing the Santorio Fit 20 wearable technology. The wearable consists of mainly four different features namely heart/ blood pressure sensor, motion sensor to determine hours of sleep, epidermal based sensor measuring sweat amount and a durable material to withstand high heat conditions.

Using an internal storage, the Santorio Fit 20 collects the user's heart rate, blood pressure, sweat amount, hours of sleep and body temperature periodically. As such, we require the user to wear the device for long periods of time such that we can optimise the accuracy of the data collected. After five days of data collection, these will be used to build a predictive model that detects the risk of a possible risk injury. This can be done through IBM Watson Studio's Auto AI which follows this sequence to build candidate pipelines:

(a) Data pre-processing
(b) Automated model selection
(c) Automated feature engineering
(d) Hyperparameter optimisation

Using the csv file generated from the data collected from our device, we will import the data into the Auto AI experiment. By selecting the target variable as heat_injury, we are using the binary classification use case. Next, select the number of training data split of 90%. Lastly, we will run the experiment to determine to most effective model in predicting the risk of a possible heat injury. From the feature importance tab, we can find out the most significant variable in resulting one suffering from a heat injury. With that in mind, we can work towards eliminating the other less significant variables and save data storage in the long run. 

These insights will aid SCDF commanders in swift decision making of stopping the serviceman from further training. In the case of operations, standbys will be activated if a frontliner is at high risk of a heat injury based on the vibration of our Santorio Fit 20. 

To strengthen the accuracy of the prediction of our wearable, we will utilise the Watson IoT platform's function to determine if the user is likely to get heat injury by creating a rule action.

However, we were unable to do it like how the source describe.

Source: https://developer.ibm.com/recipes/tutorials/visualizing-and-understanding-data-from-ibm-watson-iot-platform-by-using-ibm-data-science-experience/#r_step3

The band will alert the user through a vibration if the parameters exceeds the reference range (which increases the chance for heat injury (such as heat cramp or heat syncope). For example, if the temperature exceeds 40 degree celsius, it will alert the user. 

The data collected from our wearable will be stored into IBM Cloudant platform.

We acknowledge that there may be cases where our device fail to predict cases of heat injury. If that were to occur, our wearable will make adjustments to the reference range such that it can better predict a possible case of heat injury. Hence, the system will improve overtime, and subsequent batches of trainees and servicemen will benefit from it.

We plan to also have a webpage to give users and officers-in-charge an interactive and visual representation of the data collected in the form of graphs and charts. Most of the data will be deleted after 30 days. It will provide a holistic view of the trainee's / servicemans' performance and risk for heat injury.

If a heat injury occurs to the frontliner, and he/she was not alerted, the Officer-in-Charge can indicate the discrepancy through the webpage. The data will then be used to calibrate the reference range using Watson Studio IoT platform's rule action.



# Getting started (step-by-step solution)

Prerequisites:

Run the following in the command prompt to install the necessary node on node-red:
. npm install node-red-contrib-scx-ibmiotapp
. npm install node-red-contrib-pythonshell
Run Node-red and deploy the code
 
How to use:

1. User will connect his operation band to Watson IoT via his internet.
2. The device will detect the different parameters required through the multiple sensors in the watch
3. The data will be analysed and uploaded onto the webpage:
https://kengkoon.com/project/santorio20
4. On the page, Users are to key in their Name and Device ID to view the data
5. Also, users can indicate any occurrence of heat exhaustion or injury to help improve the prediction by the AI.


# What did your team use to build the solution

## Watson Studio's Auto AI (XGB Classifer) 
## Watson IoT
## Node-Red



# Eintein-Bot-Check-Business-Hours POC
When customers need to be handed over from the bot to an agent, we only want to do this
inside of business hours. When outside of business hours we want to apply different logic which
allows us to create a case based on a question asked by the bot.

Inside of Salesforce we have the ability to store Business Hours. 
By using Business Hours implementation, there is no need to update or modify the bot when business hours change.
The bot will automatically adjust to what has been configured.

1. Go to Setup < Quick find < Business Hours:

![image](https://user-images.githubusercontent.com/37139091/217378766-7f30b7b0-9f8d-497e-b542-2fbc722f97ae.png)

2. Build the Business Hours Apex Class 'WithinBusinessHours'

3. In the bot, add an Action of Apex type to the dialog you wish to use the logic:

![image](https://user-images.githubusercontent.com/37139091/217380378-1c4acaea-2e0f-4840-b5fb-b499af9b0a8f.png)


![image](https://user-images.githubusercontent.com/37139091/217380415-181a4129-c216-45c9-ad99-fcbdecddb0a8.png)


The input string would be a value that you set. This input would be the name of the Business
Hours you would use.
The output is a boolean, and we have to save that to a variable of the same type. Here I created
a custom boolean variable with the same name isWithin.
After that we can use this boolean in a Rule. As we can have the boolean set to TRUE or
FALSE, we will create rules. 

a. Below, I used the 'Is Within Business Hours' in a condition in the 'Chat with live agent' dialog.

![image](https://user-images.githubusercontent.com/37139091/217397309-14060ddc-0e70-425f-8c03-584fb3537257.png)

b. If BH is true, we redirect to another dialog to check agent availability (there is another repository demonstrating the flow logic used for check agent availability - https://github.com/fernandasancho/EinsteinBot_Check_Agent_Availability_Flow/blob/main/README.md)

![image](https://user-images.githubusercontent.com/37139091/217397525-347f1e6b-0330-4c40-b04e-01ea7f49e190.png)

c. Else if BH is false, we redirect to a No agent dialog:

![image](https://user-images.githubusercontent.com/37139091/217397593-a9e77ff7-0e75-4a81-a90f-73e265114e7d.png)




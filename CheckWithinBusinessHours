/**
 * Created by FernandaS on 28/08/2022.
 *
 * To be used in Bot.
 * When customers need to be handed over from the bot to an agent, we only want to do this inside of business hours.
 * This feature allow us to check agent availability before transferring to agent.
 * This Apex class get the business hours entry we need based on the 'name'. This name will be provided by the bot.
 * 
 */


public class CheckWithinBusinessHours {
	@InvocableMethod(label = 'Within Business Hours Check')
	public static List<Boolean> makeGetCallout(List<String> Name) {
        
String BHName= String.valueOf(+Name[0]);
        
// Get Business hours based on name, input from bot
BusinessHours bh = [SELECT Id FROM BusinessHours WHERE name= :BHName];
        
// Create Datetime with current date/time in local time zone
Datetime targetTime = Datetime.now();
        
// Find whether the time is within business hours
Boolean isWithin= BusinessHours.isWithin(bh.id, targetTime);
return new List<Boolean>{isWithin};
}
	}

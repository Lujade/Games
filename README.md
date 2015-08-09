# Games
UnityGames

using UnityEngine;
using UnityEngine.UI;
using System.Collections;

public class TextController : MonoBehaviour {

	public 			Text text;
	private enum 	States {Title, Drifting, Scan, Scan2, Crash, Land, EnterCave, PassCave, Fight, Wounded, Wreckage, GoodEnd, NormEnd};
	private 		States mystate;
	
	// Use this for initialization
	void Start () {
		mystate = States.Title;					{Title();}
}
	
	// Update is called once per frame
	void Update () {
		//print (mystate);
		if 		(mystate == States.Title)		{Title();}
		else if (mystate == States.Land)		{Land();}
		else if (mystate == States.Drifting)	{Drifting();}
		else if (mystate == States.Scan)		{Scan();}
		else if (mystate == States.Scan2)		{Scan2();}
		else if (mystate == States.Crash)		{Crash();}
		else if (mystate == States.Land)		{Land();}
		else if (mystate == States.EnterCave)	{EnterCave();}
		else if (mystate == States.PassCave)	{PassCave();}
		else if (mystate == States.Fight)		{Fight();}
		else if (mystate == States.Wounded)		{Wounded();}
		else if (mystate == States.Wreckage)	{Wreckage();}
		else if (mystate == States.GoodEnd)		{GoodEnd();}
		else if (mystate == States.NormEnd)		{NormEnd();}
}
#region State handler methods
	void Drifting(){
		text.text = "After weeks of drifting through deep space you finally " +
				"see something worth a second glance. A tiny planet hovering" +
				" almost motionless against a backdrop of nothingness. You " +
				"decide to land your shuttle, and scavenge any material you" +
				" can from this desolate planet... Conditions on the surface look rough.\n\n" + 
				"Press L to and land immediately.\n\nPress S to search for another" + 
				" landing zone.";
		if 		(Input.GetKeyDown (KeyCode.S))			{mystate = States.Scan;}
		else if (Input.GetKeyDown (KeyCode.L))			{mystate = States.Crash;}
}


	void Crash(){
		text.text = "You attempt to land the shuttle. The landing quickly becomes dangerous as "+
					"surface conditions are too rough. The shuttle destabilises and crashes " + 
					"to the ground. The shuttle and it contents are incenirated on impact. Game Over" +
					"\n\nPress Space to try again.";
		if 		(Input.GetKeyDown (KeyCode.Space))		{mystate = States.Title;}
}

	void Title(){
			text.text = "\n\n\n\n\n\nYou're alone out there...\n\nPress Spacebar to begin.";
		if 		(Input.GetKeyDown (KeyCode.Space))		{mystate = States.Drifting;}
}
		
	void Scan(){
		text.text = "You scan a potential landing zone. Looks safe. Press down to Land, Up to scan another zone.";
		if 		(Input.GetKeyDown (KeyCode.DownArrow))	{mystate = States.Land;}
		else if (Input.GetKeyDown (KeyCode.UpArrow))	{mystate = States.Scan2;}
}
	
	void Scan2(){
		text.text = "You scan another potential landing zone. Looks safe. Press down to Land, Up to scan another zone.";
		if 		(Input.GetKeyDown (KeyCode.DownArrow))	{mystate = States.Land;}
		else if (Input.GetKeyDown (KeyCode.UpArrow))	{mystate = States.Scan;}
}
	
	void Land(){
		text.text = "You succesfully land the shuttle. You step outside and begin your exploration. "+
					"A glimmer of light catches your attention, It looks like some one has crash landed "+
					"here before and the light is dancing off the debris. You decide to take a look." +
					" While approaching the wreck, you discover a trail leading to a suspicious cave." + 
					"\n\nPress E to enter or C to continue.";					
		if 		(Input.GetKeyDown (KeyCode.E))			{mystate = States.EnterCave;}
		else if (Input.GetKeyDown (KeyCode.C))			{mystate = States.PassCave;}
}
	
	void PassCave(){
		text.text = "As you stroll onwards to the wreckegae with your swagger in tact, you come " +
					"to realise something is following you, something big, its breathing down your " +
					"neck, and its prints are coming from the cave..." +
					"\n\nPress F to stand and fight, Press R to run";
		if 		(Input.GetKeyDown (KeyCode.F))			{mystate = States.Fight;}
		else if (Input.GetKeyDown (KeyCode.R))			{mystate = States.Wounded;}
}
	
	void Wounded(){
		text.text = "You make the first move, dashing forward in a bound of speed you create space " +
					"enough to glance back at this 'thing'. You your eyes lock with what can only be described " +
					"as the creatures eyes, and in that instant it strikes, tearing your suit... " +
					"You've paused too long, and have narrowly missed a fatal blow. You run away but the suits tear " +
					"means you only have enough oxygen to get you back to the shuttle. Adventure Over..." +
					"\n\nPress Space to try again.";
		if 		(Input.GetKeyDown (KeyCode.Space))		{mystate = States.Title;}
}
	
	void Fight(){
		text.text = "Your instincts tell you that there is no escape, you spin on you toes lashing out with a " +
					"huge spinning kick. It's too late to aim but your body seems to have taken things into its " +
					"own hands. The kick finds it mark critically striking the creature in what appears to be its " + 
					"neck. Looks like your safe for now, although on a second glance your suit has been torn." +
					"The suit tear means you only have enough oxygen to get you back to the shuttle. Adventure Over..." +
					"\n\nPress Space to try again.";
		if  	(Input.GetKeyDown (KeyCode.Space))		{mystate = States.Title;}
}
	void EnterCave(){
		text.text = "You enter the cave and notice some interesting prints on teh floor. You realise your not the only living thing " +
					"on this rock. You proceed with caution through the mouth of the cave until suddenly you stop. There are remains " +
					" in this cave, and they're not human. A savage creature emerges from the depths of the cave, eyes fixated on you." +
					"You know you'll need to fight and look around for anything usuable. All you can see is a rock, about the size of a " +
					"fist so you grab it off the ground just as the creature lets loose a wild strike which passes over your head. " +
					"You feel the gust of the blow send chill over your whole body. Gripping the rock tight you lunge forward " +
					"slamming your shoulder into the creature's midrif. Its enough to take the fight to the ground and as you once again " +
					"lock eyes, you know what to do. You slam the rock straight into the creatures head, its arms mindless flailing as " +
					"you crunch down time and time again, until its mindless flailing ceases. As you assess the damage to your suit " +
					"you notice you have come out of this unscathed. With nothing left to see here you proceed to the wreckage." + 
					"\n\nPress P to proceed to the wreckage";
		if 		(Input.GetKeyDown (KeyCode.P))			{mystate = States.Wreckage;}	
}
	
	void Wreckage(){
		text.text = "You reach the wreckage. Its hull is torn right open so you step inside the small vessell. Lights are still flashing on " +
					"the instruments. It looks like there is still power running through the systems. As you turn to inspect the cockpit " +
					"You see that its still occupied. A human sits motionless still strapped into the seat. You must help." + 
					"\n\nPress M to search for a Med Kit, Press C to try to carry the pilot back to your ship.";
		if 		(Input.GetKeyDown (KeyCode.M))	{mystate = States.GoodEnd;}
		else if (Input.GetKeyDown (KeyCode.C))	{mystate = States.NormEnd;}
}
	
	void GoodEnd(){
		text.text = "You urgently scour the vessell for a med kit, frantically upturning everything you can lay yours hands on until... 'There " +
					"it is...' you here yourself mutter aloud. You pry it open, looking for the adrenaline shot. Its there. You drill the shot " +
					"deep into the Pilots chest and squeeze. The Pilot insantly sputters and gasps. As they come too you assure them that things will be " +
					"ok. The pilots kind eyes swallow the entire vessell with gratitude, it feels like you are teh only people in the universe. As you " +
					"help the Pilot up, they lead you to the engine room and detach the fuel cells. 'We'll be needing these' the pilot whispers, " +
					"as you nod your head soaking in the events of the day. You return to your ship satisfied.\n\nMission Success" +
					"\n\nPress Space to play again.";
		if 		(Input.GetKeyDown (KeyCode.Space))	{mystate = States.Title;}
}	
	void NormEnd(){
		text.text = "You run to the pilot rapildly unhooking them from their seat. As you gently sling the pilot over your shoulder " +
					"you can't help but think that you've forgotten something. The urgency of the situation spurs you to gather your " +
					"stength as you sprint towards your ship. As you enter, you lay the pilot down and adminster first aid through the on board " +
					"autoclinic. As the pilot comes round you let them know that everything will be ok and you'll get them home. " + 
					"As you embark on your new journey you take a look at your fuel cells and realise that they'll get you home, but you'll need " +
					" to shell out for some new cells once you land. 'They ain't gettin any cheaper' you mumble, but at least your alive..." +
					"\n\nMission Success" +
					"\n\nPress Space to play again.";
		if 		(Input.GetKeyDown (KeyCode.Space))		{mystate = States.Title;}
}
#endregion
}

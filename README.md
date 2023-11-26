# Snake

//Write a program that creates a 32 by 24 SnakeUserInterface, which has the following features:

//Clicking on a square will place a piece of wall on that square, by using the method ui.place(x, y, ui.WALL).
//Pressing the c erase all walls, by using the method ui.clear().
//The program should print the name and data of all events that occur.
//我自己写的

import java.util.Scanner;

import ui.Event;
import ui.SnakeUserInterface;
import ui.UserInterfaceFactory;

public class Events {
	SnakeUserInterface ui;
	
	Events(){
		ui = UserInterfaceFactory.getSnakeUI(32, 24);
	}
	
	void processEvent(Event event) {
		if(event.name.equals("click")) {
			Scanner dataScanner = new Scanner(event.data);
			ui.place(dataScanner.nextInt(), dataScanner.nextInt(), ui.WALL);
		} else if(event.data.equals("c")) {
			ui.clear();
		}
		ui.showChanges();
		ui.printf("%s - %s\n", event.name, event.data);
	}
	
	void start() {
		while(true) {
			Event event = ui.getEvent();
			processEvent(event);
		}
	}
	
	public static void main(String[]args){
		new Events().start();
	}
}

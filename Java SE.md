##### environment setup
1. Download JDK <http://jdk.java.net/> 
2. Setup JAVA_HOME variable <C:\Program Files\jdk-14.0.1> </Libaray/Java/JavaVirtualMachines>
3. Update PATH variable <C:\Program Files\jdk-14.0.1\bin>
4. Verify correct installation
5. IDE <http://jetbrains.com/idea/download>

##### primitive data type

integer: byte/short/int/long
float point: float/double
character: char
boolean: boolean

##### syntax
1. logic operation/ condition operation
```
if(rooms != 0 & students/rooms > 30)
if(rooms != 0 && students/rooms > 30)
```
2. for each loop
```
for(loop-variable : array)
for(float currentVal : Vals)
```
3. intern() method
```
String s1 = "I LOVE JAVA";
String s2 = "I LOVE JAVA";
System.out.println(s1 == s2);//true
System.out.println(s1.equals(s2));//true
String s3 = s1.intern();
String s4 = s2.intern();
System.out.println(s3 == s4);//true
```
```
String s1 = "I ";
s1 += "LOVE JAVA";
String s2 = "I LOVE JAVA";
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
String s3 = s1.intern();
String s4 = s2.intern();
System.out.println(s3 == s4);
```
4. scanner
```
Scanner scanner = new Scanner(System.in);
String userinput = scanner.nextLine();
String[] parts = userinput.split(" ");
```
5. StringBuilder sb = new StringBuilder(40)

6. Instant i = Instant.now();

7. Chain constructor //first line
```
public class Passenger{
  public Passenger(int freeBags) {
    this.freeBags = freeBags;
  }
  public Passenger(int freeBags, int checkedBags) {
    this(freeBags);
    this.checkedBags = checkedBags;
  }
}
```
8. Initialization blocks/ static Initializers

9. static imports

10. variable length array
```
  public static void main(String[] args) {
          testMethod("x", "b");

    }

	static void testMethod(String... list)
    {
        System.out.println(list[2]);
        System.out.println(list.length);
    }
```
11. Derived class inheri from base class using extends keyword

12. instanceof
```
if(o instanceof CargoFlight) {...}
```
-------------------------------------
13. super keyword

14. final keyword 
prevent class extending
prevent method overriding

15. abstract
require inheritance to use class
require derived class to override one or more methods

16. inheritance and constructors
```
public class CargoFlight extends Flight {
	public CargoFlight(int flightNumber){
		super(flightNumber)
	}
}
```

17.enum
```
public enum FlightCrewJob{
	FLIGHT_ATTENDANT,
	COPILOT,
	PILOT
}
FlightCrewJob job1 = FlightCrewJob.PILOT;
```
```
public enum FlightCrewJob{
	FLIGHT_ATTENDANT("Flight Attendant"),
	COPILOT("First Officer"),
	PILOT("Captain");
	
	private String title;
	public String getTitle() {return title;}
	private FlightCrewJob(String title) {
		this.title = title;
	}
}
```

18. interface
```
class Passenger implements Comparable {
	public int compareTo(Object o) {
		Passenger p = (Passenger) o;
		int returnValue = p.memberLevel - memberLevel;
		if(returnValue == 0)
			returnValue = p.memberDays - memberDays;
		return returnValue;
	}
}
```

19. Generic interface
```
class Passenger implements Comparable<Passenger> {
	public int compareTo(Passenger p) {
		//Passenger p = (Passenger) o;
		int returnValue = p.memberLevel - memberLevel;
		if(returnValue == 0)
			returnValue = p.memberDays - memberDays;
		return returnValue;
	}
}
```

20. multiple interface
```
public class Flight implements Comparable<Flight>, Iterable<Passenger> {
	private ArrayList<Passenger> passengerList = new ArrayList<>();
	public int compareTo(Flight flight){...}
	public Iterator<Passenger> iterator(){
		return passengerList.iterator();
	}
}
//main
Flight f175 = new Flight(175);
f175.add1Passenger();
for(Passenger p : f175)
	System.out.println(p.getName());
```

21. default method in interface
```
public interface MathProcessing {
	default String getFormattedOutput(){
		return null;
	}
}
```

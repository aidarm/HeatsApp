# Chapter 3. System architecture

###3.1. Building infrastructure
The building must communicate via the electrical wiring and this service is outsourced. In the building we will have two types of devices, which will be installed at every room to allow each room to operate as an autonomous unit:

1.	Sensor devices:
	* Beacon for the indoor positioning system
	* A heat sensor

Beacon is a small Bluetooth transmitter, which provides location-based information. There are many of them placed in different parts of the building.

2.	Actuators:
	* Heat actuator

Actuator is the connecting device between the software and the physical world. For example, the heat actuator will be on/off and set temperature switch.

![](http://users.metropolia.fi/~aidarm/software_engineering/actuator.png)


###3.2. Architecture overview

#####3.2.1. Database

The database will be updated from the sensors.

* The  end user gets validation of him/her being a student/staff member = Metropolia account owner from collaboration with Metropolia database. 
* Another database should be set up to take attendance of account owners. So when an account owner is in school and logged in a variable with a cache time saves a value of true to _AT SCHOOL_ and the user location in school.
* The database will register the current heat of every room as a cache time variable.  

#####3.2.2. Control policies

In the past there has been a lot of research for intelligent building. In our project the goal is not only to save energy but also maintain a high customer satisfaction. In order to do that we create 3 different time sets which define the control policies for our school heating:

1.	`Schedule time` — the time where lessons are being held. The time when school is at full or close to full capacity for realization: 07:00 - 19:00
2.	`Active time` — the time in which the school is active but no lessons are being held  for realization: weekdays 19:00 - 21:00, Saturday
3.	`Non active time` — time which in the building is not active: weekdays 21:00 - 07:00, Sunday

For those 3 different time sets there are 3 different control policies:

1.	`Heating  on` heats all rooms in campus to 22 c static
2.	`Heating saver` heats all room in the building to 16 c
3.	`Dynamic` will enable timer based on or timer base saver according to the conditions of enabling the control policies.

|               | SCHEDULE TIME |   ACTIVE TIME    |  NON-ACTIVE TIME |
| ------------- |:-------------:|:----------------:| :----------------:|
| __CONTROL POLICY__| Heating on    | Dynamic approach |Heating saver |


###3.3. Control policies behavior protocol

The control policies are being predefined to work on different times according to table system arch section 2.

The two static timer based control policies are:
* `Heating on`
* `Heating saver`

---

`Dynamic` control policy enables one of the two static control policies for the two different actors (staff member or student). It is important to remember that switching between control policies by the dynamic control policy occurs only at active time.

__Student:__
* The system is automatically heating one lab for the students as a default value.
* Every certain time the value gets updated (cache variable).
* If number of users in a specific class is bigger than half of computers in this class, then the system will enable `Heating on` control policy.
* In the same manner if any other class but the default class during active times is being heated and there are no students in the class the system will enable `Heating saver` control policy.

__Staff member (territory owner):__
* Can log in to the system and remotely heat up his/her office (meaning enabling `Heating on` control policy).
* Once logged in and inside the school during active time the system will auto prompt *"Should I turn on the heat in your office?"* (meaning enabling of `Heating on` control policy).

#Chapter 4. Requirements

###4.1. Functional requirements

*Heat.login* — all actors enter the system, using their own unique Metropolia username and password.

*Heat.login_failure* — if username or password are typed in a wrong way, then the system informs about it.

![](http://users.metropolia.fi/~aidarm/software_engineering/1.png) 

*Heat.admin.list* — admin gets a list of all of the classrooms in the building. Filtering available by section(A or B) and level or by a single input of classroom number(searching).

*Heat.admin.getInfo* — admin gets the information about the room from the sensors — radiator status, number of people, temperature values, temperature control policy name.

*Heat.admin.radiator* — admin sets the value of radiator of the selected room to true(on) or false(off) through the actuator.

*Heat.admin.temp* - admin changes the temperature of the room. Once a new temperature is sent, the input goes into a function that communicates with the actuator of the selected room. Notice, that changing the temperature is different than changing the default temperature and the value will reset itself once control policy is automatically changed.

![](http://users.metropolia.fi/~aidarm/software_engineering/2.png)

![](http://users.metropolia.fi/~aidarm/software_engineering/3.png)

![](http://users.metropolia.fi/~aidarm/software_engineering/4.png) 

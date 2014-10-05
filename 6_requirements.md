#Chapter 4. Requirements

###4.1. Functional requirements

*Heat.login* — all actors enter the system, using their own unique Metropolia username and password.

*Heat.login_failure* — if username or password are typed in a wrong way, then the system informs about it.

![](http://users.metropolia.fi/~aidarm/software_engineering/one.png) 

*Heat.admin.list* — admin gets a list of all of the classrooms in the building. Filtering available by section(A or B) and level or by a single input of classroom number(searching).

*Heat.admin.getInfo* — admin gets the information about the room from the sensors — radiator status, number of people, temperature values, temperature control policy name.

*Heat.admin.radiator* — admin sets the value of radiator of the selected room to true(on) or false(off) through the actuator.

*Heat.admin.roomTemp* - admin changes the temperature of the room. Once a new temperature is sent, the input goes into a function that communicates with the actuator of the selected room. Notice, that changing the temperature is different than changing the default temperature and the value will reset itself once control policy is automatically changed.

![](http://users.metropolia.fi/~aidarm/software_engineering/two.png)

*Heat.admin.settings* — admin gets access to global settings, where he/she is able to define default temperature values of different control policies, and values for time sets on weekly basis.

*Heat.admin.globalTemp* — admin sets the default temperature values for each of control policies. Once the value is sent, the system will connect to all actuator devices (concerning edited policy) in the building and will send the input value to the radiator.

![](http://users.metropolia.fi/~aidarm/software_engineering/three.png)

*Heat.admin.week* — admin sets weekly operation time. There are couple of pickers that will ask the user for the weekly operating hours of a desired time set. Values will be saved to the database and operate by the time value.

![](http://users.metropolia.fi/~aidarm/software_engineering/four.png) 

---

*Heat.staff.getInfo* — after staff member has logged in, there is an informational panel to appear. It is something like a limited version of *admin.getInfo*. It shows current control policy and current temperature for the office of his/her own office.

*Heat.staff.officeTemp* — almost the same as *admin.roomTemp*. The difference is that manipulations are done by staff member and only towards his/her office.

*Heat.staff.globalTemp* — almost the same as *admin.globalTemp*. The difference is that manipulations are done by staff member and only towards his/her office. UI looks exactly the same.

*Heat.staff.week* — almost the same as *admin.week*. The difference is that manipulations are done by staff member and only towards his/her office. UI looks exactly the same.

*Heat.staff.answer* — staff member sends a value (true or false) when prompted. `Should I start heating your office?` — conditional block that is being executed if the staff member is attended at campus beyond or off his/her schedule hours and user is logged in the block is prompting the user if he/she wants to turn on the heat. Then it connects to the actuator and turns it on.

![](http://users.metropolia.fi/~aidarm/software_engineering/five.png)

---

*Heat.student.list* — if student is logged in, application will list all the heated labs in the campus and show the number of people there (according to system architecture). Student as an actor has activity only during `Active time`.


![](http://users.metropolia.fi/~aidarm/software_engineering/six.png)

###4.2. Non-functional requirements

#####Usability.

We tried to make our application as simple as possible. Using Metropolia database really helps users to start interacting with the application easily, because no registration is actually needed. The only thing needed is a smartphone to launch the application, because it is mobile. Metropolia database already stores the name and permissions of the user, defining who is a student and who is a staff memeber, which is very good. Moreover, our aim is to make graphical user interface as clear and intuitive as possible, thinking about layouts, color etc. It is important that all the actors do their tasks without any kind of hesitations or misunderstandings. We also need to provide an application with a fast response time for application loading, screen refresh etc. All functions and calculations must be optimized in order to decrease proccessing times.

We intend our application to work unstoppably and only inside the Leppävaara Metropolia campus. 

#####Reliability.

One more good moment to mention Metropolia database — it is already secured. And we are sure, that if it was down, it would be up very soon. In our case we should more be concerned about, for example, beacons reliability. It is comparatively a new piece of technology and we must consider all its depths — maintainability, conformance to architecture standards, compatibility with different platforms etc.


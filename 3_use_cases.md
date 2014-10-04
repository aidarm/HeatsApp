#Chapter 3. Use cases

###3.1. User group definitions

| USER GROUP      | DEFINITION           | DESCRIPTION  |
| ------------- |-------------| -----|
| Administrator / Admin     | The campus administrator          |   Has full access to school temperature control.|
| User / Student      | Registered user in school database     |   Comes to school on a regular basis. Has no execution authorities. |
| User / Staff member | Registered user in school database     |   Has his/her own room/office, where some temperature manipulations are possible by the user.  |

###3.2. Primary actors and use cases

| PRIMARY ACTOR        | USE CASES           |
| ------------- | ------------- |
| Admin      | <ol><li>Log in</li><li>Log out</li><li>Manipulate radiators</li><li>Analyze input from the sensors</li><li>Edit all default settings</li></ol>|
| Staff member     | <ol><li>Log in</li><li>Log out</li><li>Edit his/her own office default heat settings</li><li>Remotely turn on his/her own office heating</li><li>Answer to the apllication prompt</li></ol>      |
| Student | <ol><li>Log in</li><li>Log out</li><li>Search for available classrooms</li><li>Answer to the apllication prompt</li></ol>    |

---

 <table>
  <tr>
    <td>__USE CASE ID__</td>
    <td>1</td>
  </tr>
  <tr>
    <td>__USE CASE NAME__</td>
    <td>Edit all default settings</td>
  </tr>
  <tr>
    <td>__ACTOR__</td>
    <td>Admin</td>
  </tr>
  <tr>
    <td>__DESCRIPTION__</td>
    <td>The admin should be able to manipulate different control policies of default values</td>
  </tr>
  <tr>
    <td>__NORMAL FLOW__</td>
    <td>
     <ol>
      <li>Admin selects the protocols - control policies</li>
      <li>There is a submitiion form to appear</li>
      <li><br>
       <ul>
        <li>Input the default temperature</li>
        <li>Input the weekly active time</li>
       </ul>
      </li>
      <li>Submit changes</li>
      <li>Confirmation request from the server</li>
      <li>System stores new default values</li>
      <li>Edit all default settings</li>
     </ol>
    </td>
  </tr>
  <tr>
    <td>__EXCEPTIONS__</td>
    <td>No connection to database</td>
  </tr>
  <tr>
    <td>__SPECIAL REQUIREMENTS__</td>
    <td>Admin can reset all the values</td>
  </tr>
</table> 

---

 <table>
  <tr>
    <td>__USE CASE ID__</td>
    <td>2</td>
  </tr>
  <tr>
    <td>__USE CASE NAME__</td>
    <td>Manipulate radiators</td>
  </tr>
  <tr>
    <td>__ACTOR__</td>
    <td>Admin</td>
  </tr>
  <tr>
    <td>__DESCRIPTION__</td>
    <td>The radiator inside the section of the building can be turned on/off remotely through the admin control panel. Additionally, the temperature can be changed through an actuator.</td>
  </tr>
  <tr>
    <td>__NORMAL FLOW__</td>
    <td>
     <ol>
      <li>Admin selects the section</li>
      <li>A blueprint of the section appears with a submittion form</li>
      <li>Submits the form</li>
     </ol>
    </td>
  </tr>
  <tr>
    <td>__EXCEPTIONS__</td>
    <td>The system will reset to its default setting values once it is operating on a different protocol</td>
  </tr>
</table>

---

 <table>
  <tr>
    <td>__USE CASE ID__</td>
    <td>3</td>
  </tr>
  <tr>
    <td>__USE CASE NAME__</td>
    <td>Analyze input from the sensors</td>
  </tr>
  <tr>
    <td>__ACTOR__</td>
    <td>Admin</td>
  </tr>
  <tr>
    <td>__DESCRIPTION__</td>
    <td>Admin is able to read input values from heat sensor and location beacons</td>
  </tr>
  <tr>
    <td>__NORMAL FLOW__</td>
    <td>
     <ol>
      <li>Log in</li>
      <li>Admin control panle</li>
      <li>Select the campus</li>
      <li>Select the level of the campus</li>
      <li>Select class/lab/auditorium</li>
      <li>Blueprint with sensor inputs to appear</li>
     </ol>
    </td>
  </tr>
</table>

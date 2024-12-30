# Appendix H: To create and change of Root user password, Ubuntu new user creation

**Step 1:** **Steps to create Root user password:**

**Figure 32:  Steps to create Root user password**

&#x20;

·       Open terminal

&#x20;         $sudo passwd root

&#x20;         $enter dscguest password

·       It will ask for you a new password and reenter the same password when it asks for      reconfirmation.&#x20;

&#x20;    $enter new password for root

&#x20;    $re-enter password for root.

It will show updated password successfully

**Step 2: Steps to change Root user password:**

**Figure 33:  Steps to Change Root user password**

&#x20;

·       Switch to root user

&#x20;     $su root

&#x20;     $enter the existing root user password

·       To change the root password, type as

$passwd

·       It will ask for you a new password and reenter the same password when it asks for reconfirmation.     &#x20;

·       It will show updated password successfully.

**Step 3: Steps to add new user:**

**Figure 34:  Steps to add new user**

&#x20;

·       Become root user

&#x20;   $su root

·       Once you become root user , enter  " adduser username" command  in

&#x20;  $adduser diamond

·       It will ask for you a password and reenter the same password when it asks for      reconfirmation.     &#x20;

·       It will ask “Enter new value or Press enter for default”, press enter.

·       It will ask “Is the information correct”, enter ‘y’.

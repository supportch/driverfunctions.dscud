# Appendix H: To create and change of Root user password, Ubuntu new user creation

### Step 1: Steps to create Root user password

![](broken-reference)

* Open terminal \
  \
  &#x20;            _$sudo passwd root_&#x20;

&#x20;                     _$enter dscguest password_&#x20;

* It will ask for you a new password and reenter the same password when it asks for reconfirmation. \
  \
  &#x20;             _$enter new password for root_\
  \
  &#x20;             _$re-enter password for root._\

* It will show updated password successfully.

### Step 2: Steps to change Root user password

![](broken-reference)

* Switch to root user

&#x20;                       _$su root_&#x20;

&#x20;                       _$enter the existing root user password_&#x20;

* To change the root password, type as&#x20;

&#x20;                       _$passwd_&#x20;

* &#x20;It will ask for you a new password and reenter the same password when it asks for reconfirmation\

* &#x20;It will show updated password successfully.

### Step 3: Steps to add new user

![](broken-reference)

* Become root user

&#x20;                   _$su root_&#x20;

* Once you become root user , enter " adduser username" command in\
  \
  &#x20;            _$adduser diamond_\

* It will ask for you a password and re-enter the same password when it asks for reconfirmation.
* It will ask “Enter new value or Press enter for default”, press enter.&#x20;
* It will ask “Is the information correct”, enter ‘y’.

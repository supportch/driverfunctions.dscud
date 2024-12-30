# General Information

All code specific to this project, with the possible exception of kernel interrupt service routine code or operating system dependent code, will reside in a single file named saturn.c and associated header file saturn.h. Code in this file may refer to / depend on code in other existing files included in the driver package. All such dependencies must be noted in the project documentation.

In the case that interrupt functions need to be included in the kernel, or other changes need to be made to the kernel or other operating system dependent files, those changes should be explicitly indicated by the developer so that we can keep track of the specifications of these other files.

All DSCUD driver functions follow these general operating guidelines:

Upon entry, all parameters are checked for compliance to the limits defined for the board. If any parameter is invalid, an error code and error text string are returned indicating the error. Error codes are provided in dscud.h and saturn.h. New error codes and strings may be defined only by agreement with DSC engineering. If all parameters are valid, the function will execute as specified.

If the function executes correctly, the return value is DE\_NONE. Otherwise the return value is as specified by the function definition.

All functions use data structures, parameters, and parameter array pointers as defined in saturn.h.

Many functions poll status bits (ADWAIT, ADBUSY, DABUSY, TDBUSY, EEBUSY) to determine when the board has completed the operation. All such polling must include a timeout so that the function can exit in case of a hardware error without hanging the computer. All polling is on the order of 10 microseconds or less. A sufficient timeout value is 100 microseconds or anything close that can be approximated in software.

&#x20;

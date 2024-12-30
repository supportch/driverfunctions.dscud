# 3. Common Task Reference

Universal Driver provides a set of functions that cover most of the features on Diamond Systems' I/O boards. Each board contains a different set of features with different valid parameter ranges. Not all driver functions apply to all boards, so not all of the tasks described here apply to all boards. The board reference information in Chapter 9 lists each function applicable to each board, along with the relevant features and valid parameter ranges for the various functions. Below is a list of common tasks that are explained in this chapter. User interrupts are explained in Chapter 5.

### **Task Summary**

* Performing an A/D.&#x20;
* Performs A/D conversions one at a time on one channel or a range of channels.&#x20;
* Performing an A/D Scan.&#x20;
* Performs A/D conversions in groups on a range of channels.&#x20;
* Interrupt-Based A/D Sample or Scan.&#x20;
* Performs A/D conversions using interrupts for faster sampling rates.&#x20;
* Performing a D/A Conversion.&#x20;
* Performs a D/A conversion on a specific channel.&#x20;
* Performing a D/A Conversion Scan.&#x20;
* Performs a D/A conversion on multiple, specified channels.&#x20;
* Interrupt-Based D/A Conversion Scan.&#x20;
* Performs D/A conversions using interrupt-based I/O.&#x20;
* Performing Digital I/O Operations.&#x20;
* Performs bit and byte read and write operations.&#x20;
* Checking Interrupt Operation Status.&#x20;
* Checks the status of the currently-running interrupt operation.&#x20;
* Performing an A/D Autocalibration.&#x20;
* Performs an A/D auto-calibration on a selected A/D mode or all A/D modes.&#x20;
* Performing a D/A Autocalibration.&#x20;
* Performs a D/A auto-calibration.&#x20;
* A/D Calibration Verification.&#x20;
* Checks the error in A/D LSB counts after calibration.&#x20;
* D/A Calibration Verification.&#x20;
* Checks the error in D/A LSB counts after calibration.

NOTE: In the step-by-step instructions for performing each task, it is assumed that you will already be making the proper calls to dscInit(), dscInitBoard(), dscFreeBoard(), and dscFree() in your application.

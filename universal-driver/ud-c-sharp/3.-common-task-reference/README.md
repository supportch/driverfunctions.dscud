# 3. Common Task Reference

Universal Driver provides a set of functions that cover most of the features on Diamond Systems' I/O boards. Each board contains a different set of features with different valid parameter ranges. Not all driver functions apply to all boards, so not all of the tasks described here apply to all boards.

## **Task Summary**

* Performing an A/D.&#x20;
* Performs A/D conversions one at a time on one channel or a range of channels.&#x20;
* Performing an A/D Scan.&#x20;
* Performs A/D conversions in groups on a range of channels.&#x20;
* Performing a D/A Conversion.&#x20;
* Performs a D/A conversion on a specific channel.&#x20;
* Performing a D/A Conversion Scan.&#x20;
* Performs a D/A conversion on multiple, specified channels.&#x20;
* Performing Digital I/O Operations.&#x20;
* Performs bit and byte read and write operations.&#x20;
* Performing an A/D Autocalibration.&#x20;
* Performs an A/D auto-calibration on a selected A/D mode or all A/D modes.&#x20;
* Performing a D/A Autocalibration.&#x20;
* A/D Calibration Verification.&#x20;
* Checks the error in A/D LSB counts after calibration.&#x20;
* D/A Calibration Verification.&#x20;
* Checks the error in D/A LSB counts after calibration.

NOTE: In the step-by-step instructions for performing each task, it is assumed that you will already be making the proper calls to dscInit(), dscInitBoard() and dscFree() in your C# application.

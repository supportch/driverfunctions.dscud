# 3. Common Task Reference

SAMD51 provides a set of functions that cover most of the features on Jetson boards. Each board contains a different set of features with different valid parameter ranges. Not all functions apply to all boards. The board specific functions described in Chapter 8 lists each function applicable to each board, along with the relevant features and valid parameter ranges for the various functions. Below is a list of common tasks that are explained in this chapter.&#x20;

### **Task Summary**

* Performing an A/D Conversion
* Performing an A/D Scan. &#x20;
* Performing a D/A Conversion.&#x20;
* Performing Digital I/O Operations.&#x20;
* WLAN Configuration.
* Fan Control.
* LTE Configuration.
* User LED Control.
* Camera Control.
* Serial Port Configuration.
* Read and Write Operation in Flash.
* Reading Temperature.
* Reading Serial Number.
* Reading Board Type.
* Reading Firmware Revision ID.

NOTE: In the step-by-step instructions for performing each task, it is assumed that you will already be making the proper calls to [DSCSAM\_InitBoard()](../9.-samd51-apis/dscsam_initboard.md) and [DSCSAM\_FreeBoard()](../9.-samd51-apis/dscsam_freeboard.md) in your application.

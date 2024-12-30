# 6.10 Booting to Windows Welcome mode.



**1.** Open the command prompt with administrative privilege and run the following command:

**C:\Windows\System32\Sysprep\sysprep.exe /oobe /generalize /shutdown**&#x20;

This M.2 2242 drive is having the final OS. Whenever this M.2 2242 drive is booted it will boot to Windows Welcome. Hence, to continue booting to Windows Welcome follow the below steps.

**Note: Take dump of the Windows 10 by following the steps mentioned in section 6.7 Extracting WIM file. This will be the image that has to be applied to** Gemini **boards.**

2\.     Restart the board with the M.2 2242 connected. It will come to Windows Welcome. It will ask for First time boot inputs.

3\.     Now start using Windows 10 on the Gemini board.

4\.     Connect Internet to Activate the License key. For more details, refer **Appendix D**.

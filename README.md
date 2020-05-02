# findString_IBMi_ACS
IBMi ACS macro to find string on 5250 Display Session

The 5250 ACS macros 'promptSearchString.mac' and 'searchString.mac' can be used to search a string in a 5250 display session. This macro is very useful if either an IBM panel or an application program does not provide a "Find" or "Position To". 

For Example...
=================================
If you are (still) using STRSQL, locating a field on prompt screen(F4) could be troublesome if you have several fields. If you know a part of the field text, you can use this macro to search the "Select and Sequence Fields" panel and auto page-down until it finds the field with matching text. And also repeat search for next occurence.

WRKQRY is another panel that may have a use for these two macros. 

I wrote this macro when I had to eye-ball search a very very long list of module names in Work With Module List (DSPMODSRC - F14). IBM probably didn't think it was worth providing a Position To field for Work with Module List panel.


Installation Instructions:
=================================
1) Navigate to the ACS macro folder. For Windows, this would typically be "C:\Users\%username%\Documents\ibm\iAccessClient\Emulator\"
2) Save the 'promptSearchString.mac' and 'searchString.mac' in the ACS Macro folder.
3) In the ACS Emulator session, navigate to 'Edit -> Preferences -> Keyboard -> Key Assignment Tab -> Category = Macros'
4) Select 'promptSearchString.mac' and click 'Assign a Key' and press ctrl+F (or any other valid combination you prefer)
5) Similary assign ctrl+N to 'searchString.mac'
6) Click save and close the preference window

The search macros should be ready to use now


As a sample, try this:
======================
1) Follow the installation instructions.
2) Once the macros are installed, prompt for the list of fields in SYSPSTAT in STRSQL
3) While on the "Select and Sequence fields" panel, press the short-cut(Ctrl-F) key you assigned for the promptSearchString.mac.
4) The macro should display a prompt window in your emulator session
5) Type USED and hit enter
6) The "Select and Sequence fields" panel will be searched (case insensitive) for string USED and will page down until it locates the field LAST_USED_TIMESTAMP
7) Press the short-cut(Ctrl-N) key you assigned for searchString.mac and the cursor will move to the next occurence of the string USED - DAYS_USED_COUNT.


Note:
======
1) This macro has been tested on Windows Operating system but hasn't been tested in Linux or mac OS.
2) Play around with the 'pausetime' attribute in 'HAScript' element if your IBM i connection is too slow or too fast.
3) If for some reason your macro folder is different that the one mentioned above, update the macro variables related parmFile accordingly.
4) This macro could possibly be used on 3270 session as well but has not been validated.


Other Wild Uses Cases of ACS Macro + Java Class combination:
===========================================================
1) Extend application program to provide Position To capability on one or more columns
2) By detecting the application screen (using Screen Title, User, System etc) and cursor location, provide prompting assistance (using Java GUI class and by using JDBC for data fetch). 
This can be useful when modifying application screen is risky or if you never had or no longer have the source code ... If you are still stuck with 5250 display.


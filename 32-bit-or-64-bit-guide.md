<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Choosing 32-bit or 64-bit Guide

## Windows Users

Use this Microsoft Guide https://support.microsoft.com/en-nz/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64 to determine if you are on a 64-bit or 32-bit version of Windows.

* If you are on a 64-bit version of Windows, you need to check whether your EHR / PMS or it’s database is running as a 64-bit or 32-bit program, and use the same for the MedImage Server. Click the button below and follow the instructions: https://www.itechtics.com/4-ways-check-windows-program-32-bit-64-bit/
* If you are on a 32-bit version of Windows, you should always use the 32-bit MedImage Server.

Important: Once you have decided whether to use 32-bit or 64-bit, please stay with that decision for all MedImage add-ons on that server.

## EHR Specific Notes


* MedTech32 and MedTech Evolution

For MedTech Users, the process name in the Task Manager will include the word ‘ibserver‘ or ‘interbase’. It may mention the word ‘Embarcadero’ (the name of it’s developers’ company). Use the same for MedImage Server as the main Interbase process uses.

You should also connect with the 64-bit or 32-bit specific ODBC window, which corresponds with the Interbase server process.

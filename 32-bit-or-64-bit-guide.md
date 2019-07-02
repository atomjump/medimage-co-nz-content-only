


# Choosing 32-bit or 64-bit Guide

## Windows Users

Use this Microsoft Guide to determine if you are on a 64-bit or 32-bit version of Windows.

    If you are on a 64-bit version of Windows, you need to check whether your EHR / PMS or it’s database is running as a 64-bit or 32-bit program, and use the same for the MedImage Server. Click the button below and follow the instructions:
    32-bit or 64-bit program
    If you are on a 32-bit version of Windows, you should always use the 32-bit MedImage Server.

Important: Once you have decided whether to use 32-bit or 64-bit, please stay with that decision for all MedImage add-ons on that server.

## EHR Specific Notes


* MedTech32 and MedTech Evolution

For MedTech Users, the process name in the Task Manager will include the word ‘ibserver‘ or ‘interbase’. It may mention the word ‘Embarcadero’ (the name of it’s developers’ company). Use the same for MedImage Server as the main Interbase process uses.

You should also connect with the 64-bit or 32-bit specific ODBC window, which corresponds with the Interbase server process.

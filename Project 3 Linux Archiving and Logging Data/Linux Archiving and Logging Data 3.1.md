## Intent
System administrators utilize these skills to perform key tasks, including overseeing and conducting data backup and recovery, determining data retention periods and backup frequency, monitoring and troubleshooting backup and restoration processes, and ensuring security for compliance requirements.

| Archiving data | To ensure it remains available in the case of a natural disaster or cyberattack. |
| :--- |:---:|
| Scheduling backups | To ensure they’re up to date and made at the appropriate frequency. |
| Monitoring log files | To prevent and detect suspicious activity and keep systems running efficiently. |

##  Creating and Restoring Backups with tar

In this lab, I am a junior administrator at Rezifp Pharma Inc.


The company conducts clinical trials on drugs for oncology, immunology, and vaccines. In recent weeks, there have been a series of malware attacks. The company is now strengthening its backup activities.


In response to the malware attacks, your department has decided to create daily full backups of the files associated with the E-Prescription Treatment database, which is the main system for many departments.

You have been tasked with:
* Creating a name for the tar archive using the department's standard naming convention.
* Creating daily full backups of the directories and files in the ~/Documents/epscript directory.
* Printing the file permission, owner, size, date, and time for each file in the archive.
* Verifying the archive after it is written to check for errors.
* Creating a file containing the output of the tar command for later review by the SysOps team, which will check file structure, permissions, and errors.
  

![image alt](https://github.com/BryanZamora871/bryanzamora871/blob/main/Sceerenshots/Screenshot%202025-05-01%20135323.png?raw=true)

The contents read in `~/Documents/epscript/` <br>
-rw-r--r--  1   sysadmin  sysadmin  75962   Jul 16   14:16   doctor10.csv <br>
-rw-r--r--  1   sysadmin  sysadmin  75962   Jul 16   14:12   doctor1.csv <br>
-rw-r--r--  1   sysadmin  sysadmin  75962   Jul 16   14:13   doctor2.csv <br>
-rw-r--r--  1   sysadmin  sysadmin  75962   Jul 16   14:15   doctor3.csv <br>
-rw-r--r--  1   sysadmin  sysadmin  75962   Jul 16   14:15   doctor4.csv <br>

The archive filename is created using the ISO 8601 standard. `20190505epscript.tar`

In order for me to archive the file I will need use this command `tar cvvWf 20190505epscript.tar epscript/ > 20190505epscript.txt`
Syntax breakdown:
* `tar` is the name of the command.
* `c` creates the archive.
*`vv`, very verbose, or verbosity level 2, prints the full file specification for each file in the archive.
* `W `verifies the archive after writing it.
* `f` specifies the filename for our archive.
* `20190505epscript.tar`: is the archive filename that we created following the ISO 8601 guidelines.

![image alt](https://github.com/BryanZamora871/bryanzamora871/blob/main/Sceerenshots/Screenshot%202025-05-01%20141410.png?raw=true)

* I extract the patient files from the archive and saved them in the `patient_search` directory. `sudo tar xvvf 20190814epscript.tar -C patient_search/ epscript/patients`<br>
* `Syntax` breakdown:
* `xvvf` refers to the options.
* `20190814epscript.tar` is the archive name.
* `-C` saves the indicated patient directory and its files.
* `patient_search/` is the indicated directory.
* `epscript/patients` is the directory that contains the patient files.  We are extracting files from this directory in the tar archive.

  I verified that the patient files were extracted to the `patient_search directory`, then I ran `ls -l patient_search/epscript/patients`.




  

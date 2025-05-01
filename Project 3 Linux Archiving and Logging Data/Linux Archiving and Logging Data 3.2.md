## Incremental Backups with tar
Incremental backups are completed after a full backup is performed on a system, only capturing what has changed since the last incremental backup.
* Incremental backups store a list of which files have changed in a snapshot file, with the extension `.snar`.
* The snapshot is created when the admin creates the initial level-0 backup.
* Every time an incremental backup completes, a new snapshot is created that contains only files that have changed since the last full or incremental backup.

## Restoring Data with Incremental Backups

In this lab, I will continue as a junior administrator at Rezifp Pharma Inc, which has just adopted a new backup policy. <br>
I will be responsible for validating the new backup process by performing the following two tests:
* Use a backup to restore lost patient files.
* Create two new files and perform an incremental backup. <br>


I will use the following process to test the new restoration procedure:
* List and verify the existing files in the `testenvir` directory.
* Create a level 0 backup on Sunday containing the entire `testenvir` directory.
* Simulate a cyberattack by deleting the `patient` directory from the testenvir parent folder.
* Verify the `patient` directory is missing.
* Restore the missing `patient` directory from the incremental backup.
* List and verify the `patient` directory to verify the restoration was successful.
* Create two new files in the `patient` directory.
* Create an incremental backup on Monday and verify that the new `patient` files have been properly backed up.

![image alt](https://github.com/BryanZamora871/bryanzamora871/blob/main/Sceerenshots/Screenshot%202025-05-01%20150343.png?raw=true)
In my `~/Documents/epscript directory`, I created a level 0 backup of the `testenvir` directory, which contains the `doctor`, `patient`, and `treatment` directories.
I ran `tar cvvWf epscript_back_sun.tar --listed-incremental=epscript_backup.snar --level=0 testenvir` <br>
<br>
tar: testenvir: Directory is new <br>
tar: testenvir/doctor: Directory is new <br>
tar: testenvir/patient: Directory is new <br>
tar: testenvir/treatment: Directory is new <br>
tar: testenvir/treatment/backup: Directory is new <br>
drwxr-xr-x sysadmin/sysadmin 0 2020-07-14 10:14 testenvir/ <br>
drwxr-xr-x sysadmin/sysadmin 0 2020-07-14 10:14 testenvir/doctor/ <br>
drwxr-xr-x sysadmin/sysadmin 0 2020-07-14 10:14 testenvir/patient/ <br>
drwxr-xr-x sysadmin/sysadmin 0 2020-07-14 10:14 testenvir/treatment <br>


Next, I'll simulate a natural disaster or cyberattack by removing the `patient` directory. From the `~/Documents/epscript directory`, I ran `rm -r testenvir/patient/`. I verified that the `patient` directory is removed: I ran `ls -l testenvir/`

![image alt](https://github.com/BryanZamora871/bryanzamora871/blob/main/Sceerenshots/Screenshot%202025-05-01%20152501.png?raw=true)

I ran `tar xvvf epscript_back_sun.tar -R -C ~/Documents/epscript/ testenvir/patient` to restore the missing `patient` directory

Now, I'll create an incremental backup that will include ny newly created patient documents as follows
* I ran `tar cvvWf epscript_back_mon.tar` --listed-incremental=epscript_backup.snar testenvir. <br>
* ran `tar tvvf epscript_back_mon.tar` `--incremental | less`.

![image alt](https://github.com/BryanZamora871/bryanzamora871/blob/main/Sceerenshots/Screenshot%202025-05-01%20154218.png?raw=true)






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

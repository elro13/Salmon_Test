### Notes for navigation
 
 to log in:
 
 ```
 ssh etroberts@xx.genomecenter.ucdavis.edu
 ```
 once logged in navigate to users, then into own directory
 ```
 cd /share/dennislab/users
 cd etroberts
 ```
 side note: mkdir to make a new directory, exit to leave
 
 ### Useful Commands
 ```
 
 ln -s /path/to/file
 ```
 to make a soft link to a file (-s for soft, makes it so that edits made to new file dont effect original)  
 Add & to the end of a code to make it run in the background, and type fg to make it come back to the foreground  
 if you want to know what jobs you have running (background or otherwise, run command jobs)  
 control c to end a program  
 ```
 mv file location # to move a file
 mv file newname # to rename a file
 rm file # to delete file
 rmdir directory # to delete directory
 rmdir -rf directory #to override and force delete directory even if there are things inside
 cp file location # copy a file to a new location
 ```
   
 All of above would still be running in this terminal, if my computer died, so would the job  
 To rectify this you can make screens
 ```
 screen -S name_of_screen #makes a new screen
 screen -ls # which screen you have open
 screen -r #return to screen if you have exited it
 ```
 When in a screen, control a then d (no control) to exit screen but not close screen fully ("detach")  
 If you're done with a screen type exit to get rid of it  
 If you want to look at gz files you have to use zless (just like normal less but unzips)  
 
 To call files or directories with same components in name use * (wild card) which then signify the different parts. ex:
 ```
 *.trimmed.fq.gz
 SRR9495*
 ```
 #### For loops in bash
 
 ```
 for blah in blah
 do
 whatever it is you want to do
 done
 ```
 ### Slurm
 
 ```
 sbatch file #colin made test.sh as a template, this command sends job to slurm
 squeue #to see queue
 squeue -u etroberts #to see specifically jobs by me (or whomever's username you put)
 ```
 Here is what the template test.sh looks like
 ```
 #!/bin/bash
#
#SBATCH -c 1 # Number of cores
#SBATCH -N 1 # Ensure that all cores are on one machine
#SBATCH --ntasks 1 # specify how many Slurm tasks
#SBATCH -J salmon_test # job name
#SBATCH --mem 30000 # Memory pool for all cores (see also --mem-per-cpu . Note currently implemented on cabernet, probably soon)
#SBATCH --time=1-00:00:00  # expected time of completion in days-hours:minutes:seconds (default 1-day)
#SBATCH -p production # Partition to submit to--generally gc
#SBATCH --mail-type=ALL # Type of email notification- BEGIN,END,FAIL,ALL.
#SBATCH --mail-user=etroberts@ucdavis.edu # Email to which notifications will be sent.

for sample in $(cat samples_macaque.txt); do
/share/dennislab/programs/salmon-0.14.1_linux_x86_64/bin/salmon quant --validateMappings -i rheMac10_index -l U -r fastq/$sample* -o out_macaque/$sample
done

hostname #sysadmins recommend printing hostname for debugging purposes.

```


 

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
 
 

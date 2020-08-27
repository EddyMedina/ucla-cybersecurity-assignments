# Introduction to Terminal and Bash
## Step 1: Investigation Preparation
Your first task is to set up directories to prepare for your investigation.
- Begin by making a single directory titled **Lucky_Duck_Investigations**.
- Next, within this directory of **Lucky_Duck_Investigations**, create a directory for this specific investigation titled **Roulette_loss_Investigation**.
- Within **Roulette_loss_Investigation**, create the following directories:
  - **Player_Analysis** to investigate the Casino Player.
  - **Dealer_Analysis** to investigate the Dealers.
  - **Player_Dealer_Correlation** to summarize your findings of the collusion.
- Create empty files called Notes_<Directory Name> under each of those subdirectories to be used later to add in any investigation notes.
  - For example: **Notes_Player_Analysis**
```bash
sysadmin@ubuntu-vm:~/Desktop$ mkdir Lucky_Duck_Investigations
sysadmin@ubuntu-vm:~/Desktop$ cd Lucky_Duck_Investigations/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ mkdir Roulette_loss_Investigation
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ cd Roulette_loss_Investigation/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ mkdir Player_Analysis
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ mkdir Dealer_Analysis
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ mkdir Player_Dealer_Correlation
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ touch Player_Analysis/Notes_Player_Analysis.txt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ touch Dealer_Analysis/Notes_Dealer_Analysis.txt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ touch Player_Dealer_Correlation/Notes_Player_Dealer_Correlation.txt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ ls
Dealer_Analysis  Player_Analysis  Player_Dealer_Correlation
```

## Step 2: Gathering Evidence
- Your next task is to move evidence from the specific days Lucky Duck experienced heavy losses at the roulette tables.
- Navigate to the directory where you created the Lucky_Duck_Investigations directory and run the following command to setup the evidence files:
  - wget "https://tinyurl.com/setup-evidence" && chmod +x ./setup-evidence && ./setup-evidence
- After running this command your current directory should have the following subdirectories:
  - Dealer_Schedules_0310: contains the dealer schedules
  - Lucky_Duck_Investigations: contains the investigation directories and notes files you created
  - Roulette_Player_WinLoss_0310: contains the data for player wins and losses
- The Dealer_Schedules_0310 and Roulette_Player_WinLoss_0310 directories contain the win/loss player data from the roulette tables during the week of March 10th.
  - Since the losses occurred on March 10th, 12th, and 15th, move those files into the directory Player_Analysis.
  - Since the losses occurred on March 10th, 12th, and 15th, move the schedules for those days into the directory Dealer_Analysis
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ wget "https://tinyurl.com/setup-evidence" && chmod +x ./setup-evidence && ./setup-evidence
--2020-05-05 16:13:28--  https://tinyurl.com/setup-evidence
Resolving tinyurl.com (tinyurl.com)... 104.20.58.30, 104.20.57.30, 2606:4700:10::6814:391e, ...
Connecting to tinyurl.com (tinyurl.com)|104.20.58.30|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://gist.githubusercontent.com/eddimus/e57fcb9510dd18225142cb23f236da24/raw/7e647f38d7ae8e31a3315b9c391461229f888952/Setup_Evidence_Files.sh [following]
--2020-05-05 16:13:28--  https://gist.githubusercontent.com/eddimus/e57fcb9510dd18225142cb23f236da24/raw/7e647f38d7ae8e31a3315b9c391461229f888952/Setup_Evidence_Files.sh
Resolving gist.githubusercontent.com (gist.githubusercontent.com)... 151.101.196.133
Connecting to gist.githubusercontent.com (gist.githubusercontent.com)|151.101.196.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32433 (32K) [text/plain]
Saving to: ‘setup-evidence’

setup-evidence                  100%[=======================================================>]  31.67K  --.-KB/s    in 0.04s   

2020-05-05 16:13:29 (731 KB/s) - ‘setup-evidence’ saved [32433/32433]

sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ ls
Dealer_Schedules_0310  Roulette_loss_Investigation  Roulette_Player_WinLoss_0310  setup-evidence
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ cd Roulette_Player_WinLoss_0310/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_Player_WinLoss_0310$ ll
total 40
drwxr-xr-x 2 sysadmin sysadmin 4096 May  5 16:13 ./
drwxr-xr-x 5 sysadmin sysadmin 4096 May  5 16:13 ../
-rw-r--r-- 1 sysadmin sysadmin 2259 May  5 16:13 0310_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2365 May  5 16:13 0311_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2318 May  5 16:13 0312_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2366 May  5 16:13 0313_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2366 May  5 16:13 0314_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2249 May  5 16:13 0315_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2366 May  5 16:13 0316_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2366 May  5 16:13 0317_win_loss_player_data
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_Player_WinLoss_0310$ head 0310_win_loss_player_data 
Hour    	Won/Loss	Players
12:00:00 AM	,383  	Haley Hall,Heath Medina,Deniz Howarth,Nada Ferreira 
01:00:00 AM	,273	        Mcfadden Wasim, Norman Cooper, Pruitt Krishan, Wooten Zeeshan, Dunne Farrell 
02:00:00 AM	,234	        Chanelle Tapia, Shelley Dodson , Valentino Smith
03:00:00 AM	,738   	Conal Walton, Ibrahim Roy, Indiana Moyer, Nola Portillo, Nathanial Barron
04:00:00 AM	,800	        Amirah Schneider,Mylie Schmidt,Suhayb Maguire,Millicent Betts,Avi Graves,Kayan Stuart 
05:00:00 AM	-,348	Amirah Schneider,Nola Portillo, Mylie Schmidt,Suhayb Maguire,Millicent Betts,Avi Graves
06:00:00 AM	,823  	Haley Hall,Heath Medina,Deniz Howarth,Nada Ferreira 
07:00:00 AM	,628	        Mcfadden Wasim, Norman Cooper, Pruitt Krishan, Wooten Zeeshan, Dunne Farrell 
08:00:00 AM	-,383	Chanelle Tapia, Shelley Dodson , Valentino Smith, Mylie Schmidt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_Player_WinLoss_0310$ mv 0310_win_loss_player_data 0312_win_loss_player_data 0315_win_loss_player_data /home/sysadmin/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_Player_WinLoss_0310$ cd ../
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ cd Dealer_Schedules_0310/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Dealer_Schedules_0310$ ll
total 40
drwxr-xr-x 2 sysadmin sysadmin 4096 May  5 16:13 ./
drwxr-xr-x 5 sysadmin sysadmin 4096 May  5 16:13 ../
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0310_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0311_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0312_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0313_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0314_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0315_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0316_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0317_Dealer_schedule
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Dealer_Schedules_0310$ mv 0310_Dealer_schedule 0312_Dealer_schedule 0315_Dealer_schedule /home/sysadmin/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Dealer_Schedules_0310$ cd ../
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations$ cd Roulette_loss_Investigation/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cd Player_Analysis/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ ll
total 20
drwxr-xr-x 2 sysadmin sysadmin 4096 May  5 16:20 ./
drwxr-xr-x 5 sysadmin sysadmin 4096 May  5 15:36 ../
-rw-r--r-- 1 sysadmin sysadmin 2259 May  5 16:13 0310_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2318 May  5 16:13 0312_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2249 May  5 16:13 0315_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin    0 May  5 15:37 Notes_Player_Analysis.txt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ cd ../
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cd Dealer_Analysis/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ ll
total 20
drwxr-xr-x 2 sysadmin sysadmin 4096 May  5 16:21 ./
drwxr-xr-x 5 sysadmin sysadmin 4096 May  5 15:36 ../
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0310_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0312_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0315_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin    0 May  5 15:38 Notes_Dealer_Analysis.txt
```
## Step 3: Correlating the Evidence
- Your next task is to correlate the large losses from the roulette tables to the dealer schedule in order to determine the dealer and player that are likely colluding to steal money from Lucky Duck.
  - Note: Any winnings for Luck Duck Casino are indicated with a positive number and any losses are a negative number.
Complete the following tasks:
### Player Analysis
- Navigate to the Player_Analysis directory.
- Use grep to isolate all of the losses that occurred on March 10th, 12th, and 15th.
- Place those results into a file called Roulette_Losses.
- Preview your file Roulette_Losses and analyze the data.
- Then, record in the Notes_Player_Analysis file:
  - The times the losses occurred on each day.
  - If there is a certain player that was playing during each of those times.
  - The total count of times this player was playing.
    - Hint: Use the wc command for this value.
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ grep '-' *_win_loss_player_data 
0310_win_loss_player_data:05:00:00 AM	-,348	Amirah Schneider,Nola Portillo, Mylie Schmidt,Suhayb Maguire,Millicent Betts,Avi Graves
0310_win_loss_player_data:08:00:00 AM	-,383	Chanelle Tapia, Shelley Dodson , Valentino Smith, Mylie Schmidt
0310_win_loss_player_data:02:00:00 PM	-,348	Jaden Clarkson, Kaidan Sheridan, Mylie Schmidt 
0310_win_loss_player_data:08:00:00 PM	-,348        Mylie Schmidt, Trixie Velasquez, Jerome Klein ,Rahma Buckley
0310_win_loss_player_data:11:00:00 PM	-,383	Mcfadden Wasim, Norman Cooper, Mylie Schmidt
0312_win_loss_player_data:05:00:00 AM	-,300	Montana Kirk, Alysia Goodman, Halima Little, Etienne Brady, Mylie Schmidt
0312_win_loss_player_data:08:00:00 AM	-,383        Rimsha Gardiner,Fern Cleveland, Mylie Schmidt,Kobe Higgins	
0312_win_loss_player_data:02:00:00 PM	-,348        Mae Hail,  Mylie Schmidt,Ayden Beil	
0312_win_loss_player_data:08:00:00 PM	-,792        Tallulah Rawlings,Josie Dawe, Mylie Schmidt,Hakim Stott, Esther Callaghan, Ciaron Villanueva	
0312_win_loss_player_data:11:00:00 PM	-,229        Vlad Hatfield,Kerys Frazier,Mya Butler, Mylie Schmidt,Lex Oakley,Elin Wormald	
0315_win_loss_player_data:05:00:00 AM	-,844        Arjan Guzman,Sommer Mann, Mylie Schmidt	
0315_win_loss_player_data:08:00:00 AM	-,001        Lilianna Devlin,Brendan Lester, Mylie Schmidt,Blade Robertson,Derrick Schroeder	
0315_win_loss_player_data:02:00:00 PM	-,419        Mylie Schmidt, Corey Huffman
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ grep '-' *_win_loss_player_data > Roulette_Losses
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ ll
total 24
drwxr-xr-x 2 sysadmin sysadmin 4096 May  5 16:36 ./
drwxr-xr-x 5 sysadmin sysadmin 4096 May  5 15:36 ../
-rw-r--r-- 1 sysadmin sysadmin 2259 May  5 16:13 0310_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2318 May  5 16:13 0312_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin 2249 May  5 16:13 0315_win_loss_player_data
-rw-r--r-- 1 sysadmin sysadmin    0 May  5 15:37 Notes_Player_Analysis.txt
-rw-r--r-- 1 sysadmin sysadmin 1429 May  5 16:36 Roulette_Losses
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ head Roulette_Losses 
0310_win_loss_player_data:05:00:00 AM	-,348	Amirah Schneider,Nola Portillo, Mylie Schmidt,Suhayb Maguire,Millicent Betts,Avi Graves
0310_win_loss_player_data:08:00:00 AM	-,383	Chanelle Tapia, Shelley Dodson , Valentino Smith, Mylie Schmidt
0310_win_loss_player_data:02:00:00 PM	-,348	Jaden Clarkson, Kaidan Sheridan, Mylie Schmidt 
0310_win_loss_player_data:08:00:00 PM	-,348        Mylie Schmidt, Trixie Velasquez, Jerome Klein ,Rahma Buckley
0310_win_loss_player_data:11:00:00 PM	-,383	Mcfadden Wasim, Norman Cooper, Mylie Schmidt
0312_win_loss_player_data:05:00:00 AM	-,300	Montana Kirk, Alysia Goodman, Halima Little, Etienne Brady, Mylie Schmidt
0312_win_loss_player_data:08:00:00 AM	-,383        Rimsha Gardiner,Fern Cleveland, Mylie Schmidt,Kobe Higgins	
0312_win_loss_player_data:02:00:00 PM	-,348        Mae Hail,  Mylie Schmidt,Ayden Beil	
0312_win_loss_player_data:08:00:00 PM	-,792        Tallulah Rawlings,Josie Dawe, Mylie Schmidt,Hakim Stott, Esther Callaghan, Ciaron Villanueva	
0312_win_loss_player_data:11:00:00 PM	-,229        Vlad Hatfield,Kerys Frazier,Mya Butler, Mylie Schmidt,Lex Oakley,Elin Wormald	
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ awk -F' ' '{print $1}' Roulette_Losses > Notes_Player_Analysis.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ cat Notes_Player_Analysis.txt 
0310_win_loss_player_data:05:00:00
0310_win_loss_player_data:08:00:00
0310_win_loss_player_data:02:00:00
0310_win_loss_player_data:08:00:00
0310_win_loss_player_data:11:00:00
0312_win_loss_player_data:05:00:00
0312_win_loss_player_data:08:00:00
0312_win_loss_player_data:02:00:00
0312_win_loss_player_data:08:00:00
0312_win_loss_player_data:11:00:00
0315_win_loss_player_data:05:00:00
0315_win_loss_player_data:08:00:00
0315_win_loss_player_data:02:00:00
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ grep 'Mylie Schmidt' Roulette_Losses | wc -l
13
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ echo "Mylie Schmidt:" ; grep 'Mylie Schmidt' Roulette_Losses | wc -l
Mylie Schmidt:
13
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ echo "Mylie Schmidt:" ; grep 'Mylie Schmidt' Roulette_Losses | wc -l >> Notes_Player_Analysis.txt 
Mylie Schmidt:
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ echo "Mylie Schmidt" >> Notes_Player_Analysis.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Analysis$ cat Notes_Player_Analysis.txt 
0310_win_loss_player_data:05:00:00
0310_win_loss_player_data:08:00:00
0310_win_loss_player_data:02:00:00
0310_win_loss_player_data:08:00:00
0310_win_loss_player_data:11:00:00
0312_win_loss_player_data:05:00:00
0312_win_loss_player_data:08:00:00
0312_win_loss_player_data:02:00:00
0312_win_loss_player_data:08:00:00
0312_win_loss_player_data:11:00:00
0315_win_loss_player_data:05:00:00
0315_win_loss_player_data:08:00:00
0315_win_loss_player_data:02:00:00
13
Mylie Schmidt
```
### Dealer Analysis
- Navigate to the Dealer_Analysis directory.
- This file contains the dealer schedules for the various Lucky Duck casino games: Blackjack, Roulette, and Texas Hold 'Em.
- Preview the schedule to view the format and to understand how the data is separated.
- Using your findings from the player analysis, create a separate script to look at each day and each time that you determined where losses occurred. Use awk, pipes, and grep to isolate out the following four fields:
  - Time
  - AM/PM
  - First name of roulette dealer
  - Last name of roulette dealer
- For example, if there was a loss that occurred on March 10th at 2 PM, you would write one script that found the roulette dealer that was working at that specific day and time.
  - Hint: you will have many scripts, but only a small change is required for each script.
- Run all of the scripts and append those results into a file called Dealers_working_during_losses.
- Preview your file Dealers_working_during_losses and analyze the data.
- Record in the Notes_Dealer_Analysis file:
  - The primary dealer working at the times where losses occurred.
  - How many times the dealer worked when major losses occurred.
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cd Dealer_Analysis/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ head 0310_Dealer_schedule 
Hour AM/PM	BlackJack_Dealer_FNAME LAST	Roulette_Dealer_FNAME LAST	Texas_Hold_EM_dealer_FNAME LAST

12:00:00 AM	Izabela Parrish	Marlene Mcpherson	Madina Britton
01:00:00 AM	Billy Jones	Saima Mcdermott	Summer-Louise Hammond
02:00:00 AM	Summer-Louise Hammond	Abigale Rich	John-James Hayward
03:00:00 AM	John-James Hayward	Evalyn Howell	Chyna Mercado
04:00:00 AM	Chyna Mercado	Cleveland Hanna	Katey Bean
05:00:00 AM	Katey Bean	Billy Jones	Evalyn Howell
06:00:00 AM	Evalyn Howell	Saima Mcdermott	Cleveland Hanna
07:00:00 AM	Cleveland Hanna	Abigale Rich	Billy Jones
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ cd ../
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ nano dealer_analysis.sh 
```
```typescript
GNU nano 2.9.3                                                  dealer_analysis.sh                                                             

#!/bin/bash

grep -E $1.*$2 Dealer_Analysis/$3_Dealer_schedule | awk '{print $1,$2,$5,$6}' >> Dealer_Analysis/Dealers_working_during_losses 




^G Get Help     ^O Write Out    ^W Where Is     ^K Cut Text     ^J Justify      ^C Cur Pos      M-U Undo        M-A Mark Text   M-] To Bracket
^X Exit         ^R Read File    ^\ Replace      ^U Uncut Text   ^T To Linter    ^_ Go To Line   M-E Redo        M-6 Copy Text   M-W WhereIs Next
```
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ chmod u+x dealer_analysis.sh 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Player_Analysis/Notes_Player_Analysis.txt 
0310_win_loss_player_data:05:00:00 AM
0310_win_loss_player_data:08:00:00 AM
0310_win_loss_player_data:02:00:00 PM
0310_win_loss_player_data:08:00:00 PM
0310_win_loss_player_data:11:00:00 PM
0312_win_loss_player_data:05:00:00 AM
0312_win_loss_player_data:08:00:00 AM
0312_win_loss_player_data:02:00:00 PM
0312_win_loss_player_data:08:00:00 PM
0312_win_loss_player_data:11:00:00 PM
0315_win_loss_player_data:05:00:00 AM
0315_win_loss_player_data:08:00:00 AM
0315_win_loss_player_data:02:00:00 PM

13
Mylie Schmidt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 05 AM 0310
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 08 AM 0310
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 02 PM 0310
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 08 PM 0310
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 11 PM 0310
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 05 AM 0312
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 08 AM 0312
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 02 PM 0312
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 08 PM 0312
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 11 PM 0312
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 05 AM 0315
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 08 AM 0315
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh dealer_analysis.sh 02 PM 0315
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Dealer_Analysis/Dealers_working_during_losses 
05:00:00 AM Billy Jones
08:00:00 AM Billy Jones
02:00:00 PM Billy Jones
08:00:00 PM Billy Jones
11:00:00 PM Billy Jones
05:00:00 AM Billy Jones
08:00:00 AM Billy Jones
02:00:00 PM Billy Jones
08:00:00 PM Billy Jones
11:00:00 PM Billy Jones
05:00:00 AM Billy Jones
08:00:00 AM Billy Jones
02:00:00 PM Billy Jones
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ echo "Billy Jones" >> Dealer_Analysis/Notes_Dealer_Analysis.txt ; grep 'Billy Jones' Dealer_Analysis/Dealers_working_during_losses | wc -l >> Dealer_Analysis/Notes_Dealer_Analysis.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Dealer_Analysis/Notes_Dealer_Analysis.txt 

Billy Jones
13
```
### Player/Employee Correlation
- In notes file of the Player_Dealer_Correlation directory, add your summary of the player and dealer you believe are colluding to scam Lucky Duck.
- Make sure to document your specific reasons for this finding.
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cd Player_Dealer_Correlation/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Dealer_Correlation$ cat Notes_Player_Dealer_Correlation.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Player_Dealer_Correlation$ echo "Player Colluding Information:" >> Notes_Player_Dealer_Correlation.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Player_Analysis/Notes_Player_Analysis.txt >> Player_Dealer_Correlation/Notes_Player_Dealer_Correlation.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Dealer_Analysis/Notes_Dealer_Analysis.txt >> Player_Dealer_Correlation/Notes_Player_Dealer_Correlation.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ echo "Proof that Dealer was involved" >> Player_Dealer_Correlation/Notes_Player_Dealer_Correlation.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Dealer_Analysis/Dealers_working_during_losses >> Player_Dealer_Correlation/Notes_Player_Dealer_Correlation.txt 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Player_Dealer_Correlation/Notes_Player_Dealer_Correlation.txt 
Player Colluding Information:
0310_win_loss_player_data:05:00:00 AM
0310_win_loss_player_data:08:00:00 AM
0310_win_loss_player_data:02:00:00 PM
0310_win_loss_player_data:08:00:00 PM
0310_win_loss_player_data:11:00:00 PM
0312_win_loss_player_data:05:00:00 AM
0312_win_loss_player_data:08:00:00 AM
0312_win_loss_player_data:02:00:00 PM
0312_win_loss_player_data:08:00:00 PM
0312_win_loss_player_data:11:00:00 PM
0315_win_loss_player_data:05:00:00 AM
0315_win_loss_player_data:08:00:00 AM
0315_win_loss_player_data:02:00:00 PM

13
Mylie Schmidt
Dealer Involved in Every Loss and Total Count:

Billy Jones
13
Proof that Dealer was involved
05:00:00 AM Billy Jones
08:00:00 AM Billy Jones
02:00:00 PM Billy Jones
08:00:00 PM Billy Jones
11:00:00 PM Billy Jones
05:00:00 AM Billy Jones
08:00:00 AM Billy Jones
02:00:00 PM Billy Jones
08:00:00 PM Billy Jones
11:00:00 PM Billy Jones
05:00:00 AM Billy Jones
08:00:00 AM Billy Jones
02:00:00 PM Billy Jones
```
### Step 4: Scripting your Tasks
You manager is impressed with the work you have done so far on the investigation.
- Your manager has tasked you with building a shell script that can easily analyze future employee schedules. Therefore, we can determine who was the employee working at a specific time in case losses occur again.
- This shell script can be provided to the security department to easily do the same analysis.
Complete the following tasks:
- Remain in the Dealer_Analysis directory.
- Develop a shell script called roulette_dealer_finder_by_time.sh that can analyze the employee schedule to easily find the roulette dealer at a specific time.
  - Hint: You will be using a script similar to the one you created for the "Dealer Analysis" step, except do not output the results into a file.
- Design the shell script to accept the following two arguments:
  - One for the date (four digits)
  - One for the time
Note: The argument should be able to accept AM or PM.
- Test your script on the schedules to confirm it outputs the correct dealer at the time specified.
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cd Dealer_Analysis/
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ ll
total 28
drwxr-xr-x 2 sysadmin sysadmin 4096 May  6 14:01 ./
drwxr-xr-x 5 sysadmin sysadmin 4096 May  6 13:50 ../
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0310_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0312_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin 1489 May  5 16:13 0315_Dealer_schedule
-rw-r--r-- 1 sysadmin sysadmin  312 May  6 13:57 Dealers_working_during_losses
-rw-r--r-- 1 sysadmin sysadmin   16 May  6 14:01 Notes_Dealer_Analysis.txt
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ touch roulette_dealer_finder_by_time.sh
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ awk '{print $1,$2,$5,$6}' 0310_Dealer_schedule | sed s/':00:00 '// | grep '12AM'
12AM Marlene Mcpherson
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ nano roulette_dealer_finder_by_time.sh 
```
```typescript
GNU nano 2.9.3                                           roulette_dealer_finder_by_time.sh                                                     

#!/bin/bash

awk '{print $1,$2,$5,$6}' $1_Dealer_schedule | sed s/':00:00 '// | grep $2


                                                                [ Read 4 lines ]
^G Get Help     ^O Write Out    ^W Where Is     ^K Cut Text     ^J Justify      ^C Cur Pos      M-U Undo        M-A Mark Text   M-] To Bracket
^X Exit         ^R Read File    ^\ Replace      ^U Uncut Text   ^T To Linter    ^_ Go To Line   M-E Redo        M-6 Copy Text   M-W WhereIs Next
```
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ chmod u+x roulette_dealer_finder_by_time.sh 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation/Dealer_Analysis$ sh roulette_dealer_finder_by_time.sh 0310 05AM
05AM Billy Jones
```
Bonus:  In case there is future fraud on the other Lucky Duck Games, create a shell script called roulette_dealer_finder_by_time_and_game.sh that has the three following arguments:
- One for the the specific time
- One for the specific date
- One for the casino game being played
Hint: The argument does not need to name the specific casino game.
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ touch roulette_dealer_finder_by_time_and_game.sh
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ nano roulette_dealer_finder_by_time_and_game.sh 
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ chmod u+x roulette_dealer_finder_by_time_and_game.sh
```
```typescript
GNU nano 2.9.3                                      roulette_dealer_finder_by_time_and_game.sh                                                 

#!/bin/bash
# For argument $3, 2 = Blackjack dealers, 3 = Roulette Dealers, and 4 = Texas dealers.

cut -f 1,$3 Dealer_Analysis/$1_Dealer_schedule  | sed s/':00:00 '// | grep $2

                                                                [ Read 5 lines ]
^G Get Help     ^O Write Out    ^W Where Is     ^K Cut Text     ^J Justify      ^C Cur Pos      M-U Undo        M-A Mark Text   M-] To Bracket
^X Exit         ^R Read File    ^\ Replace      ^U Uncut Text   ^T To Linter    ^_ Go To Line   M-E Redo        M-6 Copy Text   M-W WhereIs Next
```
```bash
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ cat Dealer_Analysis/0310_Dealer_schedule 
Hour AM/PM	BlackJack_Dealer_FNAME LAST	Roulette_Dealer_FNAME LAST	Texas_Hold_EM_dealer_FNAME LAST

12:00:00 AM	Izabela Parrish	Marlene Mcpherson	Madina Britton
01:00:00 AM	Billy Jones	Saima Mcdermott	Summer-Louise Hammond
02:00:00 AM	Summer-Louise Hammond	Abigale Rich	John-James Hayward
03:00:00 AM	John-James Hayward	Evalyn Howell	Chyna Mercado
04:00:00 AM	Chyna Mercado	Cleveland Hanna	Katey Bean
05:00:00 AM	Katey Bean	Billy Jones	Evalyn Howell
06:00:00 AM	Evalyn Howell	Saima Mcdermott	Cleveland Hanna
07:00:00 AM	Cleveland Hanna	Abigale Rich	Billy Jones
08:00:00 AM	Rahima Figueroa	Billy Jones	Madina Britton
09:00:00 AM	Marlene Mcpherson	Cleveland Hanna	Summer-Louise Hammond
10:00:00 AM	Izabela Parrish	Madina Britton	John-James Hayward
11:00:00 AM	Madina Britton	Summer-Louise Hammond	Chyna Mercado
12:00:00 PM	Summer-Louise Hammond	John-James Hayward	Katey Bean
01:00:00 PM	John-James Hayward	Chyna Mercado	Evalyn Howell
02:00:00 PM	Chyna Mercado	Billy Jones	Cleveland Hanna
03:00:00 PM	Katey Bean	Evalyn Howell	Rahima Figueroa
04:00:00 PM	Evalyn Howell	Cleveland Hanna	Billy Jones
05:00:00 PM	Billy Jones	Rahima Figueroa	Summer-Louise Hammond
06:00:00 PM	Rahima Figueroa	John-James Hayward	John-James Hayward
07:00:00 PM	Marlene Mcpherson	Chyna Mercado	Chyna Mercado
08:00:00 PM	Saima Mcdermott	Billy Jones	Katey Bean
09:00:00 PM	Abigale Rich	Evalyn Howell	Billy Jones
10:00:00 PM	Evalyn Howell	Katey Bean	Cleveland Hanna
11:00:00 PM	Cleveland Hanna	Billy Jones	Rahima Figueroa
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh roulette_dealer_finder_by_time_and_game.sh 0310 05AM 3
05AM	Billy Jones
sysadmin@ubuntu-vm:~/Desktop/Lucky_Duck_Investigations/Roulette_loss_Investigation$ sh roulette_dealer_finder_by_time_and_game.sh 0310 05AM 4
05AM	Evalyn Howell
```

ubuntu@ip-172-31-14-140:~$ touch notes.txt
ubuntu@ip-172-31-14-140:~$ echo "i have Line 1" > notes.txt
ubuntu@ip-172-31-14-140:~$ echo "i have Line 2" > notes.txt
ubuntu@ip-172-31-14-140:~$ echo "i have Line 3" | tee -a notes.txt
i have Line 3
ubuntu@ip-172-31-14-140:~$ echo "i have Line 3" | tee -a notes.txt
i have Line 3
ubuntu@ip-172-31-14-140:~$ cat notes.txt
i have Line 2
i have Line 3
i have Line 3
ubuntu@ip-172-31-14-140:~$ head -n 2 notes.txt
i have Line 2
i have Line 3
ubuntu@ip-172-31-14-140:~$ tail -n 2 notes.txt
i have Line 3
i have Line 3
ubuntu@ip-172-31-14-140:~$
Broadcast message from root@ip-172-31-14-140 (Fri 2026-03-27 11:33:46 UTC):

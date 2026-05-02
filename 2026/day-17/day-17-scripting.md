day-17-scripting.md
What I Learned
Used for loops to iterate over lists and number ranges
Used while loops for countdown logic with user input
Handled command-line arguments using 1,#, $@, $0
Added usage messages for missing arguments
Took user input using read
Automated package installation (nginx, curl, wget)
Checked package status using dpkg -s
Added root user validation using $EUID
Implemented error handling with set -e and ||
Created safe scripts to avoid failures and overwrites
Issue Faced & Lesson Learned: Used commas in a Bash array, causing the loop to fail, Learned that Bash arrays must be space-separated, not comma-separated

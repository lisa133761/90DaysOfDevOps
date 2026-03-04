Linux Commands Cheat Sheet

1. Process Management (Monitoring & Control)

      top: Displays real-time system resource usage and all running processes.
      htop: An interactive, color-coded process viewer (more user-friendly than top).
      ps aux: Lists every running process on the system with detailed owner information.
      kill <PID>: Sends a signal (default SIGTERM) to stop a process using its ID.
      killall <name>: Kills all processes matching a specific name (e.g., killall nginx).
      bg / fg: Sends a process to the background or brings a background process to the foreground.
      nohup <command> &: Runs a command that will keep running even after you log out.
      nice: Starts a new process with a specific priority (niceness).

2. File System (Navigation & Manipulation)

   ls -lah: Lists files with human-readable sizes, including hidden files.
   pwd: Prints the full path of the current working directory.
  mkdir -p <path>: Creates a directory and any necessary parent directories.
  du -sh: Shows the total disk usage of a specific directory in a readable format.
  df -h: Displays available disk space on all mounted file systems.
  find / -name <file>: Searches for a file by name starting from the root directory.
  grep -r "text" .: Recursively searches for a specific string within all files in a folder.
  chmod 755 <file>: Changes file permissions (Owner: Read/Write/Execute, Group/Others: Read/Execute).
  chown user:group <file>: Changes the owner and group of a file or directory.

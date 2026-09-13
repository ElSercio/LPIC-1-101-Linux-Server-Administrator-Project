# LPIC-1-101-Linux-Server-Administrator-Project
This project demonstrates the skills obtained from a preparation course to achive LPIC-1Certification. The server was created using Azure and ubuntu server 24-04.

Phase 1 (view connect-to-vm.png)
- Launched the Virtual Machine on Azure and established a remote connection using the command "ssh -i" from my personal laptop.
- Created a file named "hardware_info.txt" using the commands lspcu, free and fdisk and pipes in order to obtain CPU, RAM and Storage information.

Phase 2
- In this project is being used an Ubuntu Server, so there is no need to have a graphical.target unit as the default target.
- Therefore I changed the default target from graphical.target to multi-user.target with the command "systemctl set-default multi-user.target
- In addition, I setup a password for the user sagsadmin with the command sudo passwd sagsadmin.
  
Phase 3
- Created a directory structure ("system-records/") with subdirectories for logs, config and backups using brace expansion in a single command: mkdir -p system-records/{logs,backups,config}.
- Simulated a web server access log (access.log) and used grep with an extended regex ([45][[:digit:]][[:digit:]]$) to filter only lines containing HTTP error codes (4xx/5xx), anchoring the pattern to the end of the line to avoid false matches elsewhere in the text.
- Built a pipeline to count and rank client IPs by request frequency: cut -d" " -f1 access.log | sort | uniq -c | sort -rn. Sorting before uniq -c is required since uniq only collapses adjacent duplicate lines; the final sort -rn (numeric, descending) ensures correct ranking regardless of digit count.
- Practiced basic file editing with vi: navigation (h/j/k/l), switching between Normal and Insert mode, inserting a new line below the cursor (o), and saving/discarding changes (:wq vs :q!).

Phase 4
- Launched a background process (yes > /dev/null &) to simulate sustained CPU load, and monitored it in real time with top, confirming ~100% CPU usage under the process owner's account.
- Practiced process control signals with kill -s: STOP to suspend the process, CONT to resume it, TERM for a graceful termination request, and KILL to force termination immediately when a process cannot be    trusted to respond to TERM.
- Verified parent-child process relationships using ps -f, confirming the background job's PPID matched the current shell's PID.
- Started a new process with a lowered scheduling priority from launch using nice -n 15, and confirmed the assigned niceness value with ps -o pid,ni,cmd.

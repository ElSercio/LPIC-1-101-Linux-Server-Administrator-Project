# LPIC-1-101-Linux-Server-Administrator-Project
This project demonstrates the skills obtained from a preparation course to achieve LPIC-1Certification. The server was created using Azure and ubuntu server 24-04.

Phase 1 (view connect-to-vm.png and hardware-info-file.png)
- Launched the Virtual Machine on Azure and established a remote connection using the command "ssh -i" from my personal laptop.
- Created a file named "hardware_info.txt" using the commands lscpu, free and fdisk and pipes in order to obtain CPU, RAM and Storage information.

Phase 2 (view settingup-default-target.png)
- In this project is being used an Ubuntu Server, so there is no need to have a graphical.target unit as the default target.
- Therefore I changed the default target from graphical.target to multi-user.target with the command "systemctl set-default multi-user.target".
- In addition, I setup a password for the user sagsadmin with the command sudo passwd sagsadmin.
  
Phase 3 (view filter-HTTP-errorcodes.png and count-ips-pipeline.png)
- Created a directory structure ("system-records/") with subdirectories for logs, config and backups using brace expansion in a single command: mkdir -p system-records/{logs,backups,config}.
- Simulated a web server access log (access.log) and used grep with an extended regex ([45][[:digit:]][[:digit:]]$) to filter only lines containing HTTP error codes (4xx/5xx), anchoring the pattern to the end of the line to avoid false matches elsewhere in the text.
- Built a pipeline to count and rank client IPs by request frequency: cut -d" " -f1 access.log | sort | uniq -c | sort -rn. Sorting before uniq -c is required since uniq only collapses adjacent duplicate lines; the final sort -rn (numeric, descending) ensures correct ranking regardless of digit count.
- Practiced basic file editing with vi: navigation (h/j/k/l), switching between Normal and Insert mode, inserting a new line below the cursor (o), and saving/discarding changes (:wq vs :q!).

Phase 4
- Launched a background process (yes > /dev/null &) to simulate sustained CPU load, and monitored it in real time with top, confirming ~100% CPU usage under the process owner's account.
- Practiced process control signals with kill -s: STOP to suspend the process, CONT to resume it, TERM for a graceful termination request, and KILL to force termination immediately when a process cannot be    trusted to respond to TERM.
- Verified parent-child process relationships using ps -f, confirming the background job's PPID matched the current shell's PID.
- Started a new process with a lowered scheduling priority from launch using nice -n 15, and confirmed the assigned niceness value with ps -o pid,ni,cmd.
- Evidences:
    - ping-initiate-and-terminate.png
    - process-consuming-cpu.png
    - process-1215-stopped.png
    - process-1215-return-to-runningstate.png
    - process1215-terminated.png
 

  Phase 5
- Installed, inspected and removed a package using Debian tools: apt install, dpkg -s (package metadata) and dpkg -L (installed file locations) on the tree package, followed by apt purge and apt autoremove.
- Installed Docker Engine from the official repository and launched a Rocky Linux 9 container to practice RPM-based package management in isolation from the host system.
- Repeated the install/inspect/remove cycle inside the container using dnf install, rpm -qi (package metadata) and rpm -ql (installed file locations), then dnf remove and dnf autoremove — comparing the RPM/   dnf workflow against the Debian/apt one used earlier.
- Evidences:
    - check-package-status-on-redhat-based.png
    - create-docker-container-redhat-based.png
    - dpkg-help.png
    - dpkg-list-files-installed-by-tree-packet.png
    - dpkg-status.png
    - install-ncurses-package-on-docker-running-rockylinux9.png
    - install-with-apt.png
    - uninstall-tree-and-dependencies.png


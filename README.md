# WhoAmICTFWriteUP

 # Introduction

This report documents the steps taken to complete the "WhoAmI: The Computer Ghost Hunt" Capture The Flag (CTF) challenge. The objective of the CTF was to uncover flags hidden throughout the target machine by exploiting various vulnerabilities and conducting thorough analysis.

# Fase 1:

Upon visiting the machine's website, we analyzed the source code and discovered a JavaScript file containing a constant named "flag."

# Fase 2:

After conducting a brief investigation, we found a file named ".reminder" (http://MACHINE_IP/.reminder) on the server. This file contained the username and password required for initial SSH access.

# Fase 3:

Using the obtained credentials, we successfully accessed the machine via SSH and ran the "ls -lah" command. This revealed a file named ".flag" containing the first flag.

# Fase 4:

Following a hint, we discovered the ".hint" file located in the "/etc/passwd_max" path. The file contained a hexadecimal value, which we recognized as the flipped version of the hexadecimal password.

# Fase 5:

With the flipped password, we gained SSH access as the user "max." Once again, running "ls -lah," we found the file ".flag" containing the second flag.

# Fase 6:

By executing the command "find / -type f -perm -04000 -ls 2>/dev/null," we identified that we had sudo access (even though the user did not belong to the sudoers group) to the file "/usr/bin/find."

# Fase 7:

Using the information from gtfobins.github.io, we exploited a vulnerability in sudo, which allowed us to execute a shell as root.

# Fase 8:

After obtaining initial access as root, we located the first flag in the "/root" directory. To find the second flag, we used the command "find / | grep .flag," which led us to the last flag located in the path "/usr/share/.flag."
Conclusion

The "WhoAmI: The Computer Ghost Hunt" CTF presented a series of challenges that required a combination of web analysis, SSH exploitation, password cracking, privilege escalation, and finding hidden flags throughout the target machine. By carefully following the steps outlined in this report, we successfully completed the CTF and achieved our goal of uncovering all the flags.

Note: To maintain confidentiality and protect the CTF environment's integrity, specific paths have been redacted or replaced with "[REDACTED]."

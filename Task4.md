A script is a piece of code that does not need to be compiled. In other words, it remains in its original human-readable form and does not need to be converted to machine language. Many programs provide additional functionality via scripts; moreover, scripts make it possible to add custom functionality that did not exist via the built-in commands. Similarly, Nmap provides support for scripts using the Lua language. A part of Nmap, Nmap Scripting Engine (NSE) is a Lua interpreter that allows Nmap to execute Nmap scripts written in Lua language. However, we don’t need to learn Lua to make use of Nmap scripts.

Your Nmap default installation can easily contain close to 600 scripts. Take a look at your Nmap installation folder. On the AttackBox, check the files at /usr/share/nmap/scripts, and you will notice that there are hundreds of scripts conveniently named starting with the protocol they target. We listed all the scripts starting with the HTTP on the AttackBox in the console output below; we found around 130 scripts starting with http. With future updates, you can only expect the number of installed scripts to increase.

<img width="876" height="817" alt="image" src="https://github.com/user-attachments/assets/e66b93df-8b8b-4100-a3a5-58c59da812f7" />

You can specify to use any or a group of these installed scripts; moreover, you can install other user’s scripts and use them for your scans. Let’s begin with the default scripts. You can choose to run the scripts in the default category using --script=default or simply adding -sC. In addition to default(opens in new tab), categories include auth, broadcast, brute, default, discovery, dos, exploit, external, fuzzer, intrusive, malware, safe, version, and vuln. A brief description is shown in the following table.

auth	- Authentication related scripts
broadcast -	Discover hosts by sending broadcast messages
brute -	Performs brute-force password auditing against logins
default -	Default scripts, same as -sC
discovery -	Retrieve accessible information, such as database tables and DNS names
dos -	Detects servers vulnerable to Denial of Service (DoS)
exploit - 	Attempts to exploit various vulnerable services
external -	Checks using a third-party service, such as Geoplugin and Virustotal
fuzzer -	Launch fuzzing attacks
intrusive -	Intrusive scripts such as brute-force attacks and exploitation
malware -	Scans for backdoors
safe -	Safe scripts that won’t crash the target
version -	Retrieve service versions
vuln -	Checks for vulnerabilities or exploit vulnerable services

Some scripts belong to more than one category. Moreover, some scripts launch brute-force attacks against services, while others launch DoS attacks and exploit systems. Hence, it is crucial to be careful when selecting scripts to run if you don’t want to crash services or exploit them.

We use Nmap to run a SYN scan against 10.48.143.28 and execute the default scripts in the console shown below. The command is sudo nmap -sS -sC 10.48.143.28, where -sC will ensure that Nmap will execute the default scripts following the SYN scan. There are new details that appear below. Take a look at the SSH service at port 22; Nmap recovered all four public keys related to the running server. Consider another example, the HTTP service at port 80; Nmap retrieved the default page title. We can see that the page has been left as default.

<img width="527" height="384" alt="image" src="https://github.com/user-attachments/assets/fe61c68d-63b3-4d22-a844-f7d2b2db5d6c" />

You can also specify the script by name using --script "SCRIPT-NAME" or a pattern such as --script "ftp*", which would include ftp-brute. If you are unsure what a script does, you can open the script file with a text reader, such as less, or a text editor. In the case of ftp-brute, it states: “Performs brute force password auditing against FTP servers.” You have to be careful as some scripts are pretty intrusive. Moreover, some scripts might be for a specific server and, if chosen at random, will waste your time with no benefit. As usual, make sure that you are authorized to launch such tests on the target server.

Let’s consider a benign script, http-date, which we guess would retrieve the http server date and time, and this is indeed confirmed in its description: “Gets the date from HTTP-like services. Also, it prints how much the date differs from local time…” On the AttackBox, we execute sudo nmap -sS -n --script "http-date" 10.48.143.28 as shown in the console below.

<img width="908" height="580" alt="image" src="https://github.com/user-attachments/assets/3e894f6e-e771-4852-ae00-cb3ae3f84e6a" />

Finally, you might expand the functionality of Nmap beyond the official Nmap scripts; you can write your script or download Nmap scripts from the Internet. Downloading and using a Nmap script from the Internet holds a certain level of risk. So it is a good idea not to run a script from an author you don’t trust.

## Answer the question below

1. Knowing that Nmap scripts are saved in /usr/share/nmap/scripts on the AttackBox. What does the script http-robots.txt check for?
- <img width="888" height="81" alt="image" src="https://github.com/user-attachments/assets/f139fe00-f1fe-4d0c-b8ce-fbde096c2a3c" />
- disallowed entries
2. Can you figure out the name for the script that checks for the remote code execution vulnerability MS15-034 (CVE2015-1635)?
- http-vuln-cve2015-1635
<img width="893" height="95" alt="image" src="https://github.com/user-attachments/assets/58531fd7-38dd-4718-9c7b-b7e2048ee717" />
3. Launch the AttackBox if you haven't already. After you ensure you have terminated the VM from Task 2, start the target machine for this task. On the AttackBox, run Nmap with the default scripts -sC against 10.48.143.28. You will notice that there is a service listening on port 53. What is its full version value?
- 9.18.28-1~deb12u2-Debian
<img width="1007" height="534" alt="image" src="https://github.com/user-attachments/assets/1e715160-8581-40f2-a055-06ecd164fc47" />
4. Based on its description, the script ssh2-enum-algos “reports the number of algorithms (for encryption, compression, etc.) that the target SSH2 server offers.” What is the name of the server host key algorithm that relies on SHA2-512 and is supported by 10.48.143.28?
- <img width="986" height="803" alt="image" src="https://github.com/user-attachments/assets/44498fc5-e7c8-499c-bb5e-f662c5225ee8" />
- rsa-sha2-512

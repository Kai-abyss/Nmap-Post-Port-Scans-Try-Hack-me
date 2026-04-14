Whenever you run a Nmap scan, it is only reasonable to save the results in a file. Selecting and adopting a good naming convention for your filenames is also crucial. The number of files can quickly grow and hinder your ability to find a previous scan result. The three main formats are:

1. Normal
2. Grepable (grepable)
3. XML
There is a fourth one that we cannot recommend:

- Script Kiddie

## Normal
As the name implies, the normal format is similar to the output you get on the screen when scanning a target. You can save your scan in normal format by using -oN FILENAME; N stands for normal. Here is an example of the result.

<img width="861" height="793" alt="image" src="https://github.com/user-attachments/assets/3199934a-071f-4c5b-b243-954182f5b9aa" />

## Grepable

The grepable format has its name from the command grep; grep stands for Global Regular Expression Printer. In simple terms, it makes filtering the scan output for specific keywords or terms efficient. You can save the scan result in grepable format using -oG FILENAME. The scan output, displayed above in normal format, is shown in the console below using grepable format. The normal output is 21 lines; however, the grepable output is only 4 lines. The main reason is that Nmap wants to make each line meaningful and complete when the user applies grep. As a result, in grepable output, the lines are so long and are not convenient to read compared to normal output.

<img width="859" height="295" alt="image" src="https://github.com/user-attachments/assets/edb543ec-6906-4d5c-a1ec-5f59621ebc7f" />

An example use of grep is grep KEYWORD TEXT_FILE; this command will display all the lines containing the provided keyword. Let’s compare the output of using grep on normal output and grepable output. You will notice that the former does not provide the IP address of the host. Instead, it returned 80/tcp open http nginx 1.6.2, making it very inconvenient if you are sifting through the scan results of multiple systems. However, the latter provides enough information, such as the host’s IP address, in each line to make it complete.

<img width="824" height="370" alt="image" src="https://github.com/user-attachments/assets/6be00740-cd23-47d0-8447-79a09c107f26" />

## XML
The third format is XML. You can save the scan results in XML format using -oX FILENAME. The XML format would be most convenient to process the output in other programs. Conveniently enough, you can save the scan output in all three formats using -oA FILENAME to combine -oN, -oG, and -oX for normal, grepable, and XML.

## SCrIPT Kiddle

A fourth format is script kiddie. You can see that this format is useless if you want to search the output for any interesting keywords or keep the results for future reference. However, you can use it to save the output of the scan nmap -sS 127.0.0.1 -oS FILENAME, display the output filename, and look 31337 in front of friends who are not tech-savvy.

Pentester Terminal

<img width="841" height="695" alt="image" src="https://github.com/user-attachments/assets/9e1b52c3-d48f-43bd-a36a-8905d279eded" />

### Answer the questions below

1. Terminate the target machine of the previous task and start the target machine for this task. On the AttackBox terminal, issue the command scp pentester@10.48.163.22:/home/pentester/* . to download the Nmap reports in normal and grepable formats from the target virtual machine.

Note that the username pentester has the password THM17577

Check the attached Nmap logs. How many systems are listening on the HTTPS port?
- <img width="726" height="93" alt="image" src="https://github.com/user-attachments/assets/14ab60f9-b594-4714-a70c-6553dbf14732" />
- 3
2. What is the IP address of the system listening on port 8089
  -  172.17.20.147
  -  <img width="915" height="74" alt="image" src="https://github.com/user-attachments/assets/6bd70907-9603-4ed8-8c40-9dbee75242fb" />

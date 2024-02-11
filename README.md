<h1> Keylogging</h1>

<h2>Description</h2>
In this project, I will demonstrate the process of initiating a server within our Kali Linux environment, launching msfconsole, and conducting a search for a keylogging attack. Following this, I will illustrate how to customize the attack to suit our specific requirements before executing it. Additionally, I will provide insight into the victim's perspective, elucidating how the keystrokes from the victim are captured and stored within our Kali Linux terminal

<h2>Tools and Languages Utilized</h2>
<ul>
  <li>Kali Linux</li><br>
  <li>Windows 2016</li><br>
  <li>MSFconsole</li><br>
  <li>PostgreSQL</li>
</ul>


<h2>Program walk-through</h2>

Firstly, let's initiate by accessing our Kali Linux machine to determine its IP address. Once identified, we'll utilize this IP address as the servicing host for our key logger creation. This strategy enables us to capture keystrokes inputted on the fake website effectively.



After getting the Kali IP address we will then run the command:

    Sudo systemctl start postgresql

This command initiates the Postgres server, a highly versatile relational database renowned for its compatibility with a range of operating systems including Windows, Linux, and MacOS. Postgres serves as a robust solution for storing, managing, and retrieving extensive datasets with remarkable efficiency. Its necessity lies in our objective to securely store the key inputs obtained from the victim.




Following this stage, we'll embark on crafting our key logging attack. Our initial step involves launching the MSFconsole within Kali Linux. To accomplish this, we simply input:

     Sudo msfconsole

The program may take some time to fully load, but once it's up and running, our terminal will undergo a transformation, displaying a keystroke that reads "msf6." This indicates that MSFconsole has initialized successfully. Following the startup, we employ the search command within MSFconsole to look up "keylogger" as demonstrated earlier. While we received three matches, for this demonstration, we'll opt for the first one, represented by the "0" option.







To select option "0," we simply enter "use 0" into the MSFconsole, triggering its loading process as depicted above. Notably, the exploit we've chosen will always be highlighted in red, as illustrated. Now, to tailor the attack to our specifications, we input "show options" into the MSFconsole, revealing the necessary fields to be adjusted, marked "yes." For this demonstration, we'll set "Demo" to "True" (as indicated in the first line of the image). Next, we configure the Server Host attribute, utilizing the Kali IP obtained in a previous step for the SRVHOST setting. The third attribute to modify is SRVPORT, determining the port from which our attack will be dispatched. Here, we've opted for port 1717, facilitating TCP and UDP connections across different machines. Finally, initiating the attack is as simple as typing the "run" command.


Note: As we commence the attack, an URL is generated. This URL serves as the residence of our keylogger. Subsequently, we have the capability to fabricate a counterfeit website and embed this URL. Consequently, any text inputted on the counterfeit website will be replicated and accessible to us.




In the image below, we encounter a demonstration keylogger embedded within a website form. For demonstration purposes, it's crucial to append "/demo" to the URL obtained from the preceding image. Therefore, the complete URL becomes "http://10.1.158.100:1717/hYYigc/demo". Within the counterfeit website depicted above, there exists a straightforward username and password field.

Note: Here's the view the victim will encounter. It's important to note that this is the stage where you have the ability to craft a convincing replica website of any organization and seamlessly integrate a keylogger into it, constituting a form of phishing.





As depicted below, when the victim enters their username and password, everything appears ordinary from their perspective. However, unbeknownst to them, every keystroke they make is being copied and stored on our Kali Linux system.






In the end, our Kali Linux system quietly records every keystroke made by the user. Each input is captured and stored, providing a detailed log of their actions. This allows us to analyze and potentially utilize the gathered information. Thus, our Kali Linux becomes a crucial tool for monitoring and capturing sensitive information’s.

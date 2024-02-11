<h1> Keystroke Logging (Keylogging)</h1>

<h2>Description</h2>
In this project, I will demonstrate the process of initiating a server within our Kali Linux environment, launching msfconsole, and conducting a search for a keylogging attack. Following this, I will illustrate how to customize the attack to suit our specific requirements before executing it. Additionally, I will provide insight into the victim's perspective, elucidating how the keystrokes from the victim are captured and stored within our Kali Linux terminal

<h2>Tools and Languages Utilized</h2>
<ul>
  <li>
    
  **Kali Linux**</li>
  <li>
    
  **Windows 2016**</li>
  <li>
    
  **MSFconsole**</li>
  <li>
    
  **PostgreSQL**</li>
</ul>


<h2>Program walk-through</h2>

<h3><ins>Step 1</h3>
<ul>

<li>Firstly, let's initiate by accessing our Kali Linux machine to determine its IP address. Once identified, we'll utilize this IP address as the servicing host for our key logger creation. This strategy enables us to capture keystrokes inputted on the fake website effectively. To get the IP address we run the command:<br>
  <br>

    hostname -i

   
Another way to find the IP address is by simply using the command:

   
    ifconfig

<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/Picture1.png" height="80%" width="80%" alt="OU modification"/>

<br>
<br>
</ul>
<h3><ins>Step 2</h3>
<ul>
<li>After getting the Kali IP address we will then run the command:<br>
<br>

    Sudo systemctl start postgresql
<ul>
<li>This command initiates the Postgres server, a highly versatile relational database renowned for its compatibility with a range of operating systems including Windows, Linux, and MacOS. Postgres serves as a robust solution for storing, managing, and retrieving extensive datasets with remarkable efficiency. Its necessity lies in our objective to securely store the key inputs obtained from the victim.</li>
</ul>
</ul>
<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/2.png" height="80%" width="80%" alt="OU modification"/>
<br>
<br>
<br>

<h3><ins>Step 3</h3>
<ul>
<li>Following this stage, we'll embark on crafting our key logging attack. Our initial step involves launching the MSFconsole within Kali Linux. To accomplish this, we simply input:</li>
<br>

     Sudo msfconsole
<ul>
<li>The program may take some time to fully load, but once it's up and running, our terminal will undergo a transformation, displaying a keystroke that reads "msf6." This indicates that MSFconsole has initialized successfully. Following the startup, we employ the search command within MSFconsole to look up "keylogger" as demonstrated earlier. While we received three matches, for this demonstration, we'll opt for the first one, represented by the "0" option.</li>
</ul>
</ul>
<br>
<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/3.png" height="80%" width="80%" alt="OU modification"/>
<br>
<br>
<h3><ins>Step 4</h3>
<ul>
<li>To select option "0," we simply enter "use 0" into the MSFconsole, triggering its loading process as depicted above. Notably, the exploit we've chosen will always be highlighted in red, as illustrated. Now, to tailor the attack to our specifications, we input "show options" into the MSFconsole, revealing the necessary fields to be adjusted, marked "yes."<br>
<br>
<li>For this demonstration, we'll set "Demo" to "True" (as indicated in the first line of the image). Next, we configure the Server Host attribute, utilizing the Kali IP obtained in a previous step for the SRVHOST setting. The third attribute to modify is SRVPORT, determining the port from which our attack will be dispatched. Here, we've opted for port 1717, facilitating TCP and UDP connections across different machines. Finally, initiating the attack is as simple as typing the "run" command.</li>

<h4>Note:</h4>
<ul>
 <li> As we commence the attack, an URL is generated. This URL serves as the residence of our keylogger. Subsequently, we have the capability to fabricate a counterfeit website and embed this URL. Consequently, any text inputted on the counterfeit website will be replicated and accessible to us.</li>
</ul>
</ul>
<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/4.png" height="80%" width="80%" alt="OU modification"/>
<br>
<br>
<h3><ins>Step 5</h3>
  <ul>
<li>In the image below, we encounter a demonstration keylogger embedded within a website form. For demonstration purposes, it's crucial to append "/demo" to the URL obtained from the preceding image. Therefore, the complete URL becomes "http://10.1.158.100:1717/hYYigc/demo". Within the counterfeit website depicted above, there exists a straightforward username and password field.<br>
<h4>Note:</h4> 
  <ul>
<li>Here's the view the victim will encounter. It's important to note that this is the stage where you have the ability to craft a convincing replica website of any organization and seamlessly integrate a keylogger into it, constituting a form of phishing.</li>
</ul>
  </ul>
<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/5.png" height="80%" width="80%" alt="OU modification"/>
<br>
<br>

<h3><ins>Step 6</h3>
<ul>
<li>As depicted below, when the victim enters their username and password, everything appears ordinary from their perspective. However, unbeknownst to them, every keystroke they make is being copied and stored on our Kali Linux system.
</ul>

<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/6.png" height="80%" width="80%" alt="OU modification"/>
<br>
<br>
<h3><ins>Step 7</h3>
<ul>
<li>In the end, our Kali Linux system quietly records every keystroke made by the user. Each input is captured and stored, providing a detailed log of their actions. This allows us to analyze and potentially utilize the gathered information. Thus, our Kali Linux becomes a crucial tool for monitoring and capturing sensitive information’s.

<p align="center">
<img src="https://github.com/Salrocks/keylogging/blob/main/7.png" height="80%" width="80%" alt="OU modification"/>

</ul>

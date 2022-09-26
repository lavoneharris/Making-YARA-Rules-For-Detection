<h1>Making Yara Rules for Detection Lab</h1>


<h2>Description</h2>
This YARA Rule Lab consist of installing YARA on a Linux environment via Virtualization. We will both write our own rules and also automatically generate rules using yarGen. <br>



<h2>What are YARA Rules:</h2>
YARA rules are like a piece of programming language, they work by defining a number of variables that contain patterns found in a sample of malware. If some or all of the conditions are met, depending on the rule, then it can be used to successfully identify a piece of malware.

<br />

<h2>Why are YARA Rules Important:</h2>
YARA rules are used to classify and identify malware samples by creating descriptions of malware families based on textual or binary patterns.
<br />
<h2>Utilities Used:</h2>
- Oracle Virtual Box <br>
- Linux Terminal <br>





<h2>Environments Used </h2>
- Windows 10 <br>
- Kali Linux

<h2> Instructions:</h2>
<p align="center">
 1. We will need to download YARA on our Linux VM. <br>
 Begin by downloading the .tar.gz file from the YARA github. Link: https://github.com/virustotal/yara/releases/tag/v4.0.2 <br>
  Note: Make sure that this file is downloaded on the Kali Linux VM
<br/>
<img src="https://imgur.com/6CTJRwa.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/mCWpAJT.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/p9jSA7O.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
2. Once the .tar.gz file has been downloaded we will need to install it via Terminal. <br> 
  Use command:<br> 
 cd Downloads<br>
  sudo apt-get install automake libtool make gcc pkg-config
  <br/>
<img src="https://imgur.com/jpZXAjF.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/8S41SRZ.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
 3. Now run commands in the following order. <br>
  Use Commands:<br> 
 tar -zxf yara-4.0.2.tar.gz  <br>
                cd yara-4.0.2/  <br>
               ./bootstrap.sh  <br>
 <img src="https://imgur.com/5epfmAP.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/EfydKKH.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
 4. Next we will need compile and install with these 3 commands. <br>
  Use Commands: <br>
                    ./configure <br>
                      make <br>
                sudo make install <br>
  <img src="https://imgur.com/uOlgYNt.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/TYfkoxe.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/LW1URBG.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
5. To ensure everything is installed properly we we will run the following command. <br>
  Use Command:<br>
 make check <br>
  If everything installed properly everything should pass like the image below. <br>
  <img src="https://imgur.com/ryZf4gD.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <img src="https://imgur.com/zWCzzui.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />





<h2> Writing Yara Rules Instructions:</h2>
<p align="center">
Yara rules must have three core components that must be included. <br />
Rules: <br>
 1. Rule Name <br />
       2. Identification Values (characteristics the rule is searching for)<br />
       3. Condition (defines the condition that the file will be flagged )<br />
 <br>
 <br>
Lets create a very simple Yara rule. <br />
 1. Lets install a text editor,  by going to terminal and entering the command: sudo snap install notepad-plus-plus. <br>
 Note: we can already use mousepad if already installed on Linux.
  <img src="https://imgur.com/U3cUJJE.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
 2. Let's write the Yara Rule. We will save it as HelloString.txt but we will need to change the file extension to .yara to run properly.<br>
 See screenshot of Yara Rule if further assistance is needed.<br />
  <img src="https://imgur.com/yHPvbGk.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
  <img src="https://imgur.com/8zQUG6y.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
  <img src="https://imgur.com/To3yIa9.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
YARA Rule (Line Breakdown)<br />
 Line 1: We defined the rule name as "HelloString" with a short name of Hello. <br />
 Line 3: Declares a file property, this is a text string that will be present in the file. $a variable holds the value of Hello. <br />
 Line 6: Declares the condition that needs to be met to flag the file. $a means if any file scanned containing the string Hello will be flagged. <br />
 <br>
 <br>
 3. Create a folder named YARA Demo.<br />
   <img src="https://imgur.com/LfR88qE.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
 4. Create a sample file called asdf.txt, that will have the string Hello in it. <br />
   <img src="https://imgur.com/2wixhcA.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
 5. In Terminal, lets run the command yara HelloString.yara /root/Desktop/YARA\ Demo to see if it flags the file asdf.txt. <br />
    <img src="https://imgur.com/b56ePIw.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
   <img src="https://imgur.com/DhvUAjS.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
 6. We get an error message. After a day I was able to determine this was I was not storing in the root directory, We will need to do this for both files we created. <br />
    <img src="https://imgur.com/HWGciMB.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
   <img src="https://imgur.com/iheDPP0.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
 7. We will run the command yara HelloString.yara /root/Desktop/YARA\ Demo again in Terminal. Now you can see it flagged the file asdf.txt. <br>
    <img src="https://imgur.com/N88cNSL.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
 8. Run the command again but adding -m to the command so it reads in Terminal: yara -m HelloString.yara /root/Desktop/YARA\ Demo.<br>
 This now provides the meta information for the rule. <br>
    <img src="https://imgur.com/vwFmkBE.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
9. Now lets expand on our rule by adding new variables to the HelloString.yara file as below using the "OR" clause. <br>
    <img src="https://imgur.com/uC6m9Zf.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
Note that in conditions of the .yara file we can use the clauses "AND" & "OR" <br>
 OR = Allow the rule to flag any files that contain any of the strings.<br>
 AND = Allow the rule to flag any files that contain at least two of the strings.<br>
 <br>
 <br>
10. Let's create two new text files. We will run the command in Terminal again yara -m HelloString.yara /root/Desktop/YARA\ Demo.You will see it flagged.
<br> 
 Note: How only two were flagged because the file message.txt says "HELLO" and not "hello" so conditions are not met.
    <img src="https://imgur.com/kZ4aQrL.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
   <img src="https://imgur.com/O13ogbZ.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
   <img src="https://imgur.com/XP4Ag7X.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
   <img src="https://imgur.com/RzrSukN.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
11. Now lets expand on our rule by adding new variables to the HelloString.yara file as below using the "AND" clause. <br>
    <img src="https://imgur.com/3dJw8py.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
12. Run the command again but adding -m and -s to the command so it reads in Terminal: yara -m -s HelloString.yara /root/Desktop/YARA\ Demo. <br>
 Note: This now provides the meta information and prints the matching strings for the rule. <br>
    <img src="https://imgur.com/tncLBRb.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
   <img src="https://imgur.com/tKLonEz.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
 <br />
<br />
 YARA flags:<br>
 -m // Prints the associated meta information to the terminal after a YARA scan.<br>
 -s // Prints the matching strings to the terminal after a YARA scan.<br>
-r // Recursively scan all subfolders within the target location to ensure everything is scanned.<br>
<br />
<br />

<h1>Making Yara Rules for Detection Lab</h1>


<h2>Description</h2>



<br />


<h2>What are YARA Rules:</h2>





<br />

<h2>Why are YARA Rules Important:</h2>

<h2>Utilities Used:</h2>
- Oracle Virtual Box <br>
- Linux Terminal <br>





<h2>Environments Used </h2>
- Windows 10
- Kali Linux

<h2> Instructions:</h2>
<p align="center">
 1. We will need to download YARA on our Linux VM. Begin by downloading the .tar.gz file from the YARA github Link: https://github.com/virustotal/yara/releases/tag/v4.0.2.  <br>
  Note: Make sure that this file is downloaded on the Kali Linux VM
br/>
<img src="https://imgur.com/T1Aosof.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
2. Once the .tar.gz file has been downloaded we will need to install it via Terminal. <br> 
  Use command:<br> sudo -i <br>
               sudo apt-get install automake libtool make gcc pkg-config
  br/>
<img src="https://imgur.com/T1Aosof.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
 3. Now run commandsin the following order. <br>
  Use Commands:<br> 
 tar -zxf yara-4.0.2.tar.gz  <br>
                cd yara-4.0.2/  <br>
               ./bootstrap.sh  <br>
 4. Next we will need compile and install with these 3 commands. <br>
  Use Commands: <br>
                    ./configure <br>
                      make <br>
                sudo make install <br>
  <img src="https://imgur.com/T1Aosof.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
5. To ensure everything is installed properly we we will run the following command. <br>
  Use Command:<br>
 make check <br>
  If everything installed properly everything should pass like the image below. <br>
  <img src="https://imgur.com/T1Aosof.png" height="80%" width="80%" alt="Download Windows 10 ISO File"/>
<br />
<br />
 


# Raspberry_pi_Repeater
This repository will holed the Scripts and code for the Raspberry Pi Repeater.<br>
![Alt text](FM_Repeater_1.jpg?raw=true "Block diagram")<br>
The PCB board details for the repeater is avalible here  https://github.com/antonjan/Bacar_Raspberry_tx <br>
The filter board is a plugin board for the Raspberry pi with a 7 stage Low pass filter.<br>
The rtl dongle as input and the rbptx as transmitter with the filter board with details in link above.<br>
24Mhz to 1.7Ghz receiver input to 2M or HF transmitter. depending on your filter details.<br>
Dont use this scripts without the filter boards and only used licensed frequencies.<br>
The PCB assembled and in kit form is available at http://www.giga.co.za<br>

Rapbery_Pi_Repeater_Startup.<br>
Unzip the source code above in die home/pi/sh directory and the follow the following steps to start the repeater.<br>

1) Login with username: pi<br>
2) Password : raspberry<br>
2) go to the directory cd /home/pi/sh<br>
3) Calibrate the RTL dongle see calibrate dongle section 7<br>
4) Claibrate Tx frequency use rtl dongle after it was calibrated to look at your tx from Raspbery pi and calibrate frequency.<br>
*****************************************RX*************************************<br>
5) How to change the RX frequency<br>
5.1) Edit the file Start_70cm_RX_437000Mhz_Talk_P8011.sh_v2<br>
5.2) Edit the parameter  -f 434400000 to your requierd frequency in herts. <br>
You mite need to increase or decrease the frequency because the Dongle has some factory frequency offset.<br> 
The best is to do the frequency testing with dongle in laptop with sdr software, then get ofset and then change the frequency paramter. <br>
*****************************************TX*************************************<br>
6) How to change the TX frequency.<br>
6.1) Edit the file Start_2m_TX_145300Mhz_Listen_P8011.sh_v2<br>
6.2) There is a paramter -f 145300  change it to the requierd frequency.<br>

**************************************Start the TX first************************<br>
7) run the commands in the directory /home/pi/sh so cd to /home/pi/sh<br>
7.1) start the TX side<br>
7.2) run the following scrip<br> 
7.3)sudo ./Start_2m_TX_145300Mhz_Listen_P8011.sh_v2<br>
7.4) enter password and You should then here a small blip on the tx frequency.<br>
7.5) you will see some message on screen thats ok.<br>
*************************************Then Start the RX**************************<br>
8) Open a new terminal keeping the TX terminal open to see if everything is ok<br>
8.1) go to the directory /home/pi/sh<br>
8.2) run the following script to start the RX side.<br>
8.3) sudo ./Start_70cm_RX_437000Mhz_Talk_P8011.sh_v2<br>
8.4) enter password and you should here tx sounding like noise. ths becose the Sqaulse is not working.<br>
8.5) you should see somthing connected...<br>
8.6) Test by transmiiting on RX frequency and you should here your self on the tx side there is a bit of a delay in the beginning.<br>
8.7) there  seems to be a bit of dely about 1S beween RX and TX I can still do a lot of changes to improof the sound and squals ....<br>

**************************************How to stop the applications***************<br>
How to kill the TX application<br>
1) run the command  sudo ps -ef | grep rpirx<br>
2) if there is a process kill it with the command sudo kill [prosess id]<br>

**********************************Calibrate RTL dongle frequency****************<br>
9) Use your laptop and start your sdr sofware with waterfall display.<br>
9.1) transmit in frequency you hav mobile transever EG baufeng in 145.000Mhz<br>
9.2) see what is the frequency ofset then added that to the frequency parameters.<br>

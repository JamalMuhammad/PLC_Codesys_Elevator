# PLC_Codesys_Elevator
A Structured Text(ST) written PLC program for Elevator movement using Virtual Drive function inside Codesys


The test has been done using following version of CodeSys
Codesys version: 	CODESYS V3.5 SP14 Patch 1
Device(in program):	"Codesys SoftMotion Win V3 x64" 
Virtual PLC:		"CODESYS SoftMotion SL" or when installed it appears as "Codesys SoftMotion Win 64" in windows Start menu

We can download "CODESYS SoftMotion SL" from here: 
https://store.codesys.com/codesys-softmotion-sl.html?___store=en#Product%20Description
The unpaid demo version runs for 120 min, after that we need to restart the service. 

After "Codesys SoftMotion Win 64" is installed go to this location: C:\Program Files\CODESYS 3.5.14.10\GatewayPL
open the file "CODESYSSoftMotion.cfg" in editor (e.g. Notepad) and we can find location of the original *.cfg file , 
it should be-

Windows.WorkingDirectory=C:\ProgramData\CODESYS\CODESYSControlSoftMotionWinV3x64\82CB2619\

>go to above location and open the file "CODESYSSoftMotion.cfg" with editor. 

>here remove the ";" sign at the very start of the line where number for "NetworkPort" of OPCUA server is defined:
[CmpOPCUAServer]
;NetworkPort=4840 ;Configure the port used by the OPC UA server. Default: 4840    

>Then change the "NetworkPort" number to 4841. It should be like this:
NetworkPort=4841 ;Configure the port used by the OPC UA server. Default: 4840 

In my case I have used "NetworkPort=4841", you can use other numbers as well e.g. 4838, 4842, just make sure those ports are not in use.

I needed to make this change as the default port (for OPC_UA) 4840 is occupied in my machine(probably by KepServer) and I was getting error message 
while running the service. 

What is TCP port 4840? You can look for more info here: 
https://www.adminsub.net/tcp-udp-port-finder/4840

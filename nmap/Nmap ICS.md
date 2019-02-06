102(TCP)	siemens s7	nmap --script s7-info.nse -p 102 [host] 
		nmap -sP --script s71200-enumerate-old.nse -p 102 [host]
502(TCP)	modbus	nmap --script modicon-info -p 502 [host]

2404(TCP)	IEC 60870-5-104	nmap -Pn -n -d --script iec-identify.nse --script-args='iec-identify.timeout=500' -p 2404 [host]

20000(TCP)	DNP3	nmap -sT --script dnp3-enumerate.nse -p 20000 [host] 
		nmap --script dnp3-info -p 20000 [host]
44818(TCP)	Ethernet/IP	nmap --script enip-enumerate -sU -p 44818 [host]
47808(UDP)	BACnet	nmap --script BACnet-discover-enumerate.nse -sU -p 47808 [host]
1911(TCP)	Tridium Nixagara Fo	nmap --script fox-info.nse -p 1911 [host]
789(TCP)	Crimson V3	nmap --scripts cr3-fingerprint.nse -p 789 [host]
9600(TCP)	OMRON FINS	nmap --script ormontcp-info -p 9600 [host]
1962 (TCP)	PCWorx	nmap --script pcworx-info -p 1962 [host]
20547(TCP)	ProConOs	nmap --script proconos-info -p 20547 [host]
5007(TCP)	Melsec-Q	nmap -script melsecq-discover -sT -p 5007 [host]
5006	Melsec-Q	nmap -script melsecq-discover-udp.nse -sU -p 5006 [host]
956(TCP)	CSPV4	Unknown
4840(TCP)	OPCUA	Unknown
18245(TCP)	GE SRTP	Unknown
1200(TCP)	Codesys	nmap –script codesys-v2-discover.nse [host]
10001	atg	nmap --script atg-info -p 10001 [host]
2222	cspv4	nmap --script cspv4-info -p 2222 [host]
1911	fox	nmap --script fox-info.nse -p 1911 [host]
4800	moxa	nmap -sU --script moxa-enum -p 4800 [host]
137	siemens wincc	sudo nmap -sU --script Siemens-WINCC.nse -p137 [host]
445	stuxnet	nmap --script stuxnet-detect -p 445 [host]

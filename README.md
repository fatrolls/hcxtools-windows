# hcxtools-windows
WPA HCXTools windows


C:\Users\User\Desktop\Wep Cracker\>hcxhash2cap -help
hcxhash2cap 1.0 (C) 2021 ZeroBeat
usage:
hcxhash2cap <options>

options:
-c <file> : output cap file
            if no cap file is selected, output will be written to single cap files
            format: mac_sta.cap (mac_sta.cap_x)
-h        : show this help
-v        : show version

--pmkid-eapol=<file> : input PMKID EAPOL combi hash file
--pmkid=<file>       : input PMKID hash file
--hccapx=<file>      : input hashcat hccapx file
--hccap=<file>       : input hashcat hccap file
--john=<file>        : input John the Ripper WPAPSK hash file
--help               : show this help
--version            : show version

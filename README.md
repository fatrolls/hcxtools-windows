# hcxtools-windows
WPA HCXTools windows

```
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
```

```
C:\Users\User\Desktop\Wep Cracker>hcxessidtool -help
hcxessidtool.exe 1.0 (C) 2021 ZeroBeat
usage:
hcxessidtool.exe <options>

options:
-e <essid>  : filter by ESSID
-E <essid>  : filter by part of ESSID
-l <essid>  : filter by ESSID length
-h          : show this help
-v          : show version

--pmkid1=<file>        : input PMKID file 1
--pmkid2=<file>        : input PMKID file 2
--pmkidout12=<file>    : output only lines present in both PMKID1 and PMKID2
--pmkidout1=<file>     : output only lines present in PMKID1
--pmkidout2=<file>     : output only lines present in PMKID2
--pmkidout=<file>      : output only ESSID filtered lines present in PMKID1
--pmkidgroupout=<file> : output ESSID groups from ESSIDs present in PMKID1
--hccapx1=<file>       : input HCCAPX1
--hccapx2=<file>       : input HCCAPX2
--hccapxout12=<file>   : output only lines present in both HCCAPX1 and HCCAPX2
--hccapxout1=<file>    : output only lines present in HCCAPX1
--hccapxout2=<file>    : output only lines present in HCCAPX2
--hccapxout=<file>     : output only ESSID filtered lines present in HCCAPX1
--hccapxgroupout=<file>: output ESSID groups from ESSIDs present in HCCAPX1
--essidout=<file>      : output ESSID list
--essidmacapout=<file> : output MAC_AP:ESSID list
--help                 : show this help
--version              : show version

Main purpose is to get full advantage of reuse of PBKDF2
while merging (only) the same ESSIDs from different hash files
examples:
hcxessidtool --pmkid1=file1.16800 --pmkid2=file2.16800 --pmkidout12=joint.16800
hcxessidtool --pmkid1=file1.16800 -l 10 --pmkidout=filtered.16800
```

```
C:\Users\User\Desktop\Wep Cracker>hcxeiutool -help
hcxeiutool 1.0 (C) 2021 ZeroBeat
usage:
hcxeiutool <options>

options:
-i <file> : input wordlist
-d <file> : output digit wordlist
-x <file> : output xdigit wordlist
-c <file> : output character wordlist (A-Za-z - other characters removed)
-s <file> : output character wordlist (A-Za-z - other characters replaced by 0x0
d)
            recommended option for processing with rules
-h        : show this help
-v        : show version

--help           : show this help
--version        : show version

example:
$ hcxdumptool -i <interface> -o dump.pcapng --enable_status=31
$ hcxpcapngtool -o test.22000 -E elist dump.pcapng
$ hcxeiutool -i elist -d digitlist -x xdigitlist -c charlist -s sclist
$ cat elist digitlist xdigitlist charlist sclist > wordlisttmp
$ hashcat --stdout -r <rule> charlist >> wordlisttmp
$ hashcat --stdout -r <rule> sclist >> wordlisttmp
$ cat wordlisttmp | sort | uniq > wordlist
$ hashcat -m 22000 dump.pcapng wordlist
```

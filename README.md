| Device | NTP | SERVICES | SNMP | SYSLOG | SYSTEM | TACACS |
| :---: | :---: | :---: | :---: | :---: | :---: |:---: |
| mx1 | NOT OK | NOT OK | N/A | N/A | N/A |N/A |
<details>
<summary>MX1 ntp issues:</summary>

```
[edit system ntp]
-   boot-server 192.168.122.1;
[edit system ntp]
+    authentication-key 24 type md5 value "$9$ZfDkPz39pu1zFcyKvLX"; ## SECRET-DATA
[edit system ntp]
+    server 10.1.10.6 key 24; ## SECRET-DATA
+    server 10.1.10.7 key 24; ## SECRET-DATA
+    server 10.1.10.4 key 24; ## SECRET-DATA
+    server 10.1.10.5 key 24; ## SECRET-DATA
-    server 192.168.122.1;
[edit system ntp]
+   trusted-key 24;
+   source-address 192.168.122.10;
```
</details>
<details>
<summary>MX1 services issues:</summary>

```
[edit system services]
-    ftp;
[edit system services ssh]
+    root-login allow;
+    protocol-version v2;
[edit system services]
-    telnet;
[edit system services netconf ssh]
+     port 22;
```
</details>

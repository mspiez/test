<details>
<summary>MX1</summary>

| Device | NTP | SERVICES | SNMP | SYSLOG | SYSTEM | TACACS |
| :---: | :---: | :---: | :---: | :---: | :---: |:---: |
| mx1 | NOT OK | NOT OK | NOT OK | NOT OK | NOT OK |NOT OK |
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
<details>
<summary>MX1 snmp issues:</summary>

```
[edit]
+  snmp {
+      interface lo0.0;
+      community ntc_snmp {
+          authorization read-only;
+          clients {
+              10.1.10.1/32;
+              10.1.10.2/32;
+          }
+      }
+      trap-options {
+          source-address 192.168.122.10;
+      }
+      trap-group ntc_trap_group {
+          version v2;
+          targets {
+              10.1.10.1;
+              10.1.10.2;
+              10.1.10.3;
+              10.1.10.4;
+          }
+      }
+  }
```
</details>
<details>
<summary>MX1 syslog issues:</summary>

```
[edit system syslog]
+    archive size 10m files 10;
[edit system syslog]
+    host 10.1.10.32 {
+        any notice;
+        authorization info;
+        structured-data;
+    }
[edit system syslog file messages]
+    explicit-priority;
[edit system syslog file interactive-commands]
+    explicit-priority;
[edit system syslog]
+   source-address 192.168.122.10;
```
</details>
<details>
<summary>MX1 system issues:</summary>

```
[edit system]
+  host-name mx1;
+  commit synchronize;
```
</details>
<details>
<summary>MX1 tacacs issues:</summary>

```
[edit system]
+  authentication-order tacplus;
+  tacplus-server {
+      10.1.11.9 {
+          secret "$9$O/TzIclWLNbwgW8ZUHkPf"; ## SECRET-DATA
+          timeout 5;
+          source-address 192.168.122.10;
+      }
+      10.1.11.10 {
+          secret "$9$MDyLNbgoGiHmg4QF/9pu"; ## SECRET-DATA
+          timeout 5;
+          source-address 192.168.122.10;
+      }
+      10.1.11.8 {
+          secret "$9$pGRxORSKMX-dsKvoJDjq."; ## SECRET-DATA
+          timeout 5;
+          source-address 192.168.122.10;
+      }
+  }
+  tacplus-options {
+      exclude-cmd-attribute;
+  }
+  accounting {
+      events [ change-log interactive-commands ];
+      destination {
+          tacplus {
+              server {
+                  10.1.11.9 {
+                      secret "$9$cgXrvL-VYoaU-dk.5T3n"; ## SECRET-DATA
+                      timeout 5;
+                      source-address 192.168.122.10;
+                  }
+                  10.1.11.10 {
+                      secret "$9$6b0BCu1cyK8LNcSwYoaUD"; ## SECRET-DATA
+                      timeout 5;
+                      source-address 192.168.122.10;
+                  }
+                  10.1.11.8 {
+                      secret "$9$4YJDkfT39Cuf5IEyrvM"; ## SECRET-DATA
+                      timeout 5;
+                      source-address 192.168.122.10;
+                  }
+              }
+          }
+      }
+  }
```
</details>
</details>
<details>
<summary>MX2</summary>

| Device | NTP | SERVICES | SNMP | SYSLOG | SYSTEM | TACACS |
| :---: | :---: | :---: | :---: | :---: | :---: |:---: |
| mx2 | NOT OK | NOT OK | NOT OK | NOT OK | NOT OK |NOT OK |
<details>
<summary>MX2 ntp issues:</summary>

```
[edit system ntp]
-   boot-server 192.168.122.1;
[edit system ntp]
+    authentication-key 24 type md5 value "$9$ZfDkPz39pu1zFcyKvLX"; ## SECRET-DATA
[edit system ntp]
+    server 10.1.10.7 key 24; ## SECRET-DATA
+    server 10.1.10.6 key 24; ## SECRET-DATA
+    server 10.1.10.5 key 24; ## SECRET-DATA
+    server 10.1.10.4 key 24; ## SECRET-DATA
-    server 192.168.122.1;
[edit system ntp]
+   trusted-key 24;
+   source-address 192.168.122.20;
```
</details>
<details>
<summary>MX2 services issues:</summary>

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
<details>
<summary>MX2 snmp issues:</summary>

```
[edit]
+  snmp {
+      interface lo0.0;
+      community ntc_snmp {
+          authorization read-only;
+          clients {
+              10.1.10.1/32;
+              10.1.10.2/32;
+          }
+      }
+      trap-options {
+          source-address 192.168.122.20;
+      }
+      trap-group ntc_trap_group {
+          version v2;
+          targets {
+              10.1.10.1;
+              10.1.10.2;
+              10.1.10.3;
+              10.1.10.4;
+          }
+      }
+  }
```
</details>
<details>
<summary>MX2 syslog issues:</summary>

```
[edit system syslog]
+    archive size 10m files 10;
[edit system syslog]
+    host 10.1.10.30 {
+        any notice;
+        authorization info;
+        structured-data;
+    }
[edit system syslog file messages]
+    explicit-priority;
[edit system syslog file interactive-commands]
+    explicit-priority;
[edit system syslog]
+   source-address 192.168.122.20;
```
</details>
<details>
<summary>MX2 system issues:</summary>

```
[edit system]
+  host-name mx2;
+  commit synchronize;
```
</details>
<details>
<summary>MX2 tacacs issues:</summary>

```
[edit system]
+  authentication-order tacplus;
+  tacplus-server {
+      10.1.11.10 {
+          secret "$9$kmT3CtOREyCAvWx7Vb"; ## SECRET-DATA
+          timeout 5;
+          source-address 192.168.122.20;
+      }
+      10.1.11.8 {
+          secret "$9$rcxK87bs4ZGibwmfzF/9"; ## SECRET-DATA
+          timeout 5;
+          source-address 192.168.122.20;
+      }
+      10.1.11.9 {
+          secret "$9$SFHlMXdb2aJDdVqmTQn6"; ## SECRET-DATA
+          timeout 5;
+          source-address 192.168.122.20;
+      }
+  }
+  tacplus-options {
+      exclude-cmd-attribute;
+  }
+  accounting {
+      events [ change-log interactive-commands ];
+      destination {
+          tacplus {
+              server {
+                  10.1.11.10 {
+                      secret "$9$jxkPQ69pB1h6/lK8LN-"; ## SECRET-DATA
+                      timeout 5;
+                      source-address 192.168.122.20;
+                  }
+                  10.1.11.8 {
+                      secret "$9$TF/tBIcleWB17-ws4o"; ## SECRET-DATA
+                      timeout 5;
+                      source-address 192.168.122.20;
+                  }
+                  10.1.11.9 {
+                      secret "$9$ygCeWxVwgJZjVb.PQz6/"; ## SECRET-DATA
+                      timeout 5;
+                      source-address 192.168.122.20;
+                  }
+              }
+          }
+      }
+  }
```
</details>
</details>

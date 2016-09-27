# UFW-BLOCK-map-content_pack
UFW BLOCK with GeoIP map and counter for Graylog2.

In the following, we are 192.0.2.1 and the attacker is 192.0.2.99. This content pack will create an INPUT on 0.0.0.0:5140 and a DASHBOARD with the name UFW BLOCK. It reads syslog input with UFW lines that contain the words "UFW BLOCK", like this:

[2435.594288] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=192.0.2.99 DST=192.0.2.1 LEN=153 TOS=0x00 PREC=0x00 TTL=111 ID=26834 PROTO=UDP SPT=1036 DPT=22 LEN=133

Please follow the instructions mentioned on the site http://docs.graylog.org/en/2.1/pages/geolocation.html first, *before* using this content pack. Then log into your Graylog2 installation and go to System -> Content packs. Then choose Import content pack, select the downloaded json file and after uploading don't forget to choose 'Apply content'. Make sure the INPUT is running and see the DASHBOARD with the name UFW BLOCK.

After installing this content pack, send data to the host for example with rsyslog on Linux with lines like:

$template GRAYLOGRFC5424,"<%PRI%>%PROTOCOL-VERSION% %TIMESTAMP:::date-rfc3339% %HOSTNAME% %APP-NAME% %PROCID% %MSGID% %STRUCTURED-DATA% %msg%\n"
*.* @192.0.2.1:5140;GRAYLOGRFC5424

This content pack is not yet ready for recognizing IPv6 addresses. This content pack was created using Graylog 2.1.1+01d50e5 with Oracle Corporation 1.8.0_101 on Linux 4.2.0-42-generic.

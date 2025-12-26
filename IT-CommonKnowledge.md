# IT Common-Knowledge

## Network

Flags:

`P`, Protocol, 协议
`S`, Service,  服务

| Abbreviations |   Flag  | Description                         | Comments                                  |
| :------------ | :------ | :---------------------------------- | :---------------------------------------- |
| ARP           | `P, `   | Address Resolution Protocol         |                                           |
| DHCP          | `P, `   | Dynamic Host Configuration Protocol |                                           |
| DNS           | ` ,S`   | Domain Naming Service               |                                           |
| FINGER        | ` ,S`   |                                     | Port:79                                   |
| FTP           | `P,S`   | File Transfer Protocol              | Port:20 (for Data); Port:21 (for Service) |
| HTTP          | `P,S`   | Hype Text Transfer Protocol         | Port:80                                   |
| IAMP          | `P,S`   |                                     | Port:993
| ICMP          | `P  `   | Internet Control Message Portocol   |                                           |
| IP            | `P, `   | Internet Protocol                   |                                           |
| NAMESERVER    | ` ,S`   |                                     | Port:42                                   |
| NAT           | ` , `   |                                     |                                           |
| NETBIOS       |         |                                     | Port:137, 138                             |
| POP3          | `P,S`   | Post Office Protocol - Version 3    | Port:110                                  |
| RARP          | `P, `   | Reverse ARP                         |                                           |
| RPC           |         | Remote Procedure Call               | Port:135                                  |
| SFTP          | `P,S`   | Security FTP                        | Port:22                                   |
| SSH           |         | Security Shell Protocol             | Port:22                                   |
| SMTP          | `P,S`   | Simple Mail Transfer Protocol       | Port:25, 465                              |
| SNMP          | `P, `   |                                     | Port:161                                  |
| TCP           | `P, `   | Transport Control Protocol          |                                           |
| Telnet        | ` ,S`   |                                     | Port:23                                   |
| UDP           | `P, `   | User Datagram Protocol              |                                           |
|               |         |                                     |                                           |

FINGER, 通过C/S模式实现用户信息查询功能
NAMESERVER, 输入DNS

### Ports

+ Well-Known Ports, `    0` ~ ` 1023`, 公认端口;  
+ Dynamic Ports,    ` 1024` ~ `65535`, 动态端口; 
  + Registered Ports, ` 1024` ~ `49151`, 注册端口;  
  + Private Ports, `49152` ~ `65535`, 私有端口; 

### 网络状态

#### LISTEN

#### SYN_SENT

#### SYN_RECEIVED

#### ESTABLISHED

#### FIN_WAIT_1

#### FIN_WAIT_2

#### CLOSE_WAIT

#### CLOSING

#### LAST_ACK

#### TIME_WAIT

#### CLOSED

### "three-way handshaking" vs "four-way wavehanding"

三次握手: three-way handshaking

四次挥手: four-way wavehanding

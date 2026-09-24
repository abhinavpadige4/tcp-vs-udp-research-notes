# TCP vs UDP Comparison — Outline

## 1. Connection Model
### TCP: Connection-oriented (3-way handshake)
- SYN → SYN-ACK → ACK before any data is sent.
- Explicit teardown (FIN/ACK) at the end of the session.
### UDP: Connectionless (no handshake)
- No setup, no teardown, no session state.
- First packet is already data.

## 2. Reliability
### TCP: Reliable
- ACKs confirm receipt of every segment.
- Lost segments are retransmitted automatically.
- Checksum + sequence numbers detect corruption and loss.
### UDP: Unreliable
- No ACKs, no retransmission.
- Checksum only — bad packets are dropped, not recovered.

## 3. Ordering
### TCP: Ordered
- Sequence numbers guarantee in-order delivery to the application.
### UDP: Unordered
- Packets may arrive out of sequence; ordering is the app's problem.

## 4. Flow Control
### TCP: Yes
- Sliding window prevents the sender from overwhelming the receiver.
### UDP: No
- Sender has no feedback about receiver capacity.

## 5. Congestion Control
### TCP: Yes
- Slow start, congestion avoidance, fast retransmit, fast recovery.
### UDP: No
- Sender does not adapt to network congestion.

## 6. Header Size
### TCP: 20 bytes minimum (up to 60 with options)
### UDP: 8 bytes fixed

## 7. Speed
### TCP: Slower
- Overhead from handshake, ACKs, retransmissions, and window management.
### UDP: Faster
- Minimal overhead; no setup or reliability machinery.

## 8. Use Cases
### TCP (reliability-first)
- HTTP/HTTPS (web browsing)
- FTP / SFTP (file transfer)
- SSH (secure shell)
- SMTP / IMAP / POP3 (email)
- Database protocols (MySQL, PostgreSQL)
### UDP (speed-first)
- DNS (domain name resolution)
- DHCP (dynamic host configuration)
- NTP (time sync)
- VoIP (voice over IP)
- Live video streaming (RTP)
- Online multiplayer gaming
- QUIC (HTTP/3, built on top of UDP)

## 9. Summary Table
| Dimension | TCP | UDP |
|---|---|---|
| Connection | Oriented (3-way handshake) | Connectionless |
| Reliability | Reliable (ACKs + retransmit) | Unreliable |
| Ordering | Ordered | Unordered |
| Flow control | Yes (sliding window) | No |
| Congestion control | Yes | No |
| Header size | 20 bytes min | 8 bytes fixed |
| Speed | Slower | Faster |
| Error handling | Retransmission | Checksum only |
| Addressing | Unicast | Unicast / multicast / broadcast |
| Typical apps | HTTP, SSH, FTP, SMTP | DNS, DHCP, NTP, VoIP, streaming |

## 10. When to Choose Which
- Choose **TCP** when data integrity and ordering matter more than latency.
- Choose **UDP** when low latency matters more than perfect delivery, or when
  the application implements its own reliability (e.g., QUIC, WebRTC).

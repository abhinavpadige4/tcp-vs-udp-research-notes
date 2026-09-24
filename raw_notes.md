# Raw Notes — TCP vs UDP Research

Concatenated notes extracted from the top 5 sources in the research plan.
These are paraphrased summaries of the key claims each source makes, kept
verbatim enough to trace back to the original article.

---

## Source 1 — Avast: "TCP vs UDP: Differences Between TCP & UDP Protocols"
URL: https://www.avast.com/c-tcp-vs-udp-difference

- TCP (Transmission Control Protocol) is a connection-oriented protocol that
  establishes a session between sender and receiver before data transfer.
- UDP (User Datagram Protocol) is connectionless — it sends datagrams without
  setting up a session.
- TCP guarantees delivery via acknowledgements and retransmission of lost
  segments. UDP does not guarantee delivery.
- TCP maintains ordering of segments; UDP does not.
- TCP has flow control (sliding window) and congestion control (slow start,
  congestion avoidance, fast retransmit, fast recovery).
- TCP header is 20 bytes minimum (up to 60 with options). UDP header is a
  fixed 8 bytes.
- TCP is slower due to overhead; UDP is faster and lighter.
- TCP examples: HTTP/HTTPS, FTP, SSH, SMTP, email, file transfer.
- UDP examples: DNS, VoIP, video streaming, online gaming, DHCP, SNMP.

---

## Source 2 — AVG: "What Is the Difference Between TCP and UDP?"
URL: https://www.avg.com/en/signal/tcp-vs-udp

- TCP is reliable and ordered; UDP is unreliable and unordered.
- TCP uses a 3-way handshake (SYN, SYN-ACK, ACK) to establish a connection
  and a 4-way teardown to close it.
- UDP has no handshake and no teardown — it just sends.
- TCP provides error checking at the transport layer and retransmits on
  failure; UDP only does a checksum and drops bad packets.
- TCP is used when data integrity matters (web browsing, email, file
  transfer). UDP is used when speed matters more than perfect delivery
  (live video, gaming, voice).
- UDP is preferred for real-time applications because retransmission delay
  is worse than occasional packet loss.

---

## Source 3 — IPCisco: "TCP vs UDP | 10 Key Differences Explained"
URL: https://ipcisco.com/lesson/tcp-versus-udp

- TCP is connection-oriented, reliable, ordered, and slower.
- UDP is connectionless, unreliable, unordered, and faster.
- TCP uses sequence numbers and ACKs; UDP uses only a checksum.
- TCP supports flow control via window size; UDP has no flow control.
- TCP supports congestion control; UDP does not.
- TCP header: 20 bytes (minimum). UDP header: 8 bytes (fixed).
- TCP is full-duplex; UDP is also full-duplex but stateless.
- TCP is used by HTTP, HTTPS, FTP, SSH, SMTP, IMAP, POP3.
- UDP is used by DNS, DHCP, NTP, SNMP, RTP (voice/video), QUIC (built on UDP).
- UDP is often used for broadcast and multicast; TCP is unicast only.

---

## Source 4 — NetworkLessons: "Introduction to TCP and UDP"
URL: https://networklessons.com/network-fundamentals/introduction-to-tcp-and-udp

- Both TCP and UDP are Layer 4 (transport layer) protocols in the TCP/IP
  model, defined in RFC 793 (TCP) and RFC 768 (UDP).
- TCP provides a reliable, ordered, byte-stream service.
- UDP provides an unreliable, datagram service.
- TCP uses ports to identify applications; UDP also uses ports.
- TCP is used for applications that need reliability (web, email, file
  transfer). UDP is used for applications that need speed (streaming,
  gaming, DNS).
- TCP's 3-way handshake adds latency before the first byte of data is sent.
- UDP has no setup latency — the first packet is data.

---

## Source 5 — GeeksforGeeks: "Differences between TCP and UDP"
URL: https://www.geeksforgeeks.org/computer-networks/differences-between-tcp-and-udp

- TCP is a connection-oriented, reliable, ordered protocol.
- UDP is a connectionless, unreliable, unordered protocol.
- TCP uses a 3-way handshake; UDP does not.
- TCP has flow control and congestion control; UDP has neither.
- TCP header size: 20 bytes (minimum). UDP header size: 8 bytes (fixed).
- TCP is slower because of overhead; UDP is faster.
- TCP is used for HTTP, HTTPS, FTP, SSH, SMTP.
- UDP is used for DNS, DHCP, NTP, streaming, gaming, VoIP.
- TCP provides error recovery; UDP does not.
- TCP is used for unicast; UDP supports unicast, multicast, and broadcast.

---

## Cross-source consensus

Every source agrees on the following core facts:

1. TCP is connection-oriented; UDP is connectionless.
2. TCP is reliable and ordered; UDP is unreliable and unordered.
3. TCP has flow control and congestion control; UDP has neither.
4. TCP header is 20 bytes minimum; UDP header is 8 bytes fixed.
5. TCP is slower but safer; UDP is faster but lossy.
6. TCP examples: HTTP/HTTPS, FTP, SSH, SMTP.
7. UDP examples: DNS, DHCP, NTP, streaming, gaming, VoIP.

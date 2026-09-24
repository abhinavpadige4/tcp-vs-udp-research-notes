# 📡 TCP vs UDP — Interview-Ready Reference

> **One-liner:** TCP is connection-oriented, reliable, ordered, and slower.
> UDP is connectionless, unreliable, unordered, and faster.

---

## 🟦 1. Connection Model
> **TCP:** Connection-oriented — 3-way handshake (SYN → SYN-ACK → ACK) before data.
> **UDP:** Connectionless — no handshake, no session state.

- [ ] TCP requires a 3-way handshake before any data is sent
- [ ] UDP has no handshake — the first packet is already data
- [ ] TCP has an explicit teardown (FIN/ACK); UDP has none

---

## 🟩 2. Reliability
> **TCP:** Reliable — ACKs + automatic retransmission of lost segments.
> **UDP:** Unreliable — no ACKs, no retransmission, lost packets are dropped.

- [ ] TCP acknowledges every segment with an ACK
- [ ] TCP retransmits lost or corrupted segments
- [ ] UDP only performs a checksum and drops bad packets
- [ ] UDP does not guarantee delivery

---

## 🟨 3. Ordering
> **TCP:** Ordered — sequence numbers guarantee in-order delivery.
> **UDP:** Unordered — packets may arrive out of sequence.

- [ ] TCP uses sequence numbers to reorder segments
- [ ] UDP does not preserve packet order
- [ ] Ordering is the application's responsibility over UDP

---

## 🟧 4. Flow Control
> **TCP:** Yes — sliding window prevents overwhelming the receiver.
> **UDP:** No — sender has no feedback about receiver capacity.

- [ ] TCP advertises a window size to the sender
- [ ] TCP's sliding window throttles the sender
- [ ] UDP has no flow control mechanism

---

## 🟥 5. Congestion Control
> **TCP:** Yes — slow start, congestion avoidance, fast retransmit, fast recovery.
> **UDP:** No — sender does not adapt to network conditions.

- [ ] TCP backs off when the network is congested
- [ ] TCP uses slow start and congestion avoidance
- [ ] UDP does not adapt to congestion

---

## 🟪 6. Header Size
> **TCP:** 20 bytes minimum (up to 60 with options).
> **UDP:** 8 bytes fixed.

- [ ] TCP header is 20 bytes minimum
- [ ] UDP header is 8 bytes fixed
- [ ] UDP's smaller header reduces per-packet overhead

---

## 🟫 7. Speed
> **TCP:** Slower — handshake, ACKs, retransmissions, window management.
> **UDP:** Faster — no setup, no reliability overhead.

- [ ] TCP's handshake adds latency before the first byte
- [ ] UDP has no setup latency
- [ ] UDP is preferred for real-time applications

---

## ⚪ 8. Use Cases
> **TCP:** HTTP, HTTPS, SSH, FTP, SMTP, IMAP, POP3, databases.
> **UDP:** DNS, DHCP, NTP, VoIP, live streaming, gaming, QUIC.

- [ ] TCP is used for HTTP/HTTPS (web browsing)
- [ ] TCP is used for SSH and FTP (secure transfer)
- [ ] TCP is used for SMTP/IMAP/POP3 (email)
- [ ] UDP is used for DNS (domain resolution)
- [ ] UDP is used for DHCP and NTP
- [ ] UDP is used for VoIP and live video streaming
- [ ] UDP is used for online multiplayer gaming
- [ ] QUIC (HTTP/3) is built on top of UDP

---

## ✅ Key Takeaways

- [ ] TCP = connection-oriented, reliable, ordered, slower, safer
- [ ] UDP = connectionless, unreliable, unordered, faster, lighter
- [ ] TCP header = 20 bytes; UDP header = 8 bytes
- [ ] TCP has flow control + congestion control; UDP has neither
- [ ] Choose TCP when data integrity matters
- [ ] Choose UDP when low latency matters
- [ ] Both are Layer 4 (transport layer) protocols
- [ ] TCP is defined in RFC 793; UDP is defined in RFC 768

---

## 📚 Sources

1. Avast — <https://www.avast.com/c-tcp-vs-udp-difference>
2. AVG — <https://www.avg.com/en/signal/tcp-vs-udp>
3. IPCisco — <https://ipcisco.com/lesson/tcp-versus-udp>
4. NetworkLessons — <https://networklessons.com/network-fundamentals/introduction-to-tcp-and-udp>
5. GeeksforGeeks — <https://www.geeksforgeeks.org/computer-networks/differences-between-tcp-and-udp>

---

> **Note:** This file is a Notion-ready markdown export. To import into Notion:
> Notion → Import → Markdown & CSV → select this file. The `> ` blockquotes
> render as callouts, the `## 🟦` headings render as colored H2s, and the
> `- [ ]` bullets render as checkable to-dos.

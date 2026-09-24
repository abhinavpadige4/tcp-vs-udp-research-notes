# TCP vs UDP — A Clear Comparison

**Short answer:** TCP is a connection-oriented, reliable, ordered protocol with
flow and congestion control — slower but safe. UDP is a connectionless,
unreliable, unordered protocol with no flow or congestion control — faster but
lossy. Both live at Layer 4 (transport layer) of the TCP/IP stack.

---

## TL;DR Table

| Dimension | TCP | UDP |
|---|---|---|
| Connection | **Connection-oriented** (3-way handshake) | **Connectionless** |
| Reliability | **Reliable** (ACKs + retransmission) | **Unreliable** (no ACKs) |
| Ordering | **Ordered** (sequence numbers) | **Unordered** |
| Flow control | **Yes** (sliding window) | **No** |
| Congestion control | **Yes** (slow start, etc.) | **No** |
| Header size | **20 bytes** minimum (up to 60) | **8 bytes** fixed |
| Speed | Slower | Faster |
| Error handling | Retransmission | Checksum only |
| Addressing | Unicast | Unicast / multicast / broadcast |
| Typical apps | HTTP, HTTPS, SSH, FTP, SMTP | DNS, DHCP, NTP, VoIP, streaming |

---

## 1. Connection Model

**TCP is connection-oriented.** Before any data is exchanged, TCP performs a
**3-way handshake**:

1. Client → Server: `SYN`
2. Server → Client: `SYN-ACK`
3. Client → Server: `ACK`

Only after this handshake does data flow. The session is torn down explicitly
with a `FIN`/`ACK` exchange.

**UDP is connectionless.** There is no handshake and no teardown — the sender
just fires datagrams at the receiver. The first packet is already data.

> Sources: Avast, AVG, IPCisco, NetworkLessons, GeeksforGeeks

---

## 2. Reliability

**TCP is reliable.** Every segment is acknowledged (ACK) by the receiver. If a
segment is lost or corrupted, TCP retransmits it automatically. Sequence
numbers and checksums detect loss and corruption.

**UDP is unreliable.** There are no ACKs and no retransmission. UDP performs a
checksum; if a packet fails the checksum it is silently dropped. Whether the
data arrived is the application's problem.

> Sources: Avast, AVG, IPCisco, NetworkLessons, GeeksforGeeks

---

## 3. Ordering

**TCP preserves order.** Sequence numbers let the receiver reassemble segments
in the correct order, even if they arrive out of sequence on the wire.

**UDP does not preserve order.** Packets may arrive out of sequence, and UDP
does nothing to fix that.

> Sources: Avast, IPCisco, NetworkLessons, GeeksforGeeks

---

## 4. Flow Control

**TCP has flow control.** The receiver advertises a **window size** telling the
sender how much data it can currently accept. This prevents the sender from
overwhelming a slow receiver.

**UDP has no flow control.** The sender has no feedback about the receiver's
capacity and just keeps sending.

> Sources: Avast, IPCisco, GeeksforGeeks

---

## 5. Congestion Control

**TCP has congestion control.** Algorithms like **slow start**, **congestion
avoidance**, **fast retransmit**, and **fast recovery** let TCP back off when
the network is congested, protecting the wider network.

**UDP has no congestion control.** The sender does not adapt to network
conditions, which is why UDP-heavy traffic can contribute to congestion.

> Sources: Avast, IPCisco, GeeksforGeeks

---

## 6. Header Size

- **TCP header:** 20 bytes minimum, up to 60 bytes with options.
- **UDP header:** 8 bytes fixed (source port, dest port, length, checksum).

UDP's smaller header means less overhead per packet — a big deal for small,
frequent messages like DNS queries.

> Sources: Avast, IPCisco, GeeksforGeeks

---

## 7. Speed

**TCP is slower** because of the handshake, ACKs, retransmissions, and window
management. The first byte of data cannot be sent until the handshake
completes.

**UDP is faster** because it has no setup and no reliability machinery. The
first packet is data, and there is nothing to wait for.

> Sources: Avast, AVG, IPCisco, GeeksforGeeks

---

## 8. Use Cases

### TCP — when reliability and ordering matter
- **HTTP / HTTPS** — web browsing
- **FTP / SFTP** — file transfer
- **SSH** — secure shell
- **SMTP / IMAP / POP3** — email
- **Database protocols** — MySQL, PostgreSQL
- **Telnet** — remote terminal

### UDP — when speed matters more than perfect delivery
- **DNS** — domain name resolution
- **DHCP** — dynamic host configuration
- **NTP** — time synchronisation
- **VoIP** — voice over IP
- **Live video streaming** — RTP
- **Online multiplayer gaming**
- **QUIC / HTTP/3** — modern transport built on top of UDP

> Sources: Avast, AVG, IPCisco, NetworkLessons, GeeksforGeeks

---

## 9. When to Choose Which

- **Choose TCP** when data integrity and ordering matter more than latency —
  web pages, file transfers, email, databases, anything where a missing byte
  is unacceptable.
- **Choose UDP** when low latency matters more than perfect delivery — live
  video, voice, gaming, DNS lookups, anything where a stale frame is worse
  than a missing frame.
- **Choose UDP + your own reliability layer** (e.g., QUIC, WebRTC) when you
  want UDP's low latency but need reliability — this is the modern trend.

---

## Sources

1. Avast — *TCP vs UDP: Differences Between TCP & UDP Protocols*
   <https://www.avast.com/c-tcp-vs-udp-difference>
2. AVG — *What Is the Difference Between TCP and UDP?*
   <https://www.avg.com/en/signal/tcp-vs-udp>
3. IPCisco — *TCP vs UDP | 10 Key Differences Explained with Table & Examples*
   <https://ipcisco.com/lesson/tcp-versus-udp>
4. NetworkLessons — *Introduction to TCP and UDP*
   <https://networklessons.com/network-fundamentals/introduction-to-tcp-and-udp>
5. GeeksforGeeks — *Differences between TCP and UDP*
   <https://www.geeksforgeeks.org/computer-networks/differences-between-tcp-and-udp>

# TCP vs UDP — Research Notes

A clear, interview-ready comparison of the TCP and UDP transport-layer
protocols, backed by 5 authoritative sources.

## Quick Answer

**TCP** is connection-oriented, reliable, ordered, and slower — it uses a
3-way handshake, ACKs, retransmission, flow control, and congestion control.
**UDP** is connectionless, unreliable, unordered, and faster — no handshake,
no ACKs, no retransmission, no flow or congestion control.

| Dimension | TCP | UDP |
|---|---|---|
| Connection | Oriented (3-way handshake) | Connectionless |
| Reliability | Reliable (ACKs + retransmit) | Unreliable |
| Ordering | Ordered | Unordered |
| Flow control | Yes (sliding window) | No |
| Congestion control | Yes | No |
| Header size | 20 bytes min | 8 bytes fixed |
| Speed | Slower | Faster |
| Typical apps | HTTP, SSH, FTP, SMTP | DNS, DHCP, NTP, VoIP, streaming |

## Files

| File | Purpose |
|---|---|
| [`tcp_udp_comparison.md`](./tcp_udp_comparison.md) | **Primary deliverable** — full markdown answer with citations |
| [`notion_page.md`](./notion_page.md) | Notion-ready markdown export (colored headings + checkable bullets) |
| [`outline.md`](./outline.md) | Outline covering all required difference categories |
| [`extracted_points.json`](./extracted_points.json) | Structured JSON of key points with source IDs |
| [`raw_notes.md`](./raw_notes.md) | Concatenated raw notes from 5 sources |
| [`validation_report.txt`](./validation_report.txt) | Checklist confirming each requirement is satisfied |

## Sources

1. Avast — <https://www.avast.com/c-tcp-vs-udp-difference>
2. AVG — <https://www.avg.com/en/signal/tcp-vs-udp>
3. IPCisco — <https://ipcisco.com/lesson/tcp-versus-udp>
4. NetworkLessons — <https://networklessons.com/network-fundamentals/introduction-to-tcp-and-udp>
5. GeeksforGeeks — <https://www.geeksforgeeks.org/computer-networks/differences-between-tcp-and-udp>

## Note on Notion

The plan asked for a live Notion page. No Notion API tool was available in
this environment, so the Notion deliverable is provided as
[`notion_page.md`](./notion_page.md) — a markdown export that can be
imported into Notion via **Notion → Import → Markdown & CSV**. The colored
emoji headings render as colored H2s, blockquotes render as callouts, and
`- [ ]` bullets render as checkable to-dos.

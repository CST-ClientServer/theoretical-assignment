# COMP 3940 Theoretical Assignment  

---

## Q1. [1 mark] Throughput of a TCP connection  

**Given:**  
- Window Size = 16,000 bytes  
- RTT = 200 ms = 0.2 seconds  

### Calculation:  
Throughput = **Window Size / RTT**  
Throughput = 16,000 bytes / 0.2 seconds = **80,000 bytes/second**  

Convert to bits per second:  
80,000 bytes/second × 8 bits/byte = **640,000 bits/second = 640 Kbps**  

**Answer:**  
The throughput of the TCP connection is **640 Kbps**.

---

## Q2. [2 marks] Time to transfer an image over TCP  

**Given:**  
- Network speed = 8 Mbps  
- Data segment size = 800 bytes  
- Total overhead per segment = 100 bytes  
- ACK packet size = 100 bytes  
- Send buffer size = 32,000 bytes  
- Initial congestion window = 10 segments  
- File size = 6.4 MB = 6,553,600 bytes (assuming 1 MB = 1,024,000 bytes)  

### Part 1: Propagation delay negligible  

1. Total segments = **6,553,600 bytes / 800 bytes/segment = 8,192 segments**  
2. Segment size = **800 bytes (data) + 100 bytes (overhead) = 900 bytes**  
3. Time per segment = **900 bytes × 8 bits/byte / 8 × 10⁶ bits/sec = 0.9 ms**  
4. Time per ACK = **100 bytes × 8 bits/byte / 8 × 10⁶ bits/sec = 0.1 ms**  
5. Total time per segment = **0.9 ms + 0.1 ms = 1 ms**  
6. Total time = **8,192 segments × 1 ms/segment = 8.192 seconds**  

**Answer:**  
It will take approximately **8.192 seconds** to transfer the image when propagation delay is negligible.  

---

### Part 2: RTT = 2 seconds  

1. Max segments per window = **32,000 bytes / 900 bytes/segment ≈ 35 segments**  

**Window growth:**  
- **First RTT:** Send initial 10 segments  
- **Second RTT:** Window size doubles to 20 segments  
- **Third RTT:** Window size doubles to 40 segments (capped at 35 segments due to send buffer)  
- Segments sent = **10 + 20 + 35 = 65 segments**  

2. Remaining segments = **8,192 − 65 = 8,127 segments**  
   - RTTs required = **8,127 segments / 35 segments/RTT ≈ 232.2 RTTs**  
   - Total RTTs = **3 initial RTTs + 232.2 RTTs ≈ 235.2 RTTs**  

3. Total time = **235.2 RTTs × 2 seconds/RTT ≈ 470.4 seconds**  

**Answer:**  
It will take approximately **470.4 seconds** to transfer the image when the RTT is 2 seconds.

---

## Q3. [2 marks] VoIP streams on a channel  

**Given:**  
- Packet interval = 20 ms = 0.02 seconds  
- Voice data per packet = 160 bytes  
- Channel rate = 3.2 Mbps  
- Maximum acceptable delay = 20 ms  

### Calculation:  
1. Packet size = **160 bytes × 8 bits/byte = 1,280 bits**  
2. Data rate per stream = **1,280 bits / 0.02 seconds = 64,000 bps**  
3. Transmission time = **1,280 bits / 3,200,000 bps = 0.0004 seconds = 0.4 ms**  
4. Available time window per packet = **20 ms**  
5. Number of streams = **20 ms / 0.4 ms/packet = 50 streams**  
6. Total data rate = **50 streams × 64,000 bps/stream = 3,200,000 bps**  

**Answer:**  
Approximately **50 VoIP streams** can be accommodated on the channel.

---

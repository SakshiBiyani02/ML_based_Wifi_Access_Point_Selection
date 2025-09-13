
# Machine Learning-Based Access Point Selection and Rate Adaptation for Wi-Fi Networks in NS-3  

## Introduction  
Wi-Fi networks are essential for connectivity in homes, enterprises, and academic spaces. However, in dense environments like hostels, classrooms, and offices, users often face poor connectivity due to:  
- Overlapping Access Points (APs)  
- Weak signals  
- Congestion  

Traditional static methods for AP selection and rate control cannot adapt to real-time conditions.  

This project proposes a **Machine Learning-based adaptive solution** that dynamically selects the optimal AP and adjusts transmission rates. The goal is to:  
- Improve throughput  
- Reduce latency  
- Ensure stable Wi-Fi connectivity in crowded, dynamic environments  

---

## Problem Statement  
Most Wi-Fi clients connect to the AP with the strongest signal using predefined rate control algorithms. This ignores:  
- Interference  
- Packet loss  
- AP load  
- Historical performance  

As a result:  
- Users connect to overloaded APs  
- High latency, packet drops, and reduced throughput occur  
- Existing rate adaptation methods react too late  

➡ Our approach: A **context-aware ML-based model** that proactively selects APs and adjusts rates using real-time + historical data.  

---

##  Objectives  
- Enable **adaptive and intelligent Wi-Fi behavior**  
- Improve **AP selection** using real-time metrics (RSSI, SNR, delay)  
- Build a **data-driven ML model** for AP + rate prediction  
- Reduce **packet loss, latency, and connection drops** in dense areas  
- Evaluate **ML vs. traditional static methods**  
- Provide a **scalable, automated approach** for Wi-Fi optimization  

---

##  Proposed Methodology  
1. **Simulate Wi-Fi environment** in NS-3 with multiple APs + STAs under congestion/delay/packet loss  
2. **Extract features**: RSSI, SNR, delay, throughput, packet loss  
3. **Build dataset** with features and optimal AP + rate labels  
4. **Train ML models** (Reinforcement Learning) in Python  
5. **Real-time prediction** using a Python module  
6. **Simulate ML decisions** by feeding back into NS-3  
7. **Compare performance** with static AP + rate selection methods  

---

## Expected Outcomes  
- Trained **ML model** for AP selection + rate adaptation  
- **Integrated simulation + prediction framework** with real-time scanning  
- Improved **throughput, latency, and fairness**  
- **Comparative analysis** with traditional methods  
- A reusable **dataset for academic research**  

---

## Tools & Technologies  

| Tool / Platform       | Purpose |
|------------------------|---------|
| **NS-3**              | Wi-Fi network simulation (APs, STAs, congestion) |
| **C++**               | Custom NS-3 simulation scripts |
| **Python**            | ML model development & integration |
| **Stable-Baselines3, Gym** | Reinforcement Learning implementation |
| **Pandas, NumPy**     | Data handling & processing |
| **Matplotlib, Seaborn** | Visualization of results |
| **Google Colab / Jupyter** | Model training & testing |
| **Ubuntu (WSL / Dual Boot)** | Execution of NS-3 simulations |

## 📈 Results & Evaluation  

We compared two approaches for **Access Point (AP) selection and rate adaptation**:  

### RSSI-Only Based Model  
This model selects APs based solely on **signal strength (RSSI)**.  
==== Testing Metrics ====
Top-1 Accuracy: 0.0268
Top-5 Accuracy: 0.1709
Very poor performance due to ignoring congestion, packet loss, and other critical network factors.  

---

### Composite Score + ML Model  
This approach uses a **composite score** with **6 parameters**:  
- RSSI  
- Packet Loss  
- Congestion  
- Jitter  
- Throughput  
- Capacity  

Trained with ML models, it significantly improves AP selection accuracy.  
==== Testing Metrics ====
Top-1 Accuracy: 0.8165
Top-5 Accuracy: 0.9771

**Result:** The composite ML-based method **vastly outperforms** the RSSI-only approach, achieving over **81% Top-1 accuracy** and nearly **98% Top-5 accuracy**.  

---

##  Conclusion  
- **RSSI-only methods** are unreliable in dense environments.  
- **Composite ML-based models** capture more realistic network conditions, leading to robust and intelligent AP selection.  
- Our method demonstrates a **30x improvement in Top-1 accuracy** compared to traditional RSSI-based selection.  

---

---

## Future Scope  

While the project demonstrates significant improvements in AP selection and rate adaptation using ML models, there are several promising extensions:  

###  Full Integration with NS-3  
- Build a **tight coupling between the trained ML model and NS-3** so that AP selection and rate adaptation decisions are made in real-time during simulation.  
- Use the **ns3-gym framework** to connect reinforcement learning agents directly with NS-3 for interactive training and evaluation.  
- Enable **closed-loop simulation** where the ML model continuously adapts to network state feedback.  

###  Real-Time Data Testing  
- Collect **real Wi-Fi performance metrics** (RSSI, packet loss, jitter, throughput, congestion, AP load) from testbeds or live environments.  
- Feed this data into the trained ML model to validate predictions beyond simulation.  
- Compare performance in **controlled NS-3 simulations** vs. **real-world networks** to measure generalization ability.  

###  Scalability & Generalization  
- Extend the model to **support heterogeneous Wi-Fi standards** (802.11n/ac/ax).  
- Optimize for **multi-floor or campus-wide networks** with overlapping APs.  
- Explore **online learning** so the model can keep improving with new data in changing environments.  

###  Deployment  
- Develop a **lightweight Python or C++ agent** that can run on Wi-Fi clients (laptops, IoT devices, smartphones).  
- Integrate with **Linux Wi-Fi drivers** for live AP selection and rate control.  
- Enable **real-time visualization dashboards** for network administrators to monitor AP allocation and performance.  

---




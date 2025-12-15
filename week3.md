# 🚀 Week 3 – Application Selection for Performance Testing

---

## 🎯 Purpose of Application Selection

The objective of this phase is to select a range of applications that generate **different workload types** in order to evaluate how the Linux operating system behaves under varying performance demands. By testing multiple workload categories, it is possible to identify system bottlenecks, analyse resource utilisation, and evaluate trade-offs between performance, stability, and security.

The selected applications are lightweight, widely used, and suitable for execution on a headless Linux server accessed remotely via SSH.

---

## 📊 Application Selection Matrix

The following matrix lists the selected applications, the workload type they represent, and the justification for their inclusion in the performance evaluation.

| 🧩 Application | Workload Type      | Justification                                                                     |
| -------------- | ------------------ | --------------------------------------------------------------------------------- |
| **stress-ng**  | CPU-intensive      | Generates controlled CPU load to evaluate scheduling and CPU saturation behaviour |
| **memtester**  | Memory-intensive   | Tests memory allocation, utilisation, and stability under pressure                |
| **fio**        | Disk I/O-intensive | Simulates realistic read/write workloads to analyse disk performance              |
| **iperf3**     | Network-intensive  | Measures network throughput and bandwidth between workstation and server          |
| **nginx**      | Server / Service   | Represents a real-world server application handling client requests               |

This combination ensures coverage of CPU, memory, storage, network, and service-level workloads.

---

## 🛠️ Installation Documentation

All applications will be installed on the server system remotely via SSH using the system package manager. The following commands document the exact installation process:

```bash
sudo apt update
sudo apt install stress-ng memtester fio iperf3 nginx -y
```

Installing applications via the package manager ensures that software is sourced from trusted repositories and kept up to date with security patches.

---

## 📈 Expected Resource Profiles

Before testing, expected resource usage was identified for each application to support meaningful analysis and comparison with observed results.

| Application | Expected CPU Usage | Expected Memory Usage | Expected Disk I/O | Expected Network Usage |
| ----------- | ------------------ | --------------------- | ----------------- | ---------------------- |
| stress-ng   | Very High          | Low                   | Minimal           | None                   |
| memtester   | Low                | Very High             | Minimal           | None                   |
| fio         | Moderate           | Low                   | Very High         | None                   |
| iperf3      | Low                | Low                   | None              | Very High              |
| nginx       | Low–Moderate       | Low                   | Low               | Moderate               |

These expectations provide a baseline for identifying anomalies and performance bottlenecks during testing.

---

## 📡 Monitoring Strategy

Performance monitoring will be conducted remotely from the workstation system using SSH to avoid introducing additional load on the server. Each workload will be monitored using appropriate command-line tools selected during the planning phase.

* **CPU and process activity** will be monitored using `top` or `htop`
* **Memory usage** will be monitored using `free -h`
* **Disk I/O performance** will be analysed using `iostat`
* **Network latency and throughput** will be measured using `ping` and `iperf3`

Metrics will be captured during baseline operation and while workloads are running, enabling direct comparison between idle and stressed system states.

---

## 🧠 Reflection

This phase demonstrated the importance of selecting representative workloads when evaluating operating system performance. By choosing applications that stress different subsystems, it becomes possible to observe how resource contention, scheduling, and configuration choices impact overall system behaviour.

The selected applications provide a balanced and realistic foundation for performance evaluation in later phases of the coursework, supporting quantitative analysis and informed optimisation decisions.

---


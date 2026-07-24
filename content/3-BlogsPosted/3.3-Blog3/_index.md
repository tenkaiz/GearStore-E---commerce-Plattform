---
title: "Blog 3"
date: 2026-07-18
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# How Stratasys Built an IoT Platform for Industrial 3D Printers with AWS IoT

In recent years, 3D printing technology is no longer just for product prototyping but has become a critical part of many industries such as aerospace, automotive, healthcare, and consumer goods manufacturing. However, as the number of 3D printers grows and deploys across multiple factories, enterprises face a new challenge: how to manage, monitor, and effectively leverage the entire printer fleet in real time?

If each machine operates as an isolated silo, data becomes fragmented, device status tracking grows difficult, and maintenance relies heavily on reactive troubleshooting after outages occur. This not only reduces operational efficiency but directly impacts overall production productivity.

To address these challenges, Stratasys partnered with AWS to build the **GrabCAD IoT Platform** – an Edge-to-Cloud connected IoT infrastructure. The platform uses **AWS IoT Core** and **AWS IoT Greengrass** to collect, normalize, and analyze data from industrial 3D printers, providing a foundation for operational optimization and future AI feature development.

![GrabCAD IoT Platform Architecture Diagram](/images/3-BlogsPosted/blog3.jpg "Industrial 3D printer IoT platform architecture with AWS IoT")

---

### Why Is This IoT Platform Necessary?
When an enterprise owns dozens or hundreds of 3D printers across multiple geographical locations, manual management is no longer feasible.

Previously, data from each printer was stored separately, making it hard to track real-time machine health or evaluate overall system performance. Technical teams struggled to detect early anomaly indicators, mostly reacting only after machines failed, increasing downtime and decreasing Overall Equipment Effectiveness (OEE).

Additionally, industrial manufacturing environments impose strict security requirements between Operational Technology (OT) and Information Technology (IT) networks. Connecting data to the cloud requires strong security while retaining flexibility to integrate with management systems like MES or ERP.

Therefore, Stratasys needed an IoT platform capable of local processing at the Edge while ensuring secure connectivity to AWS Cloud and seamless future scalability.

---

### How Does GrabCAD IoT Platform Work?
The GrabCAD IoT Platform is built on an **Edge-to-Cloud** architecture:

- At factory premises, **AWS IoT Greengrass** runs on Edge Gateway devices placed next to 3D printers. This service handles data processing locally before transmitting to the cloud. Local processing reduces bandwidth consumption, lowers costs, and ensures continuous operation even during internet connectivity losses.
- Once processed, data transmits to **AWS IoT Core**, serving as a secure communication gateway between devices and cloud systems. AWS IoT Core supports bi-directional MQTT communication, enabling Stratasys to monitor real-time device health while sending remote control commands or software updates.
- Notably, the platform utilizes **Device Shadow** to persist digital twin states of every 3D printer. Even if a device goes temporarily offline, the system retains the latest state information and syncs automatically upon reconnection.

---

### Normalizing Data to Build an AI Foundation
To analyze data consistently across diverse printer lines, Stratasys adopts the **MTConnect** industrial standard. Through MTConnect, machine states, sensor metrics, error codes, and utilization rates are normalized prior to storage.

Data is then ingested into an **Amazon S3 Data Lake** via AWS services, establishing a foundation for multiple purposes:
- Equipment performance tracking.
- Production operations analytics.
- Audit compliance requirements.
- Training future Machine Learning models.

Normalizing data from the start makes integration straightforward with MES, ERP, or advanced analytics platforms.

---

### Key Benefits Delivered by the Platform
For customers using Stratasys printers, the GrabCAD IoT Platform delivers significant operational improvements:
- Real-time monitoring allows early anomaly detection, reducing machine downtime and boosting Overall Equipment Effectiveness (OEE).
- The **ARMS** remote monitoring service identifies faults before impacting production, **shortening incident resolution time by ~38%** compared to traditional support methods.
- Over-the-Air (OTA) software update support ensures security patches and new features deploy rapidly without requiring field engineers on-site.

For Stratasys, aggregating data across printer fleets yields valuable insights into real-world product usage. Anonymized data drives hardware and software enhancements and fuels new feature development tailored to customer needs.

---

### Beyond Device Monitoring
What I find impressive is that GrabCAD IoT Platform extends beyond simple cloud connectivity. It functions as a data infrastructure powering future AI capabilities.

According to Stratasys' roadmap, upcoming AI features include:
- Smart AI-powered print scheduling.
- Computer vision for real-time print quality inspection.
- Predictive Maintenance.
- Automated root cause failure analysis.
- AI-driven inventory and consumable management.
- Closed-loop Process Control during printing.

These capabilities transform the platform from passive data collection into an autonomous, self-optimizing, real-time decision-making system.

---

### Is Implementation Simple?
**Not completely.**  
AWS provides foundational building blocks like AWS IoT Core, AWS IoT Greengrass, and Amazon S3. However, constructing a complete industrial IoT platform requires device data normalization, edge architecture design, OT/IT security alignment, and integration with legacy management systems.

This is why Stratasys partnered with **GreenCustard** – an AWS Partner specializing in IoT solutions – to ensure secure and effective implementation.

---

### Personal Perspective & Conclusion
In my view, the greatest value of GrabCAD IoT Platform is not just connecting 3D printers to the internet, but turning operational data into a strategic business asset.

When printer data is standardized and centralized, enterprises can effortlessly analyze performance, discover trends, and build AI applications to optimize production workflows. What I love about this architecture is AWS offering a complete IoT ecosystem – from Edge processing and secure transport to Cloud storage and analytics – enabling smooth transition to smart manufacturing without replacing existing infrastructure.

* **Facebook post link in AWS Study Group VN:** [View post on Facebook](https://www.facebook.com/share/p/19E1XeurX2/)
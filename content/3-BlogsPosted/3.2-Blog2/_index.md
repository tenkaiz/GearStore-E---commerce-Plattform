---
title: "Blog 2"
date: 2026-07-18
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Industrial Physical AI on AWS with Galeo Tech and Multiverse Computing

When mentioning AI, many people often think of model training with large data in the cloud. However, for industries such as manufacturing, energy, logistics, or healthcare, the real challenge lies not only in building an accurate model but also in how to deploy, operate, and continuously update that model across hundreds or thousands of Edge Devices.

In industrial environments, data is continuously generated from sensors, machinery, and production lines. If data collection is unstable or the AI model cannot be deployed efficiently on hardware with limited resources, the value of AI is significantly reduced.

To solve this problem, AWS collaborated with **Galeo Tech** and **Multiverse Computing** to build a comprehensive Physical AI solution. Galeo Tech handles the data collection and MLOps pipeline from edge devices to the cloud, while Multiverse Computing optimizes and compresses AI models so they can run efficiently on industrial equipment.

![Industrial Physical AI Architecture Diagram](/images/3-BlogsPosted/blog2.jpg "Industrial Physical AI architecture lifecycle on AWS")

---

### Why Does Physical AI Need More Than an AI Model?
In many traditional AI projects, once the model is successfully trained, the work is almost done. However, with Physical AI, this is just the beginning.

Industrial devices often operate for years under unstable network conditions, constrained hardware resources, and stringent reliability requirements. This makes model updates, version management, and data synchronization a major challenge.

Without a proper MLOps pipeline, every model upgrade would have to be performed manually on each device, wasting time and increasing the risk of errors. That is why AWS builds an end-to-end AI lifecycle, keeping data and models continuously updated between cloud and edge systems.

---

### How Does Galeo Tech Address Data Collection and MLOps?
Galeo Tech focuses on bridging industrial Operational Technology (OT) systems with the AWS cloud platform.

In practice, data comes from various sources such as PLC, SCADA, OPC UA, MQTT, or Modbus. These systems were not originally designed for Machine Learning, making data normalization a critical step.

Through services like **AWS IoT Core**, **AWS IoT Greengrass**, **AWS IoT SiteWise**, **Amazon Kinesis**, and **Amazon S3**, factory data is collected, normalized, and stored into an AWS Data Lake. Even during internet outages, Edge Gateways can store data locally and auto-sync when connection is restored.

In reverse, when a new model version is uploaded to Amazon S3, **AWS Lambda** automatically identifies target device groups via **Amazon DynamoDB**, packages the model into an AWS IoT Greengrass component, and deploys it to the right devices. This enables automated AI model updates across hundreds or thousands of devices without manual work.

---

### Multiverse Computing Makes AI Models Lighter
A common issue in modern AI is that models are growing larger. Meanwhile, most industrial devices only have CPUs or GPUs with restricted memory. Directly deploying these large models results in slow inference speed, high memory usage, and heavy power consumption.

To solve this, Multiverse Computing developed **CompactifAI**, a model compression technology inspired by tensor networks and quantum computing. Unlike traditional pruning or quantization methods, CompactifAI analyzes the inner structure of neural networks to remove redundant components while preserving core critical information.

The optimization process consists of 3 steps:
1. Analyze model structure.
2. Perform compression using optimization algorithms.
3. Retrain (heal) the model to restore accuracy.

According to Multiverse Computing benchmark results, CompactifAI can **reduce model size by up to 80%**, **lower inference costs by 50–80%**, **double processing throughput**, and drastically reduce power consumption while maintaining near-zero accuracy loss. This is essential for AI applications on robots, drones, and automated manufacturing systems.

---

### Complete AI Lifecycle on AWS
What I appreciate most in this solution is that AWS does not just focus on model training, but builds the complete AI lifecycle:

- Data collection begins at industrial edge devices, then data is pushed to Amazon S3 for training using **Amazon SageMaker**.
- Once the model is generated, CompactifAI optimizes and compresses it before saving the new version to Amazon S3.
- Next, AWS Lambda, Amazon DynamoDB, and AWS IoT Greengrass automatically deploy the model to target device groups in staged rollouts to reduce deployment risks.
- Finally, inference results and operational data are sent back to the Data Lake for future re-training iterations.

Thus, the whole system forms a continuous AI loop where data improves models, and models generate new data for ongoing optimization.

---

### Not Just for Manufacturing Factories
Although example use cases focus on industrial manufacturing, this architecture applies broadly across other fields:
- Smart Factories.
- Autonomous Robotics.
- Industrial Drones.
- Energy Monitoring Systems.
- Healthcare.
- Logistics & Smart Warehousing.
- Smart Cities.

The common denominator across these sectors is the need for low-latency Edge data processing combined with centralized Cloud management.

---

### Is Implementation Simple?
**Not completely.**  
AWS provides almost all foundational services like IoT Core, Greengrass, SageMaker, Lambda, and DynamoDB. However, to succeed in industrial environments, enterprises still face challenges in OT system integration, data normalization, MLOps pipeline construction, and hardware-specific model optimization.

That is why specialized partners like Galeo Tech and Multiverse Computing are vital. They do not replace AWS services, but add specialized components that shorten deployment timelines and reduce project complexity.

---

### Personal Perspective & Conclusion
In my view, the most impressive highlight of this solution is not a single AWS service, but how AWS connects the entire Physical AI lifecycle into a seamless closed loop.

Previously, many enterprises could build good AI models but struggled with deployment, updates, and operations across thousands of industrial devices. With this architecture, AWS and its partners help automate almost the entire workflow from data collection and training to model optimization, deployment, and monitoring.

* **Facebook post link in AWS Study Group VN:** [View post on Facebook](https://www.facebook.com/share/p/1Eat9Gbha2/)
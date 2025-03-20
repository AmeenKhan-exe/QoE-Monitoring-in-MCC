QoE Monitoring & Adaptive Response System
🚀 A cloud-native system for real-time QoE (Quality of Experience) monitoring, analysis, and adaptive optimization using Google Cloud (BigQuery, Cloud Functions, Pub/Sub, Firebase, and Vertex AI).

🔹 Overview
This project automates QoE monitoring and response using GCP services. It detects network performance issues (high latency, jitter, packet loss) and automatically applies adaptive actions like:
✔ Scaling cloud resources dynamically 🚀
✔ Adjusting packet throughput to optimize network traffic 🔄
✔ Triggering user feedback surveys in Firebase 📱
✔ AI-powered adaptation using Vertex AI 🤖

🔹 Features
✅ Real-Time QoE Data Collection: Mobile & Cloud Agents collect network metrics 📊
✅ BigQuery Analytics: Stores QoE data & enables trend analysis 📈
✅ Automated Adaptive Actions: Uses Pub/Sub & Cloud Functions to optimize QoE dynamically 🔥
✅ User Feedback Integration: Firebase Surveys collect real-world QoE ratings ⭐
✅ ML-Based Anomaly Detection: Vertex AI detects abnormal QoE drops & suggests fixes 🤖

🔹 Architecture
The system is built on Google Cloud Platform (GCP) with the following components:

📡 QoE Data Collection: TShark (packet capture), Mobile Agents, and Cloud Monitoring
🗄️ Storage & Analysis: BigQuery for real-time analytics
🚀 Adaptive Response: Cloud Functions triggered via Pub/Sub
🤖 AI Optimization: Vertex AI suggests adaptive strategies
📱 User Feedback: Firebase Surveys log user experience
🔹 Setup Instructions
1️⃣ Enable Required GCP Services
Run in Cloud Shell:

gcloud services enable cloudfunctions.googleapis.com pubsub.googleapis.com compute.googleapis.com bigquery.googleapis.com aiplatform.googleapis.com
2️⃣ Deploy Cloud Function for QoE-Based Adaptation

gcloud functions deploy QoE_Adaptive_Response \
  --runtime python39 \
  --trigger-topic QoE_alerts \
  --entry-point qoe_adaptation
3️⃣ Create Pub/Sub Topic & Subscription

gcloud pubsub topics create QoE_alerts
gcloud pubsub subscriptions create qoe-adaptation-sub --topic=QoE_alerts
4️⃣ Export Firebase Feedback to BigQuery
Enable Firebase Analytics → Link it to BigQuery

🔹 Example Queries for BigQuery Analysis
Check QoE Trends (Last 24 Hours)

SELECT timestamp, latency, jitter, packet_loss, adaptation_action
FROM `your-project-id.QoE_History.QoE_Metrics`
WHERE timestamp > TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 24 HOUR)
ORDER BY timestamp DESC;
Analyze User Feedback in BigQuery

SELECT event_timestamp, event_params.key AS feedback_type, event_params.value.string_value AS feedback_value
FROM `your-project-id.analytics_123456789.events_*`
WHERE event_name = "QoE_feedback"
ORDER BY event_timestamp DESC;
🔹 Future Enhancements
🔹 Integrate AI-driven predictive analytics using AutoML 🚀
🔹 Optimize network routing dynamically using Cloud Load Balancer 🏗️
🔹 Enhance anomaly detection with real-time alerts 📡

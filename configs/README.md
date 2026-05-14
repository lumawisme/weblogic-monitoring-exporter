# Universal WebLogic Observability Exporter

This repository is a customized  fork of the official [Oracle WebLogic Monitoring Exporter](https://github.com/oracle/weblogic-monitoring-exporter). 

It contains the core Oracle exporter engine, alongside our team's **Universal Master Configuration Profile**, engineered to provide lean, high-performance telemetry for WebLogic environments of any size (Standalone, Clustered, VM, or Containerized) with direct integration into Zabbix.

## 🌟 Key Features

* **Universal Baseline:** Pre-configured for core JVM, JDBC, Thread Pool, and JMS metrics.
* **Metric Safety:** Strict adherence to numeric float requirements to prevent Prometheus/Zabbix parsing errors.
* **Subsystem Dictionary:** Advanced enterprise subsystems (Clusters, EJB, Web Services, WLDF) are pre-mapped but left inactive by default to prevent thread starvation and metric float.
* **Zabbix Native:** Designed to perfectly map 1:1 with our centralized Zabbix WebLogic Exporter templates.

## 📂 Repository Structure

* `/configs/` - **(Start Here)** Contains our custom telemetry profiles, including the `universal-master-config.yml`.
* `/src/` - The core Java source code (Maintained by Oracle upstream).
* `/samples/` - Default examples provided by Oracle.

---

## 🚀 Quick Start Guide

To use this exporter, you must package the base exporter application with our custom YAML configuration into a deployable `.war` file.

### 1. Build the Custom `.war` File
Assuming you have the base `weblogic-monitoring-exporter.war` file ready, run the following command to inject our Universal Master Configuration:

```bash
java -jar weblogic-monitoring-exporter.war -config configs/universal-master-config.yml -out wls-exporter.war

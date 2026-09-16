# AWS Cloud Capstone Project

## Secure & Highly Available Web Application on AWS

A cloud-based web application deployed on Amazon Web Services using a custom VPC, Amazon EC2, Amazon S3, IAM, Amazon CloudWatch, and Amazon SNS.

## 🌐 Live Website

**[Open the Live AWS Website](http://13.126.96.106)**

The website is hosted on an Ubuntu EC2 instance running Nginx.

---

## 🏗️ Architecture

The project uses a custom AWS network with two public subnets distributed across different Availability Zones.

### Architecture Components

- Amazon VPC
- Two Public Subnets
- Internet Gateway
- Public Route Table
- Amazon EC2
- Nginx Web Server
- Amazon S3
- AWS IAM
- Amazon CloudWatch
- Amazon SNS

### High-Level Flow

```text
                         Internet
                            │
                            ▼
                  ┌──────────────────┐
                  │ Internet Gateway │
                  └────────┬─────────┘
                           │
                           ▼
              ┌─────────────────────────┐
              │      Custom VPC          │
              │       10.0.0.0/16       │
              │                         │
              │  ┌──────────────────┐   │
              │  │ Public Subnet 1  │   │
              │  │   EC2 + Nginx    │   │
              │  └──────────────────┘   │
              │                         │
              │  ┌──────────────────┐   │
              │  │ Public Subnet 2  │   │
              │  └──────────────────┘   │
              └─────────────────────────┘

                       │
             ┌─────────┴─────────┐
             ▼                   ▼
       ┌───────────┐       ┌────────────┐
       │    S3     │       │ CloudWatch │
       │  Storage  │       │ Monitoring │
       └───────────┘       └─────┬──────┘
                                │
                                ▼
                         ┌────────────┐
                         │    SNS     │
                         │Email Alert │
                         └────────────┘

# Threat-Hunting-Log-Analysis-SSH-Brute-Force-Campaign-Detection
This repository documents the second phase of a technical security operations deployment, transitioning from data ingestion to active threat hunting. Building on the initial SIEM environment setup, this project analyzes a dataset of 3,000 OpenSSH server logs to uncover, track, and visualize an automated brute-force attack campaign using advanced Search Processing Language (SPL).

## Core Objectives
*   **Advanced SPL Querying:** Leveraged Search Processing Language for precise threat hunting, data filtering, and log correlation.
*   **Threat Intelligence Extraction:** Identified specific brute-force attack vectors, isolated the Top 5 malicious IP addresses, and extracted the most frequently targeted user accounts.
*   **Data Visualization:** Mapped timestamp data to construct dynamic timecharts detailing the hourly distribution of attacks and overall campaign metrics.

## Technical Execution & Methodology
1.  **Noise Filtering:** Initial unstructured searches returned an overwhelming volume of baseline server events. I refined the scope by explicitly querying for authentication failures (e.g., `status="Failed"`).
2.  **Statistical Correlation:** I piped the filtered results into statistical commands (`stats count by`) to isolate the exact source IPs and targeted usernames driving the high-volume authentication attempts.
3.  **Timeline Reconstruction:** Utilized the `timechart` command to map the attack frequency over time. This completely uncovered the adversary's timeline, proving the systematic and automated nature of the brute-force campaign hidden within a sea of 3,000 events.

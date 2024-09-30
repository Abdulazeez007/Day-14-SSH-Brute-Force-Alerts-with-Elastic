# Day-14-SSH-Brute-Force-Alerts-with-Elastic

In today’s digital landscape, securing remote access to servers is more critical than ever. SSH (Secure Shell) brute force attacks are one of the most common threats, where attackers attempt to gain unauthorized access by systematically guessing passwords. These attacks can lead to severe security breaches, data loss, and compromised systems. In this guide, we’ll walk you through the process of setting up alerts and visualizations in Elastic to effectively detect and monitor these attacks, empowering you to take proactive measures to safeguard your infrastructure.

## Why Monitor for SSH Brute Force Attacks?
Understanding the importance of monitoring SSH brute force attacks is crucial for maintaining a robust security posture. Here are key reasons why this monitoring is essential:

- **Early Detection:** Identifying attack attempts early allows for rapid response.
- **Pattern Recognition:** Understanding attack patterns helps improve overall security posture.
- **Compliance:** Many security standards require monitoring and alerting for unauthorized access attempts.
- **Resource Protection:** Prevent system overload from repeated login attempts.

## Setting Up the Alert
Before creating an alert, it’s crucial to understand what constitutes a brute force attack. We’ll focus on three key elements:

1. Failed login attempts
2. Targeted user accounts
3. Source IP addresses

### Configuring the Alert
1. Navigate to Elastic and click the hamburger icon, then select “Discover.”
2. Identify the relevant fields in your Elastic log for failed activities, usernames, and source IPs.
3. Save your work by clicking the “Save” button in the top right corner.
4. Click the “Alert” button and choose “Create search threshold rule.”
5. Name your alert appropriately.
6. Elastic will suggest a query based on your selected fields. Adjust the threshold as needed.
7. Save the rule to activate your alert.

## Creating a Visualization Dashboard
To gain insights into the origin of these attacks, we’ll create a geographic dashboard.

### Building the Map
1. From the hamburger menu, select “Maps” under the Analytics tab.
2. In the KQL syntax field, enter your query:

```bash
system.auth.ssh.event: * and agent.name: Pheonix-Linux-Pheonixrocks and system.auth.ssh.event: Failed
```

3. Click “Add Layer” and select “Choropleth” to shade attack origin areas.
4. Use EMS boundaries to display world countries.
5. Set the join field to `source.geo.country_iso_code` for better accuracy.
6. Save your map with a title like “SSH Failed Authentication.”

### Creating the Dashboard
1. Click “Add to Dashboard” and select “Create New Dashboard.”
2. Name your dashboard (e.g., “SSH Failed Authentication”).
3. Adjust the time range to suit your monitoring needs (e.g., last 30 days or Today).

## Conclusion
With these steps completed, you now have a robust system for detecting SSH brute force attempts. Your alert will notify you of potential attacks, while the dashboard provides a visual representation of attack origins. This setup enhances your ability to respond quickly to security threats and understand attack patterns over time.

Remember to regularly review and adjust your alert thresholds and dashboard settings to ensure they remain effective as your environment changes. By incorporating these monitoring practices, you’re taking a proactive approach to security, protecting your systems from potential breaches, and gaining valuable insights into the threat landscape facing your organization.


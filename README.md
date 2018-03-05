# Altprobe

Altprobe is a component of the Alertflex project, it has functional of a collector according to SIEM/Log Management terminologies. 

## Advantages of using Altprobe
* Based on filtering policies, Altprobe extracts events with high priority from flows of data generated by Wazuh HIDS and Suricata NIDS, makes for these events aggregation and normalization. It allows to simplify alerts and incidents management, reduces noise from a minor events.
* Indicator of Compromise hunting (The Open Source Threat Intelligence Platform MISP is used)
* Reports about a network activities and IP addresses reputation for processes on a hosts (based on events from Sysmon for Windows and Auditd for Linux, received via Wazuh IDS)
* Recognition a Host IDS agents name space inside Alerts and Netflow events, generated by Network IDS 
* SSL protocol with two-way authentication is used for secure of connections between remote and central nodes
* All logs are sent in an accumulated state inside compressed data blocks to prevents of events overflow
* In a case of loss of connection between remote and central nodes, the collector persists all alerts locally in file

## Integration with GrayLog and MISP
In tandem with Alertflex controller (see AlertflexCtrl repository on this GitHub profile), 
Altprobe can integrate a Wazuh Host IDS (OSSEC fork) and Suricata Network IDS
with Log Management platform Graylog and Threat Intelligence Platform MISP. 

Below, a diagram of configuration Altprobe and Alertflex controller for working with GrayLog and MISP

![](https://github.com/olegzhr/altprobe/blob/master/img/arch.png)

## Type of events (GELF format)

* "short_message":"alert-flex"
"full_message":"Alert from Alertflex collector/controller"

* "short_message":"event-hids"
"full_message":"IDS/FIM event from OSSEC/Wazuh"

* "short_message":"process-linux"
"full_message":"Network activity of linux process from Auditd"

* "short_message":"process-win"
"full_message":"Network activity of windows process from Sysmon"

* "short_message":"event-nids"
"full_message":"IDS event from Suricata"

* "short_message":"dns-nids"
"full_message":"DNS event from Suricata"

* "short_message":"ssh-nids"
"full_message":"SSH event from Suricata"

* "short_message":"netflow-nids"
"full_message":"Netflow event from Suricata"

## Documentation (include an installation instructions)
<http://alertflex.org/doc/>

## Screenshots
Below, a screenshot of Graylog dashboards for IDS events from Altprobe

![](https://github.com/olegzhr/altprobe/blob/master/img/graylog.jpg)

## Requirements
Altprobe was tested under Ubuntu version 14.04 with Wazuh HIDS (OSSEC fork) version 3.2 and Suricata NIDS version 4.0.3

## Support
Please [open an issue on GitHub](https://github.com/olegzhr/altprobe/issues) or send an email to <info@alertflex.org>,
if you'd like to report a bug or request a feature 


## Old version of Altprobe 
Previous version of altprobe (single package with support Ntop nProbe, ZeroMQ as sources and output to MySQL) is available under branch ``old_version``



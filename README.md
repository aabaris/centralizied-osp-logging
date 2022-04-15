Log collection, big picture:

- logs are collected via filebeats container running on all openstack nodes.

   - filebeats journald input collects operating system logs
   - filebeats filestream input collects container logs
   - static configuration of filebeats controls routing of message to specific indexes and ingestion pipelines
   - filebeats is responsible for ensuring that log delivery happens at least once and only once (queueing and tracking)

- filebeats container is deployed on all openstack nodes

   - using ansible  nerc-osp-config/playbooks/roles/log_collection 
   - pulled form registry.connect.redhat.com

- Ingestion pipelines are used to parse and process logs into form that is useful for monitoring and investigation

   - spliting out essential properties like timestamp, source, process, facility, severity, body of the message
   - openstack container log formats are varying and custom parsing rules need to be a applied based on it's source
   - removing of useless data: initially collect all data, but after some experience with it, determining what can be discareded safely

- Presentation of the data collected

   - discovery workflow -  dynamic search interface.
   - building custom views that produce daily reports based on logs collected

- configuration management of elasticsearch/kibana

   - json files in git?
   - scripts to apply via REST?

Ingestion flow:


- nerc-osp-container-logs

   - initialization and setup of helpful tags
   - redirect to a format sepcific ingestion pipeline
   - handling of ingestion outcome

- nerc-osp-container-{specific-log}
   - make a record which filters were applied
   - perform log parsing, processing
   - create records of parsing outcomes


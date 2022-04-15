main pipeline

- nerc.ingest.version
- nerc.ingest.parse.selected (which grok pipline has been selected)

grok pipelines

- nerc.ingest.parse.match (which match rules in that pipeline where applied)
- nerc.ingest.parse.error (any verbose error produced by the parser)
- nerc.ingest.parse.fail (was parser overall succesful)

parsed log entries

- nerc.log.*
- nerc.log.timestamp
- nerc.log.process.name
- nerc.log.process.pid
- nerc.log.serverity
- nerc.loc.facility
   


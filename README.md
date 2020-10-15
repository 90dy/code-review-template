# Code Review

## 12 Factor

### Codebase

* [ ] version control system (git, mercurial, subversion, ...)
* [ ] only one codebase per app
* [ ] no shared code (use libraries instead)
* [ ] multiple deploys (production, staging, development)
* [ ] same architecture by deployment

### Dependencies

* [ ] all dependencies declared via manifest (no system-wide)
* [ ] dependency isolation during execution
* [ ] uniform dependency specification between production and development

### Config

* [ ] vary between deploys
* [ ] separation of config from code (no constants)
* [ ] code could be made open source without compromising credentials
* [ ] stored in environment variables
* [ ] independently managed

### Backing Services

* [ ] uris & credentials stored in the config

### Build, Release, Run

* Build 
  * [ ] transform codebase into executable bundle
  * [ ] cannot update code after build
  * [ ] initiated at deployment by user
* Release
  * [ ] combines build with current config
  * [ ] cannot update config after release
  * [ ] versioning (ID, timestamp, semantic, ...)
  * [ ] rollback
* Run
  * [ ] initiated automatically
  * [ ] restart automatically when crashed

### Processes

* stateless
  * [ ] no sticky session (no session managed by the runtime but persisted in backing service)
  * [ ] persistence in backing service (database, object storage, ...)
  * [ ] no data stored in local file system or memory
* share nothing
  * [ ] each request is statisfied by a signle node 
  * [ ] each node doesn't independently access memory/storage

### Port binding

* [ ] execution does not rely on runtime injection of webserver (apache, tomcat, ...)
* [ ] a routing layer handles requests to the port-bound the processes

### Concurrency

* [ ] processes relies on os system's process manager (systemd, ...)
* [ ] each type of work handled by workloads process that can scale horizontally (if needed to scale) or well separated in code

### Disposability

* [ ] minimized processes startup time (few seconds)
* [ ] gracefully shutdown
  * [ ] with SIGTERM
  * [ ] waiting for small request to finish
  * [ ] long polling should be auto reconnected when no connection
  * [ ] jobs returns to the work queue
* [ ] robust against sudden death

### Dev/prod parity

* [ ] small time between writing code and deployment (hours not weeks)
* [ ] same developer that wrote code and deploy it
* [ ] no over use of different backing services between dev/prod (ex: SQLite local, PostgreSQL dev)
* [ ] usage of adapters for backing services

### Logs

* [ ] each event stream are sent to stdout
* [ ] in staging or prod, streams are captured by execution env
* [ ] in staging or prod, streams are callated to one or more destinations for viewing and archival
* [ ] only the execution environment manage archival destinations

### Admin processes

* [ ] run in an identical env as the app long running process
* [ ] run against release, with same codebase and config 

## Languages Specific

### Javascript

#### Code style

* [ ] linter
* [ ] latest es6
* [ ] static typing
* [ ] readable
* [ ] naming convention

#### Package

* [ ] engines versions specified in package.json
* [ ] no global dependencies
* [ ] versioning
* [ ] private package
* [ ] browserlist

#### Code

* [ ] no globals
* [ ] unit tests
* [ ] no side effect in functions

### Python

* [ ] linter
* [ ] readable
* [ ] naming convention
* [ ] object-oriented
*

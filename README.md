# Setup

* Disable script security for Job DSL scripts on https://jenkins.sbit.io/configureSecurity/ [^1]
* Create a pipeline job from SCM
* Run it

[^1]: Since classpath is disabled when security is present. See https://github.com/jenkinsci/job-dsl-plugin/wiki/Script-Security & https://github.com/jenkinsci/job-dsl-plugin/wiki/User-Power-Moves#use-job-dsl-in-pipeline-scripts

# Structure

```
.
├── projects                        # job-dsl files
│   ├── ${PROJECT}                  # ${PROJECT}'s files
│   │   ├── pipelines               # ${PROJECT}'s pipelines
│   │   └── config.yml              # ${PROJECT}'s metdata
│   └─── config.yml                 # Default metadata
├── src                             # Groovy files (to be deprecated in favor of lib) 
├── Jenkinsfile                     # Seed job's Jenkinsfile
├── seed.groovy                     # Seed job's job-dsl
└── README.md                       # This file
```

# Current features

* Creates per project folder
* Creates pipeline jobs for rawPipelines inside each projects' folder

# TODO

* Auto create-update seed job
* Re-enable security (load groovy as lib)
* Code-generator

# Requirements

## Plugins

* [Job DSL](https://plugins.jenkins.io/job-dsl)

* [Ansible](https://plugins.jenkins.io/ansible)
* [AnsiColor](https://plugins.jenkins.io/ansicolor)
* [GitLab](https://plugins.jenkins.io/gitlab-plugin) Optional
* [Lockable Resources](https://plugins.jenkins.io/lockable-resources)
* [SSH Agent](https://plugins.jenkins.io/ssh-agent)

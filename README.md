Newrelic Java Agent
=========


This role downloads Newrelic jvm agent and configures it.
The `newrelic_license_key` variable must be defined.

Add this role to the server that has a java app, then add an agent parameter:
`java -javaagent:/opt/newrelic/newrelic-agent-{{ newrelic_java_agent_version }}.jar -jar your-app.jar`


Considerations
------------

I have only tried this using the Java Development Kit (JDK).


Role Variables
--------------

See below the included variables:

| Variable                | Required | Default | Choices/Datatype          | Description | Example values                                                        |
|-------------------------|----------|---------|---------------------------|-------------|-----------------|
| newrelic_java_agent_app_name | yes |         | string                    | A name to identify the application  | My application  |
| newrelic_license_key    | yes      |         | string                    | It's the licence key  |                                                   |
| newrelic_java_agent_version | yes  |  3.47.1 | string                    | Version of the agent to be installed  |                                                   |
| newrelic_java_agent_user    | yes  | root    | string                     | User under which the agent will be run. This should match with the same user the java app is running under  |                                                   |
| newrelic_java_agent_group   | yes  | root    | string                     | Group under which the agent will be run. This should match with the same group the java app is running under  |                                                   |



Example Playbooks
----------------

See below.

### 1. Using AWS

```
- hosts: "{{ variable_host | default('tag_Newrelic_agent') }}"
  become: true
  roles: 
    - ansible-newrelic-java-agent
  vars:
    newrelic_java_agent_app_name: "My application"
    newrelic_java_agent_user: myuser
    newrelic_java_agent_group: mygroup
```        


License
-------

The project is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

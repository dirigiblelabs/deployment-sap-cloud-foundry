# Setup

1. Replace the following variables in **vars.yaml** before deploying:

    |           Name           |     Description                                                | Default Value |
    |--------------------------|----------------------------------------------------------------|---------------|
    | ``applicationName``      | *The application name (e.g. dirigible)*                        | N/A           |
    | ``subdomain``            | *The SAP Cloud Platform Cloud Foundry subdomain*               | N/A           |
    | ``regionId``             | *The SAP Cloud Platform Cloud Foundry region id*               | N/A           |
    | ``runtimeMemory``        | *The runtime memory for the Eclipse Dirigible runtime*         | 2G            |
    | ``runtimeDiskQuota``     | *The runtime disk quota for the Eclipse Dirigible runtime*     | 2G            |
    | ``runtimeDockerImageTag``| *The docker image version of Eclipse Dirigible*                | latest        |

1. Create XSUAA service instance with ``cf create-service xsuaa application <applicationName>-xsuaa -c xs-security.json``
    > Replace ``<applicationName>`` before executing the command
1. Deploy with ``cf push --vars-file vars.yaml``

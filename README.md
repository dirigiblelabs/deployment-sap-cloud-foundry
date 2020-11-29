# Eclipse Dirigible Deployment for SAP Cloud Platform Cloud Foundry environment

[![Eclipse License](http://img.shields.io/badge/license-Eclipse-brightgreen.svg)](LICENSE)
[![GitHub contributors](https://img.shields.io/github/contributors/dirigiblelabs/deployment-sap-cloud-foundry.svg)](https://github.com/dirigiblelabs/deployment-sap-cloud-foundry/graphs/contributors)

## Setup
1. Clone this repository
1. Navigate to the ``dirigible`` folder
1. Replace the following variables in **vars.yaml** before deploying:

    |           Name           |     Description                                                | Default Value |
    |--------------------------|----------------------------------------------------------------|---------------|
    | ``applicationName``      | *The application name (e.g. dirigible)*                        | N/A           |
    | ``subdomain``            | *The SAP Cloud Platform Cloud Foundry subdomain*               | N/A           |
    | ``regionId``             | *The SAP Cloud Platform Cloud Foundry region id*               | N/A           |
    | ``runtimeMemory``        | *The runtime memory for the Eclipse Dirigible runtime*         | 2G            |
    | ``runtimeDiskQuota``     | *The runtime disk quota for the Eclipse Dirigible runtime*     | 2G            |
    | ``runtimeDockerImageTag``| *The docker image version of Eclipse Dirigible*                | latest        |

1. Replace the ``<applicationName>`` in **xs-security.json** with the one from **vars.yaml**
1. Create XSUAA service instance with ``cf create-service xsuaa application <applicationName>-xsuaa -c xs-security.json``
    > Replace ``<applicationName>`` with the one from **vars.yaml** before executing the command
    1. To update the XSUAA service instance, for example with additional role, then execute the following command:
    > ``cf update-service <applicationName>-xsuaa -c xs-security.json``
1. Deploy with ``cf push --vars-file vars.yaml``
1. Assign the ``Developer`` and the ``Operator`` role to your user from the [SAP Cloud Platform Cockpit](https://account.hana.ondemand.com/)
1. Access the Dirigible instance at: ``https://<applicationName>-<subdomain>.cfapps.<regionId>.hana.ondemand.com``

> Note: Step by step tutorial can be found [here](https://blogs.sap.com/2020/03/15/how-to-deploy-eclipse-dirigible-in-the-sap-cloud-platform-cloud-foundry-environment/)
## License

## Setup Cloud Foundry CLI:
```
cf push dirigible \
--docker-image=dirigiblelabs/dirigiblelabs/dirigible-sap-cf:latest \
--hostname dirigible-<org-name> \
-m 2G -k 2G
```

> Note: Before executing the command, replace the `<org-name>` with the **_Org Name_** value _(a.k.a **subdomain**)_

This project is copyrighted by [SAP SE](http://www.sap.com/) and is available under the [Eclipse Public License v 1.0](https://www.eclipse.org/legal/epl-v10.html). See [LICENSE](LICENSE) and [NOTICE.txt](NOTICE.txt) for further details.

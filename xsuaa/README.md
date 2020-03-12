# Setup

1. Replace the following variables before deploying:

    |           Name           |     Description     |
    |--------------------------|---------------------|
    | ``<dirigible-name>``     | *TBD*               |

1. Create XSUAA service instance with ``cf create-service xsuaa application <dirigible-name>-xsuaa -c xs-security.json``
    > Replace ``<dirigible-name>`` before executing the command

Wazuh 4.10.1 Single-Node Deployment

# perrequisites

- a rocky linux vm or ubuntu vm
- Root or sudo access to the VM.
- At least 4 GB of RAM and 2 CPU cores (recommended for a single-node setup).

# Step 1: Update the System

- update the system with apt or yum
- install the docker and docker compose

# step 2 : Download Wazuh Docker Compose Files with git

- Clone the Wazuh Docker repository and navigate to the single-node directory.

    - git clone https://github.com/wazuh/wazuh-docker.git -b v4.10.1
    - cd wazuh-docker/single-node

# step 3 : Configure Wazuh

- nano .env
    WAZUH_API_URL=https://10.10.5.73
    WAZUH_INDEXER_URL=https://10.10.5.73
    WAZUH_DASHBOARD_URL=https://10.10.5.73
    KIBANA_URL=https://10.10.5.73

# step 4 : generate certs 

- Generate certificates for secure communication between Wazuh components.

    - docker-compose -f generate-indexer-certs.yml run --rm generator

# step 5 : start the wazuh containers 

    - docker-compose up -d

# step 6 : access the webui and check the logs if there was any errors

    - docker ps -a  - for logs 
    - access the web ui with : 10.10.5.73 (vm ip address)

# step 7 : conclusion.

- with this document by defaultly the login user was not create, have to create the user after accessing the web ui.
- go the security and the users over there with admin whatever the permissions.

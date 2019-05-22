## Dockerized - PHP & MySqlDB application test attempt, fully deployed using Ansible with some key flexibilities


### What it does ?
- PHP webpage reads from mysql database to display data. Both services running on two seperate containers.


### Prerequisite:
* Python, mysql and docker installed on main host
  ```
  sudo yum -y install docker mysql python
  ```
* Ansible modules for docker will be required for this: docker_volume, docker_image, docker_container
  ``` 
  pip install docker-py
  ```
  

### Features:  
* Persistant database updates using docker volumes
* Flexible container build/runs with ansible tags
* Quick testing using Ansible playbooks to setup independent containers
* Adding containers to default docker bridge network
* playbook run will idle for 120 seconds after MySQLDb container run


### Run and test
* Using a bank.sql sample database for test
* Run playbook
  ```
  ansible-playbook playbook.yml
  ```
* In the event of any tests/modifications to components, re-run specific containers using ansible tags
  ```
  ansible-playbook playbook.yml --tags=(create_myapp_container or create_db_container)
  ```
* Connect to database from host machine
  ```
  mysql -P 3307 -h 127.0.0.1 -u joseph -p
  ```
- Access index page from hostmachie using:
  ``` 
  http://localhost:8080
  ```

  
### Other
* Can use ansible vault to replace prompting for mysql_db password
* Attempted to use multiple options - Dockerfile, direct container run, docker volumes
* Re-running playbooks with tags will ask for MySqlDB password
* index.php page has mysql password provided
* To rebuild myapp_container, stop & remove container, remove image and then 
  ```
  ansible-playbook playbook.yml --tags=create_myapp_container
  ```

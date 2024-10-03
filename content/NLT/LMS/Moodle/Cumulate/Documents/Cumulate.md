2024.05.20

## Meeting Notes 

- Using Moodle 
	- 3.2
-  Hubble** 
- Apollo theme -> deprecated. 


## Moodle Notes
- Moodle version 4.1
	- Requires: MariaDB 10.4 
	- Requires: PHP 8.1

### Hosting questions:
- Do you have direct access to the server where the Moodle source code/ database is hosted
- Is this server hosted on a Cloud Provider/VPS provider that we can create a snapshot from?
	- OR is the instance managed through something like C-Panel? 
- Do we have credentials to access https://worth.academy/login/index.php - in order to view how existing integrations are configured and setup
- TODO:
	- Setup Docker/VM for server Ubuntu 22 
	- Setup/configure a sandbox environment - Ubuntu 22
		- Apache `sudo apt-get install apache2`
		- Install MariaDB
			- Restore DB from prod server
		- Copy Moodle source code
			- Connect to Maria DB
			- Update from 3.1.1 -> 3.5 -> 3.9 -> 4.1.2(one day each, check all plugins at each stage)
			- Install new Theme(Almandb/Adaptable/Moov).
			- Check integrations/web services 
	- Check all plugins to see if supported by 4.1.2 Moodle 
	- 
### Integration questions 
- How does Discovery integration work?
- Are there any endpoints that Discovery send requests to?
	- What in your moodle instance handles these requests(mostly via plugins or custom php scripts etc?)


### 2024.05.28
- Create screen shots/excel of all courses.
- Double check migration requirements and time.
- Check if we can possibly create snap shot of AWS environment.
- Give J moodle API key.
## Azure App Service + Database
1. Create Webapp + Database
1. Download Windows Zip OpenEMR file from [here](https://www.open-emr.org/wiki/index.php/OpenEMR_7.0.0_Windows_Installation).
1. Extract to local folder.
1. Download PEM file from MySQL and copy to sites/default/documents/certificates folder. Rename the file to mysql-ca (no extension).
1. Open /contrib/util/installScripts/InstallerAuto.php and comment out the `exit;` statement on line 78.
1. Use Azure WebApp extension to publish to web app.
1. create remote connection to app service container using `az webapp create-remote-connection --resource-group <resourcegroupname> --name <webappname>`
1. ssh to web app container using tunneled port from previous step
1. --OR-- use the SSH button from the Azure Portal to connect to SSH terminal
1. change to installScripts folder using `cd site/wwwroot/contrib/util/installScripts`
1. run this `php -f InstallerAuto.php server=open-emr-demo-server.mysql.database.azure.com loginhost=% root=<username> rootpass=<password> login=<openemr-db-user> pass=<openemr-db-pass>`
1. **optional** after script runs and database is created, either delete the InstallerAuto.php file or edit and uncomment `exit;` on line 78.
1. Browse to site and confirm login screen

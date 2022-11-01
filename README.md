# AEMaaCS Postman Collection
(Hopefully) growing Postman Collection for various AEM operations.

The Postman collection is a starting point for AEM developers and consultants. It should help you during, setup, migration, debugging and hotfixes.
All commands were tested in AEM as a Cloud Service.

Together with the [Postman Runner](https://blog.postman.com/using-csv-and-json-files-in-the-postman-collection-runner/) its also a valid bulk edit/migration tool.


## Why
There are several reasons why i created the repo. 
* Since CRXDE Lite is blocked in AEMaaCS its sometimes tough to do certain "stuff". Like quickly edit a property or delete a "nasty" node. Normally i use the [AEMaaCS Repo Browser](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/repository-browser.html?lang=en) to find the culprit, then do the necessary changes via the collection.
* Create custom packages (eg. use the aem querybuilder to find the needed assets for the package and use that payload to create the custom package.)
* Mass creation of pages for eg. migration support with the help of the postman runner
* Upload of assets (Also a valid runner (See "Runner Tasks" below) task if you want to upload multiple assets)
* Mass change of user groups (Also a valid runner task)

## Current CURL Commands
![image](https://user-images.githubusercontent.com/4376185/199194096-969b27f1-9e79-44bd-9290-86a6ee493880.png)
![image](https://user-images.githubusercontent.com/4376185/199194128-a8caed88-aca6-4f2d-828e-ba556486029f.png)
![image](https://user-images.githubusercontent.com/4376185/199194175-a38180ab-d3c0-4f49-9ab0-c686e4c5e4f8.png)


## How to use
* Create a classic (non IMS user) [within AEM](https://experienceleague.adobe.com/docs/experience-manager-64/forms/administrator-help/setup-organize-users/adding-configuring-users.html?lang=en). I might add IMS support in the future.
* Install the collection
* Setup a new [Postman Environment](https://learning.postman.com/docs/sending-requests/managing-environments/). The "Path" Variable is optional and only used for Postman Runner Tasks. It should look like this: ![image](https://user-images.githubusercontent.com/4376185/199006197-7d3a489c-6264-4308-b1f2-e2d62d030a7d.png)
* Set the Environment 
* Have Fun

## Runner Tasks
As stated above the [Postman Runner](https://blog.postman.com/using-csv-and-json-files-in-the-postman-collection-runner/) is a valid tool for bulk/mass operations. Attached is a video of what I once did for content fragments (to create them in bulk based on a .csv). You don't see the AEM Collection in the video, but the logic is exactly the same. The variable settings in minute 0:30 are best not as seen in the video but set up in the environment.

[<img src="https://previews.jumpshare.com/thumb/815bc01b796dd6f1733c957c5af19493b7a5ec55f400ae203fce6afcc4f6733e46a0a3962fcfdc4944ec31bc16a2a9977188894f46bc8f83e0abd987fd194b54815ed67a13d23159a93de527a2001c4b89a3fa4f9c522f2b2608fb58930f8a8d" width="50%">](https://jmp.sh/v/QEWpWJn4mKaIUB4DqpPh "Postman Runner Demo")

## What is not working in the cloud (or untested)

### Tree Activation
Tree Activation - Will not work in cloud since path is blocked
        curl -u admin:admin -F cmd=activate -F ignoredeactivated=true -F onlymodified=true
        -F path=/content/geometrixx http://localhost:4502/etc/replication/treeactivation.html
        
        
### Create Replication Agents

curl -u admin:admin ‘http://localhost:4502/bin/wcmcommand’ -H ‘Content-Type: application/x-www-form-urlencoded; charset=UTF-8’ --data ‘cmd=createPage&charset=utf-8&parentPath=/etc/replication/agents.author&title=ReplicationAgentTest&label=&template=/libs/cq/replication/templates/agent’

### BUNDLES:

#### Uninstall a bundle

curl -u admin:admin -daction=uninstall http://localhost:4502/system/console/bundles/“name of bundle”

#### Install a bundle
        curl -u admin:admin -F action=install -F bundlestartlevel=20 -F
        bundlefile=@“name of jar.jar” http://localhost:4502/system/console/bundles

#### Build a bundle
        curl -u admin:admin -F bundleHome=/apps/centrica/bundles/name of bundle -F
        descriptor=/apps/centrica/bundles/com.centrica.cq.wcm.core-bundle/name_of_bundle.bnd
        http://localhost:4502/libs/crxde/build

#### Stop a bundle
        curl -u admin:admin http://localhost:4502/system/console/bundles/org.apache.sling.scripting.jsp
        -F action=stop

#### Start a bundle
        curl -u admin:admin http://localhost:4502/system/console/bundles/org.apache.sling.scripting.jsp
        -F action=start

#### Delete a bundle
         curl -u admin:admin -X DELETE http://localhost:4502/apps/localhost/install/com.localhost.core-6.2.26-SNAPSHOT.jar

### BACKUP
Set delay time (optional - default is 10)

curl -u admin:admin -X POST http://localhost:4502/system/console/jmx/com.adobe.granite:type=Repository/a/BackupDelay?value=0

curl -u admin:admin -X POST http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository/op/startBackup/java.lang.String?target=mvtest
        

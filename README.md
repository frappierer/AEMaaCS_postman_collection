# AEMaaCS_postman_collection
(Hopefully) growing Postman Collection for various AEM operations.

The Postman collection is a starting point for AEM developers and consultants. It should help you during, setup, migration, debugging and hotfixes.
All commands where tested in AEM as a Cloud Service.

Together with the Postman Runner (https://blog.postman.com/using-csv-and-json-files-in-the-postman-collection-runner/) its also a valid bulk edit/migration tool.


## Why
There are several reasons why i created the repo. 
* Since CRXDE Lite is blocked in AEMaaCS its sometimes tough do stuff. Like quickly edit a property are delete a "nasty" node. Normally i leverage https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/repository-browser.html?lang=en to find the culprit, then do the necessary changes via the collection.
* Create custom packages.
* Mass creation of pages for eg. migration support with the help of the postman runner
* Upload of assets (Also a valid runner task)
* Mass change of user groups (Also a valid runner task)


## How to use
* Create a classic (non IMS user) within AEM. (I might add IMS support in the future)
* Install the collection
* Setup a new Environment (https://learning.postman.com/docs/sending-requests/managing-environments/) and set the following vars: AEMURL, AEMuser, AEMpw, path (optional)
** See https://jmp.sh/YuUCn3MG
* Set the Environment 
* Have Fun

## Demo
Will follow.

# AEMaaCS Postman Collection
(Hopefully) growing Postman Collection for various AEM operations.

The Postman collection is a starting point for AEM developers and consultants. It should help you during, setup, migration, debugging and hotfixes.
All commands were tested in AEM as a Cloud Service.

Together with the [Postman Runner](https://blog.postman.com/using-csv-and-json-files-in-the-postman-collection-runner/) its also a valid bulk edit/migration tool.


## Why
There are several reasons why i created the repo. 
* Since CRXDE Lite is blocked in AEMaaCS its sometimes tough do stuff. Like quickly edit a property are delete a "nasty" node. Normally i use the [AEMaaCS Repo Browser](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/repository-browser.html?lang=en) to find the culprit, then do the necessary changes via the collection.
* Create custom packages.
* Mass creation of pages for eg. migration support with the help of the postman runner
* Upload of assets (Also a valid runner task)
* Mass change of user groups (Also a valid runner task)

## Current CURL Commands
![image](https://user-images.githubusercontent.com/4376185/198990904-fe687e0a-7d2f-40a6-a038-bf40552bc684.png)
![image](https://user-images.githubusercontent.com/4376185/198990959-ef2f3c0b-7ebd-46d4-b452-a676952114c0.png)

## How to use
* Create a classic (non IMS user) within AEM. (I might add IMS support in the future)
* Install the collection
* Setup a new [Postman Environment](https://learning.postman.com/docs/sending-requests/managing-environments/). The "Path" Variable is optional and omly used for Postman Runner Tasks. It should look like this: ![image](https://user-images.githubusercontent.com/4376185/199006197-7d3a489c-6264-4308-b1f2-e2d62d030a7d.png)
* Set the Environment 
* Have Fun

## Runner Tasks
As stated above the [Postman Runner](https://blog.postman.com/using-csv-and-json-files-in-the-postman-collection-runner/) is a valid tool for bulk operations. Attached is a video of what I once did for content fragments (to create them in bulk based on a .csv). You don't see the AEM Collection in the video, but the logic is exactly the same. The variable settings in minute 0:30 are best not as seen in the video but set up in the environment.

[<img src="https://previews.jumpshare.com/thumb/815bc01b796dd6f1733c957c5af19493b7a5ec55f400ae203fce6afcc4f6733e46a0a3962fcfdc4944ec31bc16a2a9977188894f46bc8f83e0abd987fd194b54815ed67a13d23159a93de527a2001c4b89a3fa4f9c522f2b2608fb58930f8a8d" width="50%">](https://jmp.sh/v/QEWpWJn4mKaIUB4DqpPh "Postman Runner Demo")


## Demo
Will follow.

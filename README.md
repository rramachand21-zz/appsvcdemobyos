# App Service Demo - Bring your own storage

This dotnetcore web application is a sample application that shows how you can use the "Bring your own storage" feature in Azure App Services to integrate your App Service with an Azure storage (blobs or files)

The home page refers to some images, css and js files that are in an azure blob storage and Azure app services can be configured to mount the blob storage to have those contents readily available to the web application.

<b>Steps to deploy to Azure App Service:</b>

1. Create an Azure Blob Storage or Azure Files share - https://docs.microsoft.com/en-us/azure/storage/
2. Upload the contents of this <a href="https://github.com/rramachand21/appsvcdemobyos/blob/master/wwwroot_upload_to_storage.zip">folder</a> to your azure storage. 
3. Create an Azure App Service on Linux or Web App for Containers - https://docs.microsoft.com/en-us/azure/app-service/containers/ 
4. Link the Azure Blob storage container or Azure Files share with the Azure App Service - the mount path to use is /home/site/wwwroot/wwwroot

<b>Sample Az CLI command:</b>
<br/>
<code>
az webapp config storage-account add -g YourResourceGroup -n YourAppServiceName --custom-id YourCustomId --storage-type AzureBlob --account-name YourStorageAccountName --share-name YourStorageContainerOrShareName --access-key <youraccesskey> --mount-path /home/site/wwwroot/wwwroot
  </code>

5. Deploy this github repo to your Azure App Service - https://docs.microsoft.com/en-us/azure/app-service/app-service-continuous-deployment 

You can now browse to your web application hosted on Azure App Service.




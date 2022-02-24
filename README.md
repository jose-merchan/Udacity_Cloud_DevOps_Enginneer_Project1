# Udacity_Cloud_DevOps_Enginneer_Project1
Site contains the details required to illustrate the project steps
## 1. The first step is to create an S3 bucket with Public access permissions. 
  * We access to S3 by searching for S3 on the 
![Captura de pantalla 2022-02-24 a las 15 28 56](https://user-images.githubusercontent.com/23102562/155543448-9a08b470-7948-485a-847f-8629e56dbd2b.png)
  * Click on "Create Bucket" Button 
![Captura de pantalla 2022-02-24 a las 15 28 07](https://user-images.githubusercontent.com/23102562/155543304-c356fe63-5de2-46a3-87df-f9da69416029.png)
  * On the new page we provide a unique name
![Captura de pantalla 2022-02-24 a las 15 31 50](https://user-images.githubusercontent.com/23102562/155544053-ac2ce128-facb-4d22-8f7a-1e39031b779e.png)
  * And make sure "Block Public Access" is disabled
![Captura de pantalla 2022-02-24 a las 15 32 56](https://user-images.githubusercontent.com/23102562/155544254-063ad10c-7324-4a7e-b94a-726f9e1290a2.png)
  * Access the newly created bucket by clicking on its name
![Captura de pantalla 2022-02-24 a las 15 34 52](https://user-images.githubusercontent.com/23102562/155544589-7e62a744-2d70-42f7-a2e4-3a11181cce17.png)
  * Go to permissions > Edit Bucket policy, modifyng the JSON policy provided but associated to the ARN of the bucket
![Captura de pantalla 2022-02-24 a las 15 35 48](https://user-images.githubusercontent.com/23102562/155544819-ff6c4742-4860-4fdc-a676-405627f2aab3.png)
  * After commiting the changes, the Bucket becomes publicly accesible
![Captura de pantalla 2022-02-24 a las 15 36 42](https://user-images.githubusercontent.com/23102562/155544982-134bfacc-5e5b-45e6-96e9-64e5628d723d.png)

## 2. Upload files to the bucket
  * Download and unzip the zip folder and Upload the files and folder one by one. To that end go to the Object tab and click on Upload
![Captura de pantalla 2022-02-24 a las 15 38 28](https://user-images.githubusercontent.com/23102562/155545285-77c928c3-bbd7-4687-970f-3c8a7d67f39c.png)
  * Files at the folder "root" directoy are added using the "Add File" whereas the other three folders were added the three at the same time by selecting "Add Folder". 
![Captura de pantalla 2022-02-24 a las 15 39 24](https://user-images.githubusercontent.com/23102562/155545625-e8a44852-e28b-4d8d-957c-39f5cb958de7.png)
* After add them, clicked on Upload and wait for around 10 minutes till the upload finished
![Captura de pantalla 2022-02-24 a las 15 41 48](https://user-images.githubusercontent.com/23102562/155545817-5e69ed84-89c0-4987-ba65-ed9a1a17c385.png)
* Once the upload process finished, the files and folder appears on the bucket (with folders represented with the corresponding prefix/file structure)
![Captura de pantalla 2022-02-24 a las 15 42 26](https://user-images.githubusercontent.com/23102562/155546087-b6e7dc76-789c-42e9-9207-ac0c34d6fb74.png)


## 3. After the content has been added the next step is to make an Static web Site based on S3. In the bucket, we select the "Properties" tab and scroll down to the section "Static WebSite Hosting" and click on the edit button.

![Captura de pantalla 2022-02-24 a las 15 44 09](https://user-images.githubusercontent.com/23102562/155546351-0b54481a-3b57-45e1-80ce-173db6295bcf.png)
  * Click on the "Enable" radio button, to enable the functionality and referenced the index document and the click on Save
![Captura de pantalla 2022-02-24 a las 15 45 20](https://user-images.githubusercontent.com/23102562/155546651-c5944856-6c79-42d5-acd7-1d1fe34d3965.png)

* After that, the functionality gets enabled and the corresponding website endpoint provided: http://my-jmmerchan-bucket.s3-website-us-east-1.amazonaws.com
![Captura de pantalla 2022-02-24 a las 15 46 58](https://user-images.githubusercontent.com/23102562/155546940-07cf4013-02eb-440c-b77a-02597a5b45bc.png)

> We can browse to the Static Website
![Captura de pantalla 2022-02-24 a las 15 48 55](https://user-images.githubusercontent.com/23102562/155547302-dec0ef79-ca52-4dda-8d74-6a0ca4c11eaa.png)


## 4. Next we make the site available via AWS CDN - CloudFront:
  * In the Service Search bar we look for CloudFront
![Captura de pantalla 2022-02-24 a las 15 51 42](https://user-images.githubusercontent.com/23102562/155547842-8ce875a5-d935-4e03-864a-c92b1a6c95d5.png)
  * Go to distribution and click on "Create Distibution"
![Captura de pantalla 2022-02-24 a las 15 52 53](https://user-images.githubusercontent.com/23102562/155548077-12681f3d-eb1e-494f-a7af-3182628e8759.png)
  * In the new page we configured the Distribution as follow:
    * We use the S3 Static website instead of selecting the bucket from the "Origin" drop-down menu
    
    ![Captura de pantalla 2022-02-24 a las 15 55 39](https://user-images.githubusercontent.com/23102562/155548555-da6574c7-9cb3-49f8-a9e3-263327b4bbea.png)

    * The rest of the settings remains with their default values with the exception of "Default Cache Behavior" > Viewer > "Viwer Protocol policy" which we change to Redirect HTTP to HTTPS (from Default HTTP and HTTPS) as per the screenshots provided in the guide
    
    ![Captura de pantalla 2022-02-24 a las 15 56 37](https://user-images.githubusercontent.com/23102562/155548761-7309bb80-2710-4737-9330-8570615c0901.png)
  
    * Click on "Create Distribution" and wait till the status changed does not say anything about "Deploying" (in my case, it moved from Deploying to simply show the "execution date" in the "Last modify" column)
    
    ![Captura de pantalla 2022-02-24 a las 15 59 04](https://user-images.githubusercontent.com/23102562/155549183-718015a0-b01c-42a6-8b70-fb61c92435ee.png)
    
    * The distribution domain (d2j8z2x3xkcu9e.cloudfront.net) is provided and we can also navigate to this page  
    ![Captura de pantalla 2022-02-24 a las 16 01 05](https://user-images.githubusercontent.com/23102562/155549527-8aa6e528-b574-4d72-9a68-73e3cbc9b522.png)
    ![Captura de pantalla 2022-02-24 a las 16 02 02](https://user-images.githubusercontent.com/23102562/155549716-7ffb5aab-d04a-418e-bddf-92d4b8c2a2e8.png)

> A side note worth mentioning is since we are redirecting HTTP to HTTPS as part of CloudFront distribution configuration we can now navigate to an HTTPS site
  ![Captura de pantalla 2022-02-24 a las 16 04 08](https://user-images.githubusercontent.com/23102562/155550136-566d8f2e-3b90-4f6d-b63e-df49ef6a4e19.png)



### Till this point we have accessed the site using the:
1. "Static Web Page" endpoint: **http://my-jmmerchan-bucket.s3-website-us-east-1.amazonaws.com/**
2.  The "Distribution domain URL": **https://d2j8z2x3xkcu9e.cloudfront.net**
3.  The last way of accessing is by using the S3 URL asociated to the Object index.html: **https://my-jmmerchan-bucket.s3.amazonaws.com/index.html**
![Captura de pantalla 2022-02-24 a las 16 06 31](https://user-images.githubusercontent.com/23102562/155550549-a7817949-8f7f-4b33-a108-df99b502e290.png)



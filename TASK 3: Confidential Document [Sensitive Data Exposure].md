## Introduction
This section demonstrates how to exploit improper access controls and directory traversal vulnerabilities in a web application. By leveraging exposed endpoints and weak validation, we can access confidential files stored in an unsecured FTP directory.

***

## Steps to Exploit the Vulnerability

**Step 1: Navigate to the "About Us" Section**
> * Open the application and go to the About Us section from the left menu.
>
>![image](https://github.com/user-attachments/assets/9a178b9b-659f-4a09-a814-2c0f86ff6c83)
> * Locate the sentence: _"Check out our boring terms of use if you are interested in such lame stuff."_
>
>![image](https://github.com/user-attachments/assets/4b2e7411-a4b1-4467-b8d2-5fca35298c2b)
> * This is a clickable link to download the legal.md file.


**Step 2: Intercept the Request**
> * Open Burp Suite and turn on the Intercept feature under the Proxy tab.
> * Click the link to download legal.md.


**Step 3: Analyze the Intercepted Request**
> * In Burp Suite’s Intercept tab, observe the request:
>  ```
>  GET /ftp/legal.md HTTP/1.1
>  ```
> 
>![image](https://github.com/user-attachments/assets/215a23f4-9d82-4752-a3f9-c62f8b6bc61b)
> * Right-click on the intercepted request and select Send to Repeater.
>
>![image](https://github.com/user-attachments/assets/b1448100-9761-4adf-a807-ec0116deb14f)

**Step 4: Use the Repeater Tab**
> * Go to the Repeater tab in Burp Suite.
>
>![image](https://github.com/user-attachments/assets/56422a82-4fae-42f6-a589-f4eb983a7a48)
> * In the Request section, click Send and review the response:
>
>![image](https://github.com/user-attachments/assets/aebb0ce6-4f25-417a-8cdc-0c91718953cb)
> * The response contains the contents of legal.md.


**Step 5: Access the Parent Directory**
> * In the Request section, modify the first line to remove /legal.md:
> ```
> GET /ftp/ HTTP/1.1
> ```
>
>![image](https://github.com/user-attachments/assets/75598300-ee4c-4abd-8ac0-e0b237de87df)
> * Click Send to resend the request.
>
>![image](https://github.com/user-attachments/assets/ee5642da-76fe-4a29-bba8-883b302ed946)


**Step 6: Inspect the Directory Listing**
> In the Response tab, you will see a directory listing of all files in the _ftp_ directory.
> 
>![image](https://github.com/user-attachments/assets/ee5642da-76fe-4a29-bba8-883b302ed946)
> 
>Search for _legal.md_ to confirm the directory contents.
>
>![image](https://github.com/user-attachments/assets/ed0f375b-6d8a-4e49-b34b-43d5b2f6f89d)
> Notice that all files have a .md extension.


**Step 7: Identify a Confidential File**
> * In the Response tab, search for .md to locate all available files.
> * Identify a suspicious file, such as _acquisitions.md_. The title suggests it could contain confidential information.
>
>![image](https://github.com/user-attachments/assets/12be3be6-802c-4dfd-a3c4-8e1be5998333)


**Step 8: Access the Confidential File**
> * Modify the request in the Request section to target acquisitions.md:
> ```
> GET /ftp/acquisitions.md HTTP/1.1
> ```
>
>![image](https://github.com/user-attachments/assets/4617e8c4-940b-4e4e-af78-43c3af253b41)
>Click Send to resend the request.


**Step 9: Review the Response**
>* In the Response tab, view the contents of acquisitions.md.
>
>![image](https://github.com/user-attachments/assets/079c552c-ddee-4685-ac72-3d6872c5db4b)

**Step 10: Verify the Results**
> * Return to the application.
> * Open the Scoreboard or any page displaying the results.
>
>![image](https://github.com/user-attachments/assets/bc740571-07e4-4c09-862f-286ee3892ff9)


***

## How This Exploit Works
> **Directory Traversal:**
> >Removing /legal.md from the request exposes the parent directory (/ftp/) and its contents.
>
> **Insecure File Access:**
> >The application fails to restrict access to sensitive files, allowing users to retrieve them directly by modifying the file path.

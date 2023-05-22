<a href="https://zerodha.tech"><img src="https://zerodha.tech/static/images/github-badge.svg" align="right" /></a>

## Frappe S3 Attachment

Frappe app to make file upload automatically upload and read from s3 and download from S3.

#### Features.

1. Upload both public and private files to s3.
2. Stream files from S3, when file is viewed everytime.
3. Lets you add S3 credentials
    (aws key, aws secret, bucket name, folder name) through ui and migrate existing
    files.
4. Deletes from s3 whenever a file is deleted in ui.
5. Files are uploaded categorically in the format.
    {s3_folder_path}/{year}/{month}/{day}/{doctype}/{file_hash}
6. Download files from S3 in your site's public and private folder.
7. Update details in database after reverse migrating from S3

#### Installation.

1. bench get-app --branch v13 [https://github.com/Improwised/Frappe-attachments-s3.git](https://github.com/Improwised/frappe_s3_attachment)
2. bench --site {site} install-app frappe_s3_attachment

#### Configuration Setup.

1. Open single doctype "s3 File Attachment"
2. Enter (Bucket Name, AWS key, AWS secret, S3 bucket Region name, Folder Name)
    Folder Name- folder name is the default folder path in s3.
3. Migrate existing files lets all the existing files in private and public folders
    to be migrated to s3.
4. Delete From Cloud when selected deletes the file form s3 bucket whenever a file
    is deleted from ui. By default the Delete from cloud will be unchecked.
    
### Setup for migrating from S3 to local

1. There is Migrating to local button in "s3 File Attachment"
2. It will migrate all files from s3 to local folder.<br/>
   Updated path for private files - private/files/{fileName.Extension}<br/>
   Updated path for public files - files/{fileName.Extension}

### Safely removing a Zerodha app and install Improwised frappe s3 attachment.

1. This will remove Zerodha app from site
```
$ bench --site {site} uninstall-app frappe_s3_attachment 
```
2. Get App of Improwised. If, any overwritten permission needed, provide yes
```
$ bench get-app --branch v13 https://github.com/Improwised/frappe_s3_attachment.git 
```
3. This will install Improwised Frappe S3 attachment in site
```
$ bench --site {site} install-app frappe_s3_attachment 
```
4. After Migrating to local, to remove improwised frappe-s3-attachment do step 5.
5. This will remove Improwised app from site
```
$bench --site {site} uninstall-app frappe_s3_attachment 
```

#### License

MIT

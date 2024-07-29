# File Uploader
A robust PHP class for handling single or multiple file uploads

> [!CAUTION]
> All example codes herein are strictly for illustration purposes only. It's recommended to optimize before using for production.

## Instantiating the Class :

The `FileUploader` can be instantiated using the standard PHP syntax as follows

```php

<?php

$FU = new FileUploader($htmlName = '', $uploadPath = '', $allowedExtArr = array(), $sizeLimit = '', $widthLimit= '', $heightLimit = '', $fileTerm = '');

/****
 *  @param $htmlName => The name of the HTML file input element
 * 
 *  @param $uploadPath => The path on your server where the file is to be uploaded to 
 * 
 *  @param $allowedExtArr => An array of the file extension(s) that are allowed 
 * 
 *  @param $sizeLimit => The max size of the file that is allowed
 * 
 *  @param $widthLimit => The width of the image file that is allowed
 *  
 *  @param $heightLimit => The height of the image file that is allowed
 *  
 *  @param $fileTerm => The terminology you wish to use the address the file being uploades; E.g  image,         
 *  picture, spreadsheet, pdf, file etc
 *  
 ****/        


?>

```

## Features & Usage Guide :

### Checking if the File Input Contains a File :
To verify that the HTML file input element referenced by `$htmlName` parameter actually contains a file that can be uploaded, simply call the `fileIsSelected()` method as shown below 

```php

<?php

$FU->fileIsSelected();

/****
 * 
 *  @return TRUE => file is selected
 *  @return FALSE => file is not selected
 * 
 ****/        

?>

```

### Uploading a File :
To upload any file, simply call the `upload()` method as shown below 

```php

<?php

$FU->upload();


/****
 * 
 *  @return TRUE => file was successfully uploaded
 *  @return FALSE => file was not successfully uploaded
 * 
 ****/        

?>

```

### Full File Upload Example :

```php

<?php

$FU = new FileUploader('myFileInputElementName', 'myUploadPath');

if($FU->fileIsSelected()){ // Check if file input element contains a file
    
    if($FU->upload()){ // Upload the file
                
        //If file upload was successful, we fetch the uploaded files
        $uploadedFilesArr = $FU->getUploadedFiles(true);
        
        //Loop through the array of uploaded files ($uploadedFilesArr) and save the files to database or do whatever you wish with them
                

    }else
        $uploadErr = $FU->getErrors(); //If upload failed, get the errors to know why
                                        
    
}else{

  //Alert File Not Selected

}

?>

```

### Overwriting Existing File in Upload Path :
Existing file with same name in the target upload path can be overwritten by calling the `setOverwrite()` method as shown below

```php

<?php

$FU->setOverwrite($bool: TRUE | FALSE);

?>

```

### Renaming Existing File in Upload Path :
Existing file with same name in the target upload path can be renamed by calling the `setRename()` method as shown below

```php

<?php

$FU->setRename($ren, $numOnly=false, $alphaOnly=false);

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $ren => bool: TRUE | FALSE -> A boolean flag that instruct the uploader to rename the file 
 * 
 * @param $numOnly => bool: TRUE | FALSE -> A boolean flag that instruct the uploader to use digits only while 
 * renaming the file
 * 
 * @param $alphaOnly => bool: TRUE | FALSE -> A boolean flag that instruct the uploader to use alphabets only 
 * while renaming the file
 * 
****/

?>

```

### Set File Upload Path :
To set a new upload path, simply call `setUploadPath()` method as shown below

```php

<?php

$FU->setUploadPath($path);

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $path => Your desired upload path 
 * 
****/

?>

```

### Set Allowed File Extensions :
To set file extensions that are allowed, simply call `setAllowedExt()` method as shown below

```php

<?php

$FU->setAllowedExt($extArr);

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $extArr => array of all permissible file extensions E.g array("png", "jpg", "jpeg", "svg") 
 * 
****/

?>

```

### Set Maximum Allowed File Size :
To set maximum file size that are allowed, simply call `setMaxSize()` method as shown below

```php

<?php

$FU->setMaxSize($maxSize);

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $maxSize => A number representing the maximum allowed file size in byte
 * 
****/

?>

```

### Set Maximum Files Allowed :
To set the maximum number of files that are allowed, simply call `setMaxUploads()` method as shown below

```php

<?php

$FU->setMaxUploads($max, $uploadCounts, $cmt='');

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $max => A number representing the maximum allowed files count
 * 
 * @param $uploadCounts => A counter holding count of files uploaded
 * 
 * @param $cmt => A comment message to be displayed if maximum allowed file count is exceeded
 * 
****/

?>

```

### Get Uploaded File Names :
To get the names of the uploaded files, simply call `getUploadedFiles()` method as shown below

```php

<?php

$FU->getUploadedFiles($retArr = TRUE);

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $retArr => boolean: If TRUE returns the array of all uploaded file names
 * 
****/

?>

```


### Get Uploaded Files Original Names :
To get the original names of the uploaded files, simply call `getOriginalFileNames()` method as shown below

```php

<?php

$FU->getOriginalFileNames($retArr = false);

/****
 * 
 * PARAM DEFINITION
 * 
 * @param $retArr => boolean: If TRUE returns the array of all uploaded file original names
 * 
****/

?>

```


> [!NOTE]
> Explore the FileUploader class for other useful getters and setters method


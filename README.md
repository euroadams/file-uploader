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

> [!NOTE]
> Explore the FileUploader class for other useful getters and setters method


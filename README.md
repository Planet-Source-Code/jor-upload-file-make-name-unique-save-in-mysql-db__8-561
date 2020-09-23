<div align="center">

## Upload file, make name unique, save in MySql DB


</div>

### Description

This code will upload a file from a client computer to your server,

give the file a new, unique name

and save the new filename into a MySql database.

It also checks the size of the file so you can give a maximum size for all files that will be uploaded.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Jor](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/jor.md)
**Level**          |Beginner
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__8-2.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/jor-upload-file-make-name-unique-save-in-mysql-db__8-561/archive/master.zip)





### Source Code

```
***upload.html***
<html>
<head>
</title></title>
</head>
<body>
<form name=form1 action=upload.php method=post enctype=multipart/form-data>
<input type=file name=FileToUpload>
<input type=hidden name=MaxFileSize value=64000>
</form>
</body>
</html>
***upload.php***
<?php
if ($FileToUpload_type == 'image/gif') {
$type = '.gif';
}
if ($FileToUpload_type == 'image/pjpeg') {
$type = '.jpg';
}
if ($FileToUpload_type == 'image/x-png') {
$type = '.jpg';
}
$newfile = substr($FileToUpload, -9);
if($FileToUpload_name = '') {
print("No file was selected!");
}
elseif($FileToUpload_size > $MaxFileSize) {
print("The file to upload is too big");
}
else {
$global_db = mysql_connect('localhost', 'User', 'Password');
mysql_select_db('DBName', $global_db) or die("Connection error");
$query = "INSERT INTO Filetable (File) VALUES ('$newfile$type')";
$result = mysql_query($query) or die("ERROR");
move_uploaded_file($FileToUpload, "/full/path/on/your/server/images/$newfile$type");
}
?>
```


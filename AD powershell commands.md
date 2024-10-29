## Reset Password
>Set-ADAccountPassword -Server domain -Identity username

replace the 'domain' name and username ex: Set-ADAccountPassword -Server google.com -Identity prabhudev

## Display fullname of a user 
>Get-ADUser -Identity username -Properties DisplayName | Select-Object DisplayName
replace username with actual username

## Check is user account is enabled with username prompt
>$User = Read-Host -Prompt 'Input the user name'; Get-ADUser -Filter {name -like $User -or samaccountname -like $User} | select SamAccountName, Enabled

## Read usernames from a txt file and check if the users are active
$ $infile = "C:\Users\prabhudev\Desktop\Users.txt"
#
$ $users = Get-Content $infile  
#
$ foreach ($user in $users) { 
$ $aduser = Get-ADUser -Filter {name -like $user -or samaccountname -like $user} -ErrorAction SilentlyContinue
$ if ($aduser) {
$  $aduser | select SamAccountName, Enabled
$ } 
$ else { 
$  Write-Host "User '$user' not found in AD"
$  }
$ }

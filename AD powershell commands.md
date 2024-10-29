## Reset Password
>Set-ADAccountPassword -Server domain -Identity username

replace the 'domain' name and username ex: Set-ADAccountPassword -Server google.com -Identity prabhudev

## Display fullname of a user 
>Get-ADUser -Identity username -Properties DisplayName | Select-Object DisplayName
replace username with actual username

## User status with username prompt
>$User = Read-Host -Prompt 'Input the user name'; Get-ADUser -Filter {name -like $User -or samaccountname -like $User} | select SamAccountName, Enabled

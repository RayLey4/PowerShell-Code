# 定义导出路径
$ExportPath = "C:\ExportedUsers.csv"

# 获取所有用户并导出
Get-ADUser -Filter * -Properties SamAccountName,GivenName,Surname,UserPrincipalName,EmailAddress,Enabled,PasswordLastSet |
    Select-Object SamAccountName,GivenName,Surname,UserPrincipalName,EmailAddress,Enabled,PasswordLastSet |
    Export-Csv -Path $ExportPath -NoTypeInformation -Encoding UTF8

Write-Host "用户信息已导出到 $ExportPath" -ForegroundColor Green

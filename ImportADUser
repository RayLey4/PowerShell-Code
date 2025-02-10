# 导入用户的 CSV 文件路径
$ImportPath = "C:\ExportedUsers.csv"

# 定义用户创建路径（目标 OU）
$TargetOU = "OU=OU,DC=dc,DC=eu"

# 导入用户并创建
Import-Csv -Path $ImportPath | ForEach-Object {
    $SamAccountName = $_.SamAccountName
    $GivenName = $_.GivenName
    $Surname = $_.Surname
    $UserPrincipalName = $_.UserPrincipalName
    $EmailAddress = $_.EmailAddress
    $Enabled = [bool]::Parse($_.Enabled)

    # 设置显示名称（Name），可使用 GivenName 和 Surname 或 SamAccountName
    $Name = "$GivenName $Surname"
    if (-not $GivenName -or -not $Surname) { $Name = $SamAccountName }

    # 创建用户
    New-ADUser -SamAccountName $SamAccountName `
               -Name $Name `
               -GivenName $GivenName `
               -Surname $Surname `
               -UserPrincipalName $UserPrincipalName `
               -EmailAddress $EmailAddress `
               -Path $TargetOU `
               -AccountPassword (ConvertTo-SecureString "Password01!" -AsPlainText -Force) `
               -Enabled $Enabled

    Write-Host "用户 $SamAccountName 已成功创建！" -ForegroundColor Green
}

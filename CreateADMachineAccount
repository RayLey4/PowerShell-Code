# Define the file path
$CSVPath = "C:\Computer.csv"
$Computers = Import-Csv -Path $CSVPath

#create computer account
foreach ($Computer in $Computers) {
    $Name = $Computer.Name
    $sAMAccountName = $Computer.sAMAccountName
    $DN = $Computer.DN
# check if computer exist
    if (Get-ADComputer -Filter { Name -eq $Name }) {
        Write-Host "Computer $Name exist, skip create" -ForegroundColor Yellow
    }
    else {
    #create computer account
    New-ADComputer -Name $Name -SAMAccountName $sAMAccountName -Path $DN -Enabled $true -PassThru |
    Select-Object Name, DistinguishedName

    Write-Host "Computer $Name Create Successfully" -ForegroundColor Green
    }
}
Write-Host "All the Computers created finished!" -ForegroundColor Cyan


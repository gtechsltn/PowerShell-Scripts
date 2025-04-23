# PowerShell Scripts

## Delete File: Check if File Exists Before Deleting (Recommended)
```
Set-ExecutionPolicy -Scope LocalMachine -ExecutionPolicy RemoteSigned -Force

Clear-Host

$CurrentDir = (Get-Location).Path
Write-Host "Get-Location into CurrentDir variable: DONE" -ForegroundColor DarkGreen -BackgroundColor Black

Try {    
    # Code that may throw an exception

    $filePath = "C:\Path\To\Your\File.xml"

    if (Test-Path $filePath) {
        Remove-Item -Path $filePath -Force
        Write-Output "Deleted: $filePath"
    } else {
        Write-Output "File not found: $filePath"
    }

    Set-Location -Path 'D:\D2\ThirdSight.DataMigration' -PassThru
    Write-Host "Set-Location -Path 'D:\D2\ThirdSight.DataMigration': DONE" -ForegroundColor DarkGreen -BackgroundColor Black
    Write-Host "------------------------------------------------------------" -ForegroundColor DarkGreen -BackgroundColor Black

}
Catch [System.Exception] {
    # Code to handle the error

    Write-Host $_.Exception.Message -ForegroundColor Red -BackgroundColor Yellow
}
Finally {
    # Code that runs regardless of an error occurring or not

    Set-Location -Path $CurrentDir -PassThru
    Write-Host "Set-Location -Path '$CurrentDir' : DONE" -ForegroundColor DarkGreen -BackgroundColor Black
    Write-Host "------------------------------------------------------------" -ForegroundColor DarkGreen -BackgroundColor Black
}
```

# Map network printer for XYZ Technology Solutions
$PrinterIP = "192.168.1.100"
$PrinterName = "XYZ-Office-Printer"

# Add printer port
Add-PrinterPort -Name "IP_$PrinterIP" -PrinterHostAddress $PrinterIP

# Add printer using the port
Add-Printer -Name $PrinterName `
            -DriverName "Generic / Text Only" `
            -PortName "IP_$PrinterIP"

Write-Host "Printer $PrinterName mapped successfully"
Links: [[PROGRAMMING]]
Rel: [[windows]]; [[ps1 bs]]

.ps1

--- 


### tuples:
```powershell
$a = ("this", "this1", "that")

$a | ForEach-Object {
    Write-Host $_
    }


$A = Get-ChildItem c:\temp\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

### for loops:
```powershell
$computers = import-csv “c:temp\computers.csv”

ForEach ($computer in $computers){

	$computername = $($computer.Computername)
	$ipaddress = $($computer.IPaddress)
	$office = $($computer.Office)
	$owner = $($computer.Owner)

	Write-host $computername $ipaddress $office $owner
	}
```

```powershell
$Name = @()
$Phone = @()

Import-Csv H:\Programs\scripts\SomeText.csv |

    ForEach-Object {
        $Name += $_.Name
        $Phone += $_."Phone Number"
    }

$inputNumber = Read-Host -Prompt "Phone Number"
if ($Phone -contains $inputNumber)
    {
    Write-Host "Customer Exists!"

    $Where = [array]::IndexOf($Phone, $inputNumber)
      
    Write-Host "Customer Name: " $Name[$Where]
    }
```
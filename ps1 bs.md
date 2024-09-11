Links: [[PROGRAMMING]]
Rel: [[PowerShell]]

--- 

**general_uninstall_draft.ps1**

```powershell

$msiErrors = @{
    # SOURCE: https://docs.microsoft.com/en-us/windows/win32/msi/error-codes
    0="ERROR_SUCCESS:  `nThe action completed successfully.`n`n";
    13="ERROR_INVALID_DATA:  `nThe data is invalid.`n`n";
    87="ERROR_INVALID_PARAMETER:  `nOne of the parameters was invalid.`n`n";
    120="ERROR_CALL_NOT_IMPLEMENTED:  `nThis value is returned when a custom action attempts to call a function that cannot be called from custom actions. The function returns the value ERROR_CALL_NOT_IMPLEMENTED. Available beginning with Windows Installer version 3.0.`n`n";
    1259="ERROR_APPHELP_BLOCK:  `nIf Windows Installer determines a product may be incompatible with the current operating system, it displays a dialog box informing the user and asking whether to try to install anyway. This error code is returned if the user chooses not to try the installation.`n`n";
    1601="ERROR_INSTALL_SERVICE_FAILURE:  `nThe Windows Installer service could not be accessed. Contact your support personnel to verify that the Windows Installer service is properly registered.`n`n";
    1602="ERROR_INSTALL_USEREXIT:  `nThe user cancels installation.`n`n";
    1603="ERROR_INSTALL_FAILURE:  `nA fatal error occurred during installation.`n`n";
    1604="ERROR_INSTALL_SUSPEND:  `nInstallation suspended, incomplete.`n`n";
    1605="ERROR_UNKNOWN_PRODUCT:  `nThis action is only valid for products that are currently installed.`n`n";
    1606="ERROR_UNKNOWN_FEATURE:  `nThe feature identifier is not registered.`n`n";
    1607="ERROR_UNKNOWN_COMPONENT:  `nThe component identifier is not registered.`n`n";
    1608="ERROR_UNKNOWN_PROPERTY:  `nThis is an unknown property.`n`n";
    1609="ERROR_INVALID_HANDLE_STATE:  `nThe handle is in an invalid state.`n`n";
    1610="ERROR_BAD_CONFIGURATION:  `nThe configuration data for this product is corrupt. Contact your support personnel.`n`n";
    1611="ERROR_INDEX_ABSENT:  `nThe component qualifier not present.`n`n";
    1612="ERROR_INSTALL_SOURCE_ABSENT:  `nThe installation source for this product is not available. Verify that the source exists and that you can access it.`n`n";
    1613="ERROR_INSTALL_PACKAGE_VERSION:  `nThis installation package cannot be installed by the Windows Installer service. You must install a Windows service pack that contains a newer version of the Windows Installer service.`n`n";
    1614="ERROR_PRODUCT_UNINSTALLED:  `nThe product is uninstalled.`n`n";
    1615="ERROR_BAD_QUERY_SYNTAX:  `nThe SQL query syntax is invalid or unsupported.`n`n";
    1616="ERROR_INVALID_FIELD:  `nThe record field does not exist.`n`n";
    1618="ERROR_INSTALL_ALREADY_RUNNING:  `nAnother installation is already in progress. Complete that installation before proceeding with this install.For information about the mutex, see _MSIExecute Mutex.`n`n";
    1619="ERROR_INSTALL_PACKAGE_OPEN_FAILED:  `nThis installation package could not be opened. Verify that the package exists and is accessible, or contact the application vendor to verify that this is a valid Windows Installer package.`n`n";
    1620="ERROR_INSTALL_PACKAGE_INVALID:  `nThis installation package could not be opened. Contact the application vendor to verify that this is a valid Windows Installer package.`n`n";
    1621="ERROR_INSTALL_UI_FAILURE:  `nThere was an error starting the Windows Installer service user interface. Contact your support personnel.`n`n";
    1622="ERROR_INSTALL_LOG_FAILURE:  `nThere was an error opening installation log file. Verify that the specified log file location exists and is writable.`n`n";
    1623="ERROR_INSTALL_LANGUAGE_UNSUPPORTED:  `nThis language of this installation package is not supported by your system.`n`n";
    1624="ERROR_INSTALL_TRANSFORM_FAILURE:  `nThere was an error applying transforms. Verify that the specified transform paths are valid.`n`n";
    1625="ERROR_INSTALL_PACKAGE_REJECTED:  `nThis installation is forbidden by system policy. Contact your system administrator.`n`n";
    1626="ERROR_FUNCTION_NOT_CALLED:  `nThe function could not be executed.`n`n";
    1627="ERROR_FUNCTION_FAILED:  `nThe function failed during execution.`n`n";
    1628="ERROR_INVALID_TABLE:  `nAn invalid or unknown table was specified.`n`n";
    1629="ERROR_DATATYPE_MISMATCH:  `nThe data supplied is the wrong type.`n`n";
    1630="ERROR_UNSUPPORTED_TYPE:  `nData of this type is not supported.`n`n";
    1631="ERROR_CREATE_FAILED:  `nThe Windows Installer service failed to start. Contact your support personnel.`n`n";
    1632="ERROR_INSTALL_TEMP_UNWRITABLE:  `nThe Temp folder is either full or inaccessible. Verify that the Temp folder exists and that you can write to it.`n`n";
    1633="ERROR_INSTALL_PLATFORM_UNSUPPORTED:  `nThis installation package is not supported on this platform. Contact your application vendor.`n`n";
    1634="ERROR_INSTALL_NOTUSED:  `nComponent is not used on this machine.`n`n";
    1635="ERROR_PATCH_PACKAGE_OPEN_FAILED:  `nThis patch package could not be opened. Verify that the patch package exists and is accessible, or contact the application vendor to verify that this is a valid Windows Installer patch package.`n`n";
    1636="ERROR_PATCH_PACKAGE_INVALID:  `nThis patch package could not be opened. Contact the application vendor to verify that this is a valid Windows Installer patch package.`n`n";
    1637="ERROR_PATCH_PACKAGE_UNSUPPORTED:  `nThis patch package cannot be processed by the Windows Installer service. You must install a Windows service pack that contains a newer version of the Windows Installer service.`n`n";
    1638="ERROR_PRODUCT_VERSION:  `nAnother version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs in Control Panel.`n`n";
    1639="ERROR_INVALID_COMMAND_LINE:  `nInvalid command line argument. Consult the Windows Installer SDK for detailed command-line help.`n`n";
    1640="ERROR_INSTALL_REMOTE_DISALLOWED:  `nThe current user is not permitted to perform installations from a client session of a server running the Terminal Server role service.`n`n";
    1641="ERROR_SUCCESS_REBOOT_INITIATED:  `nThe installer has initiated a restart. This message is indicative of a success.`n`n";
    1642="ERROR_PATCH_TARGET_NOT_FOUND:  `nThe installer cannot install the upgrade patch because the program being upgraded may be missing or the upgrade patch updates a different version of the program. Verify that the program to be upgraded exists on your computer and that you have the correct upgrade patch.`n`n";
    1643="ERROR_PATCH_PACKAGE_REJECTED:  `nThe patch package is not permitted by system policy.`n`n";
    1644="ERROR_INSTALL_TRANSFORM_REJECTED:  `nOne or more customizations are not permitted by system policy.`n`n";
    1645="ERROR_INSTALL_REMOTE_PROHIBITED:  `nWindows Installer does not permit installation from a Remote Desktop Connection.`n`n";
    1646="ERROR_PATCH_REMOVAL_UNSUPPORTED:  `nThe patch package is not a removable patch package. Available beginning with Windows Installer version 3.0.`n`n";
    1647="ERROR_UNKNOWN_PATCH:  `nThe patch is not applied to this product. Available beginning with Windows Installer version 3.0.`n`n";
    1648="ERROR_PATCH_NO_SEQUENCE:  `nNo valid sequence could be found for the set of patches. Available beginning with Windows Installer version 3.0.`n`n";
    1649="ERROR_PATCH_REMOVAL_DISALLOWED:  `nPatch removal was disallowed by policy. Available beginning with Windows Installer version 3.0.`n`n";
    1650="ERROR_INVALID_PATCH_XML:  `nThe XML patch data is invalid. Available beginning with Windows Installer version 3.0.`n`n";
    1651="ERROR_PATCH_MANAGED_ADVERTISED_PRODUCT:  `nAdministrative user failed to apply patch for a per-user managed or a per-machine application that is in advertise state. Available beginning with Windows Installer version 3.0.`n`n";
    1652="ERROR_INSTALL_SERVICE_SAFEBOOT:  `nWindows Installer is not accessible when the computer is in Safe Mode. Exit Safe Mode and try again or try using System Restore to return your computer to a previous state. Available beginning with Windows Installer version 4.0.`n`n";
    1653="ERROR_ROLLBACK_DISABLED:  `nCould not perform a multiple-package transaction because rollback has been disabled. Multiple-Package Installations cannot run if rollback is disabled. Available beginning with Windows Installer version 4.5.`n`n";
    1654="ERROR_INSTALL_REJECTED:  `nThe app that you are trying to run is not supported on this version of Windows. A Windows Installer package, patch, or transform that has not been signed by Microsoft cannot be installed on an ARM computer.`n`n";
    3010="ERROR_SUCCESS_REBOOT_REQUIRED:  `nA restart is required to complete the install. This message is indicative of a success. This does not include installs where the ForceReboot action is run.`n`n";
}

$successes = @(0, 1614, 1641, 3010)
$notifiers = @(1618, 1642)


# Variables:

$programRE = ""
$idNumber = ""


# The Script:
If ($idNumber -eq "") {
    # assumes an empty input box here & value given for $programRE
    $program = Get-WmiObject -Class Win32_Product -Filter "Name like '%$programRE%'"
    $varused = $programRE
} Else {
    # even if $programRE is ALSO populated by user, will default to use a given IdentifyingNumber,
    # which is a more precice method of finding the Program.
    If ($idNumber -notlike "{*}") {
        # Error handling for input mistakes:
        If ($idNumber -like "{*") {
            $idNumber = $idNumber + "}"
        } ElseIf ($idNumber -like "*}") {
            $idNumber = "{" + $idNumber
        } Else {
            $idNumber = "{" + $idNumber + "}"
        }
    }
    $program = Get-WmiObject -Class Win32_Product -Filter "IdentifyingNumber='$idNumber'"
    $varused = $idNumber
}

If ($program -is [Array]) {
    Write-Host "!NOTIFY"
    Write-Host "Found multiple Programs matching the input:"
    ForEach ($p in $program) {
        Write-Host $p.Name
        Write-Host $p.IdentifyingNumber
        Write-Host "`n" # place an extra newline between results
    }
    Write-Host "`nPlease adjust/narrow your search term or opt to use the Identifying Number."
    Write-Host "Nothing was uninstalled..."
    exit 0
} ElseIf ($program -eq $none) {
    Write-Host "!NOTIFY"
    Write-Host "Program matching $varused was not found to be installed."
    # add logic here for possible on-the-fly adjustments
    # e.g. try again after removing the last character of $programRE? Again?
    Write-Host "Nothing was uninstalled..."
} Else {
    Write-Host "UNINSTALL RESULTS OF: $varused `n`n"
    $result = $program.Uninstall()
    ForEach ($ec in $msiErrors.Keys) {
        If ($result.ReturnValue -eq $ec) {
            If ($ec -in $notifiers) {
                Write-Host "!NOTIFY"
            }
            Write-Host $msiErrors[$ec]
            If ($ec -in $successes) {
                exit 0
            } Else { exit 1 }
        }
    }
    # Getting this far means the script hasn't exited yet. 
    Write-Host "The Script failed to understand the ReturnValue of $result.ReturnValue"
    Write-Host "and therefore has exited as 'Failed'."
    Write-Host "Step 1: Consult Google"
    Write-Host "Step 2: Decide what you, the User, did wrong."
    exit 1
}
```

--- 

**enablerdp.ps1**
```powershell

$check1 = Get-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections"

if ($check1.fDenyTSConnections -eq 1) {
    Write-host "RDP Disabled.  Enabling RDP"
    Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -value "0"
    Enable-NetFirewallRule -DisplayGroup "Remote Desktop"

    $check2 = Get-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections"
    if ($check2.fDenyTSConnections -eq 0) {
        Write-host "RDP is now Enabled.  Exiting."
        exit -0
    }
    else {
        Write-host "RDP Disabled (and did not Enable when making an attempt).  Please enable it manually."
        exit -1
    }
}
elseif($check1.fDenyTSConnections -eq 0) {
    Write-host "RDP Enabled.  Exiting"
    exit -0
}
```

--- 
**confirm_win7_esu.ps1**
```powershell

function Read-ESULicence {
    $fullLicenseBlock = cscript /nologo "$env:systemroot\system32\slmgr.vbs" /dlv

    $exitingas = 1
    $idx = -1
    $esuLicenseBlock = @()
    ForEach ($line in $fullLicenseBlock) {
        $idx += 1
        if ($line -like "Name:*Client-ESU*") {
            $exitingas = 0 
            $esuLicenseBlock += $line
            $end = $idx + 13
            for ($i=$idx+1; $i -le $end; $i++) {
                $esuLicenseBlock += $fullLicenseBlock[$i]
            }              
        }
    }
    return $exitingas, $fullLicenseBlock, $esuLicenseBlock
}


function Evaluate-ESULicence {
    Param(
        [int]$exas,
        [array]$fullLB,
        [array]$esuLB,
        [bool]$secondattempt=$false
        )
    if ($exas -eq 1) {
        write-Host "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -"
        Write-Host "THE ESU MAK HAS NOT BEEN APPLIED..."
        Write-Host "SEE BELOW FOR FULL OUTPUT OF slmgr.vbs"
        write-Host "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -`n`n"

        ForEach ($line in $fullLB) {Write-Host $line}
        exit 1
    } else {
        Write-Host "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -"
        Write-Host "THE ESU MAK HAS BEEN APPLIED!"

        if ($esuLB[11] -like "*Unlicensed") {
            if ($secondattempt -eq $false) {
                Write-Host "Currently Unlicenced... Attempting to activate..."

                $activationID = $esuLB[2].split()[2]
                cscript /nologo "$env:systemroot\system32\slmgr.vbs" /ato $activationID
                
                $ec2, $fLB2, $eLB2 = Read-ESULicence
                Evaluate-ESULicence -exas $ec2 -fullLB $fLB2 -esuLB $eLB2 -secondattempt $true
            } else {
                Write-Host 'ERROR: "Unlicensed"'
                }
        } else {
            Write-Host 'SUCCESS: "Licensed"'
        }
        write-Host "- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -`n`n"

        ForEach ($line in $esuLB) {Write-Host $line}
        exit 0
    }
} 


$exas, $fullLB, $esuLB = Read-ESULicence

Evaluate-ESULicence -exas $exas -fullLB $fullLB -esuLB $esuLB
```

--- 

**testing_collect_ad_computer_info.ps1**

```powershell
Import-Module -Name ActiveDirectory

$D = Get-ADDomain
$D = $D.Name

$outdir = "$env:SystemDrive\temp"

if (!(Test-Path -Path $outdir)) {
    New-Item -ItemType directory -Path $outdir
    }

$outfi = "$outdir\" "$D" + "_computers_" + "" + ".csv"
Get-ADComputer -Filter * | Export-CSV "$outfi"


#######################################################
#######################################################

Import-Module -Name ActiveDirectory

$D = Get-ADDomain
$D = $D.Name
$U = $Env:CS_PROFILE_UID

Write-Output ('"'+"$U"+'": [ # '+"$D")
$Computers = Get-ADComputer -Filter *
ForEach ($C in $Computers) {
    $name = $($C.Name)
    $enabled = $($C.Enabled)
    Write-Output ("`t"+'("'+"$name"+'",'+" $enabled"+"),")
}
Write-Output ("`t],")
```
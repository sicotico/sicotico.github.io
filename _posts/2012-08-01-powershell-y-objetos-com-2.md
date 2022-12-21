---
layout: post
title: "PowerShell y objetos COM"
date: "2012-08-01"
categories: dev
---

No siempre PowerShell nos resuelve el problema , esta en pleno crecimiento. Un truquito que podemos utilizar , sin abusar mucho , es utilizar los objeto COM que hemos utilizado VBS o WSH. En este caso será el objeto `WScript.Network`

\[box type="info"\] He localizado este blog en el que el autor ha realizdo el ejerciciod e reconvertir scripts tipos de VSH a el nuevo PowerShell [Blog Pauerschell](https://pauerschell.blogspot.com.es/2010/03/powershell-and-network-drives.html)

\[/box\]

 

            
    Param(            
        \[string\]$Drive,            
        \[string\]$Unc            
        )            
    $net = New-Object -com WScript.Network            
    if ($Drive.length -eq 1) { $Drive = $Drive +':' }            
    "$Drive $UNC"            
    $net.mapnetworkdrive($Drive, $Unc)            
    # ToDo -- currently I don#t need it            
    #$net.mapnetworkdrive($Drive+ ':',$Unc, $bProfile, $User, $password)            
}            

function Get-NetworkDrives            
{            

    $mappedDrives = @{}            
    $net = New-Object -com WScript.Network             
    $a = $net.EnumNetworkDrives()            
    $anz = $a.count()            

    for ($i = 0; $i -lt $anz; $i = $i + 2)            
    {            
        $drive = $a.item($i)            
        $path = $a.item($i+1)            
        $mappedDrives\[$drive\] = $path            
    }            
    $mappedDrives            
}            

function Remove-NetworkDrive($Drive)            
{            

    $net = New-Object -com WScript.Network            
    if ($Drive.length -eq 1) { $Drive += ':' }            
    $net.removenetworkdrive($Drive)            
}

 

También indico las fuentes originales:

[Logon\_MapNetworkDrive.htm](https://www.computerperformance.co.uk/Logon/Logon_MapNetworkDrive.htm) [LogonScript\_enumnetworkdrives.htm#EnumNetworkDrives\_Syntax](https://www.computerperformance.co.uk/powershell/index.htm) [Powershell index.htm](https://www.computerperformance.co.uk/powershell/index.htm) [Blogs technet, hey scripting Guy](https://blogs.technet.com/heyscriptingguy/)

---
title: Windows PowerShell への SMO アセンブリの読み込み | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9886d80c305dba251e6e3ab22ddb4dfb39783748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712057"
---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a><span data-ttu-id="3163a-102">Windows PowerShell への SMO アセンブリの読み込み</span><span class="sxs-lookup"><span data-stu-id="3163a-102">Load the SMO Assemblies in Windows PowerShell</span></span>
  <span data-ttu-id="3163a-103">このトピックでは、SQL Server PowerShell プロバイダーを使用しない Windows PowerShell スクリプトに SQL Server 管理オブジェクト (SMO) アセンブリを読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3163a-103">This topic describes how to load the SQL Server Management Object (SMO) assemblies in Windows PowerShell scripts that do not use the SQL Server PowerShell provider.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="3163a-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="3163a-104">Before You Begin</span></span>  
 <span data-ttu-id="3163a-105">SMO アセンブリを読み込むための推奨メカニズムは、`sqlps` モジュールを読み込むことです。</span><span class="sxs-lookup"><span data-stu-id="3163a-105">The preferred mechanism for loading the SMO assemblies is to load the `sqlps` module.</span></span> <span data-ttu-id="3163a-106">モジュールに含まれている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーは、自動的に SMO アセンブリを読み込み、PowerShell スクリプトでの SMO オブジェクトの実用性を拡張する機能も実装します。</span><span class="sxs-lookup"><span data-stu-id="3163a-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider included in the module automatically loads the SMO assemblies, and also implements features that extend the usefulness of the SMO objects in PowerShell scripts.</span></span>  
  
 <span data-ttu-id="3163a-107">ただし、次の 2 つの場合については、直接 SMO アセンブリを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="3163a-107">There are two cases where you may need to load the SMO assemblies directly:</span></span>  
  
-   <span data-ttu-id="3163a-108">スクリプトが、プロバイダーを参照する最初のコマンドまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スナップインのコマンドレットより先に SMO オブジェクトを参照する場合。</span><span class="sxs-lookup"><span data-stu-id="3163a-108">If your script references a SMO object before the first command that references the provider or cmdlets from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins.</span></span>  
  
-   <span data-ttu-id="3163a-109">プロバイダーやコマンドレットを使用しない別の言語 (C#、Visual Basic など) から SMO コードを移植する場合。</span><span class="sxs-lookup"><span data-stu-id="3163a-109">You want to port SMO code from another language, such as C# or Visual Basic, which does not use the provider or cmdlets.</span></span>  
  
## <a name="example-loading-the-sql-server-management-objects"></a><span data-ttu-id="3163a-110">例: SQL Server 管理オブジェクトの読み込み</span><span class="sxs-lookup"><span data-stu-id="3163a-110">Example: Loading the SQL Server Management Objects</span></span>  
 <span data-ttu-id="3163a-111">SMO アセンブリを読み込むコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3163a-111">The following code loads the SMO assemblies:</span></span>  
  
```powershell
# Loads the SQL Server Management Objects (SMO)  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg = "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
Update-FormatData -PrependPath SQLProvider.Format.ps1xml
Pop-Location  
```  
  
## <a name="see-also"></a><span data-ttu-id="3163a-112">参照</span><span class="sxs-lookup"><span data-stu-id="3163a-112">See Also</span></span>  
 [<span data-ttu-id="3163a-113">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="3163a-113">SQL Server PowerShell</span></span>](sql-server-powershell.md)  

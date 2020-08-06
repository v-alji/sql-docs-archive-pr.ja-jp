---
title: プログラムによる使用可能なパッケージの列挙 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically enumerate packages [SSIS]
- existence testing [Integration Services]
- enumerating packages [Integration Services]
ms.assetid: 254ec7ee-d3ff-4361-8995-46e9b9c4dc95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053f2e598b1cc18e68ee2182092188367ee7f10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713237"
---
# <a name="enumerating-available-packages-programmatically"></a><span data-ttu-id="a6cd9-102">プログラムによる使用可能なパッケージの列挙</span><span class="sxs-lookup"><span data-stu-id="a6cd9-102">Enumerating Available Packages Programmatically</span></span>
  <span data-ttu-id="a6cd9-103">プログラムにより [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを操作する際に、個々のパッケージまたはフォルダーが存在するかどうかを判断したり、読み込みと実行が可能な保存済みパッケージを列挙したりする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to enumerate the saved packages that are available to load and execute.</span></span> <span data-ttu-id="a6cd9-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> <span data-ttu-id="a6cd9-105">パッケージまたはフォルダーが存在するかどうかの判断</span><span class="sxs-lookup"><span data-stu-id="a6cd9-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="a6cd9-106">保存済みのパッケージの読み込みと実行を行う前に、プログラムによってそのパッケージが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run it:</span></span>  
  
|<span data-ttu-id="a6cd9-107">保存先</span><span class="sxs-lookup"><span data-stu-id="a6cd9-107">Storage Location</span></span>|<span data-ttu-id="a6cd9-108">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="a6cd9-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="a6cd9-109">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="a6cd9-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="a6cd9-110">フォルダーに保存されているパッケージを一覧表示する前に、プログラムによりそのフォルダーが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-110">To determine programmatically whether a folder exists before attempting to list the packages stored in it, call one of the following methods:</span></span>  
  
|<span data-ttu-id="a6cd9-111">保存先</span><span class="sxs-lookup"><span data-stu-id="a6cd9-111">Storage Location</span></span>|<span data-ttu-id="a6cd9-112">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="a6cd9-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="a6cd9-113">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="a6cd9-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  
 [<span data-ttu-id="a6cd9-114">先頭に戻る</span><span class="sxs-lookup"><span data-stu-id="a6cd9-114">Back to top</span></span>](#top)  
  
##  <a name="enumerating-available-packages"></a><a name="listing"></a> <span data-ttu-id="a6cd9-115">使用可能なパッケージの列挙</span><span class="sxs-lookup"><span data-stu-id="a6cd9-115">Enumerating Available Packages</span></span>  
 <span data-ttu-id="a6cd9-116">プログラムにより保存済みパッケージの一覧を取得するには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-116">To obtain a list of saved packages programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="a6cd9-117">保存先</span><span class="sxs-lookup"><span data-stu-id="a6cd9-117">Storage Location</span></span>|<span data-ttu-id="a6cd9-118">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="a6cd9-118">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="a6cd9-119">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="a6cd9-119">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A>|  
  
 <span data-ttu-id="a6cd9-120">次のサンプルは、これらのメソッドの使用方法を示すコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-120">The following samples are console applications that demonstrate the use of these methods.</span></span>  
  
###  <a name="example-ssis-package-store"></a><a name="listing_store"></a> <span data-ttu-id="a6cd9-121">例 (SSIS パッケージ ストア)</span><span class="sxs-lookup"><span data-stu-id="a6cd9-121">Example (SSIS Package Store)</span></span>  
 <span data-ttu-id="a6cd9-122"><xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> メソッドを使用して、SSIS パッケージ ストアに保存されているパッケージを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> method to list packages stored in the SSIS Package Store.</span></span> <span data-ttu-id="a6cd9-123">SSIS パッケージ ストアによって管理される既定のストレージの場所は、ファイル システムおよび MSDB です。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-123">The default storage locations that are managed by the SSIS Package store are File System and MSDB.</span></span> <span data-ttu-id="a6cd9-124">これらの場所の中に、追加の論理フォルダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-124">You can create additional logical folders within these locations.</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlServer = "."  
  
    ssisApplication = New Application()  
  
    ' Get packages stored in MSDB.  
    sqlFolder = "MSDB"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in MSDB:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
      Console.WriteLine()  
    End If  
  
    ' Get packages stored in the File System.  
    sqlFolder = "File System"  
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)  
    If sqlPackages.Count > 0 Then  
      Console.WriteLine("Packages stored in the File System:")  
      For Each sqlPackage In sqlPackages  
        Console.WriteLine(sqlPackage.Name)  
      Next  
    End If  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSSIS_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlServer = ".";  
  
      ssisApplication = new Application();  
  
      // Get packages stored in MSDB.  
      sqlFolder = "MSDB";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in MSDB:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
        Console.WriteLine();  
      }  
  
      // Get packages stored in the File System.  
      sqlFolder = "File System";  
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);  
      if (sqlPackages.Count > 0)  
      {  
        Console.WriteLine("Packages stored in the File System:");  
        foreach (PackageInfo sqlPackage in sqlPackages)  
        {  
          Console.WriteLine(sqlPackage.Name);  
        }  
      }  
  
      Console.Read();  
  
    }  
  
  }  
  
}  
```  
  
 [<span data-ttu-id="a6cd9-125">先頭に戻る</span><span class="sxs-lookup"><span data-stu-id="a6cd9-125">Back to top</span></span>](#top)  
  
###  <a name="example-sql-server"></a><a name="listing_sql"></a> <span data-ttu-id="a6cd9-126">例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a6cd9-126">Example (SQL Server)</span></span>  
 <span data-ttu-id="a6cd9-127"><xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> メソッドを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインスタンスに保存されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> method to list [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that are stored in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim sqlFolder As String  
    Dim sqlServer As String  
    Dim sqlUser As String  
    Dim sqlPassword As String  
  
    Dim ssisApplication As Application  
    Dim sqlPackages As PackageInfos  
    Dim sqlPackage As PackageInfo  
  
    sqlFolder = String.Empty  
    sqlServer = "(local)"  
    sqlUser = String.Empty  
    sqlPassword = String.Empty  
  
    ssisApplication = New Application()  
  
    sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword)  
  
    For Each sqlPackage In sqlPackages  
      Console.WriteLine(sqlPackage.Name)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace EnumeratePackagesSql_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
  
      string sqlFolder;  
      string sqlServer;  
      string sqlUser;  
      string sqlPassword;  
  
      Application ssisApplication;  
      PackageInfos sqlPackages;  
  
      sqlFolder = String.Empty;  
      sqlServer = "(local)";  
      sqlUser = String.Empty;  
      sqlPassword = String.Empty;  
  
      ssisApplication = new Application();  
  
      sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword);  
  
      foreach (PackageInfo sqlPackage in sqlPackages)  
      {  
        Console.WriteLine(sqlPackage.Name);  
      }  
  
      Console.Read();  
  
    }  
  }  
}  
```  
  
 [<span data-ttu-id="a6cd9-128">先頭に戻る</span><span class="sxs-lookup"><span data-stu-id="a6cd9-128">Back to top</span></span>](#top)  
  
<span data-ttu-id="a6cd9-129">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="a6cd9-129">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a6cd9-130">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-130">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a6cd9-131">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="a6cd9-131">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a6cd9-132">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="a6cd9-132">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cd9-133">参照</span><span class="sxs-lookup"><span data-stu-id="a6cd9-133">See Also</span></span>  
 [<span data-ttu-id="a6cd9-134">パッケージの管理 &#40;SSIS サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="a6cd9-134">Package Management &#40;SSIS Service&#41;</span></span>](../service/package-management-ssis-service.md)  
  
  

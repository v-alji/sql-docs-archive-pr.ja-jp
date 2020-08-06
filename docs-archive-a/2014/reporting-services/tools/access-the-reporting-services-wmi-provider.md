---
title: Reporting Services WMI プロバイダーへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db0848ae8c988229a1804bbd4b19e6c38b68c35f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737927"
---
# <a name="access-the-reporting-services-wmi-provider"></a><span data-ttu-id="8c347-102">Reporting Services WMI プロバイダーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8c347-102">Access the Reporting Services WMI Provider</span></span>
  <span data-ttu-id="8c347-103">Reporting Services WMI プロバイダーは、ネイティブ モードのレポート サーバー インスタンスの管理に使用できる 2 つの WMI クラスを、スクリプトを通じて公開します。</span><span class="sxs-lookup"><span data-stu-id="8c347-103">The Reporting Services WMI provider exposes two WMI classes for administration of Native mode report server instances through scripting:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8c347-104">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] リリース以降では、WMI プロバイダーはネイティブ モードのレポート サーバーに対してのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8c347-104">Starting with the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, the WMI provider is supported for only native mode report servers.</span></span> <span data-ttu-id="8c347-105">SharePoint モードのレポート サーバーは、SharePoint サーバーの全体管理ページおよび PowerShell スクリプトを使用して管理できます。</span><span class="sxs-lookup"><span data-stu-id="8c347-105">SharePoint mode report servers can be managed with SharePoint Central Administration pages and PowerShell scripts.</span></span>  
  
|<span data-ttu-id="8c347-106">クラス</span><span class="sxs-lookup"><span data-stu-id="8c347-106">Class</span></span>|<span data-ttu-id="8c347-107">名前空間</span><span class="sxs-lookup"><span data-stu-id="8c347-107">Namespace</span></span>|<span data-ttu-id="8c347-108">説明</span><span class="sxs-lookup"><span data-stu-id="8c347-108">Description</span></span>|  
|-----------|---------------|-----------------|  
|<span data-ttu-id="8c347-109">MSReportServer_Instance</span><span class="sxs-lookup"><span data-stu-id="8c347-109">MSReportServer_Instance</span></span>|<span data-ttu-id="8c347-110">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \ v11</span><span class="sxs-lookup"><span data-stu-id="8c347-110">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11</span></span>|<span data-ttu-id="8c347-111">インストールされているレポート サーバーに接続するための基本情報をクライアントに提供します。</span><span class="sxs-lookup"><span data-stu-id="8c347-111">Provides basic information required for a client to connect to an installed report server.</span></span>|  
|<span data-ttu-id="8c347-112">MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="8c347-112">MSReportServer_ConfigurationSetting</span></span>|<span data-ttu-id="8c347-113">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \ V11\ Admin</span><span class="sxs-lookup"><span data-stu-id="8c347-113">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11\Admin</span></span>|<span data-ttu-id="8c347-114">レポート サーバー インスタンスのインストール パラメーターとランタイム パラメーターを表します。</span><span class="sxs-lookup"><span data-stu-id="8c347-114">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="8c347-115">これらのパラメーターはレポート サーバーの構成ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="8c347-115">These parameters are stored in the configuration file for the report server.</span></span><br /><br /> <span data-ttu-id="8c347-116">**\*\* 重要 \*\*** このクラスは管理者権限でのみアクセス可能です。</span><span class="sxs-lookup"><span data-stu-id="8c347-116">**\*\* Important \*\*** This class is only accessible with administrative privileges.</span></span>|  
  
 <span data-ttu-id="8c347-117">上記のクラスの各インスタンスは、レポート サーバー インスタンスごとに作成されます。</span><span class="sxs-lookup"><span data-stu-id="8c347-117">An instance of each of the above classes is created for each report server instance.</span></span> <span data-ttu-id="8c347-118">レポート サーバーによって公開されている WMI オブジェクト (.NET Framework 自体によって公開されている WMI プログラミング インターフェイスを含む) へは、Microsoft またはサード パーティの任意のツールを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8c347-118">You can use any Microsoft or third party tools to access the WMI objects exposed by the report server, including WMI programming interfaces exposed by the .NET Framework itself.</span></span> <span data-ttu-id="8c347-119">このトピックでは、PowerShell コマンド [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx)を使用した、WMI クラスのインスタンスに対するアクセス方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c347-119">This topic describes how to access and use the WMI class instances with the PowerShell command [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).</span></span>  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a><span data-ttu-id="8c347-120">名前空間文字列内のインスタンス名の確認</span><span class="sxs-lookup"><span data-stu-id="8c347-120">Determine the Instance Name in the Namespace String</span></span>  
 <span data-ttu-id="8c347-121">Reporting Services WMI クラスの名前空間パスに含まれるインスタンス名は、名前付き Reporting Services インスタンスのインストール時に指定したインスタンス名のエンコードです。</span><span class="sxs-lookup"><span data-stu-id="8c347-121">The instance name in the namespace path for the Reporting Services WMI classes is an encoding of the instance names that you specify when installing the named Reporting Services instances.</span></span> <span data-ttu-id="8c347-122">つまり、インスタンス名に含まれる特殊文字はエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="8c347-122">Namely, special characters in the instance names are encoded.</span></span> <span data-ttu-id="8c347-123">たとえば、アンダースコア (_) は "_5f" としてエンコードされるので、"My_Instance" のインスタンス名は WMI 名前空間パス内では "My_5fInstance" としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="8c347-123">For example, an underline (_) is encoded as "_5f", so an instance name of "My_Instance" is encoded as "My_5fInstance" in the WMI namespace path.</span></span>  
  
 <span data-ttu-id="8c347-124">使用しているレポート サーバー インスタンスについて、WMI 名前空間パス内でのエンコード後のインスタンス名の一覧を表示するには、次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c347-124">To list the encoded instance names of your report server instances in the WMI namespace path, use the following PowerShell command:</span></span>  
  
```powershell
Get-WmiObject -Namespace root\Microsoft\SqlServer\ReportServer -Class __Namespace -ComputerName hostname | Select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a><span data-ttu-id="8c347-125">PowerShell を使用した WMI クラスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8c347-125">Access the WMI Classes Using PowerShell</span></span>  
 <span data-ttu-id="8c347-126">WMI クラスにアクセスするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c347-126">To access the WMI classes, run the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace <namespacename> -Class <classname> -ComputerName <hostname>  
```  
  
 <span data-ttu-id="8c347-127">たとえば、ホスト myrshost の既定のレポート サーバー インスタンス上で MSReportServer_ConfigurationSetting クラスにアクセスするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c347-127">For example, to access the MSReportServer_ConfigurationSetting class on the default report server instance of the host myrshost, run the following command.</span></span> <span data-ttu-id="8c347-128">このコマンドを正常に実行するには、既定のレポート サーバー インスタンスが myrshost 上にインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c347-128">The default report server instance must be installed on myrshost for this command to succeed.</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 <span data-ttu-id="8c347-129">このコマンド構文は、すべてのクラス プロパティ名と値を出力します。</span><span class="sxs-lookup"><span data-stu-id="8c347-129">This command syntax outputs all class property names and values.</span></span> <span data-ttu-id="8c347-130">既定のレポート サーバー インスタンス (RS_MSSQLSERVER) の名前空間内のクラスにアクセスしている場合でも、MSReportServer_ConfigurationSetting クラスのすべてのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="8c347-130">Note that all instances of the class MSReportServer_ConfigurationSetting is returned, even though you are accessing the class in the namespace of the default report server instance (RS_MSSQLSERVER).</span></span> <span data-ttu-id="8c347-131">たとえば、myrshost が、既定のレポート サーバー インスタンスと、SHAREPOINT という名前付きレポート サーバー インスタンスを使用してインストールされている場合、このコマンドは、それら両方のレポート サーバー インスタンスのプロパティ名と値を出力します。</span><span class="sxs-lookup"><span data-stu-id="8c347-131">For example, if myrshost is installed with the default report server instance and a named report server instance called SHAREPOINT, this command will return two WMI objects and output the property names and values for both report server instances.</span></span>  
  
 <span data-ttu-id="8c347-132">複数のインスタンスが返される場合、特定のクラス インスタンスが返されるようにするには、-Filter パラメーターを使用して、固有の値 (InstanceName など) を持つプロパティで結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="8c347-132">To return a specific class instance when multiple instances are returned, use the -Filter parameter to filter the results based on properties with unique values such as InstanceName.</span></span> <span data-ttu-id="8c347-133">たとえば、既定のレポート サーバー インスタンスの WMI オブジェクトのみを返すには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c347-133">For example, to return only the WMI object for the default report server instance, use the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a><span data-ttu-id="8c347-134">使用可能なメソッドとプロパティの照会</span><span class="sxs-lookup"><span data-stu-id="8c347-134">Query the Available Methods and Properties</span></span>  
 <span data-ttu-id="8c347-135">特定の Reporting Services WMI クラスで使用できるメソッドとプロパティを確認するには、Get-WmiObject から Get-Member へと結果をパイプします。</span><span class="sxs-lookup"><span data-stu-id="8c347-135">To see what methods and properties are available in one of the Reporting Services WMI classes, pipe the results from Get-WmiObject to the Get-Member command.</span></span> <span data-ttu-id="8c347-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8c347-136">For example:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 <span data-ttu-id="8c347-137">Reporting Services WMI クラスのプロパティとメソッドのドキュメントについては、「...」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c347-137">For documentation on the properties and methods of the Reporting Services WMI classes, see ....</span></span>  
  
## <a name="use-a-wmi-method-or-property"></a><span data-ttu-id="8c347-138">WMI のメソッドまたはプロパティの使用</span><span class="sxs-lookup"><span data-stu-id="8c347-138">Use a WMI Method or Property</span></span>  
 <span data-ttu-id="8c347-139">Reporting Services クラスに対する WMI オブジェクトを用意し、使用可能なメソッドとプロパティを確認したら、それらのメソッドとプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c347-139">Once you have the WMI objects to the Reporting Services classes and know the available methods and properties, you can use these methods and properties.</span></span> <span data-ttu-id="8c347-140">たとえば、SHAREPOINT という名前付きレポート サーバー インスタンスを SharePoint 統合モードで作成した場合は、次のコマンド シーケンスを使用して、SharePoint サーバーの全体管理サイトの URL を取得できます。</span><span class="sxs-lookup"><span data-stu-id="8c347-140">For example, if you have a named report server instance in SharePoint integrated mode called SHAREPOINT, use the following command sequence to retrieve the URL for the SharePoint Central Administration site:</span></span>  
  
```powershell
$rsconfig = Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='SHAREPOINT'"  
$rsconfig.GetAdminSiteUrl()  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c347-141">参照</span><span class="sxs-lookup"><span data-stu-id="8c347-141">See Also</span></span>
 <span data-ttu-id="8c347-142">[Reporting Services WMI プロバイダーライブラリリファレンス &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8c347-142">[Reporting Services WMI Provider Library Reference &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="8c347-143">RSReportServer 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="8c347-143">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  

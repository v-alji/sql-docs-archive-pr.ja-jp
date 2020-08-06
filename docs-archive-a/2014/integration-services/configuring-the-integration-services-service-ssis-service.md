---
title: Integration Services サービスの構成 (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- configuration files [Integration Services]
- service [Integration Services], configuring
- default configuration files
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c70c41377a2c302e1a021c6ade2a9d487579fa64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738629"
---
# <a name="configuring-the-integration-services-service-ssis-service"></a><span data-ttu-id="73354-102">Integration Services サービスの構成 (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="73354-102">Configuring the Integration Services Service (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="73354-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="73354-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] <span data-ttu-id="73354-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="73354-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="73354-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="73354-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="73354-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの設定は、構成ファイルに基づきます。</span><span class="sxs-lookup"><span data-stu-id="73354-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service relies on a configuration file for its settings.</span></span> <span data-ttu-id="73354-107">既定では、この構成ファイルの名前は MsDtsSrvr.ini.xml であり、ファイルは%ProgramFiles%\Microsoft SQL server に保存されています。</span><span class="sxs-lookup"><span data-stu-id="73354-107">By default, the name for this configuration file is MsDtsSrvr.ini.xml, and the file is located in the folder, %ProgramFiles%\Microsoft SQL Server\120\DTS\Binn.</span></span>  
  
 <span data-ttu-id="73354-108">通常は、この構成ファイルに変更を加える必要も、この構成ファイルの既定の場所を変更する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="73354-108">Typically, you do not have to make any changes to this configuration file, nor do you have to change the file's default location.</span></span> <span data-ttu-id="73354-109">ただし、パッケージが [!INCLUDE[ssDE](../includes/ssde-md.md)]の名前付きインスタンスまたはリモート インスタンス、あるいは [!INCLUDE[ssDE](../includes/ssde-md.md)]の複数のインスタンスに格納されている場合は、構成ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73354-109">However, you will have to modify the configuration file if your packages are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)], or in multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="73354-110">また、構成ファイルを既定の場所とは別の場所に移動する場合は、ファイルの場所を指定するレジストリ キーを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73354-110">Also, if you move the configuration file to a location other than the default location, you will have to modify the Registry key that specifies the file location.</span></span>  
  
## <a name="configuration-file-contents"></a><span data-ttu-id="73354-111">構成ファイルの内容</span><span class="sxs-lookup"><span data-stu-id="73354-111">Configuration File Contents</span></span>  
 <span data-ttu-id="73354-112">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]をインストールすると、セットアップ プロセスによって [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの構成ファイルが作成およびインストールされます。</span><span class="sxs-lookup"><span data-stu-id="73354-112">When you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the setup process creates and installs the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="73354-113">この構成ファイルには、次の設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="73354-113">This configuration file contains the following settings:</span></span>  
  
-   <span data-ttu-id="73354-114">サービスが停止すると、パッケージに中止コマンドが送信されます。</span><span class="sxs-lookup"><span data-stu-id="73354-114">Packages are sent a stop command when the service stops.</span></span>  
  
-   <span data-ttu-id="73354-115">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト エクスプローラー内の [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に表示するルート フォルダーは、[MSDB] および [ファイル システム] フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="73354-115">The root folders to display for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in Object Explorer of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] are the MSDB and File System folders.</span></span>  
  
-   <span data-ttu-id="73354-116">サービスが管理するファイルシステム内のパッケージ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、%ProgramFiles%\Microsoft SQL server に格納されています。</span><span class="sxs-lookup"><span data-stu-id="73354-116">The packages in the file system that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages are located in %ProgramFiles%\Microsoft SQL Server\120\DTS\Packages.</span></span>  
  
 <span data-ttu-id="73354-117">この構成ファイルは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するパッケージを含む msdb データベースも指定します。</span><span class="sxs-lookup"><span data-stu-id="73354-117">This configuration file also specifies which msdb database contains the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service will manage.</span></span> <span data-ttu-id="73354-118">既定では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] と同時にインストールされる [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のインスタンスの msdb データベース内にあるパッケージを管理するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="73354-118">By default, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed at the same time as [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="73354-119">[!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスが同時にインストールされない場合、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]のローカルの既定インスタンスの msdb データベース内にあるパッケージを管理するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="73354-119">If an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] is not installed at the same time, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the local, default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
### <a name="default-configuration-file-example"></a><span data-ttu-id="73354-120">既定の構成ファイルの例</span><span class="sxs-lookup"><span data-stu-id="73354-120">Default Configuration File Example</span></span>  
 <span data-ttu-id="73354-121">次の設定を含む既定の構成ファイルを以下の例に示します。</span><span class="sxs-lookup"><span data-stu-id="73354-121">The following example shows a default configuration file that specifies the following settings:</span></span>  
  
-   <span data-ttu-id="73354-122">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが停止すると、パッケージは実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="73354-122">Packages stop running when the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service stops.</span></span>  
  
-   <span data-ttu-id="73354-123">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 内のパッケージ ストレージのルート フォルダーは、[MSDB] および [ファイル システム] フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="73354-123">The root folders for package storage in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are MSDB and File System.</span></span>  
  
-   <span data-ttu-id="73354-124">このサービスは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のローカルの既定インスタンスの msdb データベースに格納されるパッケージを管理します。</span><span class="sxs-lookup"><span data-stu-id="73354-124">The service manages packages that are stored in the msdb database of the local, default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="73354-125">このサービスは、ファイル システムの [パッケージ] フォルダーに格納されるパッケージを管理します。</span><span class="sxs-lookup"><span data-stu-id="73354-125">The service manages packages that are stored in the file system in the Packages folder.</span></span>  
  
 <span data-ttu-id="73354-126">**既定の構成ファイルの例**</span><span class="sxs-lookup"><span data-stu-id="73354-126">**Example of a Default Configuration File**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file"></a><span data-ttu-id="73354-127">構成ファイルの変更</span><span class="sxs-lookup"><span data-stu-id="73354-127">Modification of the Configuration File</span></span>  
 <span data-ttu-id="73354-128">構成ファイルを変更することによって、サービスが停止した場合にパッケージを継続して実行できるようにしたり、オブジェクト エクスプローラー内に別のルート フォルダーを表示したり、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するファイル システム内に別のフォルダーまたは追加のフォルダーを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="73354-128">You can modify the configuration file to allow packages to continue running if the service stops, to display additional root folders in Object Explorer, or to specify a different folder or additional folders in the file system to be managed by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="73354-129">たとえば、`SqlServerFolder` 型の別のルート フォルダーを作成して、[!INCLUDE[ssDE](../includes/ssde-md.md)]の追加インスタンスの msdb データベースでパッケージを管理できます。</span><span class="sxs-lookup"><span data-stu-id="73354-129">For example, you can create additional root folders of type, `SqlServerFolder`, to manage packages in the msdb databases of additional instances of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73354-130">一部の文字は、フォルダー名には無効です。</span><span class="sxs-lookup"><span data-stu-id="73354-130">Some characters are not valid in folder names.</span></span> <span data-ttu-id="73354-131">フォルダー名として有効な文字は、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] クラスの **System.IO.Path** および **GetInvalidFilenameChars** フィールドによって決まります。</span><span class="sxs-lookup"><span data-stu-id="73354-131">Valid characters for folder names are determined by the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] class **System.IO.Path** and the **GetInvalidFilenameChars** field.</span></span> <span data-ttu-id="73354-132">**GetInvalidFilenameChars** フィールドでは、 **Path** クラスのメンバーに渡されるパス文字列引数に指定できない、プラットフォーム固有の文字配列が指定されます。</span><span class="sxs-lookup"><span data-stu-id="73354-132">The **GetInvalidFilenameChars** field provides a platform-specific array of characters that cannot be specified in path string arguments passed to members of the **Path** class.</span></span> <span data-ttu-id="73354-133">無効な文字のセットは、ファイル システムによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="73354-133">The set of invalid characters can vary by file system.</span></span> <span data-ttu-id="73354-134">通常、無効な文字は、引用符 (")、小なり (<) 文字、およびパイプ (|) 文字です。</span><span class="sxs-lookup"><span data-stu-id="73354-134">Typically, invalid characters are the quotation mark ("), less than (<) character, and pipe (|) character.</span></span>  
  
 <span data-ttu-id="73354-135">ただし、 [!INCLUDE[ssDE](../includes/ssde-md.md)]の名前付きインスタンスまたはリモート インスタンスに格納されているパッケージを管理するには、構成ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73354-135">However, you will have to modify the configuration file to manage packages that are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="73354-136">構成ファイルを更新しないと、 **で** オブジェクト エクスプローラー [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して名前付きインスタンスまたはリモート インスタンス上の msdb データベースに格納されているパッケージを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="73354-136">If you do not update the configuration file, you cannot use **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to view packages that are stored in the msdb database on the named instance or the remote instance.</span></span> <span data-ttu-id="73354-137">**オブジェクト エクスプローラー** を使用してこのようなパッケージを表示しようとすると、次のエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="73354-137">If you try to use **Object Explorer** to view these packages, you receive the following error message:</span></span>  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 <span data-ttu-id="73354-138">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの構成ファイルを変更するには、テキスト エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="73354-138">To modify the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, you use a text editor.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73354-139">サービス構成ファイルを変更したら、更新されたサービス構成を使用するためにサービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73354-139">After you modify the service configuration file, you must restart the service to use the updated service configuration.</span></span>  
  
### <a name="modified-configuration-file-example"></a><span data-ttu-id="73354-140">変更された構成ファイルの例</span><span class="sxs-lookup"><span data-stu-id="73354-140">Modified Configuration File Example</span></span>  
 <span data-ttu-id="73354-141">変更された [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]の構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="73354-141">The following example shows a modified configuration file for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="73354-142">このファイルは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] という名前のサーバー上で、 `InstanceName` と呼ばれる `ServerName`の名前付きインスタンス用のファイルです。</span><span class="sxs-lookup"><span data-stu-id="73354-142">This file is for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] called `InstanceName` on a server named `ServerName`.</span></span>  
  
 <span data-ttu-id="73354-143">**SQL Server の名前付きインスタンス用構成ファイルの変更例**</span><span class="sxs-lookup"><span data-stu-id="73354-143">**Example of a Modified Configuration File for a Named Instance of SQL Server**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file-location"></a><span data-ttu-id="73354-144">構成ファイルの場所の変更</span><span class="sxs-lookup"><span data-stu-id="73354-144">Modification of the Configuration File Location</span></span>  
<span data-ttu-id="73354-145">レジストリキー **HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\ServiceConfigFile**は、サービスが使用する構成ファイルの場所と名前を指定し [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="73354-145">The Registry key **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\ServiceConfigFile** specifies the location and name for the configuration file that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses.</span></span> <span data-ttu-id="73354-146">レジストリキーの既定値は C:\Program、 **SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**です。</span><span class="sxs-lookup"><span data-stu-id="73354-146">The default value of the Registry key is **C:\Program Files\Microsoft SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**.</span></span> <span data-ttu-id="73354-147">レジストリ キーの値を更新すると、構成ファイルに別の名前と場所を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="73354-147">You can update the value of the Registry key to use a different name and location for the configuration file.</span></span> <span data-ttu-id="73354-148">パスのバージョン番号 (SQL Server の 120) は、 [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] SQL Server のバージョンによって異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="73354-148">Note that the version number in the path (120 for SQL Server  [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]) will vary depending on the SQL Server version.</span></span> 
  
  
> [!CAUTION]  
>  <span data-ttu-id="73354-149">レジストリの編集を誤ると、深刻な問題が発生し、オペレーティング システムの再インストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="73354-149">Incorrectly editing the Registry can cause serious problems that may require you to reinstall your operating system.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="73354-150">レジストリの誤った編集により発生した問題に関しては、一切責任を負わないものとします。</span><span class="sxs-lookup"><span data-stu-id="73354-150">cannot guarantee that problems resulting from editing the Registry incorrectly can be resolved.</span></span> <span data-ttu-id="73354-151">レジストリを編集する前に、重要なデータをすべてバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="73354-151">Before editing the Registry, back up any valuable data.</span></span> <span data-ttu-id="73354-152">レジストリのバックアップ、復元、および編集の方法については、 [!INCLUDE[msCoName](../includes/msconame-md.md)] サポート技術情報の記事「 [Microsoft Windows レジストリの説明](https://support.microsoft.com/kb/256986)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73354-152">For information about how to back up, restore, and edit the Registry, see the [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base article, [Description of the Microsoft Windows registry](https://support.microsoft.com/kb/256986).</span></span>  
  
 <span data-ttu-id="73354-153">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、サービスの開始時に構成ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="73354-153">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service loads the configuration file when the service is started.</span></span> <span data-ttu-id="73354-154">レジストリ エントリを変更した場合、サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73354-154">Any changes to the Registry entry require that the service be restarted.</span></span>  
  
  

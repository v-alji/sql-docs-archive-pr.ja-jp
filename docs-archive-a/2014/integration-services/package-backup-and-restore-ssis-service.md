---
title: パッケージのバックアップと復元 (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4cd6f3856b69485c01e4b38d89e2f7e2ec56f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644548"
---
# <a name="package-backup-and-restore-ssis-service"></a><span data-ttu-id="f4715-102">パッケージのバックアップと復元 (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="f4715-102">Package Backup and Restore (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="f4715-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4715-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="f4715-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f4715-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="f4715-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="f4715-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f4715-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージは、ファイル システムや [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] システム データベースの msdb に保存できます。</span><span class="sxs-lookup"><span data-stu-id="f4715-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages can be saved to the file system or msdb, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] system database.</span></span> <span data-ttu-id="f4715-107">msdb に保存されたパッケージは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップおよび復元機能を使用してバックアップおよび復元できます。</span><span class="sxs-lookup"><span data-stu-id="f4715-107">Packages saved to msdb can be backed up and restored using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore features.</span></span>  
  
 <span data-ttu-id="f4715-108">msdb データベースのバックアップおよび復元の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4715-108">For more information about backing up and restoring the msdb database, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f4715-109">SQL Server データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="f4715-109">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [<span data-ttu-id="f4715-110">システム データベースのバックアップと復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4715-110">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="f4715-111">には、パッケージの管理に使用する **dtutil** コマンド プロンプト ユーティリティ (dtutil.exec) が付属しています。</span><span class="sxs-lookup"><span data-stu-id="f4715-111">includes the **dtutil** command-prompt utility (dtutil.exec), which you can use to manage packages.</span></span> <span data-ttu-id="f4715-112">詳細については、「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4715-112">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f4715-113">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="f4715-113">Configuration Files</span></span>  
 <span data-ttu-id="f4715-114">パッケージに含まれるすべての構成ファイルはファイル システムに格納されています。</span><span class="sxs-lookup"><span data-stu-id="f4715-114">Any configuration files that the packages include are stored in the file system.</span></span> <span data-ttu-id="f4715-115">msdb データベースをバックアップするとき、これらのファイルはバックアップされません。したがって、msdb に保存されたパッケージの安全を確保するための計画の一部として、構成ファイルを定期的にバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4715-115">These files are not backed up when you back up the msdb database; therefore, you should make sure that the configuration files are backed up regularly as part of your plan for securing packages saved to msdb.</span></span> <span data-ttu-id="f4715-116">msdb データベースのバックアップに構成を含めるには、ファイル ベースの構成の代わりに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成の種類の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f4715-116">To include configurations in the backup of the msdb database, you should consider using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type instead of file-based configurations.</span></span>  
  
## <a name="packages-stored-in-the-file-system"></a><span data-ttu-id="f4715-117">ファイル システムに保存されたパッケージ</span><span class="sxs-lookup"><span data-stu-id="f4715-117">Packages Stored in the File System</span></span>  
 <span data-ttu-id="f4715-118">サーバーのファイル システムのバックアップ計画には、ファイル システムに保存されるパッケージのバックアップも含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4715-118">The backup of packages that are saved to the file system should be included in the plan for backing up the file system of the server.</span></span> <span data-ttu-id="f4715-119">既定で MsDtsSrvr.ini.xml という名前を持つ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービス構成ファイルには、このサービスで監視されるサーバー上のフォルダーが定義されています。</span><span class="sxs-lookup"><span data-stu-id="f4715-119">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service configuration file, which has the default name MsDtsSrvr.ini.xml, lists the folders on the server that the service monitors.</span></span> <span data-ttu-id="f4715-120">これらのフォルダーを必ずバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="f4715-120">You should make sure these folders are backed up.</span></span> <span data-ttu-id="f4715-121">さらに、パッケージをサーバー上の他のフォルダーに格納している場合は、これらのフォルダーもバックアップに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4715-121">Additionally, packages may be stored in other folders on the server and you should make sure to include these folders in the backup.</span></span>  
  
  

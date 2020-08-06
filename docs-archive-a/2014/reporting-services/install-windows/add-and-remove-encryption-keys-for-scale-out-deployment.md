---
title: スケールアウト配置の暗号化キーを追加および削除する (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- deleting encryption keys
- removing encryption keys
- adding encryption keys
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 2da86fb3-4b4d-407f-9825-74dcc42486f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3926e57c1ad3bb884af8debf7f831092b223a3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742970"
---
# <a name="add-and-remove-encryption-keys-for-scale-out-deployment-ssrs-configuration-manager"></a><span data-ttu-id="4c8fd-102">スケールアウト配置に関する暗号化キーの追加と削除 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="4c8fd-102">Add and Remove Encryption Keys for Scale-Out Deployment (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="4c8fd-103">1 つのレポート サーバー データベースを複数のレポート サーバーで共有するように構成すると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をスケールアウト配置モデルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-103">You can run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a scale-out deployment model by configuring multiple report servers to use a shared report server database.</span></span> <span data-ttu-id="4c8fd-104">スケールアウト配置でのメンバーシップは、レポート サーバーがレポート サーバー データベースに暗号化キーを格納するかどうかに基づいています。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-104">Membership in a scale-out deployment is based on whether the report server stores an encryption key in the report server database.</span></span> <span data-ttu-id="4c8fd-105">特定のレポート サーバー インスタンスの暗号化キーを追加および削除することで、スケールアウト配置のメンバーシップを制御できます。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-105">You can control scale-out deployment membership by adding and removing encryption keys for specific report server instances.</span></span> <span data-ttu-id="4c8fd-106">配置からノードを削除する場合は、それらを任意の順序で削除できます。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-106">If you are removing nodes from the deployment, you can remove them in any order.</span></span> <span data-ttu-id="4c8fd-107">配置にノードを追加する場合は、既に配置の一部になっているレポート サーバーのすべての新しいインスタンスを結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-107">If you are adding nodes to a deployment, you must join any new instances from a report server that is already part of the deployment.</span></span>  
  
## <a name="using-the-reporting-services-configuration-tool-to-configure-scale-out-deployment"></a><span data-ttu-id="4c8fd-108">Reporting Services 構成ツールを使用したスケールアウト配置の構成</span><span class="sxs-lookup"><span data-stu-id="4c8fd-108">Using the Reporting Services Configuration Tool to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="4c8fd-109">スケールアウト配置を最も簡単に構成するには、Reporting Services 構成ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-109">The easiest way to configure a scale-out deployment is to use the Reporting Services Configuration tool.</span></span> <span data-ttu-id="4c8fd-110">詳細情報と手順については、「[ネイティブ モード レポート サーバーのスケールアウト配置の構成 &#40;SSRS 構成マネージャー&#41;](configure-a-native-mode-report-server-scale-out-deployment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-110">For more information and step-by-step instructions, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](configure-a-native-mode-report-server-scale-out-deployment.md).</span></span>  
  
## <a name="using-rskeymgmt-to-configure-scale-out-deployment"></a><span data-ttu-id="4c8fd-111">rskeymgmt を使用したスケールアウト配置の構成</span><span class="sxs-lookup"><span data-stu-id="4c8fd-111">Using Rskeymgmt to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="4c8fd-112">共有レポート サーバー データベースを使用するようにレポート サーバー インスタンスを初期化するには、 **rskeymgmt** ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-112">Use the **rskeymgmt** utility to initialize a report server instance to use a shared report server database.</span></span> <span data-ttu-id="4c8fd-113">レポート サーバーをスケールアウト配置に追加するには、レポート サーバーを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-113">Adding a report server to a scale-out deployment requires that you initialize the report server.</span></span> <span data-ttu-id="4c8fd-114">初期化には管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-114">Initialization requires administrator permissions.</span></span> <span data-ttu-id="4c8fd-115">配置に結合するレポート サーバーをホストするリモート コンピューターの管理者資格情報も必要です。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-115">You must have administrator credentials for the remote computer that hosts the report server you are joining to the deployment.</span></span>  
  
#### <a name="how-to-join-a-report-server-to-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="4c8fd-116">レポート サーバーをスケールアウト配置に結合する方法 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="4c8fd-116">How to join a report server to a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="4c8fd-117">レポート サーバー スケールアウト配置のメンバーであるレポート サーバーをホストするコンピューターで、 **rskeymgmt.exe** をローカルに実行します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-117">Run **rskeymgmt.exe** locally on the computer that hosts a report server that is already a member of the report server scale-out deployment.</span></span>  
  
2.  <span data-ttu-id="4c8fd-118">`-j` 引数を使用して、レポート サーバーをレポート サーバー データベースに結合します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-118">Use the `-j` argument to join a report server to the report server database.</span></span> <span data-ttu-id="4c8fd-119">`-m` 引数と `-n` 引数を使用して、配置に追加するリモート レポート サーバー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-119">Use the `-m` and `-n` arguments to specify the remote report server instance you want to add to the deployment.</span></span> <span data-ttu-id="4c8fd-120">`-u` 引数と `-v` 引数を使用して、リモート コンピューター上の管理者アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-120">Use the `-u` and `-v` arguments to specify an administrator account on the remote computer.</span></span> <span data-ttu-id="4c8fd-121">同じコンピューター上の複数のレポート サーバー インスタンスを使用してスケールアウト配置を作成する場合、使用する構文は若干異なります。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-121">If you are creating a scale-out deployment using multiple report server instances on the same computer, the syntax to use is slightly different.</span></span> <span data-ttu-id="4c8fd-122">使用する必要がある構文の詳細については、「[rskeymgmt ユーティリティ &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-122">For more information about the syntax you should use, see [rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md).</span></span>  
  
     <span data-ttu-id="4c8fd-123">次の例は、リモート レポート サーバーをスケールアウト配置に結合する場合に指定する必要がある引数を示しています (リモート コンピューターでの管理者権限がある場合は、資格情報を省略できます)。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-123">The following example illustrates the arguments you must specify if you are joining a remote report server to a scale-out deployment (you can omit credentials if you have administrator permissions on the remote computer):</span></span>  
  
    ```  
    rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
    ```  
  
#### <a name="how-to-remove-a-report-server-from-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="4c8fd-124">レポート サーバーをスケールアウト配置から削除する方法 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="4c8fd-124">How to remove a report server from a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="4c8fd-125">削除するレポート サーバーの rsreportserver.config ファイルを開き、インストール ID を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-125">Open the rsreportserver.config file of the report server you want to remove and find the installation ID.</span></span> <span data-ttu-id="4c8fd-126">既定では、このファイルは Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer にあります。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-126">By default, this file is located at Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer).</span></span>  
  
     <span data-ttu-id="4c8fd-127">単一のインスタンスをインストールした場合、rsreportserver.config ファイルはコンピューター上に 1 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-127">If you installed a single instance, there will only be one rsreportserver.config file on the computer.</span></span> <span data-ttu-id="4c8fd-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の複数のインスタンスがインストールされている場合は、Reporting Services 構成ツールの [サーバーの状態] ページを使用し、削除するレポート サーバーのインスタンス識別子 (たとえば、MSSQL.2) を検索します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-128">If multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are installed, use the Server Status page in the Reporting Services Configuration tool to find the instance identifier (for example, MSSQL.2) for the report server that you want to remove.</span></span> <span data-ttu-id="4c8fd-129">レポート サーバー インスタンスのプログラム ファイルを格納するフォルダーの名前は、インスタンス識別子に基づきます (たとえば、Program Files\Microsoft SQL Server\MSSQL.2)。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-129">The name of the folder that stores the program files for the report server instance will be based on the instance identifier (for example, Program Files\Microsoft SQL Server\MSSQL.2).</span></span>  
  
2.  <span data-ttu-id="4c8fd-130">**rskeymgmt.exe**を実行します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-130">Run **rskeymgmt.exe**.</span></span> <span data-ttu-id="4c8fd-131">これは、レポート サーバー スケールアウト配置に含まれているどのレポート サーバーでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-131">You can run it on any report server that is part of the report server scale-out deployment.</span></span>  
  
3.  <span data-ttu-id="4c8fd-132">`-r` 引数を使用して、スケールアウト配置からレポート サーバー インスタンスを解放します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-132">Use the `-r` argument to release the report server instance from the scale-out deployment.</span></span> <span data-ttu-id="4c8fd-133">指定する必要がある引数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-133">The following example illustrates the arguments you must specify:</span></span>  
  
    ```  
    rskeymgmt -r <installation ID>  
    ```  
  
 <span data-ttu-id="4c8fd-134">これらの手順によってスケール アウト配置からレポート サーバーが削除されますが、レポート サーバーの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスはアンインストールされません。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-134">These steps remove the report server from a scale-out deployment, but they do not uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance on the report server.</span></span> <span data-ttu-id="4c8fd-135">スケール アウト配置からレポート サーバーを削除した後、サーバー上で [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] が不要になった場合は、そのサーバーから [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアンインストールできます。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-135">After you remove the report server from the scale-out deployment, you can uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] from the server if you no longer need [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on that server.</span></span> <span data-ttu-id="4c8fd-136">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[SQL Server の既存のインスタンスのアンインストール &#40;セットアップ&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8fd-136">For information, see [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8fd-137">参照</span><span class="sxs-lookup"><span data-stu-id="4c8fd-137">See Also</span></span>  
 <span data-ttu-id="4c8fd-138">[SSRS Configuration Manager &#40;暗号化キーの構成と管理&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="4c8fd-138">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="4c8fd-139">レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="4c8fd-139">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
  
  

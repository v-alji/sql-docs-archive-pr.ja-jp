---
title: Oracle パブリッシャーのバックアップと復元 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6b994c34e4f4bebc010fe6d71bbd43f6e557cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631812"
---
# <a name="backup-and-restore-for-oracle-publishers"></a><span data-ttu-id="761e1-102">Oracle パブリッシャーのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="761e1-102">Backup and Restore for Oracle Publishers</span></span>
  <span data-ttu-id="761e1-103">バックアップと復元を実行する場合は、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="761e1-103">Follow these guidelines when backing up and restoring:</span></span>  
  
-   <span data-ttu-id="761e1-104">パブリッシャーのバックアップ中は、ログ リーダー エージェントを実行したり、パブリッシュされたテーブルでその他のデータベースの処理を実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="761e1-104">Ensure the Log Reader Agent does not run and that other database activity on the published tables does not occur while the Publisher is being backed up.</span></span>  
  
-   <span data-ttu-id="761e1-105">パブリッシャーとディストリビューターは同時にバックアップします。</span><span class="sxs-lookup"><span data-stu-id="761e1-105">Backup up the Publisher and Distributor at the same time.</span></span>  
  
-   <span data-ttu-id="761e1-106">パブリッシャーまたはディストリビューターを復元する必要がある場合は、すべてのサブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="761e1-106">If the Publisher or Distributor must be restored, reinitialize all subscriptions.</span></span>  
  
-   <span data-ttu-id="761e1-107">バックアップからサブスクライバーを復元するには (サブスクリプションの再初期化は不要)、前回のサブスクリプション データベースのバックアップ完了後にディストリビューション データベースに配信されたトランザクションも使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="761e1-107">To restore a Subscriber from a backup (without having to reinitialize subscriptions), the transactions delivered to the distribution database after the last subscription database backup was completed must still be available.</span></span> <span data-ttu-id="761e1-108">トランザクションが使用できる時間の長さは、ディストリビューションの保有期間の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="761e1-108">The length of time transactions are available depends on distribution retention settings.</span></span> <span data-ttu-id="761e1-109">これらの設定については、「[サブスクリプションの有効期限と非アクティブ化](../subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="761e1-109">For information on these settings, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="761e1-110">データベースを復元した結果、パブリッシャーまたはディストリビューターが同期しなくなった場合は、レプリケーション エージェントによってエラー メッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="761e1-110">If the Publisher or Distributor becomes out of sync as the result of a database restore, the replication agents log error messages.</span></span> <span data-ttu-id="761e1-111">この時点で、関連するパブリケーションとサブスクリプションをすべて削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="761e1-111">At this point, you must drop and recreate all relevant publications and subscriptions:</span></span>  
  
    1.  <span data-ttu-id="761e1-112">パブリケーションおよびサブスクリプションの定義のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="761e1-112">Script the definition of the publications and subscriptions.</span></span> <span data-ttu-id="761e1-113">詳しくは、「 [Scripting Replication](../scripting-replication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="761e1-113">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
         <span data-ttu-id="761e1-114">パブリッシャーとディストリビューターの状態のバージョン間でパブリケーションの定義が変更された場合は、スクリプトを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="761e1-114">If the definition of the publications has changed between the versions of the Publisher and Distributor states, you will need to modify the scripts.</span></span>  
  
    2.  <span data-ttu-id="761e1-115">パブリケーションとサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="761e1-115">Drop the publications and subscriptions.</span></span>  
  
    3.  <span data-ttu-id="761e1-116">手順 1. で作成したスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="761e1-116">Run the scripts created in step 1.</span></span>  
  
     <span data-ttu-id="761e1-117">パブリッシャーを削除および再構成する必要がある場合は、 **MSSQLSERVERDISTRIBUTOR** パブリック シノニムと、 **CASCADE** オプションで構成した Oracle レプリケーション ユーザーを削除して、Oracle パブリッシャーからすべてのレプリケーション オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="761e1-117">If the Publisher must be dropped and reconfigured, drop the **MSSQLSERVERDISTRIBUTOR** public synonym and the configured Oracle replication user with the **CASCADE** option to remove all replication objects from the Oracle Publisher.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761e1-118">参照</span><span class="sxs-lookup"><span data-stu-id="761e1-118">See Also</span></span>  
 <span data-ttu-id="761e1-119">[レプリケートされたデータベースのバックアップと復元](../administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="761e1-119">[Back Up and Restore Replicated Databases](../administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="761e1-120">[Configure an Oracle Publisher (Oracle パブリッシャーの構成)](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="761e1-120">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="761e1-121">Oracle パブリッシングの概要</span><span class="sxs-lookup"><span data-stu-id="761e1-121">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  

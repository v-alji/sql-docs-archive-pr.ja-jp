---
title: トランザクションパブリケーションのバックアップによる初期化を有効にする (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e22614c8c4f5250db3966e747b686091512774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632363"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="8b28d-102">トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8b28d-102">Enable Initialization with a Backup for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8b28d-103">バックアップからトランザクション パブリケーションに対してサブスクリプションを初期化するには、パブリケーションを有効にしてバックアップからの初期化を許可し、サブスクリプションの作成時にバックアップ情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b28d-103">To initialize a subscription to a transactional publication from a backup, enable the publication to allow initialization from a backup, and then specify backup information when creating the subscription:</span></span>  
  
-   <span data-ttu-id="8b28d-104">パブリケーションは、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b28d-104">Enable the publication on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="8b28d-105">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b28d-105">For more information about accessing this dialog box, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="8b28d-106">バックアップ情報は、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="8b28d-106">Specify backup information with the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="8b28d-107">**sp_addsubscription** で必要とされるパラメーターに関する詳細については、「[トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)](initialize-a-transactional-subscription-from-a-backup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b28d-107">For more information about the parameters required by **sp_addsubscription**, see [Initialize a Transactional Subscription from a Backup &#40;Replication Transact-SQL Programming&#41;](initialize-a-transactional-subscription-from-a-backup.md).</span></span>  
  
### <a name="to-enable-initialization-with-a-backup"></a><span data-ttu-id="8b28d-108">バックアップを使用した初期化を有効にするには</span><span class="sxs-lookup"><span data-stu-id="8b28d-108">To enable initialization with a backup</span></span>  
  
1.  <span data-ttu-id="8b28d-109">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、 **[バックアップ ファイルからの初期化を許可]** オプションに対して **[True]** の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b28d-109">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Allow initialization from backup files** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b28d-110">参照</span><span class="sxs-lookup"><span data-stu-id="8b28d-110">See Also</span></span>  
 [<span data-ttu-id="8b28d-111">スナップショットを使用しないトランザクション サブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="8b28d-111">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  

---
title: マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a2306db72fd3f0098e18ff058796a5498eafcac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736259"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a><span data-ttu-id="ceb90-102">マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="ceb90-102">Clean Up Merge Metadata (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="ceb90-103">マージ レプリケーションのメタデータは、パブリケーションの保有期間設定に基づき、マージ エージェントによって定期的にクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="ceb90-103">Merge replication metadata is cleaned up periodically by the Merge Agent based on the retention setting for the publication.</span></span> <span data-ttu-id="ceb90-104">クリーンアップは、パブリッシャーおよびサブスクライバーの [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)、 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) の各システム テーブルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ceb90-104">This occurs at the Publisher and Subscriber in the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) system tables.</span></span> <span data-ttu-id="ceb90-105">これらのテーブルに格納されたデータは、レプリケーションのストアド プロシージャを使って、プログラムからクリーンアップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ceb90-105">You can also programmatically clean up the data in these tables using replication stored procedures.</span></span>  
  
### <a name="to-manually-clean-up-merge-metadata"></a><span data-ttu-id="ceb90-106">マージ メタデータを手動でクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="ceb90-106">To manually clean up merge metadata</span></span>  
  
1.  <span data-ttu-id="ceb90-107">パブリッシャーのパブリケーション データベースで [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="ceb90-107">At the Publisher on the publication database, execute [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).</span></span>  
  
2.  <span data-ttu-id="ceb90-108">Optional手順 1. で削除した行の数は、 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、および[MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)の各システムテーブルから、それぞれ、、およびの各出力パラメーターで返され **@num_genhistory_rows** **@num_contents_rows** **@num_tombstone_rows** ます。</span><span class="sxs-lookup"><span data-stu-id="ceb90-108">(Optional) Note the number of rows removed in step 1 from the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), and [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) system tables, returned respectively in the **@num_genhistory_rows**, **@num_contents_rows**, and **@num_tombstone_rows** output parameters.</span></span>  
  
3.  <span data-ttu-id="ceb90-109">サブスクライバーで手順 1. と手順 2. を繰り返し、サブスクリプション データベースのメタデータをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="ceb90-109">Repeat steps 1 and 2 at the Subscriber to clean up metadata on the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb90-110">参照</span><span class="sxs-lookup"><span data-stu-id="ceb90-110">See Also</span></span>  
 [<span data-ttu-id="ceb90-111">サブスクリプションの有効期限と非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="ceb90-111">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  

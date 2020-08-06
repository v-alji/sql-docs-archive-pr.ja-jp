---
title: データファイルとデルタファイルのペアのマージの監視とトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5dc57d08f3db1792a9359b3aa79aaceecd03a025
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644631"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a><span data-ttu-id="875a8-102">データ ファイルとデルタ ファイルのペアのマージに関する監視とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="875a8-102">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>
  <span data-ttu-id="875a8-103">インメモリ OLTP は、マージ ポリシーを使用して、データ ファイルとデルタ ファイルの隣接するペアを自動的にマージします。</span><span class="sxs-lookup"><span data-stu-id="875a8-103">In-Memory OLTP uses a merge policy to merge adjacent data and delta file pairs automatically.</span></span> <span data-ttu-id="875a8-104">マージ操作を無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="875a8-104">You cannot disable merge activity.</span></span>  
  
 <span data-ttu-id="875a8-105">データ ファイルとデルタ ファイルのペアは、次のように監視できます。</span><span class="sxs-lookup"><span data-stu-id="875a8-105">You can monitor data and delta file pairs, as follows:</span></span>  
  
-   <span data-ttu-id="875a8-106">ストレージの全体的なサイズとインメモリ ストレージのサイズを比較します。</span><span class="sxs-lookup"><span data-stu-id="875a8-106">Compare the size of in-memory storage to overall size of storage.</span></span> <span data-ttu-id="875a8-107">ストレージが過度に大きい場合、マージが発生していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="875a8-107">If the storage is dis-proportionately large, then it is likely that merge is not getting triggered.</span></span> <span data-ttu-id="875a8-108">詳細については、</span><span class="sxs-lookup"><span data-stu-id="875a8-108">For information</span></span>  
  
-   <span data-ttu-id="875a8-109">[Transact-sql&#41;&#40;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql)使用し dm_db_xtp_checkpoint_files て、データファイルとデルタファイル内の使用されている領域を確認し、必要に応じてマージがトリガーされないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="875a8-109">Look at the used space in data and delta files using [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) to see if merge is not getting triggered when it should.</span></span>  
  
## <a name="performing-a-manual-merge"></a><span data-ttu-id="875a8-110">手動マージの実行</span><span class="sxs-lookup"><span data-stu-id="875a8-110">Performing a Manual Merge</span></span>  
 <span data-ttu-id="875a8-111">[Sp_xtp_merge_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)を使用して、手動マージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="875a8-111">You can use [sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) to perform a manual merge.</span></span>  
  
 <span data-ttu-id="875a8-112">次のクエリを使用して、データ ファイルとデルタ ファイルに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="875a8-112">Use the following query to retrieve information about the data and delta files,</span></span>  
  
```sql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 <span data-ttu-id="875a8-113">マージされていない3つのデータファイルが見つかったとします。</span><span class="sxs-lookup"><span data-stu-id="875a8-113">Assume that you found three data files that have not been merged.</span></span> <span data-ttu-id="875a8-114">最初のデータ ファイルの `lower_bound_tsn` 値と最後のデータ ファイルの `upper_bound_tsn` を使用して、次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="875a8-114">Using the `lower_bound_tsn` value of the first data file and the `upper_bound_tsn` of the last data file, you can issue the following command:</span></span>  
  
```sql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 <span data-ttu-id="875a8-115">15,836 の行が含まれるデータ ファイルと 5,279 の削除行が含まれるデルタ ファイルのペアが 3 組あったとします。</span><span class="sxs-lookup"><span data-stu-id="875a8-115">Assume that the three data and delta file pairs each had 15,836 rows and 5,279 deleted rows.</span></span> <span data-ttu-id="875a8-116">マージ後、新しいデータ ファイルの行数は 31,872、削除行は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="875a8-116">After the merge, the new data file has 31,872 rows and 0 deleted rows.</span></span> <span data-ttu-id="875a8-117">新しいデータ ファイルのサイズが、最初に割り当てられたサイズである 128 MB を大きく上回る場合があります。</span><span class="sxs-lookup"><span data-stu-id="875a8-117">The size of the new data file can be much larger than the initially allocated size of 128MB.</span></span> <span data-ttu-id="875a8-118">これは、手動マージによってマージ ポリシーがオーバーライドされ、要求されたファイルのマージが強制されるためです。</span><span class="sxs-lookup"><span data-stu-id="875a8-118">This is because manual merge overrides the merge policy and forces the merge of the requested files.</span></span>  
  
 <span data-ttu-id="875a8-119">[メモリ最適化テーブルを持つデータベースのチェックポイントファイルのブログ状態の移行で](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/)は、データファイルとデルタファイルのペアの開始からガベージコレクションへの状態遷移について説明します。</span><span class="sxs-lookup"><span data-stu-id="875a8-119">The blog [State Transition of Checkpoint Files in Databases with Memory-Optimized Tables](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/) describes state transition of data and delta file pairs from inception to garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875a8-120">参照</span><span class="sxs-lookup"><span data-stu-id="875a8-120">See Also</span></span>  
 [<span data-ttu-id="875a8-121">メモリ最適化オブジェクト用ストレージの作成と管理</span><span class="sxs-lookup"><span data-stu-id="875a8-121">Creating and Managing Storage for Memory-Optimized Objects</span></span>](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  

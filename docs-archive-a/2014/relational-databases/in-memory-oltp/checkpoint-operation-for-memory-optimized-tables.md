---
title: メモリ最適化テーブルのチェックポイント操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 07560ea0bf147198fb759f6769ae1c6d5c68a71e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741014"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a><span data-ttu-id="dcd18-102">メモリ最適化テーブルのチェックポイント操作</span><span class="sxs-lookup"><span data-stu-id="dcd18-102">Checkpoint Operation for Memory-Optimized Tables</span></span>
  <span data-ttu-id="dcd18-103">データ ファイルとデルタ ファイルのメモリ最適化データに対してチェックポイントを定期的に作成して、トランザクション ログのアクティブな部分を進める必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcd18-103">A checkpoint needs to occur periodically for memory-optimized data in data and delta files to advance the active part of transaction log.</span></span> <span data-ttu-id="dcd18-104">チェックポイントにより、メモリ最適化テーブルでは最後に正常終了したチェックポイントまで復元および復旧することができ、トランザクション ログのアクティブな部分が適用されてメモリ最適化テーブルが更新され、復旧が完了します。</span><span class="sxs-lookup"><span data-stu-id="dcd18-104">The checkpoint allows memory-optimized tables to restore or recover to the last successful checkpoint and then the active portion of transaction log is applied to update the memory-optimized tables to complete the recovery.</span></span> <span data-ttu-id="dcd18-105">ディスク ベース テーブルとメモリ最適化テーブルのチェックポイント操作は個別の操作です。</span><span class="sxs-lookup"><span data-stu-id="dcd18-105">The checkpoint operation for disk-based tables and memory-optimized tables are distinct operations.</span></span> <span data-ttu-id="dcd18-106">ディスク ベース テーブルとメモリ最適化テーブルに関する各シナリオとチェックポイント動作について、次に説明します。</span><span class="sxs-lookup"><span data-stu-id="dcd18-106">The following describes different scenarios and the checkpoint behavior for disk-based and memory-optimized tables:</span></span>  
  
## <a name="manual-checkpoint"></a><span data-ttu-id="dcd18-107">手動チェックポイント</span><span class="sxs-lookup"><span data-stu-id="dcd18-107">Manual Checkpoint</span></span>  
 <span data-ttu-id="dcd18-108">手動でチェックポイントを作成すると、ディスク ベース テーブルおよびメモリ最適化テーブルの両方のチェックポイントが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="dcd18-108">When you issue a manual checkpoint, it closes the checkpoint for both disk-based and memory-optimized tables.</span></span> <span data-ttu-id="dcd18-109">アクティブなデータ ファイルは、一部分しか入力されていない場合でも閉じられます。</span><span class="sxs-lookup"><span data-stu-id="dcd18-109">The active data file is closed even though it may be partially filled.</span></span>  
  
## <a name="automatic-checkpoint"></a><span data-ttu-id="dcd18-110">自動チェックポイント</span><span class="sxs-lookup"><span data-stu-id="dcd18-110">Automatic Checkpoint</span></span>  
 <span data-ttu-id="dcd18-111">自動チェックポイントは、ディスク ベース テーブルとメモリ最適化テーブルではデータの保存方法が異なるため、実装方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="dcd18-111">Automatic checkpoint is implemented differently for disk-based and memory-optimized tables because of the different ways the data is persisted.</span></span>  
  
 <span data-ttu-id="dcd18-112">ディスクベースのテーブルの場合、recovery interval 構成オプションに基づいて自動チェックポイントが取得されます (詳細については、「[データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="dcd18-112">For disk-based tables, an automatic checkpoint is taken based on the recovery interval configuration option (for more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)).</span></span>  
  
 <span data-ttu-id="dcd18-113">メモリ最適化テーブルでは、最後のチェックポイント以降にトランザクションログファイルが 512 MB より大きくなると、自動チェックポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dcd18-113">For memory-optimized tables, an automatic checkpoint is taken when transaction log file becomes bigger than 512 MB since the last checkpoint.</span></span> <span data-ttu-id="dcd18-114">512 MB には、ディスクベーステーブルとメモリ最適化テーブルの両方のトランザクションログレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcd18-114">512 MB includes transaction log records for both disk-based and memory-optimized tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd18-115">参照</span><span class="sxs-lookup"><span data-stu-id="dcd18-115">See Also</span></span>  
 [<span data-ttu-id="dcd18-116">メモリ最適化オブジェクト用ストレージの作成と管理</span><span class="sxs-lookup"><span data-stu-id="dcd18-116">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  

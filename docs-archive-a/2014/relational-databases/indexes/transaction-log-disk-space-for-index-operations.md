---
title: インデックス操作用のトランザクション ログのディスク領域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index disk space [SQL Server]
- space [SQL Server], indexes
- transaction logs [SQL Server], disk space
- disk space [SQL Server], transaction logs
- space [SQL Server], transaction logs
ms.assetid: 4f8a4922-4507-4072-be67-c690528d5c3b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c34c9ff7a9494496d6c60d5920184c0ce86131d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739913"
---
# <a name="transaction-log-disk-space-for-index-operations"></a><span data-ttu-id="6b58c-102">インデックス操作用のトランザクション ログのディスク領域</span><span class="sxs-lookup"><span data-stu-id="6b58c-102">Transaction Log Disk Space for Index Operations</span></span>
  <span data-ttu-id="6b58c-103">大規模なインデックス操作では、大量のデータが読み込まれるためにトランザクション ログがすぐにいっぱいになることがあります。</span><span class="sxs-lookup"><span data-stu-id="6b58c-103">Large-scale index operations can generate large data loads that can cause the transaction log to fill quickly.</span></span> <span data-ttu-id="6b58c-104">インデックス操作を確実にロールバックできるようにするには、インデックス操作が完了するまでトランザクション ログを切り捨てることができません。ただし、インデックス操作中にログをバックアップすることはできます。</span><span class="sxs-lookup"><span data-stu-id="6b58c-104">To make sure that the index operation can be rolled back, the transaction log cannot be truncated until the index operation has completed; however, the log can be backed up during the index operation.</span></span> <span data-ttu-id="6b58c-105">このため、トランザクション ログには、インデックス操作中のインデックス操作によるトランザクションと同時実行ユーザーによるトランザクションの両方を格納できるだけの十分な空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="6b58c-105">Therefore, the transaction log must have sufficient room to store both the index operation transactions and any concurrent user transactions for the duration of the index operation.</span></span> <span data-ttu-id="6b58c-106">これは、インデックス操作がオフラインでもオンラインでも同じです。</span><span class="sxs-lookup"><span data-stu-id="6b58c-106">This is true for both offline and online index operations.</span></span> <span data-ttu-id="6b58c-107">オフライン インデックス操作中は基になるテーブルにアクセスできないので、ユーザー トランザクションはそれほど多くなく、ログの増大もそれほど速くない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6b58c-107">Because the underlying tables cannot be accessed during an offline index operation, there may be few user transactions and the log may not grow as quickly.</span></span> <span data-ttu-id="6b58c-108">オンライン インデックス操作では同時実行ユーザーによる操作を防ぐことができないので、大規模なオンライン インデックス操作で同時実行ユーザーによる膨大なトランザクションが発生すると、ログの切り捨てオプションが使用されずに、トランザクション ログが増大し続けることがあります。</span><span class="sxs-lookup"><span data-stu-id="6b58c-108">Online index operations do not prevent concurrent user activity, therefore, large-scale online index operations combined with significant concurrent user transactions can cause continuous growth of the transaction log without an option to truncate the log.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="6b58c-109">Recommendations</span><span class="sxs-lookup"><span data-stu-id="6b58c-109">Recommendations</span></span>  
 <span data-ttu-id="6b58c-110">大規模なインデックス操作を実行する場合は、次の推奨事項を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="6b58c-110">When you run large-scale index operations, consider the following recommendations:</span></span>  
  
1.  <span data-ttu-id="6b58c-111">大規模なインデックス操作をオンラインで実行する前に、トランザクション ログを必ずバックアップし切り捨てを行います。また、予定しているインデックス トランザクションとユーザー トランザクションを格納できるだけの十分な領域をログのために用意しておきます。</span><span class="sxs-lookup"><span data-stu-id="6b58c-111">Make sure the transaction log has been backed up and truncated before running large-scale index operations online, and that the log has sufficient space to store the projected index and user transactions.</span></span>  
  
2.  <span data-ttu-id="6b58c-112">インデックス操作の場合は、SORT_IN_TEMPDB オプションを ON に設定することを検討します。</span><span class="sxs-lookup"><span data-stu-id="6b58c-112">Consider setting the SORT_IN_TEMPDB option to ON for the index operation.</span></span> <span data-ttu-id="6b58c-113">この設定により、インデックス トランザクションが同時実行のユーザー トランザクションから分離されます。</span><span class="sxs-lookup"><span data-stu-id="6b58c-113">This separates the index transactions from the concurrent user transactions.</span></span> <span data-ttu-id="6b58c-114">インデックス トランザクションは、 **tempdb** データベースのトランザクション ログに格納され、同時実行ユーザー トランザクションはユーザー データベースのトランザクション ログに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6b58c-114">The index transactions will be stored in the **tempdb** transaction log, and the concurrent user transactions will be stored in the transaction log of the user database.</span></span> <span data-ttu-id="6b58c-115">これにより、ユーザー データベースのトランザクション ログをインデックス操作中に必要に応じて切り捨てられるようになります。</span><span class="sxs-lookup"><span data-stu-id="6b58c-115">This allows for the transaction log of the user database to be truncated during the index operation if it is required.</span></span> <span data-ttu-id="6b58c-116">さらに、 **tempdb** データベースのログとユーザー データベース ログを別のディスク上に格納すれば、2 つのログで同じディスク領域を奪い合うことはありません。</span><span class="sxs-lookup"><span data-stu-id="6b58c-116">Additionally, if the **tempdb** log is not on the same disk as the user database log, the two logs are not competing for the same disk space.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b58c-117">**tempdb** データベースとトランザクション ログに、インデックス操作を処理できるだけの十分なディスク領域があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6b58c-117">Verify that the **tempdb** database and transaction log have sufficient disk space to handle the index operation.</span></span> <span data-ttu-id="6b58c-118">インデックス操作が完了するまで、 **tempdb** データベースのトランザクション ログを切り捨てることはできません。</span><span class="sxs-lookup"><span data-stu-id="6b58c-118">The **tempdb** transaction log cannot be truncated until the index operation is completed.</span></span>  
  
3.  <span data-ttu-id="6b58c-119">インデックス操作の最小ログ記録を行うことができるデータベース復旧モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b58c-119">Use a database recovery model that allows for minimal logging of the index operation.</span></span> <span data-ttu-id="6b58c-120">これにより、ログのサイズを削減し、ログでログ領域がいっぱいになるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="6b58c-120">This may reduce the size of the log and prevent the log from filling the log space.</span></span>  
  
4.  <span data-ttu-id="6b58c-121">明示的なトランザクションではオンライン インデックス操作を実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="6b58c-121">Do not run the online index operation in an explicit transaction.</span></span> <span data-ttu-id="6b58c-122">ログの切り捨ては、明示的なトランザクションが終了するまで行われません。</span><span class="sxs-lookup"><span data-stu-id="6b58c-122">The log will not be truncated until the explicit transaction ends.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="6b58c-123">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6b58c-123">Related Content</span></span>  
 [<span data-ttu-id="6b58c-124">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="6b58c-124">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="6b58c-125">インデックスのディスク領域の例</span><span class="sxs-lookup"><span data-stu-id="6b58c-125">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
  

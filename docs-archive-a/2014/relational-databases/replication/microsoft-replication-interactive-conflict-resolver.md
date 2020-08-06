---
title: Microsoft レプリケーション インタラクティブ競合回避モジュール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8cbd2231ab1ab357321f9887bced986e182e608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741845"
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a><span data-ttu-id="570c9-102">Microsoft レプリケーション インタラクティブ競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="570c9-102">Microsoft Replication Interactive Conflict Resolver</span></span>
  <span data-ttu-id="570c9-103">インタラクティブ競合回避モジュールは、Windows 同期マネージャーを使用して同期が行われるマージ サブスクリプションに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="570c9-103">The Interactive Conflict Resolver can be used for merge subscriptions that are synchronized using Windows Synchronization Manager.</span></span> <span data-ttu-id="570c9-104">これにより、データ競合に対する結果の表示、比較、編集、および選択ができます。</span><span class="sxs-lookup"><span data-stu-id="570c9-104">It allows you to view, compare, edit, and select the outcome for data conflicts.</span></span> <span data-ttu-id="570c9-105">レプリケーションには、コミットされた後で競合結果の表示および修正を行うことができる競合表示モジュールも含まれます。</span><span class="sxs-lookup"><span data-stu-id="570c9-105">Replication also includes the Conflict Viewer, which allows you to view and modify conflict outcomes after they have been committed.</span></span> <span data-ttu-id="570c9-106">インタラクティブ競合回避モジュールを使用すると、同期中に結果を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="570c9-106">The Interactive Conflict Resolver allows you to select the outcome during synchronization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="570c9-107">論理レコードに関連する競合は、インタラクティブ競合回避モジュールには表示されません。</span><span class="sxs-lookup"><span data-stu-id="570c9-107">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="570c9-108">これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="570c9-108">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="570c9-109">詳細については、「[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](view-conflict-information-for-merge-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="570c9-109">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="570c9-110">オプション</span><span class="sxs-lookup"><span data-stu-id="570c9-110">Options</span></span>  
 <span data-ttu-id="570c9-111">**列名**</span><span class="sxs-lookup"><span data-stu-id="570c9-111">**Column name**</span></span>  
 <span data-ttu-id="570c9-112">テーブルのすべての列の名前です。</span><span class="sxs-lookup"><span data-stu-id="570c9-112">The name of all columns in the table.</span></span> <span data-ttu-id="570c9-113">1 つまたは複数の列が競合するデータを持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="570c9-113">One or more columns might have conflicting data.</span></span> <span data-ttu-id="570c9-114">どの列が競合するかにかかわらず、競合で優先された行全体が、優先されなかった行全体を上書きします。</span><span class="sxs-lookup"><span data-stu-id="570c9-114">Regardless of which columns conflict, the entire winning row will overwrite the entire losing row.</span></span>  
  
 <span data-ttu-id="570c9-115">**[提案された解決策]**</span><span class="sxs-lookup"><span data-stu-id="570c9-115">**Suggested Resolution**</span></span>  
 <span data-ttu-id="570c9-116">アーティクルの競合回避モジュールによって提案された解決策です。</span><span class="sxs-lookup"><span data-stu-id="570c9-116">The suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="570c9-117">**発行元**</span><span class="sxs-lookup"><span data-stu-id="570c9-117">**Publisher**</span></span>  
 <span data-ttu-id="570c9-118">パブリッシャーでのデータ値です。</span><span class="sxs-lookup"><span data-stu-id="570c9-118">The data value at the Publisher.</span></span>  
  
 <span data-ttu-id="570c9-119">**サブスクライバー**</span><span class="sxs-lookup"><span data-stu-id="570c9-119">**Subscriber**</span></span>  
 <span data-ttu-id="570c9-120">サブスクライバーでのデータ値です。</span><span class="sxs-lookup"><span data-stu-id="570c9-120">The data value at the Subscriber.</span></span>  
  
 <span data-ttu-id="570c9-121">**[推奨設定を優先]** 、 **[パブリッシャーを優先]** 、 **[サブスクライバーを優先]**</span><span class="sxs-lookup"><span data-stu-id="570c9-121">**Accept Suggested**, **Accept Publisher**, and **Accept Subscriber**</span></span>  
 <span data-ttu-id="570c9-122">パブリッシャーまたはサブスクライバーのどちらが競合に優先されなかったかによって、どちらかが適用される行を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="570c9-122">Click to accept the row that will be applied at either the Publisher or the Subscriber, depending on which one lost the conflict.</span></span> <span data-ttu-id="570c9-123">パブリッシャーが競合に優先されなかった場合、その他のすべてのサブスクライバーは、次にパブリッシャーと同期される際に、競合に優先される行を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="570c9-123">If the Publisher lost the conflict, all other Subscribers will receive the winning row the next time they synchronize with the Publisher.</span></span>  
  
 <span data-ttu-id="570c9-124">**[残りの競合を自動的に解決]**</span><span class="sxs-lookup"><span data-stu-id="570c9-124">**Resolve remaining conflicts automatically**</span></span>  
 <span data-ttu-id="570c9-125">アーティクルの競合回避モジュールによって提案された解決策を使用して、残りの競合を解決します。</span><span class="sxs-lookup"><span data-stu-id="570c9-125">Resolve all remaining conflicts using the suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="570c9-126">**[参照用にこの競合の詳細をログに記録する]**</span><span class="sxs-lookup"><span data-stu-id="570c9-126">**Log the details of the conflict for later reference**</span></span>  
 <span data-ttu-id="570c9-127">システム テーブルでの競合の詳細をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="570c9-127">Logs the details of the conflict in system tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570c9-128">参照</span><span class="sxs-lookup"><span data-stu-id="570c9-128">See Also</span></span>  
 <span data-ttu-id="570c9-129">[インタラクティブな競合解決](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="570c9-129">[Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span></span>  
 <span data-ttu-id="570c9-130">[マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="570c9-130">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 <span data-ttu-id="570c9-131">[Windows 同期マネージャーを使用したサブスクリプションの同期 &#40;Windows 同期マネージャー&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span><span class="sxs-lookup"><span data-stu-id="570c9-131">[Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span></span>  
 [<span data-ttu-id="570c9-132">マージ レプリケーションの競合検出および解決の詳細</span><span class="sxs-lookup"><span data-stu-id="570c9-132">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  

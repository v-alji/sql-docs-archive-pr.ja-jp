---
title: インタラクティブな競合解決 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57d0de17c4d958a1b842748810ba24717e6866e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630971"
---
# <a name="interactive-conflict-resolution"></a><span data-ttu-id="9e074-102">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="9e074-102">Interactive Conflict Resolution</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="9e074-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションには、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャーでの要求時同期中に、手動で競合を解決できるインタラクティブ競合回避モジュールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9e074-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on-demand synchronization in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="9e074-104">インタラクティブ競合回避モジュールを実行時に有効化すると、グラフィカル インターフェイスに競合する各行のデータが表示されます。ここから、競合するデータを表示および編集し、個々の競合を解決できます。</span><span class="sxs-lookup"><span data-stu-id="9e074-104">Activated at run time, the Interactive Resolver is a graphical interface that displays data for each conflicting row, and provides options for viewing and editing the conflict data, and resolving each conflict individually.</span></span>  
  
 <span data-ttu-id="9e074-105">インタラクティブ競合回避モジュールは競合表示モジュールに似ています。</span><span class="sxs-lookup"><span data-stu-id="9e074-105">The Interactive Resolver resembles the Conflict Viewer.</span></span> <span data-ttu-id="9e074-106">ただし、競合表示モジュールではマージ同期後に解決済みの競合の結果が表示されるのに対して、インタラクティブ競合回避モジュールでは解決の前に各競合が表示されるため、マージ同期時に取り込むデータを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9e074-106">However, the Conflict Viewer displays the results of conflicts that are already resolved after merge synchronization, and the Interactive Resolver displays each conflict prior to resolution, allowing you to determine the outcome of each conflict during merge synchronization.</span></span> <span data-ttu-id="9e074-107">いずれかのユーザーが、競合発生時にインタラクティブ競合回避モジュールを監視できるようになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e074-107">Someone should be available to monitor the Interactive Resolver when a conflict occurs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e074-108">インタラクティブな競合回避には Windows 同期マネージャーが必要です。</span><span class="sxs-lookup"><span data-stu-id="9e074-108">Interactive Resolution requires Windows Synchronization Manager.</span></span> <span data-ttu-id="9e074-109">同期が Windows 同期マネージャーの外部で (スケジュールされた同期、または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] かレプリケーション モニターでの要求時同期として) 実行される場合、競合は、アーティクルに指定された競合回避モジュールに従って、ユーザーの介入なしに自動的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="9e074-109">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span> <span data-ttu-id="9e074-110">論理レコードに関連する競合は、インタラクティブ競合回避モジュールには表示されません。</span><span class="sxs-lookup"><span data-stu-id="9e074-110">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="9e074-111">これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e074-111">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="9e074-112">詳細については、「[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](../view-conflict-information-for-merge-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e074-112">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a><span data-ttu-id="9e074-113">アーティクル競合回避モジュールおよびインタラクティブ競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="9e074-113">Article Resolvers and the Interactive Resolver</span></span>  
 <span data-ttu-id="9e074-114">競合回避モジュール (既定の競合回避モジュール、ビジネス ロジック ハンドラー、カスタム競合回避モジュールのいずれか) は、パブリケーションの作成時に特定のアーティクルに割り当てられます。そこでルールのセットによって、競合している行データを入力したときにどのデータセットを使用するかが決まります。</span><span class="sxs-lookup"><span data-stu-id="9e074-114">Conflict resolvers (either the default resolver, a business logic handler, or a custom resolver) are assigned to specific articles when a publication is created, and use a set of rules to determine which set of data should be used when conflicting row data is entered.</span></span> <span data-ttu-id="9e074-115">インタラクティブ競合回避モジュールは、競合でどのデータを優先するかを指定するルールを持つ独立した競合回避モジュールではなく、既定またはカスタムの競合回避モジュールと組み合わせて使用するツールです。</span><span class="sxs-lookup"><span data-stu-id="9e074-115">The Interactive Resolver is not a separate conflict resolver with rules for determining conflict winners and losers, but a tool used in conjunction with default and custom resolvers.</span></span> <span data-ttu-id="9e074-116">アーティクル競合回避モジュールでは、どの行を競合で優先し、どの行を優先しないかが指定されますが、インタラクティブ競合回避モジュールでは、その結果にユーザーが介入し、データを受け入れたり、拒否したり、変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="9e074-116">The article resolver still determines the winning and losing row, but the Interactive Resolver allows user intervention to accept, reject, or modify the results.</span></span>  
  
 <span data-ttu-id="9e074-117">インタラクティブ競合回避モジュールを使用するには、競合回避を必要とする各アーティクルまたはサブスクリプションに対して、インタラクティブな競合回避を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e074-117">To use the Interactive Resolver, interactive resolution must be enabled for each article and subscription that requires it.</span></span> <span data-ttu-id="9e074-118">1 つ以上のアーティクルまたはサブスクリプションで有効にしておくと、マージ同期中に競合が検出された場合、インタラクティブ競合回避モジュールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e074-118">After it is enabled for one or more articles and subscriptions, the Interactive Resolver is used when a conflict is detected during merge synchronization.</span></span>  
  
 <span data-ttu-id="9e074-119">インタラクティブ競合回避モジュールを使用するには、「[Specify Interactive Conflict Resolution for Merge Articles](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution)」 (マージ アーティクルにインタラクティブな競合解決を指定する) と「[Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)](../synchronize-a-subscription-using-windows-synchronization-manager.md)」 (Windows 同期マネージャーを使用してサブスクリプションを同期する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e074-119">To use the Interactive Resolver, see [Specify Interactive Conflict Resolution for Merge Articles](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution) and [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e074-120">参照</span><span class="sxs-lookup"><span data-stu-id="9e074-120">See Also</span></span>  
 [<span data-ttu-id="9e074-121">マージ レプリケーションの競合検出および解決の詳細</span><span class="sxs-lookup"><span data-stu-id="9e074-121">Advanced Merge Replication Conflict Detection and Resolution</span></span>](advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  

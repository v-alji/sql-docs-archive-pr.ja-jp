---
title: レポートパラメーターの概念 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b740362daea83b50a62f0b4453ce818ab21ace7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713850"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a><span data-ttu-id="ac394-102">レポート パラメーターの概念 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ac394-102">Report Parameters Concept (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ac394-103">関連するレポートをリンクさせたり、レポートの外観を制御したり、レポート データをフィルター選択したり、レポートの範囲を特定のユーザーまたは場所に絞り込んだりする目的で、レポートにはパラメーターを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="ac394-103">You can add parameters to a report to link related reports, to control the report appearance, to filter report data, or to narrow the scope of a report to specific users or locations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="ac394-104">レポート パラメーターは次の方法で作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-104">Report parameters are created in the following ways:</span></span>  
  
-   <span data-ttu-id="ac394-105">自動: クエリ変数を含んだデータセット クエリを定義すると自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-105">Automatically, when you define dataset query that contains query variables.</span></span> <span data-ttu-id="ac394-106">クエリ変数ごとに、同じ名前の対応するデータセット クエリ パラメーターおよびレポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-106">For each query variable, a corresponding dataset query parameter and report parameter with the same names are created.</span></span> <span data-ttu-id="ac394-107">クエリ パラメーターには、クエリ変数の参照のほか、ストアド プロシージャの入力パラメーターの参照を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ac394-107">A query parameter can be a reference to a query variable or to an input parameter for a stored procedure.</span></span>  
  
-   <span data-ttu-id="ac394-108">自動: クエリ パラメーターを含んだ共有データセットへの参照を追加すると自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-108">Automatically, when you add a reference to a shared dataset that contains query parameters.</span></span>  
  
-   <span data-ttu-id="ac394-109">手動: レポート データ ペインでは、レポート パラメーターを手動で作成できます。</span><span class="sxs-lookup"><span data-stu-id="ac394-109">Manually, when you create report parameters in the Report Data pane.</span></span> <span data-ttu-id="ac394-110">パラメーターは、レポート内の式に含めることのできる組み込みコレクションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="ac394-110">Parameters are one of the built-in collections that you can include in an expression in a report.</span></span> <span data-ttu-id="ac394-111">式はレポート定義の中で値を定義するために頻繁に使用されます。パラメーターを使用して、レポートの外観を制御したり、関連するサブレポート (またはパラメーターを使用する他のレポート) に値を渡したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac394-111">Because expressions are used to define values throughout a report definition, you can use parameters to control report appearance or to pass values to related subreports or reports that also use parameters.</span></span>  
  
 <span data-ttu-id="ac394-112">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="ac394-112">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="ac394-113">データがレポートに返される前や後にレポート データをフィルター処理する目的でパラメーターは頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-113">Parameters are frequently used to filter report data both before and after the data is returned to the report.</span></span> <span data-ttu-id="ac394-114">詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac394-114">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ac394-115">レポートをデザインするときは、レポート パラメーターはレポート定義に保存されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-115">When you design a report, report parameters are saved in the report definition.</span></span> <span data-ttu-id="ac394-116">レポートをパブリッシュするときは、レポート パラメーターはレポート定義とは別に保存され管理されます。</span><span class="sxs-lookup"><span data-stu-id="ac394-116">When you publish a report, report parameters are saved and managed separately from the report definition.</span></span> <span data-ttu-id="ac394-117">レポート サーバーにレポートを保存した後、次のことを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ac394-117">After you save the report to the report server, you can do the following:</span></span>  
  
-   <span data-ttu-id="ac394-118">レポート パラメーターの値を (レポート定義とは関係なく) レポート サーバー上で直接変更する。</span><span class="sxs-lookup"><span data-stu-id="ac394-118">Change report parameter values directly on the report server independently from the report definition.</span></span>  
  
-   <span data-ttu-id="ac394-119">同じレポート定義へのリンクとして複数のリンク レポートを作成し、それぞれのリンク レポートに、レポート サーバー上で別々に管理できる一連のパラメーター値を割り当てる。</span><span class="sxs-lookup"><span data-stu-id="ac394-119">Create multiple linked reports in which each linked report is a link to the report definition with a separate set of parameter values that can be managed independently on the report server.</span></span>  
  
 <span data-ttu-id="ac394-120">レポートのスナップショットや履歴、または、パブリッシュされたレポートに対するサブスクリプションを作成する予定がある場合は、レポート パラメーターが、レポートのデザイン要件にどのような影響を及ぼすかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac394-120">If you plan to create report snapshots, histories, or subscriptions to a published report, you must understand how report parameters affect the design requirements for the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac394-121">参照</span><span class="sxs-lookup"><span data-stu-id="ac394-121">See Also</span></span>  
 <span data-ttu-id="ac394-122">[レポート作成の概念 &#40;レポートビルダーと SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ac394-122">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ac394-123">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ac394-123">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ac394-124">チュートリアル: レポートへのパラメーターの追加 &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="ac394-124">Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;</span></span>](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  

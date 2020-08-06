---
title: '方法: レポートをフィルター処理する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Upgrade Advisor], filtering
- filtering reports [Reporting Services]
ms.assetid: bc3dbe16-f6c1-4f07-8d88-2b8e86302c7e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4946b9ea208c0fad98426b7c7fc4247cfaa47680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644810"
---
# <a name="how-to-filter-reports"></a><span data-ttu-id="7897a-102">レポートに表示する問題を選択する方法</span><span class="sxs-lookup"><span data-stu-id="7897a-102">How to: Filter Reports</span></span>
  <span data-ttu-id="7897a-103">このトピックでは、アップグレードアドバイザーレポートビューアーを使用して、レポートにフィルターを適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7897a-103">This topic describes how you can use the Upgrade Advisor Report Viewer to apply filters to a report.</span></span>  
  
### <a name="to-filter-reports"></a><span data-ttu-id="7897a-104">レポートに表示する問題を選択するには</span><span class="sxs-lookup"><span data-stu-id="7897a-104">To filter reports</span></span>  
  
1.  <span data-ttu-id="7897a-105">レポート ビューアーで、フィルター選択するレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-105">In the report viewer, display the report that you want to filter.</span></span> <span data-ttu-id="7897a-106">手順については、「 [How to: View a Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7897a-106">For instructions, see [How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md).</span></span>  
  
2.  <span data-ttu-id="7897a-107">[**フィルター条件**] ボックスの一覧で、表示する問題の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7897a-107">In the **Filter by** list, select a type of issue to view:</span></span>  
  
    -   <span data-ttu-id="7897a-108">**すべての問題**。</span><span class="sxs-lookup"><span data-stu-id="7897a-108">**All issues**.</span></span> <span data-ttu-id="7897a-109">解決済みとしてマークされていないすべての問題を表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-109">This displays all issues that have not been marked as resolved.</span></span>  
  
    -   <span data-ttu-id="7897a-110">**すべてのアップグレードの問題**。</span><span class="sxs-lookup"><span data-stu-id="7897a-110">**All upgrade issues**.</span></span> <span data-ttu-id="7897a-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレードに関連するすべての問題を表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-111">This displays all issues that are related to upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="7897a-112">**アップグレード前の問題**。</span><span class="sxs-lookup"><span data-stu-id="7897a-112">**Pre-upgrade issues**.</span></span> <span data-ttu-id="7897a-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレード前に解決する必要があるすべての問題を表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-113">This displays all issues that should or must be fixed before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="7897a-114">**移行に関するすべての問題**。</span><span class="sxs-lookup"><span data-stu-id="7897a-114">**All migration issues**.</span></span> <span data-ttu-id="7897a-115">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのデータまたはアプリケーションの移行に関連するすべての問題を表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-115">This displays all issues that are related to migrating data or applications to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="7897a-116">**解決済みの問題**。</span><span class="sxs-lookup"><span data-stu-id="7897a-116">**Resolved Issues**.</span></span> <span data-ttu-id="7897a-117">解決済みとしてマークされているすべての問題を表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-117">This displays all issues that have been marked as resolved.</span></span>  
  
    -   <span data-ttu-id="7897a-118">**未解決の問題**。</span><span class="sxs-lookup"><span data-stu-id="7897a-118">**Unresolved Issues**.</span></span> <span data-ttu-id="7897a-119">まだ解決されていないすべての問題を表示します。</span><span class="sxs-lookup"><span data-stu-id="7897a-119">This displays all issues that have not yet been resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7897a-120">参照</span><span class="sxs-lookup"><span data-stu-id="7897a-120">See Also</span></span>  
 <span data-ttu-id="7897a-121">[アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7897a-121">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="7897a-122">[アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="7897a-122">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="7897a-123">[アップグレードアドバイザーの操作方法に関するトピック](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="7897a-123">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="7897a-124">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="7897a-124">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

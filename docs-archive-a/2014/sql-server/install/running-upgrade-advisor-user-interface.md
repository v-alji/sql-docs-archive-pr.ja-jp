---
title: アップグレードアドバイザーの実行 (ユーザーインターフェイス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a5e47ef2b8183823dff884e114adc420e371adf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645349"
---
# <a name="running-upgrade-advisor-user-interface"></a><span data-ttu-id="9ef25-102">アップグレード アドバイザーの実行 (ユーザー インターフェイス)</span><span class="sxs-lookup"><span data-stu-id="9ef25-102">Running Upgrade Advisor (User Interface)</span></span>
  <span data-ttu-id="9ef25-103">アップグレード アドバイザーを実行すると、アップグレードの計画時にローカルまたはリモートのコンポーネントを分析できます。</span><span class="sxs-lookup"><span data-stu-id="9ef25-103">You can run Upgrade Advisor to analyze local or remote components during upgrade planning.</span></span> <span data-ttu-id="9ef25-104">アップグレードアドバイザーによって、分析されるコンポーネントとインスタンスごとにレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ef25-104">Upgrade Advisor produces a report for each component and instance that is analyzed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9ef25-105">アップグレード アドバイザーは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のリモート インスタンスを分析しません。</span><span class="sxs-lookup"><span data-stu-id="9ef25-105">Upgrade Advisor does not analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9ef25-106">[!INCLUDE[ssRS](../../includes/ssrs.md)] のインスタンスを分析するには、[!INCLUDE[ssRS](../../includes/ssrs.md)] がインストールされているコンピューターにアップグレード アドバイザーをインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef25-106">To analyze an instance of [!INCLUDE[ssRS](../../includes/ssrs.md)], Upgrade Advisor must be installed on the computer where [!INCLUDE[ssRS](../../includes/ssrs.md)] is installed.</span></span>  
>   
>  <span data-ttu-id="9ef25-107">Integration Services を分析するに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] インストールされ、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 同じコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef25-107">To analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services, you must have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] installed and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed on the same computer.</span></span>  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="9ef25-108">アップグレードアドバイザー分析ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="9ef25-108">Running the Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="9ef25-109">アップグレード アドバイザー分析ウィザードの実行には、次の 6 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="9ef25-109">Running the Upgrade Advisor Analysis Wizard has six steps:</span></span>  
  
1.  <span data-ttu-id="9ef25-110">アップグレード アドバイザーの開始ページからウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-110">Launch the wizard from the Upgrade Advisor start page.</span></span>  
  
2.  <span data-ttu-id="9ef25-111">分析するサーバーとコンポーネントを特定します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-111">Identify server and components to analyze.</span></span>  
  
3.  <span data-ttu-id="9ef25-112">認証情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-112">Gather authentication information.</span></span>  
  
4.  <span data-ttu-id="9ef25-113">コンポーネントの種類に基づいて追加パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-113">Gather additional parameters based on component type.</span></span>  
  
5.  <span data-ttu-id="9ef25-114">選択したコンポーネントを分析します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-114">Analyze selected components.</span></span>  
  
6.  <span data-ttu-id="9ef25-115">アップグレードの問題に関するレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-115">Generate report of upgrade issues.</span></span>  
  
 <span data-ttu-id="9ef25-116">アップグレードアドバイザー分析ウィザードの詳細については、「[アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef25-116">For more information about the Upgrade Advisor Analysis Wizard, see [How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).</span></span>  
  
 <span data-ttu-id="9ef25-117">各手順に必要な特定の情報については、「 [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef25-117">For specific information that is required for each step, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a><span data-ttu-id="9ef25-118">アップグレードアドバイザーレポートビューアーの実行</span><span class="sxs-lookup"><span data-stu-id="9ef25-118">Running the Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="9ef25-119">アップグレードアドバイザー分析ウィザードで生成されたレポートを表示するには、アップグレードアドバイザーレポートビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ef25-119">You use the Upgrade Advisor Report Viewer to view reports generated by the Upgrade Advisor Analysis Wizard.</span></span> <span data-ttu-id="9ef25-120">レポートを読み込んだら、次の条件でレポートのコンポーネントをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="9ef25-120">When the report is loaded, you can filter the components of the report by the following factors:</span></span>  
  
-   <span data-ttu-id="9ef25-121">すべての問題</span><span class="sxs-lookup"><span data-stu-id="9ef25-121">All issues</span></span>  
  
-   <span data-ttu-id="9ef25-122">アップグレードに関するすべての問題</span><span class="sxs-lookup"><span data-stu-id="9ef25-122">All upgrade issues</span></span>  
  
-   <span data-ttu-id="9ef25-123">アップグレード前の問題</span><span class="sxs-lookup"><span data-stu-id="9ef25-123">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="9ef25-124">移行に関するすべての問題</span><span class="sxs-lookup"><span data-stu-id="9ef25-124">All migration issues</span></span>  
  
-   <span data-ttu-id="9ef25-125">解決した問題</span><span class="sxs-lookup"><span data-stu-id="9ef25-125">Resolved issues</span></span>  
  
-   <span data-ttu-id="9ef25-126">未解決の問題</span><span class="sxs-lookup"><span data-stu-id="9ef25-126">Unresolved issues</span></span>  
  
 <span data-ttu-id="9ef25-127">レポート ビューアーを使用するための操作手順については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef25-127">For step-by-step instructions for using the report viewer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9ef25-128">アップグレード アドバイザーのレポートを表示する方法</span><span class="sxs-lookup"><span data-stu-id="9ef25-128">How to: View an Upgrade Advisor Report</span></span>](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [<span data-ttu-id="9ef25-129">レポートに表示する問題を選択する方法</span><span class="sxs-lookup"><span data-stu-id="9ef25-129">How to: Filter Reports</span></span>](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [<span data-ttu-id="9ef25-130">レポートをエクスポートする方法</span><span class="sxs-lookup"><span data-stu-id="9ef25-130">How to: Export Reports</span></span>](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ef25-131">参照</span><span class="sxs-lookup"><span data-stu-id="9ef25-131">See Also</span></span>  
 <span data-ttu-id="9ef25-132">[アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="9ef25-132">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="9ef25-133">[アップグレードアドバイザーのユーザーインターフェイスリファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9ef25-133">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 <span data-ttu-id="9ef25-134">[アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9ef25-134">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9ef25-135">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="9ef25-135">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

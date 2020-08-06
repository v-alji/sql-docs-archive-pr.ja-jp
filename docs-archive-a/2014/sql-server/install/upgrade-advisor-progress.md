---
title: アップグレードアドバイザーの進行状況 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b504b8f1c8392ad2cf55837dc65bbb2f019d6f48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640374"
---
# <a name="upgrade-advisor-progress"></a><span data-ttu-id="d551d-102">アップグレード アドバイザーの進行状況</span><span class="sxs-lookup"><span data-stu-id="d551d-102">Upgrade Advisor Progress</span></span>
  <span data-ttu-id="d551d-103">アップグレード アドバイザー分析では、選択した各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントの分析を実行する専用アナライザーから開始します。</span><span class="sxs-lookup"><span data-stu-id="d551d-103">Upgrade Advisor analysis starts with a dedicated analyzer that performs an analysis of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that you selected.</span></span> <span data-ttu-id="d551d-104">コンポーネントが分析されると、**進行状況を示すダイアログボックス**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d551d-104">As components are analyzed, progress is reported in the **Progress** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d551d-105">Options</span><span class="sxs-lookup"><span data-stu-id="d551d-105">Options</span></span>  
 <span data-ttu-id="d551d-106">**操作**</span><span class="sxs-lookup"><span data-stu-id="d551d-106">**Action**</span></span>  
 <span data-ttu-id="d551d-107">分析対象として選択された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d551d-107">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that is selected for analysis.</span></span>  
  
 <span data-ttu-id="d551d-108">**状態**</span><span class="sxs-lookup"><span data-stu-id="d551d-108">**Status**</span></span>  
 <span data-ttu-id="d551d-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントの進行状況インターフェイスから返された状態値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d551d-109">Displays the status value returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component progress interface.</span></span>  
  
 <span data-ttu-id="d551d-110">**Message**</span><span class="sxs-lookup"><span data-stu-id="d551d-110">**Message**</span></span>  
 <span data-ttu-id="d551d-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのアナライザーから返されたエラー、失敗、または成功のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d551d-111">Displays error, failure, or success messages returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] individual analyzer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d551d-112">分析所要時間が非常に長い場合、その分析を停止してアップグレード アドバイザー分析ウィザードを終了してから、そのウィザードを再実行できます。</span><span class="sxs-lookup"><span data-stu-id="d551d-112">If the analysis is taking too long, you can stop the analysis, exit the Upgrade Advisor Analysis Wizard, and then rerun the wizard.</span></span> <span data-ttu-id="d551d-113">分析時間を短縮するには、スキャンするコンポーネントを少なくします。</span><span class="sxs-lookup"><span data-stu-id="d551d-113">To reduce analysis time, select fewer components to scan.</span></span>  
  
 <span data-ttu-id="d551d-114">分析が完了すると、そのレポートがファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d551d-114">When analysis is complete, the report is written to a file.</span></span> <span data-ttu-id="d551d-115">レポートを表示するには、[**レポートの起動**] をクリックして、このページからレポートビューアーを起動します。</span><span class="sxs-lookup"><span data-stu-id="d551d-115">You can view the report by clicking **Launch Report** to launch the report viewer from this page.</span></span> <span data-ttu-id="d551d-116">後でレポートを表示する場合は、アップグレードアドバイザーの開始ページから**アップグレードアドバイザーレポートビューアー**を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="d551d-116">If you want to view the report later, you can open the **Upgrade Advisor Report Viewer** from the Upgrade Advisor start page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d551d-117">以前のレポートはサーバーを分析するたびに保存されています。</span><span class="sxs-lookup"><span data-stu-id="d551d-117">Previous reports are saved every time you analyze a server.</span></span> <span data-ttu-id="d551d-118">保存されるレポートのファイル名には、タイムスタンプが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d551d-118">The reports are saved using the timestamp for the file name.</span></span> <span data-ttu-id="d551d-119">レポート ビューアーでは、保存されている最近 5 件のレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d551d-119">The report viewer displays the latest five saved reports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d551d-120">参照</span><span class="sxs-lookup"><span data-stu-id="d551d-120">See Also</span></span>  
 <span data-ttu-id="d551d-121">[方法: アップグレードアドバイザーを起動する](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="d551d-121">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="d551d-122">[アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="d551d-122">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="d551d-123">[SQL Server コンポーネント](../../../2014/sql-server/install/sql-server-components.md) </span><span class="sxs-lookup"><span data-stu-id="d551d-123">[SQL Server Components](../../../2014/sql-server/install/sql-server-components.md) </span></span>  
 <span data-ttu-id="d551d-124">[アップグレードアドバイザーのユーザーインターフェイスリファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d551d-124">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 [<span data-ttu-id="d551d-125">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="d551d-125">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

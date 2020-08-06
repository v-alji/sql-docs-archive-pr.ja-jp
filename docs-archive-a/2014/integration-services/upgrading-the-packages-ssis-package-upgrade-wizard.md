---
title: パッケージのアップグレード (SSIS パッケージアップグレードウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13228dabc1566b592733da4afd8ebde3671ee0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633197"
---
# <a name="upgrading-the-packages-ssis-package-upgrade-wizard"></a><span data-ttu-id="123f4-102">[パッケージをアップグレードしています] (SSIS パッケージ アップグレード ウィザード)</span><span class="sxs-lookup"><span data-stu-id="123f4-102">Upgrading the Packages (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="123f4-103">**[パッケージをアップグレードしています]** ページでは、パッケージのアップグレードの進行状況を表示したり、アップグレード プロセスを中断したりできます。</span><span class="sxs-lookup"><span data-stu-id="123f4-103">Use the **Upgrading the Packages** page to view the progress of package upgrade and to interrupt the upgrade process.</span></span> <span data-ttu-id="123f4-104">[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードでは、選択したパッケージが 1 つずつアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="123f4-104">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard upgrades the selected packages one by one.</span></span>  
  
 <span data-ttu-id="123f4-105">**SQL Server データベースまたはパッケージ ストアに保存されたアップグレード済みパッケージを表示するには**</span><span class="sxs-lookup"><span data-stu-id="123f4-105">**To view upgraded packages that were saved to a SQL Server database or to the package store**</span></span>  
  
-   <span data-ttu-id="123f4-106">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]のオブジェクト エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のローカル インスタンスに接続し、 **[格納されたパッケージ]** ノードを展開すると、アップグレードされたパッケージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="123f4-106">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], in Object Explorer, connect to the local instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], and then expand the **Stored Packages** node to see the packages that were upgraded.</span></span>  
  
 <span data-ttu-id="123f4-107">**SQL Server データ ツールからアップグレードされたパッケージを表示するには**</span><span class="sxs-lookup"><span data-stu-id="123f4-107">**To view upgraded packages that were upgraded from SQL Server Data Tools**</span></span>  
  
-   <span data-ttu-id="123f4-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のプロジェクトを開き、 **[SSIS パッケージ]** ノードを展開すると、アップグレードされたパッケージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="123f4-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and then expand the **SSIS Packages** node to see the upgraded packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="123f4-109">Options</span><span class="sxs-lookup"><span data-stu-id="123f4-109">Options</span></span>  
 <span data-ttu-id="123f4-110">**メッセージウィンドウ**</span><span class="sxs-lookup"><span data-stu-id="123f4-110">**Message pane**</span></span>  
 <span data-ttu-id="123f4-111">アップグレード プロセス中に、進行状況メッセージと概要情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="123f4-111">Displays progress messages and summary information during the upgrade process.</span></span>  
  
 <span data-ttu-id="123f4-112">**操作**</span><span class="sxs-lookup"><span data-stu-id="123f4-112">**Action**</span></span>  
 <span data-ttu-id="123f4-113">アップグレード処理で実行されるアクションを表示します。</span><span class="sxs-lookup"><span data-stu-id="123f4-113">View the actions in the upgrade.</span></span>  
  
 <span data-ttu-id="123f4-114">**状態**</span><span class="sxs-lookup"><span data-stu-id="123f4-114">**Status**</span></span>  
 <span data-ttu-id="123f4-115">各アクションの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="123f4-115">View the result of each action.</span></span>  
  
 <span data-ttu-id="123f4-116">**Message**</span><span class="sxs-lookup"><span data-stu-id="123f4-116">**Message**</span></span>  
 <span data-ttu-id="123f4-117">各アクションによって生成されるエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="123f4-117">View the error messages that each action generates.</span></span>  
  
 <span data-ttu-id="123f4-118">**Stop**</span><span class="sxs-lookup"><span data-stu-id="123f4-118">**Stop**</span></span>  
 <span data-ttu-id="123f4-119">パッケージのアップグレードを停止します。</span><span class="sxs-lookup"><span data-stu-id="123f4-119">Stop the package upgrade.</span></span>  
  
 <span data-ttu-id="123f4-120">**Report**</span><span class="sxs-lookup"><span data-stu-id="123f4-120">**Report**</span></span>  
 <span data-ttu-id="123f4-121">パッケージのアップグレード結果を含むレポートの処理を選択します。</span><span class="sxs-lookup"><span data-stu-id="123f4-121">Select what you want to do with the report that contains the results of the package upgrade:</span></span>  
  
-   <span data-ttu-id="123f4-122">レポートをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="123f4-122">View the report online.</span></span>  
  
-   <span data-ttu-id="123f4-123">レポートをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="123f4-123">Save the report to a file.</span></span>  
  
-   <span data-ttu-id="123f4-124">レポートをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="123f4-124">Copy the report to the Clipboard</span></span>  
  
-   <span data-ttu-id="123f4-125">レポートを電子メール メッセージとして送信します。</span><span class="sxs-lookup"><span data-stu-id="123f4-125">Send the report as an e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="123f4-126">参照</span><span class="sxs-lookup"><span data-stu-id="123f4-126">See Also</span></span>  
 [<span data-ttu-id="123f4-127">Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="123f4-127">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  

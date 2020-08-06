---
title: パッケージ実行のレポートのトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fc476ac-bd69-434e-9636-70776e0b3b6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b20d9c9c02af3f3df96e2ef46a7b25251793fa55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642864"
---
# <a name="troubleshooting-reports-for-package-execution"></a><span data-ttu-id="7e494-102">パッケージ実行のレポートのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7e494-102">Troubleshooting Reports for Package Execution</span></span>
  <span data-ttu-id="7e494-103">現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] カタログに配置された [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの監視とトラブルシューティングに役立つ標準レポートを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7e494-103">In the current release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], standard reports are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to help you monitor and troubleshoot [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that have been deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span> <span data-ttu-id="7e494-104">これらのパッケージ レポートの中には、パッケージの実行状態を確認する場合や、実行が失敗した原因を特定する場合に特に役立つレポートが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="7e494-104">Two of these package reports in particular help you to view package execution status and identify the cause of execution failures.</span></span>  
  
-   <span data-ttu-id="7e494-105">**Integration Services ダッシュボード** : このレポートは、過去 24 時間の間に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上で実行されたすべてのパッケージに関する概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7e494-105">**Integration Services Dashboard** - This report provides an overview of all the package executions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance in the past 24 hours.</span></span> <span data-ttu-id="7e494-106">このレポートには、各パッケージの状態、操作の種類、パッケージ名などに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e494-106">The report displays information such as Status, Operation Type, Package Name, etc., for each package.</span></span>  
  
     <span data-ttu-id="7e494-107">開始時刻、終了時刻、および期間は次のように解釈できます。</span><span class="sxs-lookup"><span data-stu-id="7e494-107">The Start Time, End Time, and Duration can be interpreted as follows:</span></span>  
  
    -   <span data-ttu-id="7e494-108">パッケージがまだ実行されている場合は、"期間 = 現在の時刻 - 開始時刻" です。</span><span class="sxs-lookup"><span data-stu-id="7e494-108">If the package is still running, then Duration = current time - Start Time</span></span>  
  
    -   <span data-ttu-id="7e494-109">パッケージが完了した場合は、"期間 = 終了時刻 - 開始時刻" です。</span><span class="sxs-lookup"><span data-stu-id="7e494-109">If the package has completed, then Duration = End Time - Start Time</span></span>  
  
     <span data-ttu-id="7e494-110">ダッシュ ボードでは、サーバーで実行されたそれぞれのパッケージに対し、"ズーム イン" 機能を使用して、発生した可能性のあるパッケージ実行エラーの特定の詳細を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="7e494-110">For each package that has run on the server, the dashboard allows you to "zoom in" to find specific details on package execution errors that may have occurred.</span></span> <span data-ttu-id="7e494-111">たとえば、 **[概要]** をクリックすると、実行に含まれるタスクの状態の概要が表示されます。 **[すべてのメッセージ]** をクリックすると、パッケージの実行の一部としてキャプチャされた詳細メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e494-111">For example, click **Overview** to display a high-level overview of the status of the tasks in the execution, or **All Messages** to display the detailed messages that were captured as part of the package execution.</span></span>  
  
     <span data-ttu-id="7e494-112">**[フィルター]** をクリックし、 **[フィルターの設定]** ダイアログで条件を選択することにより、各ページに表示されるテーブルにフィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="7e494-112">You can filter the table displayed on any page by clicking **Filter** and then selecting criteria in the **Filter Settings** dialog.</span></span> <span data-ttu-id="7e494-113">使用できるフィルター条件は、表示されるデータに依存します。</span><span class="sxs-lookup"><span data-stu-id="7e494-113">The filter criteria available depends on the data being displayed.</span></span> <span data-ttu-id="7e494-114">**[フィルターの設定]** ダイアログの並べ替えアイコンをクリックすることで、レポートの並べ替え順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7e494-114">You can change the sort order of the report by clicking the sort icon in the **Filter Settings** dialog.</span></span>  
  
-   <span data-ttu-id="7e494-115">**"利用状況 - すべての実行" レポート** : このレポートには、サーバーで実行されたすべての [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の実行に関する概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e494-115">**Activity - All Executions Report** - This report displays a summary of all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] executions that have been performed on the server.</span></span> <span data-ttu-id="7e494-116">この概要には、状態、開始時刻、終了時刻など、各実行の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e494-116">The summary displays information for each execution such as status, start time, and end time.</span></span> <span data-ttu-id="7e494-117">各概要エントリには、実行中に生成されたメッセージやパフォーマンス データを含め、実行に関する詳細へのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e494-117">Each summary entry includes links to more information about the execution including messages generated during execution and performance data.</span></span> <span data-ttu-id="7e494-118">Integration Services ダッシュボードと同様に、テーブルにフィルターを適用して、表示される情報を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7e494-118">As with the Integration Services Dashboard, you can apply a filter to the table to narrow down the information displayed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7e494-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="7e494-119">Related Tasks</span></span>  
 [<span data-ttu-id="7e494-120">Integration Services サーバーのレポートの表示</span><span class="sxs-lookup"><span data-stu-id="7e494-120">View Reports for the Integration Services Server</span></span>](../view-reports-for-the-integration-services-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="7e494-121">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="7e494-121">Related Content</span></span>  
 [<span data-ttu-id="7e494-122">Integration Services サーバーのレポート</span><span class="sxs-lookup"><span data-stu-id="7e494-122">Reports for the Integration Services Server</span></span>](../reports-for-the-integration-services-server.md)  
  
 [<span data-ttu-id="7e494-123">パッケージ実行のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="7e494-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  

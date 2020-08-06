---
title: リンク レポートを作成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed5e70c9ff8179ae05186685e21303693fc9aed7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642531"
---
# <a name="create-a-linked-report"></a><span data-ttu-id="023f0-102">リンク レポートを作成する</span><span class="sxs-lookup"><span data-stu-id="023f0-102">Create a Linked Report</span></span>
  <span data-ttu-id="023f0-103">リンク レポートは、既存のレポートへのアクセス ポイントとなるレポート サーバー アイテムです。</span><span class="sxs-lookup"><span data-stu-id="023f0-103">A linked report is a report server item that provides an access point to an existing report.</span></span> <span data-ttu-id="023f0-104">概念的には、プログラムを実行したりファイルを開くのに使用する、プログラム ショートカットに似ています。</span><span class="sxs-lookup"><span data-stu-id="023f0-104">Conceptually, it is similar to a program shortcut that you use to run a program or open a file.</span></span>

 <span data-ttu-id="023f0-105">リンク レポートは、既存のレポートから派生し、元のレポート定義を保持しています。</span><span class="sxs-lookup"><span data-stu-id="023f0-105">A linked report is derived from an existing report and retains the original's report definition.</span></span> <span data-ttu-id="023f0-106">リンク レポートは、常に、元のレポートのレポート レイアウトおよびデータ ソース プロパティを継承します。</span><span class="sxs-lookup"><span data-stu-id="023f0-106">A linked report always inherits report layout and data source properties of the original report.</span></span> <span data-ttu-id="023f0-107">セキュリティ、パラメーター、場所、サブスクリプション、スケジュールなど、その他のプロパティおよび設定はすべて、元のレポートとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="023f0-107">All other properties and settings can be different from those of the original report, including security, parameters, location, subscriptions, and schedules.</span></span>

 <span data-ttu-id="023f0-108">既存のレポートの追加バージョンを作成するときに、リンク レポートを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="023f0-108">You can create a linked report when you want to create additional versions of an existing report.</span></span> <span data-ttu-id="023f0-109">たとえば、単一の地域の売上レポートを使用し、すべての販売区域について、地域固有のレポートを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="023f0-109">For example, you could use a single regional sales report to create region-specific reports for all of your sales territories.</span></span>

 <span data-ttu-id="023f0-110">リンク レポートは通常はパラメーター化されたレポートに基づいていますが、パラメーター化されたレポートは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="023f0-110">Although linked reports are typically based on parameterized reports, a parameterized report is not required.</span></span> <span data-ttu-id="023f0-111">リンク レポートは、異なる設定で既存のレポートを配置する場合にも作成できます。</span><span class="sxs-lookup"><span data-stu-id="023f0-111">You can create linked reports whenever you want to deploy an existing report with different settings.</span></span>

### <a name="to-create-a-linked-report"></a><span data-ttu-id="023f0-112">リンク レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="023f0-112">To create a linked report</span></span>

1.  <span data-ttu-id="023f0-113">レポート マネージャーで、リンク先のレポートのあるフォルダーに移動し、オプション メニューを開いて、 **[リンク レポートの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="023f0-113">In Report Manager, navigate to the folder containing the report that you want to link to, and then open the options menu can click **Create Linked Report**.</span></span>

2.  <span data-ttu-id="023f0-114">新規リンク レポートの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="023f0-114">Type a name for the new linked report.</span></span> <span data-ttu-id="023f0-115">必要に応じて、説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="023f0-115">Optionally type a description.</span></span>

3.  <span data-ttu-id="023f0-116">レポートを別のフォルダーに保存するには、 **[場所の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="023f0-116">To select a different folder for the report, click **Change Location**.</span></span> <span data-ttu-id="023f0-117">保存先のフォルダーをクリックするか、または **[場所]** ボックスにフォルダー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="023f0-117">Click the folder you want to use, or type the folder name in the **Location** box.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="023f0-118">別のフォルダーを指定しない場合、現在のフォルダー (リンク先のレポートが保存されているフォルダー) にリンク レポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="023f0-118">If you do not select a different folder, the linked report is created in the current folder (where the report it is based on is stored).</span></span>

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="023f0-119">リンク レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="023f0-119">The linked report opens.</span></span>

     <span data-ttu-id="023f0-120">リンク レポートのアイコンは、レポート サーバーによって管理されるその他のアイテムのアイコンとは異なります。</span><span class="sxs-lookup"><span data-stu-id="023f0-120">A linked report's icon differs from other items managed by a report server.</span></span> <span data-ttu-id="023f0-121">次のアイコンでリンク レポートを示します。</span><span class="sxs-lookup"><span data-stu-id="023f0-121">The following icon indicates a linked report:</span></span>

     <span data-ttu-id="023f0-122">![リンク レポート アイコン](../media/hlp-16linked.gif "リンク レポート アイコン")</span><span class="sxs-lookup"><span data-stu-id="023f0-122">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>

## <a name="see-also"></a><span data-ttu-id="023f0-123">参照</span><span class="sxs-lookup"><span data-stu-id="023f0-123">See Also</span></span>
 <span data-ttu-id="023f0-124">[レポートを開いて閉じる &#40;レポートマネージャー&#41;](../reports/open-and-close-a-report-report-manager.md) [新しいリンクレポートページ &#40;レポートマネージャー](../new-linked-report-page-report-manager.md)&#41;[[アイテムの場所の選択] ページ](../choose-item-location-page-report-manager.md)&#40;レポートマネージャー&#41;[全般プロパティ] ページ、レポート &#40;](../general-properties-page-reports-report-manager.md)レポートマネージャー&#41;REPORTING SERVICES の[概念 &#40;ssrs&#41;](../reporting-services-concepts-ssrs.md) [レポートマネージャー &#40;ssrs ネイティブモード](../report-manager-ssrs-native-mode.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="023f0-124">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) [New Linked Report Page &#40;Report Manager&#41;](../new-linked-report-page-report-manager.md) [Choose Item Location Page &#40;Report Manager&#41;](../choose-item-location-page-report-manager.md) [General Properties Page, Reports &#40;Report Manager&#41;](../general-properties-page-reports-report-manager.md) [Reporting Services Concepts &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md)</span></span>



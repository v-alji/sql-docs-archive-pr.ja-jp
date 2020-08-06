---
title: '[リンクの選択] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a89a555d-efa3-45d6-951e-db78ec6a2c8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc40fe726555babee8d9940e198a93577bd6a09f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634323"
---
# <a name="choose-link-page-report-manager"></a><span data-ttu-id="5511d-102">[リンクの選択] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="5511d-102">Choose Link Page (Report Manager)</span></span>
  <span data-ttu-id="5511d-103">[リンクの選択] ページでは、現在選択しているリンク レポートに基づいて別のレポートを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5511d-103">Use the Choose Link page to choose a different report upon which to base the currently selected linked report.</span></span> <span data-ttu-id="5511d-104">リンク レポートは、レポート サーバーに既にパブリッシュされている他のレポートに基づいています。</span><span class="sxs-lookup"><span data-stu-id="5511d-104">Linked reports are based on other reports already published to a report server.</span></span> <span data-ttu-id="5511d-105">リンク レポートでは基本レポートのレイアウトとデータを使用しますが、個々のプロパティ ページを使用してパラメーターのプロパティ、セキュリティ設定、名前、説明、および場所をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="5511d-105">A linked report uses the layout and data of the base report, but has separate property pages so that you can customize parameter properties, security settings, name, description, and location.</span></span>  
  
 <span data-ttu-id="5511d-106">[リンクの選択] ページでは、リンク レポートで使用する別のパブリッシュされたレポートを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5511d-106">Through the Choose Link page, you can choose a different published report to use with the linked report.</span></span> <span data-ttu-id="5511d-107">リンク レポートの他の設定 (セキュリティ設定やパラメーター設定など) は、リンク情報を変更しても影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="5511d-107">Other settings of the linked report (such as security and parameter settings) are unaffected by changes to the link information.</span></span> <span data-ttu-id="5511d-108">レポート サーバーでは選択内容が検証されないため、リンク レポートで指定したパラメーターと同じパラメーターを使用するレポートを選択してください。</span><span class="sxs-lookup"><span data-stu-id="5511d-108">The report server will not validate your selection, so be sure to choose a report that has the same parameters as those you specified on the linked report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="5511d-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="5511d-109">Navigation</span></span>  
 <span data-ttu-id="5511d-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5511d-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-choose-link-page"></a><span data-ttu-id="5511d-111">[リンクの選択] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="5511d-111">To open the Choose Link page</span></span>  
  
1.  <span data-ttu-id="5511d-112">レポート マネージャーを開き、変更するリンク レポートを探します。</span><span class="sxs-lookup"><span data-stu-id="5511d-112">Open Report Manager, and locate the linked report you want to change.</span></span>  
  
2.  <span data-ttu-id="5511d-113">リンク レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5511d-113">Hover over the linked report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="5511d-114">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5511d-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="5511d-115">この操作により、リンク レポートの **[全般]** プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="5511d-115">This opens the **General** properties page for the linked report.</span></span>  
  
4.  <span data-ttu-id="5511d-116">プロパティ ページの **[全般]** タブで、 **[リンクの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5511d-116">On the **General** tab, on the properties page, click **Change Link**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5511d-117">Options</span><span class="sxs-lookup"><span data-stu-id="5511d-117">Options</span></span>  
 <span data-ttu-id="5511d-118">**場所**</span><span class="sxs-lookup"><span data-stu-id="5511d-118">**Location**</span></span>  
 <span data-ttu-id="5511d-119">フォルダーのパスとレポート名を含む、パブリッシュされたレポートの完全な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5511d-119">Specify the full name of the published report, including the folder path and report name.</span></span> <span data-ttu-id="5511d-120">完全なレポート名を入力するか、ツリー ビューを使用して、使用するレポートに移動できます。</span><span class="sxs-lookup"><span data-stu-id="5511d-120">You can type the full name of the report or use the tree view to navigate to the report you want to use.</span></span>  
  
 <span data-ttu-id="5511d-121">**ツリー ビュー**</span><span class="sxs-lookup"><span data-stu-id="5511d-121">**Tree view**</span></span>  
 <span data-ttu-id="5511d-122">レポート サーバーのフォルダー階層にあるすべてのフォルダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5511d-122">Shows all of the folders in the report server folder hierarchy.</span></span> <span data-ttu-id="5511d-123">ツリー ビューを使用して **[場所]** フィールドに入力するには、レポート名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5511d-123">To use the tree view to fill in the **Location** field, click the name of the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5511d-124">参照</span><span class="sxs-lookup"><span data-stu-id="5511d-124">See Also</span></span>  
 <span data-ttu-id="5511d-125">[[全般] プロパティページ、レポート &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5511d-125">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="5511d-126">[[新しいリンクレポート] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5511d-126">[New Linked Report Page &#40;Report Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span></span>  
 [<span data-ttu-id="5511d-127">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="5511d-127">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  

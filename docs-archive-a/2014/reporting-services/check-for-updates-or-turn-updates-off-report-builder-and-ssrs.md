---
title: 更新を確認するか、更新をオフにします (レポートビルダーと SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9c69792d-d7c4-453b-ae2f-6d2d071d8606
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 088d41e71d770f746367f2760cff8ff67b15623c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640759"
---
# <a name="check-for-updates-or-turn-updates-off-report-builder-and-ssrs"></a><span data-ttu-id="449a3-102">更新を確認するまたは更新をオフにする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="449a3-102">Check for Updates or Turn Updates Off (Report Builder and SSRS)</span></span>
  <span data-ttu-id="449a3-103">レポートを開くたびに、レポート ビルダーによって、そのレポートにあるレポート パーツのパブリッシュ済みインスタンスがレポート サーバー、またはレポート サーバーと統合されている SharePoint サイト上で更新されたかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="449a3-103">Every time you open a report, Report Builder checks to see if the published instances of report parts in that report have been updated on the report server or SharePoint site integrated with a report server.</span></span> <span data-ttu-id="449a3-104">また、データセットやパラメーターなどのレポート パーツの依存アイテムに変更が加えられたかどうかも確認されます。</span><span class="sxs-lookup"><span data-stu-id="449a3-104">It also checks for changes in the report parts' dependent items, such as the dataset and parameters.</span></span> <span data-ttu-id="449a3-105">レポート パーツまたはレポート パーツの依存アイテムがサイトまたはサーバー上で更新されている場合は、レポート内の情報バーに、更新されたパーツの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="449a3-105">If any report parts or their dependencies have been updated on the site or server, an information bar in your report displays the number of updated parts.</span></span> <span data-ttu-id="449a3-106">更新は、表示して受け入れることも、拒否することもできます。また、情報バーを消去することもできます。</span><span class="sxs-lookup"><span data-stu-id="449a3-106">You can choose to view and accept or reject the updates, or dismiss the information bar.</span></span>  
  
 <span data-ttu-id="449a3-107">情報バーを無効にして、レポート パーツのパブリッシュ済みインスタンスの変更に関する情報が表示されないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="449a3-107">You can also disable the information bar and not be informed if published instances of report parts have changed.</span></span> <span data-ttu-id="449a3-108">これは、そのユーザーが開くすべてのレポートでこの機能を無効にするためのユーザー設定です。</span><span class="sxs-lookup"><span data-stu-id="449a3-108">This is a user setting; it will be disabled for all reports that you open.</span></span> <span data-ttu-id="449a3-109">情報バーを無効にした場合でも、更新を確認できます。</span><span class="sxs-lookup"><span data-stu-id="449a3-109">Even if you have disabled the information bar, you can still check for updates.</span></span>  
  
### <a name="to-turn-on-and-off-report-part-updates"></a><span data-ttu-id="449a3-110">レポート パーツ更新のオン/オフを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="449a3-110">To turn on and off report part updates</span></span>  
  
1.  <span data-ttu-id="449a3-111">[レポートビルダー] ボタンをクリックし、[**オプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="449a3-111">Click the Report Builder button, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="449a3-112">[**オプション**] ダイアログボックスの [**リソース**] タブで、[**個人用レポートのレポートパーツに更新を表示する**] チェックボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="449a3-112">In the **Options** dialog box, on the **Resources** tab, select or clear the **Show updates to report parts in my reports** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="449a3-113">これは、ユーザー設定です。</span><span class="sxs-lookup"><span data-stu-id="449a3-113">This is a user setting.</span></span> <span data-ttu-id="449a3-114">そのユーザーが開くすべてのレポートで無効になります。</span><span class="sxs-lookup"><span data-stu-id="449a3-114">It will be disabled for all reports that you open.</span></span>  
  
### <a name="to-check-for-updates"></a><span data-ttu-id="449a3-115">更新を確認するには</span><span class="sxs-lookup"><span data-stu-id="449a3-115">To check for updates</span></span>  
  
-   <span data-ttu-id="449a3-116">レポートの外部またはレポート本文でデザイン画面を右クリックし、[**更新プログラムの確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="449a3-116">Right-click the design surface outside the report, or in the report body, and click **Check for Updates**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449a3-117">参照</span><span class="sxs-lookup"><span data-stu-id="449a3-117">See Also</span></span>  
 <span data-ttu-id="449a3-118">[レポートパーツ &#40;レポートビルダーと SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="449a3-118">[Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="449a3-119">[レポートパーツ &#40;レポートビルダーと SSRS&#41;をパブリッシュおよび再パブリッシュする](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="449a3-119">[Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="449a3-120">[レポートパーツを参照し、既定のフォルダー &#40;レポートビルダーおよび SSRS に設定&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="449a3-120">[Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="449a3-121">[レポートパーツ &#40;レポートビルダーと SSRS&#41;のトラブルシューティング](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="449a3-121">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="449a3-122">レポート ビルダーのレポート パーツおよびデータセット</span><span class="sxs-lookup"><span data-stu-id="449a3-122">Report Parts and Datasets in Report Builder</span></span>](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  

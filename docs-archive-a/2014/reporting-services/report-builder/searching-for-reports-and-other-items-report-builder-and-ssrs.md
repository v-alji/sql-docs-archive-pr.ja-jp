---
title: レポートおよび他のアイテムの検索 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a964cbdbc674fb3d29e18b5e5075695f0033801e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631605"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a><span data-ttu-id="0ac98-102">レポートおよび他のアイテムの検索 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0ac98-102">Searching for Reports and Other Items (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="0ac98-103">レポート マネージャーを使用して、名前や説明からレポート サーバーの特定のアイテムを検索できます。</span><span class="sxs-lookup"><span data-stu-id="0ac98-103">You can use Report Manager to search a report server for specific items by name or description.</span></span> <span data-ttu-id="0ac98-104">検索できるアイテムは、パブリッシュされているレポート、レポート モデル、フォルダー、共有データ ソース、およびリソースです。</span><span class="sxs-lookup"><span data-stu-id="0ac98-104">You can search for published reports, report models, folders, shared data sources, and resources.</span></span> <span data-ttu-id="0ac98-105">スケジュール、所有者、ロールの割り当て、レポート履歴の特定のスナップショット、またはサブスクリプションは検索できません。</span><span class="sxs-lookup"><span data-stu-id="0ac98-105">You cannot search for schedules, owners, role assignments, specific snapshots in report history, or subscriptions.</span></span> <span data-ttu-id="0ac98-106">検索は、アイテムが保存されているレポート サーバー データベースに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="0ac98-106">The search is performed on the report server database where the items are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ac98-107">ファイル システムの検索を実行しても、レポート サーバーによって管理されているアイテムの検索結果は返されません。</span><span class="sxs-lookup"><span data-stu-id="0ac98-107">Performing a file system search will not return search results for items managed by a report server.</span></span>  
  
-   <span data-ttu-id="0ac98-108">レポート マネージャーでアイテムを検索するには、ページの先頭にある **[検索]** テキスト ボックスに検索文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="0ac98-108">To search for items in Report Manager, type a search string in the **Search for** text box at the top of the page.</span></span> <span data-ttu-id="0ac98-109">検索は、フォルダー階層の最上位ノードから開始され、続いて各分岐にわたり実行されます。</span><span class="sxs-lookup"><span data-stu-id="0ac98-109">Searches begin at the top node in the folder hierarchy and then proceed through every branch.</span></span> <span data-ttu-id="0ac98-110">特定の分岐へのアクセス権がない場合、その分岐は検索されません。</span><span class="sxs-lookup"><span data-stu-id="0ac98-110">If you do not have permission to access a specific branch, that branch is skipped.</span></span> <span data-ttu-id="0ac98-111">これには、他のユーザーが所有する [個人用レポート] フォルダー、および通常アクセスできない他のフォルダーが該当します。</span><span class="sxs-lookup"><span data-stu-id="0ac98-111">This applies to My Reports folders that belong to other users, and to other folders that are not generally available.</span></span> <span data-ttu-id="0ac98-112">検索結果には、表示権限のあるレポートやアイテムのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ac98-112">Only reports and items that you have permission to view are included in the search results.</span></span>  
  
-   <span data-ttu-id="0ac98-113">名前や説明からアイテムを検索するには、検索したいテキストのすべてまたは一部を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ac98-113">To search for an item by name or description, specify all or part of the text that you want to match.</span></span> <span data-ttu-id="0ac98-114">検索文字列の大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="0ac98-114">The search string is not case-sensitive.</span></span> <span data-ttu-id="0ac98-115">検索条件の指定や除外を行う正符号 (+) や負符号 (-) などの検索演算子は使用できません。</span><span class="sxs-lookup"><span data-stu-id="0ac98-115">You cannot use search operators such as plus (+) or minus (-) symbols to require or exclude search criteria.</span></span>  
  
-   <span data-ttu-id="0ac98-116">レポート内の特定のテキストを検索するには、レポートの最上部にあるツール バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ac98-116">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0ac98-117">参照</span><span class="sxs-lookup"><span data-stu-id="0ac98-117">See Also</span></span>  
 <span data-ttu-id="0ac98-118">[レポートマネージャー &#40;レポートビルダーおよび SSRS&#41;でのレポートの検索と表示](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ac98-118">[Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ac98-119">[個人用レポート &#40;レポートビルダーおよび SSRS&#41;の使用](using-my-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ac98-119">[Using My Reports &#40;Report Builder and SSRS&#41;](using-my-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ac98-120">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ac98-120">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0ac98-121">レポートを開閉する &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="0ac98-121">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)  
  
  

---
title: レポートを開閉する (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- opening reports
- closing reports
- reports [Reporting Services], opening
ms.assetid: a9db1caf-1e7d-41ee-9aed-e09fd0712f9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae9da3f95b7d754d16648e6b6a78ddfa39a499c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633746"
---
# <a name="open-and-close-a-report-report-manager"></a><span data-ttu-id="a19ea-102">レポートを開閉する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="a19ea-102">Open and Close a Report (Report Manager)</span></span>
  <span data-ttu-id="a19ea-103">レポート サーバーにパブリッシュされたレポートは、レポート マネージャーを使って閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="a19ea-103">You can use Report Manager to view reports that have been published to a report server.</span></span> <span data-ttu-id="a19ea-104">既定では、すべてのレポートが HTML 形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="a19ea-104">By default, all reports open in HTML.</span></span> <span data-ttu-id="a19ea-105">開いたレポートをエクスポートすることにより、他のアプリケーションの形式で閲覧することもできます。</span><span class="sxs-lookup"><span data-stu-id="a19ea-105">After a report is open, you can export it to view it in other application formats.</span></span> <span data-ttu-id="a19ea-106">対話機能を持ったレポートや対話型データを含んだレポート ビルダーのレポートでは、リンクをクリックして追加のレポートまたはデータを閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="a19ea-106">If the report contains interactive features or if it is a Report Builder report that contains interactive data, you can click the links to view additional reports or data.</span></span>  
  
### <a name="to-view-a-report"></a><span data-ttu-id="a19ea-107">レポートを表示するには</span><span class="sxs-lookup"><span data-stu-id="a19ea-107">To view a report</span></span>  
  
1.  <span data-ttu-id="a19ea-108">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="a19ea-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="a19ea-109">フォルダーを参照するか、名前を指定して検索し、レポートを見つけます。</span><span class="sxs-lookup"><span data-stu-id="a19ea-109">Find a report by browsing folders or searching for a report by name.</span></span> <span data-ttu-id="a19ea-110">**[コンテンツ]** ページのフォルダー名またはフォルダー アイコンをクリックして、フォルダーのコンテンツを参照します。</span><span class="sxs-lookup"><span data-stu-id="a19ea-110">Browse folder contents by clicking a folder name or folder icon in the **Contents** page.</span></span> <span data-ttu-id="a19ea-111">ページの先頭にある **[検索]** ボックスにレポート名の全部または一部を入力して、レポートを検索します。</span><span class="sxs-lookup"><span data-stu-id="a19ea-111">Search for a report by typing all or part of the report name in the **Search for** text box at the top of the page.</span></span>  
  
3.  <span data-ttu-id="a19ea-112">レポートを表示するには、レポート名またはアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a19ea-112">To view a report, click a report name or an icon.</span></span> <span data-ttu-id="a19ea-113">次のアイコンがレポートを表します。</span><span class="sxs-lookup"><span data-stu-id="a19ea-113">The following icon indicates a report:</span></span>  
  
     <span data-ttu-id="a19ea-114">![[レポート] アイコン](../media/hlp-16doc.gif "[レポート] アイコン")</span><span class="sxs-lookup"><span data-stu-id="a19ea-114">![Report icon](../media/hlp-16doc.gif "Report icon")</span></span>  
  
     <span data-ttu-id="a19ea-115">一部のレポートでは、ユーザー名とパスワードまたはパラメーター値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a19ea-115">Some reports require you to provide either a user name and password or a parameter value</span></span>  
  
4.  <span data-ttu-id="a19ea-116">レポートを閉じるには、レポート マネージャーを終了するか、別のページまたはフォルダーを参照します (たとえば、 **[戻る]** をクリックするか、またはページの先頭にあるフォルダー リンクをクリックします)。</span><span class="sxs-lookup"><span data-stu-id="a19ea-116">To close the report, close Report Manager or browse to another page or folder (for example, by clicking the **Back** button or clicking a folder link at the top of the page).</span></span>  
  
     <span data-ttu-id="a19ea-117">レポートを閉じても、レポートはブラウザーのキャッシュから削除されません。</span><span class="sxs-lookup"><span data-stu-id="a19ea-117">Closing a report does not remove it from the browser cache.</span></span> <span data-ttu-id="a19ea-118">レポートへの接続を切断するには、ブラウザーを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a19ea-118">You must close the browser to disconnect the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19ea-119">参照</span><span class="sxs-lookup"><span data-stu-id="a19ea-119">See Also</span></span>  
 <span data-ttu-id="a19ea-120">[レポートやその他のアイテム &#40;レポートビルダーおよび SSRS&#41;を検索する](../report-builder/searching-for-reports-and-other-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a19ea-120">[Searching for Reports and Other Items &#40;Report Builder  and SSRS&#41;](../report-builder/searching-for-reports-and-other-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a19ea-121">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a19ea-121">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="a19ea-122">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a19ea-122">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a19ea-123">レポート サーバー コンテンツの管理 &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="a19ea-123">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](../report-server/report-server-content-management-ssrs-native-mode.md)  
  
  

---
title: レポートのレポート サーバーへの保存 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48dfef01-ed8c-4f23-90c3-de67c90a97dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d80e35c447593e89d422e72ea31ec6be34c3619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739432"
---
# <a name="save-reports-to-a-report-server-report-builder"></a><span data-ttu-id="e2688-102">レポートのレポート サーバーへの保存 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="e2688-102">Save Reports to a Report Server (Report Builder)</span></span>
  <span data-ttu-id="e2688-103">レポート ビルダーでは、レポート定義をレポート サーバーに保存できます (レポートのパブリッシュとも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="e2688-103">In Report Builder, you can save a report definition to a report server (also known as publishing a report).</span></span> <span data-ttu-id="e2688-104">レポート サーバーにレポートを保存すると、他のユーザーがレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e2688-104">When the report is saved to a report server, other users can view the report.</span></span> <span data-ttu-id="e2688-105">パブリッシュしたレポートを実行するたびに最新のデータが取得されます。</span><span class="sxs-lookup"><span data-stu-id="e2688-105">Each time you run the published report, you will retrieve the most current data.</span></span> <span data-ttu-id="e2688-106">表示されたレポートの静的コピーを保存するには、レポートを他のファイル形式にエクスポートし、それを保存するか、またはレポート履歴機能を使用して、表示されたレポートのバージョンを保存します。</span><span class="sxs-lookup"><span data-stu-id="e2688-106">To save a static copy of a rendered report, export the report to a different file format and save it or use the report history feature to save versions of rendered reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2688-107">レポート定義の保存場所は、レポートのプレビュー時に、レポートがサーバー上で処理されるか、ローカルで処理されるかに影響しません。</span><span class="sxs-lookup"><span data-stu-id="e2688-107">The location of the saved report definition does not affect whether the report is processed on the server or processed locally when you preview the report.</span></span>  
  
### <a name="to-save-a-report-to-a-report-server"></a><span data-ttu-id="e2688-108">レポートをレポート サーバーに保存するには</span><span class="sxs-lookup"><span data-stu-id="e2688-108">To save a report to a report server</span></span>  
  
1.  <span data-ttu-id="e2688-109">レポート ビルダーのボタンの **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2688-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="e2688-110">[**名前を付けて保存** _\<Report Item\>_ ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2688-110">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2688-111">レポートを再保存すると、自動的に以前の場所に再保存されます。</span><span class="sxs-lookup"><span data-stu-id="e2688-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="e2688-112">場所を変更するには、[名前を付けて保存] を使用します。</span><span class="sxs-lookup"><span data-stu-id="e2688-112">Use the Save As option to change location.</span></span>  
  
2.  <span data-ttu-id="e2688-113">必要に応じて、 **[最近使ったサイトとサーバー]** をクリックし、最近使用したレポート サーバーと SharePoint サイトの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="e2688-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="e2688-114">レポートを保存するレポート サーバーの場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="e2688-114">Browse to the report server location where you want to save the report.</span></span>  
  
4.  <span data-ttu-id="e2688-115">**[名前]** ボックスに、レポートの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e2688-115">In **Name**, type the name of the report.</span></span>  
  
5.  <span data-ttu-id="e2688-116">**[アイテムの種類]** で、保存するレポート アイテムの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2688-116">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="e2688-117">レポートの種類はレポート (\*.rdl) です。</span><span class="sxs-lookup"><span data-stu-id="e2688-117">The type for reports is Reports(\*.rdl).</span></span>  
  
### <a name="to-save-a-report-as-a-different-name"></a><span data-ttu-id="e2688-118">レポートを別の名前で保存するには</span><span class="sxs-lookup"><span data-stu-id="e2688-118">To save a report as a different name</span></span>  
  
1.  <span data-ttu-id="e2688-119">レポート ビルダー のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2688-119">From the Report Builder button, click **Save As**.</span></span> <span data-ttu-id="e2688-120">[**名前を付けて保存** _\<Report Item\>_ ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2688-120">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e2688-121">レポートを保存するレポート サーバーの場所またはファイル共有を参照します。</span><span class="sxs-lookup"><span data-stu-id="e2688-121">Browse to the report server location or to the file share where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="e2688-122">**[名前]** ボックスに、レポートの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e2688-122">In **Name**, type the name of the report.</span></span>  
  
4.  <span data-ttu-id="e2688-123">**[アイテムの種類]** で、保存するレポート アイテムの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2688-123">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="e2688-124">レポートの種類はレポート (\*.rdl) です。</span><span class="sxs-lookup"><span data-stu-id="e2688-124">The type for reports is Reports(\*.rdl).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2688-125">参照</span><span class="sxs-lookup"><span data-stu-id="e2688-125">See Also</span></span>  
 <span data-ttu-id="e2688-126">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e2688-126">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e2688-127">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e2688-127">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e2688-128">[レポートの保存 &#40;レポートビルダー&#41;](saving-reports-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e2688-128">[Saving Reports &#40;Report Builder&#41;](saving-reports-report-builder.md) </span></span>  
 [<span data-ttu-id="e2688-129">別の種類のファイルとしてレポートをエクスポートする &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e2688-129">Export a Report as Another File Type &#40;Report Builder and SSRS&#41;</span></span>](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)  
  
  

---
title: '[レポートビルダーのオプション] ダイアログボックスの [設定] (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10427"
ms.assetid: 423360de-9bed-462e-921f-60a5abab004f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07bd4a7f9dfe1abd8ab76765cb1ac10ff5227066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633776"
---
# <a name="report-builder-options-dialog-box-settings-report-builder"></a><span data-ttu-id="5b1cc-102">[設定] (レポート ビルダーの [オプション] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="5b1cc-102">Report Builder Options Dialog Box, Settings (Report Builder)</span></span>
  <span data-ttu-id="5b1cc-103">[**レポートビルダー** ] ボタンをクリックし、[**オプション**] をクリックして、最近使用したファイルと接続の表示オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-103">Click the **Report Builder** button and then click **Options** to set options for showing recent files and connections.</span></span> <span data-ttu-id="5b1cc-104">既定のレポート サーバーを変更することも、既定のレポート サーバーがなければ追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-104">You can also change the default report server, or add one if you don't have a default.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="5b1cc-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="5b1cc-105">UI element list</span></span>  
 <span data-ttu-id="5b1cc-106">**[既定で使用するレポート サーバーまたは SharePoint サイト]**</span><span class="sxs-lookup"><span data-stu-id="5b1cc-106">**Use this report server or SharePoint site by default**</span></span>  
 <span data-ttu-id="5b1cc-107">このオプションは、管理者によって設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-107">Your administrator may have configured this.</span></span> <span data-ttu-id="5b1cc-108">値には、 http:// または https:// で始まる整形式の URL を設定できます。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-108">The value can be a well-formed URL starting with http:// or https://.</span></span> <span data-ttu-id="5b1cc-109">この設定によって、テーブル/マトリックス ウィザードやグラフ ウィザードで既定で表示されるデータ ソース接続が決まります。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-109">This setting determines which data source connections appear by default in the Table/Matrix and Chart wizards.</span></span> <span data-ttu-id="5b1cc-110">また、レポートはこのサーバーで処理され、このサーバーのリソースを参照できます。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-110">In addition, your reports will be processed on this server and you can reference resources from this server.</span></span>  
  
 <span data-ttu-id="5b1cc-111">別のレポート サーバーを選択した場合、変更を有効にするにはレポート ビルダーの再起動が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-111">If you select a different report server, you may need to restart Report Builder in order for this change to take affect.</span></span>  
  
 <span data-ttu-id="5b1cc-112">**[既定でレポート パーツをパブリッシュするフォルダー]**</span><span class="sxs-lookup"><span data-stu-id="5b1cc-112">**Publish report parts to this folder by default**</span></span>  
 <span data-ttu-id="5b1cc-113">レポート ビルダーは、パブリッシュされたレポート パーツをこのフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-113">Report Builder will save report parts that you publish to this folder.</span></span> <span data-ttu-id="5b1cc-114">フォルダーが存在せず、レポート サーバー上にフォルダーを作成する権限がある場合は、レポート ビルダーによってフォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-114">If the folder does not exist yet and you have permissions to create folders on the report server, Report Builder will create this folder.</span></span>  
  
 <span data-ttu-id="5b1cc-115">この設定を有効にするためにレポート ビルダーを再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-115">You do not need to restart Report Builder for this setting to take effect.</span></span>  
  
 <span data-ttu-id="5b1cc-116">**[表示する最近使ったサイトおよびサーバーの数]**</span><span class="sxs-lookup"><span data-stu-id="5b1cc-116">**Show this number of recent sites and servers**</span></span>  
 <span data-ttu-id="5b1cc-117">**[レポートを開く]** ダイアログ ボックスおよび **[レポートとして保存]** ダイアログ ボックスに表示する最近使ったサイトと接続の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-117">Specify the number of recent sites and connections to show in the **Open Report** and **Save As Report** dialog boxes.</span></span>  
  
 <span data-ttu-id="5b1cc-118">**[表示する最近使った共有データセットとデータ ソース接続の数]**</span><span class="sxs-lookup"><span data-stu-id="5b1cc-118">**Show this number of recent shared datasets and data source connections**</span></span>  
 <span data-ttu-id="5b1cc-119">**[データセットのプロパティ]** ダイアログ ボックスと、データ領域ウィザードの **[データ ソースへの接続の選択]** ページに表示される、最近使った共有データセットとデータ ソース接続の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-119">Specify the number of recent shared datasets and data source connections to show in the **Dataset Properties** dialog box and the **Choose a connection to a data source** page of the Data Regions Wizard.</span></span>  
  
 <span data-ttu-id="5b1cc-120">**[表示する最近使ったドキュメントの数]**</span><span class="sxs-lookup"><span data-stu-id="5b1cc-120">**Show this number of recent documents**</span></span>  
 <span data-ttu-id="5b1cc-121">[レポート ビルダー] ボタンをクリックしたときに表示する最近使ったドキュメントの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-121">Specify the number of recent documents to show when you click the Report Builder button.</span></span>  
  
 <span data-ttu-id="5b1cc-122">**[最近使ったすべてのアイテムの一覧をクリア]**</span><span class="sxs-lookup"><span data-stu-id="5b1cc-122">**Clear all recent item lists**</span></span>  
 <span data-ttu-id="5b1cc-123">最近使ったサイトとサーバー、共有データセット、共有データ ソース接続、およびドキュメントの現在の一覧をクリアします。</span><span class="sxs-lookup"><span data-stu-id="5b1cc-123">Clear the current lists of recent sites and servers, shared datasets, shared data source connections, and documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b1cc-124">参照</span><span class="sxs-lookup"><span data-stu-id="5b1cc-124">See Also</span></span>  
 [<span data-ttu-id="5b1cc-125">レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ</span><span class="sxs-lookup"><span data-stu-id="5b1cc-125">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  

---
title: '[取得] ダイアログボックス (ソース管理) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.GetVersionDialog
helpviewer_keywords:
- Get dialog box
ms.assetid: 048564d3-6c58-405b-8b57-b690fbfdbe9e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d949a649a35ee3c5a6521223d45975b7c372aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645796"
---
# <a name="get-dialog-box-source-control"></a><span data-ttu-id="30dff-102">[取得] ダイアログ ボックス ([ソース管理])</span><span class="sxs-lookup"><span data-stu-id="30dff-102">Get Dialog Box (Source Control)</span></span>
  <span data-ttu-id="30dff-103">選択した項目の読み取り専用コピーをソース管理データベースから取得して、作業フォルダーまたはその他の指定のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="30dff-103">Retrieves a read-only copy of the selected item from the source control database to your working folder, or another folder that you specify.</span></span>  
  
## <a name="dialog-box-access"></a><span data-ttu-id="30dff-104">ダイアログ ボックスの表示</span><span class="sxs-lookup"><span data-stu-id="30dff-104">Dialog Box Access</span></span>  
 <span data-ttu-id="30dff-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のソリューション エクスプローラーで、項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="30dff-105">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], select an item in Solution Explorer.</span></span> <span data-ttu-id="30dff-106">[**ファイル**] メニューの [**ソース管理] を**クリックし、[**取得**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30dff-106">On the **File** menu, click **Source Control,** then click **Get**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30dff-107">ソリューション エクスプローラーで項目を右クリックしても、このダイアログ ボックスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="30dff-107">This dialog box is also available by right-clicking the item in Solution Explorer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="30dff-108">Options</span><span class="sxs-lookup"><span data-stu-id="30dff-108">Options</span></span>  
 <span data-ttu-id="30dff-109">**操作**</span><span class="sxs-lookup"><span data-stu-id="30dff-109">**Action**</span></span>  
 <span data-ttu-id="30dff-110">取得する項目に対して実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="30dff-110">Specifies the action being performed on the items to retrieve.</span></span>  
  
 <span data-ttu-id="30dff-111">**[列]**</span><span class="sxs-lookup"><span data-stu-id="30dff-111">**Columns**</span></span>  
 <span data-ttu-id="30dff-112">表示する列とその表示順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="30dff-112">Identifies columns to display and the order in which they are displayed.</span></span>  
  
 <span data-ttu-id="30dff-113">**[平面表示]**</span><span class="sxs-lookup"><span data-stu-id="30dff-113">**Flat View**</span></span>  
 <span data-ttu-id="30dff-114">取得するファイルをソース管理接続の下に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="30dff-114">Display the files you are retrieving as flat lists under their source control connection.</span></span>  
  
 <span data-ttu-id="30dff-115">**更新時刻**</span><span class="sxs-lookup"><span data-stu-id="30dff-115">**Modified Time**</span></span>  
 <span data-ttu-id="30dff-116">項目が最後に変更された時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="30dff-116">Displays the time when an item was last modified.</span></span>  
  
 <span data-ttu-id="30dff-117">**名前**</span><span class="sxs-lookup"><span data-stu-id="30dff-117">**Name**</span></span>  
 <span data-ttu-id="30dff-118">取得する項目の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="30dff-118">Display the names of the items to retrieve.</span></span> <span data-ttu-id="30dff-119">選択した項目の横にチェックボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30dff-119">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="30dff-120">特定の項目を取得しない場合は、そのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="30dff-120">If you do not want to retrieve a particular item, clear its check box.</span></span>  
  
 <span data-ttu-id="30dff-121">**Options**</span><span class="sxs-lookup"><span data-stu-id="30dff-121">**Options**</span></span>  
 <span data-ttu-id="30dff-122">ボタンの右側の矢印をクリックすると、Source Safe のプラグインに固有の取得オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30dff-122">Displays source safe plug-in-specific get options when the arrow to the right of the button is clicked.</span></span>  
  
 <span data-ttu-id="30dff-123">**Sort**</span><span class="sxs-lookup"><span data-stu-id="30dff-123">**Sort**</span></span>  
 <span data-ttu-id="30dff-124">表示する列の順序を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="30dff-124">Sort the order of the displayed columns.</span></span>  
  
 <span data-ttu-id="30dff-125">**ツリービュー**</span><span class="sxs-lookup"><span data-stu-id="30dff-125">**Tree View**</span></span>  
 <span data-ttu-id="30dff-126">取得する項目のフォルダーおよびファイル階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="30dff-126">Display the folder and file hierarchy for the items you are retrieving.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dff-127">参照</span><span class="sxs-lookup"><span data-stu-id="30dff-127">See Also</span></span>  
 <span data-ttu-id="30dff-128">[ファイルの取得](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="30dff-128">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="30dff-129">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="30dff-129">Solution Explorer Source Control</span></span>](../../2014/database-engine/solution-explorer-source-control.md)  
  
  

---
title: チェックアウトを元に戻す |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ff6e6041b59caa75bf7f8530d915db48e0379338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632057"
---
# <a name="undo-checkouts"></a><span data-ttu-id="4e4e0-102">チェックアウトの取り消し</span><span class="sxs-lookup"><span data-stu-id="4e4e0-102">Undo Checkouts</span></span>
  <span data-ttu-id="4e4e0-103">[**チェックアウトの取り消し**] コマンドを使用すると、既存のチェックアウトを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-103">You can use the **Undo Checkout** command to cancel an existing checkout.</span></span> <span data-ttu-id="4e4e0-104">この機能は、ファイルを変更して保存した後に、その変更をロールバックする必要が生じた場合などに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-104">This is particularly useful when you have modified and saved a file, and then later need to roll back your changes.</span></span>  
  
 <span data-ttu-id="4e4e0-105">[**チェックアウトの取り消しの詳細オプション**] ダイアログボックスで設定したオプションに応じて、Studio 環境では、項目の作業コピーをローカルディスクに残しておくか、ソース管理された最新のバージョンに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-105">Depending on the options you set in the **Undo Checkout Advanced Options** dialog box, the Studio environment either leaves the working copy of the item on your local disk or replaces it with the latest source-controlled version.</span></span> <span data-ttu-id="4e4e0-106">他のユーザーがソース管理システムのコンテキスト外で項目を修正した場合は、最新バージョンを取得できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-106">If someone has modified the item outside the context of the source control system, the retrieved version may not be the latest one.</span></span>  
  
### <a name="to-undo-a-checkout"></a><span data-ttu-id="4e4e0-107">チェックアウトを元に戻すには</span><span class="sxs-lookup"><span data-stu-id="4e4e0-107">To undo a checkout</span></span>  
  
1.  <span data-ttu-id="4e4e0-108">ソリューション エクスプローラーでプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="4e4e0-109">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**チェックアウトの取り消し**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-109">On the **File** menu, point to **Source Control**, and then click **Undo Checkout**.</span></span>  
  
3.  <span data-ttu-id="4e4e0-110">[**チェックアウトの取り消し**] ダイアログボックスで、適切なオプションを選択し、[**チェックアウトの取り消し**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-110">In the **Undo Checkout** dialog box, select the appropriate options, and then click the **Undo Checkout** button.</span></span>  
  
     <span data-ttu-id="4e4e0-111">**[列]**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-111">**Columns**</span></span>  
     <span data-ttu-id="4e4e0-112">表示する列と、その表示順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-112">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="4e4e0-113">**[平面表示]**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-113">**Flat View**</span></span>  
     <span data-ttu-id="4e4e0-114">項目をソース管理接続の下に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-114">Display the items as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="4e4e0-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-115">**Name**</span></span>  
     <span data-ttu-id="4e4e0-116">チェックアウトを取り消す項目の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-116">Displays the names of the items for which to undo the checkout.</span></span> <span data-ttu-id="4e4e0-117">選択した項目の横にチェックボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-117">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="4e4e0-118">項目のチェックアウトを取り消さない場合は、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-118">If you do not want to undo the checkout of an item, clear its check box.</span></span>  
  
     <span data-ttu-id="4e4e0-119">**Options**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-119">**Options**</span></span>  
     <span data-ttu-id="4e4e0-120">ボタンの右側の矢印をクリックすると、ソース管理のプラグインに固有のチェックアウトの取り消しオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-120">Displays source control plug-in-specific undo checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="4e4e0-121">**Sort**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-121">**Sort**</span></span>  
     <span data-ttu-id="4e4e0-122">表示列の順序を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-122">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="4e4e0-123">**ツリービュー**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-123">**Tree View**</span></span>  
     <span data-ttu-id="4e4e0-124">チェックアウトを元に戻す項目のフォルダーおよび項目階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-124">Display the folder and item hierarchy for items on which you are reversing the checkout.</span></span>  
  
     <span data-ttu-id="4e4e0-125">**[チェックアウトの取り消し]**</span><span class="sxs-lookup"><span data-stu-id="4e4e0-125">**Undo Checkout**</span></span>  
     <span data-ttu-id="4e4e0-126">チェックアウトを元に戻して、チェックアウトされたファイルに対する変更を破棄します。</span><span class="sxs-lookup"><span data-stu-id="4e4e0-126">Revert the checkout, discarding any changes to the checked-out file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e4e0-127">参照</span><span class="sxs-lookup"><span data-stu-id="4e4e0-127">See Also</span></span>  
 <span data-ttu-id="4e4e0-128">[ファイルのチェックアウト](../../2014/database-engine/check-out-files.md) </span><span class="sxs-lookup"><span data-stu-id="4e4e0-128">[Check Out Files](../../2014/database-engine/check-out-files.md) </span></span>  
 [<span data-ttu-id="4e4e0-129">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="4e4e0-129">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  

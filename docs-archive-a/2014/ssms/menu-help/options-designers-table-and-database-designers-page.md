---
title: '[オプション] ([デザイナー]/[テーブルおよびデータベースデザイナー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Designers.Table_Designer
ms.assetid: b43f4b97-17b9-4004-a824-f77b9e145741
author: stevestein
ms.author: sstein
ms.openlocfilehash: d8a1218b4ea1ae9c6f9cf734bb33a2a4bebcb167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643065"
---
# <a name="options-designers-table-and-database-designers-page"></a><span data-ttu-id="8d1c2-102">[オプション] ([デザイナー]/[テーブルおよびデータベースデザイナー] ページ)</span><span class="sxs-lookup"><span data-stu-id="8d1c2-102">Options (Designers-Table and Database Designers Page)</span></span>
  <span data-ttu-id="8d1c2-103">このページを使用すると、デザイナーの既定の動作を設定できます。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-103">Use this page to determine the default behavior of the designer.</span></span> <span data-ttu-id="8d1c2-104">この設定にアクセスするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[デザイナー]** フォルダーを展開して、 **[テーブル デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-104">To access the settings, on the **Tools** menu, click **Options**, expand the **Designers** folder, and click **Table Designer**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="8d1c2-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="8d1c2-105">UI element list</span></span>  
 <span data-ttu-id="8d1c2-106">**[テーブル デザイナーの更新のために接続文字列のタイムアウト値をオーバーライドする]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-106">**Override connection string time-out value for table designer updates**</span></span>  
 <span data-ttu-id="8d1c2-107">テーブル デザイナーの処理に新しいタイムアウト値を設定することを許可します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-107">Permits a new time-out value to be set for the actions of the table designer.</span></span> <span data-ttu-id="8d1c2-108">テーブル デザイナーで大きなテーブルを処理する必要があり、テーブルの変更に時間がかかる場合に、この設定が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-108">This can be useful when the table designer affects a large table and requires extra time to complete the table modification.</span></span>  
  
 <span data-ttu-id="8d1c2-109">**[トランザクションがタイムアウトするまでの時間]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-109">**Transaction time-out after**</span></span>  
 <span data-ttu-id="8d1c2-110">テーブル デザイナーのタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-110">Sets a time-out value for the table designer.</span></span>  
  
 <span data-ttu-id="8d1c2-111">**[変更スクリプトの自動生成]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-111">**Auto generate change scripts**</span></span>  
 <span data-ttu-id="8d1c2-112">テーブル デザイナーで定義された変更を実装するためのスクリプトを自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-112">Automatically creates a script to implement the changes defined in the table designer.</span></span>  
  
 <span data-ttu-id="8d1c2-113">**[Null の主キーに関する警告]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-113">**Warn on null primary keys**</span></span>  
 <span data-ttu-id="8d1c2-114">主キー用に選択したフィールドで NULL 値を格納できる場合に、警告ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-114">Provides a warning dialog box when a field that is selected for a primary key can contain null values.</span></span>  
  
 <span data-ttu-id="8d1c2-115">**[相違点の検出に関する警告]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-115">**Warn about difference detection**</span></span>  
 <span data-ttu-id="8d1c2-116">このチェック ボックスをオンにした場合、変更の保存時に、ユーザーが行った変更と別のユーザーが行った変更との間で発生したすべての競合がメッセージ ボックスに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-116">If you check this box, when you save the changes, a message box will list any conflicts between your changes and changes that were made by another user.</span></span>  
  
 <span data-ttu-id="8d1c2-117">**[該当テーブルに関する警告]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-117">**Warn about tables affected**</span></span>  
 <span data-ttu-id="8d1c2-118">警告ダイアログ ボックスを開き、操作の影響を受けるテーブルを一覧表示し、確認を求めるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-118">Provides a warning dialog box that lists the tables to be affected by the action and prompts for confirmation.</span></span>  
  
 <span data-ttu-id="8d1c2-119">**[テーブルの再作成を必要とする変更を保存できないようにする]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-119">**Prevent saving changes that require table re-creation**</span></span>  
 <span data-ttu-id="8d1c2-120">テーブルの再作成を必要とする変更を行うことができないようにします。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-120">Prevents a user from making changes that require re-creating the table.</span></span> <span data-ttu-id="8d1c2-121">次の操作を行うには、テーブルを再作成する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-121">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="8d1c2-122">新しい列をテーブルの中央に追加する。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-122">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="8d1c2-123">列を削除する。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-123">Dropping a column</span></span>  
  
-   <span data-ttu-id="8d1c2-124">列の NULL 値許容属性を変更する。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-124">Changing column nullability</span></span>  
  
-   <span data-ttu-id="8d1c2-125">列の順序を変更する。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-125">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="8d1c2-126">列のデータ型を変更する</span><span class="sxs-lookup"><span data-stu-id="8d1c2-126">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="8d1c2-127">**[既定のテーブル ビュー]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-127">**Default table view**</span></span>  
 <span data-ttu-id="8d1c2-128">デザイナーでテーブルを表示する方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-128">Select the way you want to see tables in the designers:</span></span>  
  
-   <span data-ttu-id="8d1c2-129">**Standard**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-129">**Standard**</span></span>  
  
     <span data-ttu-id="8d1c2-130">テーブル ヘッダー、すべての列名、データ型、[NULL を許容] 設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-130">Shows the table header, all column names, data types, and the Allow Nulls setting.</span></span>  
  
-   <span data-ttu-id="8d1c2-131">**[列名]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-131">**Column Names**</span></span>  
  
     <span data-ttu-id="8d1c2-132">列名を表示します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-132">Shows the column names.</span></span>  
  
-   <span data-ttu-id="8d1c2-133">**[キー]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-133">**Key**</span></span>  
  
     <span data-ttu-id="8d1c2-134">テーブル ヘッダーと主キー列を表示します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-134">Shows the table header and the primary key columns.</span></span>  
  
-   <span data-ttu-id="8d1c2-135">**[テーブル名のみ]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-135">**Name Only**</span></span>  
  
     <span data-ttu-id="8d1c2-136">テーブルのヘッダーと名前のみ表示します。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-136">Shows only the table header with it's name.</span></span>  
  
-   <span data-ttu-id="8d1c2-137">**Custom**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-137">**Custom**</span></span>  
  
     <span data-ttu-id="8d1c2-138">表示する列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-138">Allows you to choose which columns to view.</span></span>  
  
 <span data-ttu-id="8d1c2-139">**[新しいダイアグラムで [テーブルの追加] ダイアログを起動する]**</span><span class="sxs-lookup"><span data-stu-id="8d1c2-139">**Launch add table dialog on new diagram**</span></span>  
 <span data-ttu-id="8d1c2-140">デザイナーを開いたときに、 **[テーブルの追加]** ダイアログ ボックスを自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="8d1c2-140">Automatically opens the **Add Table** dialog box when the designers open.</span></span>  
  
  

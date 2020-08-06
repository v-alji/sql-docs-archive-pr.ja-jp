---
title: '[テーブルのプロパティの編集] ダイアログボックス (SSAS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6664d244f5f653610b37bd628abdb2263e015c0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644202"
---
# <a name="edit-table-properties-dialog-box-ssas"></a><span data-ttu-id="0be88-102">[テーブルのプロパティの編集] ダイアログ ボックス (SSAS)</span><span class="sxs-lookup"><span data-stu-id="0be88-102">Edit Table Properties Dialog Box (SSAS)</span></span>
  <span data-ttu-id="0be88-103">**[テーブルのプロパティの編集]** ダイアログ ボックスを使用すると、テーブルのインポート ウィザードを使用してモデル デザイナーにインポートされたテーブルのプロパティを表示して変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="0be88-103">The **Edit Table Properties** dialog box enables you to view and modify the properties of tables that are imported into the model designer by using the Table Import Wizard.</span></span> <span data-ttu-id="0be88-104">このダイアログ ボックスにアクセスするには、モデル デザイナーでテーブルを選択し、 **[テーブル]** メニュー、 **[テーブルのプロパティ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0be88-104">To access this dialog box, in the model designer, select a table, then click the **Table** menu, and then click **Table Properties**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="0be88-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="0be88-105">UI element list</span></span>  
 <span data-ttu-id="0be88-106">このダイアログ ボックスのオプションは、最初にデータをインポートしたときに一覧からテーブルを選択したか SQL クエリを使用したかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0be88-106">The options for this dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span>  
  
## <a name="table-preview-mode"></a><span data-ttu-id="0be88-107">テーブルのプレビュー モード</span><span class="sxs-lookup"><span data-stu-id="0be88-107">Table Preview Mode</span></span>  
 <span data-ttu-id="0be88-108">**[テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="0be88-108">**Table name**</span></span>  
 <span data-ttu-id="0be88-109">モデル内のデータ テーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-109">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0be88-110">ここで名前を編集することはできません。</span><span class="sxs-lookup"><span data-stu-id="0be88-110">You cannot edit the name here.</span></span> <span data-ttu-id="0be88-111">テーブル名は、モデル デザイナーの下部にあるテーブル タブを右クリックして変更できます。</span><span class="sxs-lookup"><span data-stu-id="0be88-111">However, you can change the name of the table by right-clicking the table tab at the bottom of the model designer.</span></span>  
  
 <span data-ttu-id="0be88-112">**接続名**</span><span class="sxs-lookup"><span data-stu-id="0be88-112">**Connection name**</span></span>  
 <span data-ttu-id="0be88-113">現在使用している接続の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-113">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="0be88-114">**ソース名**</span><span class="sxs-lookup"><span data-stu-id="0be88-114">**Source name**</span></span>  
 <span data-ttu-id="0be88-115">データの取得先のテーブルが表示されます。変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0be88-115">Display or change the table from which the data is obtained.</span></span>  
  
 <span data-ttu-id="0be88-116">現在のテーブルと異なる列を持つテーブルにソースを変更すると、列が異なることを示す警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-116">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="0be88-117">現在のテーブルに含める列を選択し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0be88-117">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="0be88-118">テーブルの左側にあるチェック ボックスをオンにすると、テーブル全体を置換できます。</span><span class="sxs-lookup"><span data-stu-id="0be88-118">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0be88-119">テーブルのデータ ソースを変更すると、事実上、現在のテーブルの内容が、新しいソース テーブルの内容で置換されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-119">When you change the data source of a table, you essentially replace the contents of the current table with the contents of the new source table.</span></span>  
  
 <span data-ttu-id="0be88-120">**[列名の取得元]**</span><span class="sxs-lookup"><span data-stu-id="0be88-120">**Column names from**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="0be88-121">**ソース**</span><span class="sxs-lookup"><span data-stu-id="0be88-121">**Source**</span></span>|<span data-ttu-id="0be88-122">選択したソース テーブルの列名で現在の列名を置換します。</span><span class="sxs-lookup"><span data-stu-id="0be88-122">Select this option to replace the current column names with the column names from the selected source table.</span></span>|  
|<span data-ttu-id="0be88-123">**Model**</span><span class="sxs-lookup"><span data-stu-id="0be88-123">**Model**</span></span>|<span data-ttu-id="0be88-124">モデル内に存在する現在の列名を使用します。</span><span class="sxs-lookup"><span data-stu-id="0be88-124">Select this option to use the current column names as they exist in the model.</span></span>|  
  
 <span data-ttu-id="0be88-125">**[プレビューの更新]**</span><span class="sxs-lookup"><span data-stu-id="0be88-125">**Refresh preview**</span></span>  
 <span data-ttu-id="0be88-126">クリックすると、現在選択しているソース テーブルのデータ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-126">Click to view the columns of data in the currently selected source table.</span></span>  
  
 <span data-ttu-id="0be88-127">**[切り替え先]**</span><span class="sxs-lookup"><span data-stu-id="0be88-127">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="0be88-128">**[テーブルのプレビュー]**</span><span class="sxs-lookup"><span data-stu-id="0be88-128">**Table preview**</span></span>|<span data-ttu-id="0be88-129">選択しているテーブルと限定された数行分のデータをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="0be88-129">Select this option to preview the selected table and a limited number of rows of data.</span></span>|  
|<span data-ttu-id="0be88-130">**クエリエディター**</span><span class="sxs-lookup"><span data-stu-id="0be88-130">**Query editor**</span></span>|<span data-ttu-id="0be88-131">選択しているデータ ソースに対するクエリを表示します。</span><span class="sxs-lookup"><span data-stu-id="0be88-131">Select this option to view the query against the selected data source.</span></span> <span data-ttu-id="0be88-132">このオプションは、すべてのデータ ソースで使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="0be88-132">This option is not available for all data sources.</span></span>|  
  
 <span data-ttu-id="0be88-133">**列ヘッダーのチェック ボックス**</span><span class="sxs-lookup"><span data-stu-id="0be88-133">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="0be88-134">列をデータ インポートの対象にする場合は、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0be88-134">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="0be88-135">列をデータ インポートの対象から除外する場合は、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="0be88-135">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="0be88-136">**列ヘッダーの下矢印ボタン**</span><span class="sxs-lookup"><span data-stu-id="0be88-136">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="0be88-137">列のデータをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="0be88-137">Filter data in the column.</span></span>  
  
 <span data-ttu-id="0be88-138">**行フィルターのクリア**</span><span class="sxs-lookup"><span data-stu-id="0be88-138">**Clear row filters**</span></span>  
 <span data-ttu-id="0be88-139">適用されているフィルターをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="0be88-139">Click to remove any filters that have been applied.</span></span>  
  
 <span data-ttu-id="0be88-140">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="0be88-140">**OK**</span></span>  
 <span data-ttu-id="0be88-141">クリックすると、列の置換も含めて、加えたすべての変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-141">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="query-design-mode"></a><span data-ttu-id="0be88-142">クエリ デザイン モード</span><span class="sxs-lookup"><span data-stu-id="0be88-142">Query Design Mode</span></span>  
 <span data-ttu-id="0be88-143">**[テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="0be88-143">**Table name**</span></span>  
 <span data-ttu-id="0be88-144">モデル内のデータ テーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-144">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0be88-145">ここでは名前を編集できませんが、デザイナーの下部にあるテーブル タブを右クリックすると、テーブル名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0be88-145">You cannot edit the name here; however, you can change the name of the table by right-clicking the table tab at the bottom of the designer.</span></span>  
  
 <span data-ttu-id="0be88-146">**接続名**</span><span class="sxs-lookup"><span data-stu-id="0be88-146">**Connection name**</span></span>  
 <span data-ttu-id="0be88-147">現在使用している接続の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-147">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="0be88-148">**[切り替え先]**</span><span class="sxs-lookup"><span data-stu-id="0be88-148">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="0be88-149">**[テーブルのプレビュー]**</span><span class="sxs-lookup"><span data-stu-id="0be88-149">**Table preview**</span></span>|<span data-ttu-id="0be88-150">選択しているテーブルと数行分のデータをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="0be88-150">Select this option to preview the selected table and a few rows of data.</span></span>|  
|<span data-ttu-id="0be88-151">**クエリエディター**</span><span class="sxs-lookup"><span data-stu-id="0be88-151">**Query editor**</span></span>|<span data-ttu-id="0be88-152">選択しているデータ ソースに対して発行されるクエリを表示します。</span><span class="sxs-lookup"><span data-stu-id="0be88-152">Select this option to view the query that will be issued against the selected data source.</span></span>|  
  
 <span data-ttu-id="0be88-153">**Sql ステートメント**</span><span class="sxs-lookup"><span data-stu-id="0be88-153">**Sql statement**</span></span>  
 <span data-ttu-id="0be88-154">行を取得するために、現在のデータ ソースに対して発行された SQL ステートメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-154">Displays the SQL statement that is issued against the current data source to retrieve rows.</span></span> <span data-ttu-id="0be88-155">既定では、すべての行が取得されますが、フィルターをデザインするか、SQL ステートメントを手動で編集することによって、行のサブセットを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="0be88-155">By default, all rows are retrieved, but you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="0be88-156">**検証**</span><span class="sxs-lookup"><span data-stu-id="0be88-156">**Validate**</span></span>  
 <span data-ttu-id="0be88-157">クリックすると、選択しているデータ ソースとプロバイダーについて、ステートメントの構文が正しいかどうかが検証されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-157">Click to verify that the statement is syntactically correct for the selected data source and provider.</span></span>  
  
 <span data-ttu-id="0be88-158">**設計**</span><span class="sxs-lookup"><span data-stu-id="0be88-158">**Design**</span></span>  
 <span data-ttu-id="0be88-159">クリックすると、ビジュアル クエリ デザイナーが開き、クエリ ステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0be88-159">Click to open a visual query designer and build a query statement.</span></span> <span data-ttu-id="0be88-160">デザイナーの使用方法の詳細については、デザイナーで F1 キーを押してください。</span><span class="sxs-lookup"><span data-stu-id="0be88-160">For information about how to use the designer, press F1 from the designer.</span></span>  
  
 <span data-ttu-id="0be88-161">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="0be88-161">**OK**</span></span>  
 <span data-ttu-id="0be88-162">クリックすると、列の置換も含めて、加えたすべての変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="0be88-162">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be88-163">参照</span><span class="sxs-lookup"><span data-stu-id="0be88-163">See Also</span></span>  
 [<span data-ttu-id="0be88-164">テーブルと列 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="0be88-164">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  

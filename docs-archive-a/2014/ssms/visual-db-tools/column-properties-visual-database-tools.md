---
title: '[列のプロパティ] (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6aeb4d01cae7c09c27cafa8284638bf0a7de9691
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711490"
---
# <a name="column-properties-visual-database-tools"></a><span data-ttu-id="c92f5-102">[列のプロパティ] \(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c92f5-102">Column Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="c92f5-103">列のプロパティのセットには、テーブル デザイナーの **[列のプロパティ]** タブに表示される完全なセット ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースでのみ使用可能) と、サーバー エクスプローラーでプロパティ ウィンドウに表示されるサブセットの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="c92f5-103">There are two sets of properties for columns: a full set that you can see in the **Column Properties** tab within Table Designer (available only for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) and a subset you can see in the Properties window using Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c92f5-104">このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。</span><span class="sxs-lookup"><span data-stu-id="c92f5-104">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c92f5-105">使用中の設定やエディションに応じて、表示されるダイアログ ボックスとメニュー コマンドがヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c92f5-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c92f5-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="c92f5-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="c92f5-107">[プロパティ] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="c92f5-107">Properties Window</span></span>  
 <span data-ttu-id="c92f5-108">サーバー エクスプローラーで列を選択したとき、次のプロパティが [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-108">These properties appear in the Properties window when you select a column in Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c92f5-109">これらのプロパティは読み取り専用であり、サーバー エクスプローラーを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-109">These properties, accessed using Server Explorer, are read-only.</span></span> <span data-ttu-id="c92f5-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの列プロパティを編集するには、テーブル デザイナーで列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-110">To edit column properties for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, select the column in Table Designer.</span></span> <span data-ttu-id="c92f5-111">そのプロパティについては、後でこのトピックの中で説明します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-111">Those properties are described later in this topic.</span></span>  
  
 <span data-ttu-id="c92f5-112">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-112">**Identity Category**</span></span>  
 <span data-ttu-id="c92f5-113">展開すると、 **[オブジェクト名]** プロパティと **[データベース]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-113">Expands to show the **Name** and **Database** properties.</span></span>  
  
 <span data-ttu-id="c92f5-114">**Name**</span><span class="sxs-lookup"><span data-stu-id="c92f5-114">**Name**</span></span>  
 <span data-ttu-id="c92f5-115">列の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-115">Shows the name of the column.</span></span>  
  
 <span data-ttu-id="c92f5-116">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-116">**Database**</span></span>  
 <span data-ttu-id="c92f5-117">選択した列のデータ ソースの名前が表示されます</span><span class="sxs-lookup"><span data-stu-id="c92f5-117">Shows the name of the data source for the selected column.</span></span> <span data-ttu-id="c92f5-118">(OLE DB にのみ適用)。</span><span class="sxs-lookup"><span data-stu-id="c92f5-118">(Applies only to OLE DB.)</span></span>  
  
 <span data-ttu-id="c92f5-119">**[その他] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-119">**Misc Category**</span></span>  
 <span data-ttu-id="c92f5-120">展開すると、その他のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-120">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="c92f5-121">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-121">**Data Type**</span></span>  
 <span data-ttu-id="c92f5-122">選択した列のデータ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-122">Shows the data type of the selected column.</span></span> <span data-ttu-id="c92f5-123">詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92f5-123">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="c92f5-124">**[IDENTITY インクリメント]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-124">**Identity Increment**</span></span>  
 <span data-ttu-id="c92f5-125">ID 列の以降の各行で **[IDENTITY シード]** に追加される増分値が表示されます</span><span class="sxs-lookup"><span data-stu-id="c92f5-125">Shows the increment that will be added to the **Identity Seed** for each subsequent row of the identity column.</span></span> <span data-ttu-id="c92f5-126">( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="c92f5-126">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="c92f5-127">**[IDENTITY シード]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-127">**Identity Seed**</span></span>  
 <span data-ttu-id="c92f5-128">テーブル内で ID 列の最初の行に割り当てられるシード値が表示されます</span><span class="sxs-lookup"><span data-stu-id="c92f5-128">Shows the seed value assigned to the first row in the table for the identity column.</span></span> <span data-ttu-id="c92f5-129">( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="c92f5-129">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="c92f5-130">**[Is Identity]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-130">**Is Identity**</span></span>  
 <span data-ttu-id="c92f5-131">選択されている列がテーブルの ID 列であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-131">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="c92f5-132">( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="c92f5-132">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="c92f5-133">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-133">**Length**</span></span>  
 <span data-ttu-id="c92f5-134">文字ベースのデータ型で許容される文字数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-134">Shows the number of characters allowed for character-based data types.</span></span>  
  
 <span data-ttu-id="c92f5-135">**NULL 値の使用**</span><span class="sxs-lookup"><span data-stu-id="c92f5-135">**Nullable**</span></span>  
 <span data-ttu-id="c92f5-136">列で NULL が許容されるかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-136">Shows whether or not the column allows null values.</span></span>  
  
 <span data-ttu-id="c92f5-137">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-137">**Precision**</span></span>  
 <span data-ttu-id="c92f5-138">数値データ型で許容される最大桁数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-138">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="c92f5-139">数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-139">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="c92f5-140">**スケール**</span><span class="sxs-lookup"><span data-stu-id="c92f5-140">**Scale**</span></span>  
 <span data-ttu-id="c92f5-141">数値データ型の小数点の右側にある桁数の最大数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-141">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="c92f5-142">この値は、有効桁数以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c92f5-142">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="c92f5-143">数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-143">This property shows **0** for nonnumeric data types.</span></span>  
  
## <a name="column-properties-tab"></a><span data-ttu-id="c92f5-144">[列のプロパティ] タブ</span><span class="sxs-lookup"><span data-stu-id="c92f5-144">Column Properties Tab</span></span>  
 <span data-ttu-id="c92f5-145">これらのプロパティにアクセスするには、サーバー エクスプローラーで列が属しているテーブルを右クリックした後、 **[テーブル定義を開く]** を選択し、テーブル デザイナーの [テーブル] グリッドで行を選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-145">To access these properties, in Server Explorer right-click the table to which the column belongs, choose **Open Table Definition**, and select the row in the table grid in Table Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c92f5-146">これらのプロパティは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-146">These properties apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c92f5-147">**[全般] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-147">**General Category**</span></span>  
 <span data-ttu-id="c92f5-148">展開すると、 **[オブジェクト名]** 、 **[Null を許容]** 、 **[データ型]** 、 **[既定値またはバインド]** 、 **[長さ]** 、 **[有効桁数]** 、 **[小数点以下桁数]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-148">Expands to show **Name**, **Allow Nulls**, **Data Type**, **Default Value or Binding**, **Length**, **Precision**, and **Scale**.</span></span>  
  
 <span data-ttu-id="c92f5-149">**Name**</span><span class="sxs-lookup"><span data-stu-id="c92f5-149">**Name**</span></span>  
 <span data-ttu-id="c92f5-150">列の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-150">Displays the name of the column.</span></span> <span data-ttu-id="c92f5-151">名前を編集するには、テキスト ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-151">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c92f5-152">既存のクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムからこの列を参照している場合、列の名前を変更すると、そのオブジェクトが無効になります。</span><span class="sxs-lookup"><span data-stu-id="c92f5-152">If existing queries, views, user-defined functions, stored procedures, or programs refer to the column, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="c92f5-153">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-153">**Allow Nulls**</span></span>  
 <span data-ttu-id="c92f5-154">列のデータ型で NULL が許容されるかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-154">Shows whether or not the column's data type allows null values.</span></span>  
  
 <span data-ttu-id="c92f5-155">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-155">**Data Type**</span></span>  
 <span data-ttu-id="c92f5-156">選択した列のデータ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-156">Shows the data type for the selected column.</span></span> <span data-ttu-id="c92f5-157">このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-157">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span> <span data-ttu-id="c92f5-158">詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92f5-158">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="c92f5-159">**[既定値またはバインド]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-159">**Default Value or Binding**</span></span>  
 <span data-ttu-id="c92f5-160">列に値が指定されていない場合の、列の既定値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-160">Shows the default for this column when no value is specified for this column.</span></span> <span data-ttu-id="c92f5-161">このドロップダウン リストに、データ ソースで定義されているグローバル既定値がすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-161">The drop-down list contains all global defaults defined in the data source.</span></span> <span data-ttu-id="c92f5-162">列にグローバル既定値をバインドする場合は、ドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-162">To bind the column to a global default, select from the drop-down list.</span></span> <span data-ttu-id="c92f5-163">列に既定の制約を作成する場合は、既定値をテキストとして直接入力します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-163">Alternatively, to create a default constraint for the column, type the default value directly as text.</span></span>  
  
 <span data-ttu-id="c92f5-164">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-164">**Length**</span></span>  
 <span data-ttu-id="c92f5-165">文字ベースのデータ型で許容される文字数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-165">Shows the number of characters allowed for character-based data types.</span></span> <span data-ttu-id="c92f5-166">このプロパティは、文字に基づくデータ型にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-166">This property is only available for character-based data types.</span></span>  
  
 <span data-ttu-id="c92f5-167">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-167">**Precision**</span></span>  
 <span data-ttu-id="c92f5-168">数値データ型で許容される最大桁数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-168">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="c92f5-169">数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-169">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="c92f5-170">このプロパティは、数値のデータ型にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-170">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="c92f5-171">**スケール**</span><span class="sxs-lookup"><span data-stu-id="c92f5-171">**Scale**</span></span>  
 <span data-ttu-id="c92f5-172">数値データ型の小数点の右側にある桁数の最大数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-172">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="c92f5-173">この値は、有効桁数以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c92f5-173">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="c92f5-174">数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-174">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="c92f5-175">このプロパティは、数値のデータ型にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-175">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="c92f5-176">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-176">**Table Designer Category**</span></span>  
 <span data-ttu-id="c92f5-177">展開すると、その他のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-177">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="c92f5-178">**Collation**</span><span class="sxs-lookup"><span data-stu-id="c92f5-178">**Collation**</span></span>  
 <span data-ttu-id="c92f5-179">選択した列における照合順序の設定が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-179">Shows the collation setting for the selected column.</span></span> <span data-ttu-id="c92f5-180">この設定を変更するには、 **[照合順序]** をクリックした後、値の右側にある **[...]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="c92f5-180">To change this setting, click **Collation** and then click the ellipses **(...)** to the right of the value.</span></span>  
  
 <span data-ttu-id="c92f5-181">**[計算列の指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-181">**Computed Column Specification Category**</span></span>  
 <span data-ttu-id="c92f5-182">展開すると、 **[式]** と **[永続化されている]** のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-182">Expands to show properties for **Formula** and **Is Persisted**.</span></span> <span data-ttu-id="c92f5-183">列が計算列である場合、式も表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-183">If the column is computed, the formula will also be displayed.</span></span> <span data-ttu-id="c92f5-184">式を編集するには、このカテゴリを展開して、 **[式]** プロパティで式を編集します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-184">To edit the formula, expand this category and edit it in the **Formula** property.</span></span>  
  
 <span data-ttu-id="c92f5-185">**[数式]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-185">**Formula**</span></span>  
 <span data-ttu-id="c92f5-186">選択した列が計算列の場合に、列で使用される式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-186">Shows the formula that the selected column uses if it is a computed column.</span></span> <span data-ttu-id="c92f5-187">このフィールドで式を入力したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-187">In this field you can enter or change a formula.</span></span>  
  
 <span data-ttu-id="c92f5-188">**[永続化されている]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-188">**Is Persisted**</span></span>  
 <span data-ttu-id="c92f5-189">データ ソースを使用して計算列を保存できます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-189">Allows you to save the computed column with the data source.</span></span> <span data-ttu-id="c92f5-190">保存された計算列にインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-190">A persisted computed column can be indexed.</span></span>  
  
 <span data-ttu-id="c92f5-191">**[圧縮データ型]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-191">**Condensed Data Type**</span></span>  
 <span data-ttu-id="c92f5-192">フィールドのデータ型に関する情報が表示されます。SQL の CREATE TABLE ステートメントと同じ形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-192">Displays information about the field's data type, in the same format as the SQL CREATE TABLE statement.</span></span> <span data-ttu-id="c92f5-193">たとえば、最大 20 文字の可変長文字列を含むフィールドは "varchar(20)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-193">For example, a field containing a variable-length string with a maximum length of 20 characters would be represented as "varchar(20)."</span></span> <span data-ttu-id="c92f5-194">このプロパティを変更するには、値を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-194">To change this property, type the value directly.</span></span>  
  
 <span data-ttu-id="c92f5-195">**説明**</span><span class="sxs-lookup"><span data-stu-id="c92f5-195">**Description**</span></span>  
 <span data-ttu-id="c92f5-196">列の説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-196">Shows the description of the column.</span></span> <span data-ttu-id="c92f5-197">完全な説明を表示したり、説明を表示したりするには、[説明] をクリックして、プロパティの右側にある **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c92f5-197">To see the full description or to edit it, click Description, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="c92f5-198">**[フルテキストの指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-198">**Full-text Specification Category**</span></span>  
 <span data-ttu-id="c92f5-199">展開すると、フルテキスト列に関するプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-199">Expands to show properties specific to full-text columns.</span></span>  
  
 <span data-ttu-id="c92f5-200">**[Is Full-text Indexed]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-200">**Is Full-text Indexed**</span></span>  
 <span data-ttu-id="c92f5-201">この列にフルテキスト インデックスが作成されているかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-201">Indicates whether this column is full-text indexed.</span></span> <span data-ttu-id="c92f5-202">この列のデータ型がフルテキスト検索に対応している場合、およびこの列が属するテーブルにフルテキスト インデックスが指定されている場合にのみ、このプロパティを **[はい]** に設定できます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-202">This property can be set to **Yes** only if the data type for this column is full-text searchable and if the table to which this column belongs has a full-text index specified for it.</span></span> <span data-ttu-id="c92f5-203">この値を編集するには、値をクリックしてドロップダウン リストを展開し、新しい値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-203">To change this value, click it, expand the drop-down list, and choose a new value.</span></span>  
  
 <span data-ttu-id="c92f5-204">**[フルテキスト型列]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-204">**Full-text type column**</span></span>  
 <span data-ttu-id="c92f5-205">image 型の列のドキュメントの種類を定義するために使用される列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-205">Shows which column is used to define the document type of a column of type image.</span></span> <span data-ttu-id="c92f5-206">image データ型を使用して、.doc ファイルや XML ファイルなどのさまざまなドキュメントを保存できます</span><span class="sxs-lookup"><span data-stu-id="c92f5-206">The image data type can be used to store documents ranging from .doc files to xml files.</span></span>  
  
 <span data-ttu-id="c92f5-207">**Language**</span><span class="sxs-lookup"><span data-stu-id="c92f5-207">**Language**</span></span>  
 <span data-ttu-id="c92f5-208">列のインデックス作成に使用される言語を指定します</span><span class="sxs-lookup"><span data-stu-id="c92f5-208">Indicates the language used to index the column.</span></span>  
  
 <span data-ttu-id="c92f5-209">**[統計的セマンティクス]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-209">**Statistical Semantics**</span></span>  
 <span data-ttu-id="c92f5-210">選択されている列に対する統計的セマンティック インデックスを有効にするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-210">Select whether to enable statistical semantic indexing for the selected column.</span></span> <span data-ttu-id="c92f5-211">詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92f5-211">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="c92f5-212">**[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、 **[統計的セマンティクス]** オプションは **[いいえ]** に設定され、変更できません。</span><span class="sxs-lookup"><span data-stu-id="c92f5-212">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** option is set to **No** and cannot be modified.</span></span> <span data-ttu-id="c92f5-213">**[言語]** を選択する前に **[統計的セマンティクス]** オプションで **[はい]** を選択した場合、 **[言語]** 列で使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-213">If you select **Yes** for the **Statistical Semantics** option prior to selecting a **Language**, then the languages available in the **Language** column will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
 <span data-ttu-id="c92f5-214">**[SQL Server 以外のサブスクライバーがある]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-214">**Has Non-SQL Server Subscriber**</span></span>  
 <span data-ttu-id="c92f5-215">列に Microsoft SQL Server 以外のサブスクライバーが含まれているかどうかが表示されます</span><span class="sxs-lookup"><span data-stu-id="c92f5-215">Shows whether the column has a non-Microsoft SQL Server subscriber.</span></span>  
  
 <span data-ttu-id="c92f5-216">**[IDENTITY の指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c92f5-216">**Identity Specification Category**</span></span>  
 <span data-ttu-id="c92f5-217">展開すると、 **[ID]** 、 **[ID の増分値]** 、 **[IDENTITY シード]** のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-217">Expands to show properties for **Is Identity**, **Identity Increment**, and **Identity Seed**.</span></span>  
  
 <span data-ttu-id="c92f5-218">**[Is Identity]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-218">**Is Identity**</span></span>  
 <span data-ttu-id="c92f5-219">選択されている列がテーブルの ID 列であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-219">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="c92f5-220">プロパティを変更するには、テーブル デザイナーでテーブルを開き、 **[プロパティ]** ウィンドウでプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-220">To change the property, open the table in Table Designer and edit the properties in the **Properties** window.</span></span> <span data-ttu-id="c92f5-221">この設定は、 *int*などの数値に基づくデータ型の列にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-221">This setting applies only to columns with a number-based data type, such as *int*.</span></span>  
  
 <span data-ttu-id="c92f5-222">**[IDENTITY インクリメント]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-222">**Identity Increment**</span></span>  
 <span data-ttu-id="c92f5-223">以降の各行で **[IDENTITY シード]** に追加される増分値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-223">Shows the increment that will be added to the **Identity Seed** for each subsequent row.</span></span> <span data-ttu-id="c92f5-224">このセルを空白にすると、既定により値が 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-224">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="c92f5-225">このプロパティを編集するには、値を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-225">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="c92f5-226">**[IDENTITY シード]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-226">**Identity Seed**</span></span>  
 <span data-ttu-id="c92f5-227">テーブルの最初の行に割り当てられる値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-227">Shows the value assigned to the first row in the table.</span></span> <span data-ttu-id="c92f5-228">このセルを空白にすると、既定により値が 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-228">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="c92f5-229">このプロパティを編集するには、値を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-229">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="c92f5-230">**[Deterministic]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-230">**Is Deterministic**</span></span>  
 <span data-ttu-id="c92f5-231">選択した列のデータ型を明確に決定できるかどうかが表示されます</span><span class="sxs-lookup"><span data-stu-id="c92f5-231">Shows whether the data type of the selected column can be determined with certainty.</span></span>  
  
 <span data-ttu-id="c92f5-232">**[DTS-published]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-232">**Is DTS-published**</span></span>  
 <span data-ttu-id="c92f5-233">列が SSIS によりパブリッシュされているかどうかが表示されます</span><span class="sxs-lookup"><span data-stu-id="c92f5-233">Shows whether the column is DTS-published.</span></span>  
  
 <span data-ttu-id="c92f5-234">**[Indexable]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-234">**Is Indexable**</span></span>  
 <span data-ttu-id="c92f5-235">選択した列にインデックスを作成できるかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-235">Shows whether the selected column can be indexed.</span></span> <span data-ttu-id="c92f5-236">たとえば、不明確な計算列にはインデックスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="c92f5-236">For example, non-deterministic computed columns cannot be indexed.</span></span>  
  
 <span data-ttu-id="c92f5-237">**[Merge-published]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-237">**Is Merge-published**</span></span>  
 <span data-ttu-id="c92f5-238">列がマージによりパブリッシュされているかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-238">Shows whether the column is merge-published.</span></span>  
  
 <span data-ttu-id="c92f5-239">**[Not For Replication]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-239">**Is Not For Replication**</span></span>  
 <span data-ttu-id="c92f5-240">レプリケーション時に元の ID 値を保持するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-240">Indicates whether original identity values are preserved during replication.</span></span> <span data-ttu-id="c92f5-241">このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-241">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="c92f5-242">**[Replicated]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-242">**Is Replicated**</span></span>  
 <span data-ttu-id="c92f5-243">この列を別の場所にレプリケートされるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-243">Shows whether this column is replicated in another location.</span></span>  
  
 <span data-ttu-id="c92f5-244">**[RowGuid]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-244">**Is RowGuid**</span></span>  
 <span data-ttu-id="c92f5-245">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でこの列が ROWGUID として使用されるかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-245">Indicates whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the column as a ROWGUID.</span></span> <span data-ttu-id="c92f5-246">この値は、データ型がの列に対してのみ **[はい]** に設定でき `uniqueidentifier` ます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-246">You can set this value to **Yes** only for a column with the data type of `uniqueidentifier`.</span></span> <span data-ttu-id="c92f5-247">このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c92f5-247">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="c92f5-248">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="c92f5-248">**Size**</span></span>  
 <span data-ttu-id="c92f5-249">列のデータ型で許容されるサイズがバイト単位で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-249">Shows the size in bytes allowed by column's data type.</span></span> <span data-ttu-id="c92f5-250">たとえば、`nchar` データ型の長さが 10 (文字数) でも、Unicode 文字セットの場合のサイズは 20 になります。</span><span class="sxs-lookup"><span data-stu-id="c92f5-250">For example, a `nchar` data type may have a length of 10 (the number of characters) but it would have a size of 20 to account for Unicode character sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c92f5-251">`varchar(max)` データ型の長さは行ごとに異なります</span><span class="sxs-lookup"><span data-stu-id="c92f5-251">The length of a `varchar(max)` data type varies for each row.</span></span> <span data-ttu-id="c92f5-252">sp_help は、列の長さとして (-1) を返し `varchar(max)` ます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-252">sp_help returns (-1) as the length of `varchar(max)` column.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="c92f5-253">では、列のサイズとして -1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c92f5-253">displays -1 as the column size.</span></span>  
  
  

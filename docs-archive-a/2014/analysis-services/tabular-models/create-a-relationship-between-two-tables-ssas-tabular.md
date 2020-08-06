---
title: 2つのテーブル間のリレーションシップの作成 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.managereldb.f1
- sql12.asvs.bidtoolset.createrelatdb.f1
ms.assetid: 052d77b7-7922-408a-a200-786016ee4d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33481b8d50be9ca632bcade932d51df86c1910a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634675"
---
# <a name="create-a-relationship-between-two-tables-ssas-tabular"></a><span data-ttu-id="81690-102">2 つのテーブル間のリレーションシップの作成 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="81690-102">Create a Relationship Between Two Tables (SSAS Tabular)</span></span>
  <span data-ttu-id="81690-103">データ ソース内のテーブルに既存のリレーションシップがない場合、または新しいテーブルを追加する場合は、モデル デザイナーのツールを使用して新しいリレーションシップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="81690-103">If the tables in your data source do not have existing relationships, or if you add new tables, you can use the tools in the model designer to create new relationships.</span></span> <span data-ttu-id="81690-104">テーブル モデルでリレーションシップがどのように使用されるかについては、「 [リレーションシップ (SSAS テーブル)](relationships-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81690-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="create-a-relationship-between-two-tables"></a><span data-ttu-id="81690-105">2 つのテーブル間のリレーションシップの作成</span><span class="sxs-lookup"><span data-stu-id="81690-105">Create a relationship between two tables</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a><span data-ttu-id="81690-106">ダイアグラム ビューで 2 つのテーブル間のリレーションシップを作成するには (クリックしてドラッグ)</span><span class="sxs-lookup"><span data-stu-id="81690-106">To create a relationship between two tables in Diagram View (Click and drag)</span></span>  
  
1.  <span data-ttu-id="81690-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントし、 **[ダイアグラム ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81690-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="81690-108">テーブル内の列をクリックして、(マウスのボタンを押しながら) 関連する参照テーブル内の関連する参照列までカーソルをドラッグして、ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="81690-108">Click (and hold) on a column within a table, then drag the cursor to a related lookup column in a related lookup table, and then release.</span></span> <span data-ttu-id="81690-109">リレーションシップは自動的に正しい順序で作成されます。</span><span class="sxs-lookup"><span data-stu-id="81690-109">The relationship will be created in the correct order automatically.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a><span data-ttu-id="81690-110">ダイアグラム ビューで 2 つのテーブル間のリレーションシップを作成するには (右クリック)</span><span class="sxs-lookup"><span data-stu-id="81690-110">To create a relationship between two tables in Diagram View (Right-click)</span></span>  
  
1.  <span data-ttu-id="81690-111">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントし、 **[ダイアグラム ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81690-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="81690-112">テーブルの見出しまたは列を右クリックして、 **[リレーションシップの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81690-112">Right-click a table heading or column, and then click **Create Relationship**.</span></span>  
  
3.  <span data-ttu-id="81690-113">**[リレーションシップの作成]** ダイアログ ボックスの **[テーブル]** の下矢印をクリックし、一覧からテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-113">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="81690-114">このテーブルは、"一対多" リレーションシップの "多" の側に当たります。</span><span class="sxs-lookup"><span data-stu-id="81690-114">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
4.  <span data-ttu-id="81690-115">**[列]** で、 **[関連する参照列]** に関連するデータを含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-115">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span> <span data-ttu-id="81690-116">列を右クリックしてリレーションシップを作成した場合は、列が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="81690-116">The column is automatically selected if you right-clicked on a column to create the relationship.</span></span>  
  
5.  <span data-ttu-id="81690-117">**[関連する参照テーブル]** で、 **[テーブル]** で選択したテーブルに関連するデータの列を少なくとも 1 つ含むテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-117">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="81690-118">このテーブルは、"一対多" リレーションシップの "一" の側に当たります。つまり、選択した列には重複する値がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="81690-118">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="81690-119">間違った順序 (多対一ではなく一対多) でリレーションシップを作成しようとすると、 **[関連する参照列]** フィールドの横にアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="81690-119">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="81690-120">順序を逆にして有効なリレーションシップを作成してください。</span><span class="sxs-lookup"><span data-stu-id="81690-120">Reverse the order to create a valid relationship.</span></span>  
  
6.  <span data-ttu-id="81690-121">**[関連する参照列]** で、 **[列]** で選択した列の値と一致する一意の値を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-121">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
7.  <span data-ttu-id="81690-122">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="81690-122">Click **Create**.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a><span data-ttu-id="81690-123">データ ビューで 2 つのテーブル間のリレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="81690-123">To create a relationship between two tables in Data View</span></span>  
  
1.  <span data-ttu-id="81690-124">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]** メニューをクリックし、 **[リレーションシップの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81690-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Create Relationships**.</span></span>  
  
2.  <span data-ttu-id="81690-125">**[リレーションシップの作成]** ダイアログ ボックスの **[テーブル]** の下矢印をクリックし、一覧からテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-125">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="81690-126">このテーブルは、"一対多" リレーションシップの "多" の側に当たります。</span><span class="sxs-lookup"><span data-stu-id="81690-126">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
3.  <span data-ttu-id="81690-127">**[列]** で、 **[関連する参照列]** に関連するデータを含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-127">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span>  
  
4.  <span data-ttu-id="81690-128">**[関連する参照テーブル]** で、 **[テーブル]** で選択したテーブルに関連するデータの列を少なくとも 1 つ含むテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-128">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="81690-129">このテーブルは、"一対多" リレーションシップの "一" の側に当たります。つまり、選択した列には重複する値がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="81690-129">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="81690-130">間違った順序 (多対一ではなく一対多) でリレーションシップを作成しようとすると、 **[関連する参照列]** フィールドの横にアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="81690-130">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="81690-131">順序を逆にして有効なリレーションシップを作成してください。</span><span class="sxs-lookup"><span data-stu-id="81690-131">Reverse the order to create a valid relationship.</span></span>  
  
5.  <span data-ttu-id="81690-132">**[関連する参照列]** で、 **[列]** で選択した列の値と一致する一意の値を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="81690-132">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
6.  <span data-ttu-id="81690-133">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="81690-133">Click **Create**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81690-134">参照</span><span class="sxs-lookup"><span data-stu-id="81690-134">See Also</span></span>  
 <span data-ttu-id="81690-135">[SSAS 表形式&#41;&#40;のリレーションシップの削除](delete-relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="81690-135">[Delete Relationships &#40;SSAS Tabular&#41;](delete-relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="81690-136">リレーションシップ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="81690-136">Relationships &#40;SSAS Tabular&#41;</span></span>](relationships-ssas-tabular.md)  
  
  

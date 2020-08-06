---
title: リレーションシップの削除 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c63324918eb6919ce0abd65b5ee0765f9d7243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712525"
---
# <a name="delete-relationships-ssas-tabular"></a><span data-ttu-id="3fb1e-102">リレーションシップの削除 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="3fb1e-102">Delete Relationships (SSAS Tabular)</span></span>
  <span data-ttu-id="3fb1e-103">ダイアグラム ビューのモデル デザイナーまたは [リレーションシップの管理] ダイアログ ボックスを使用して、既存のリレーションシップを削除できます。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-103">You can delete existing relationships by using the model designer in Diagram View or by using the Manage Relationships dialog box.</span></span> <span data-ttu-id="3fb1e-104">テーブル モデルでリレーションシップがどのように使用されるかについては、「 [リレーションシップ (SSAS テーブル)](relationships-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="considerations-for-deleting-relationships"></a><span data-ttu-id="3fb1e-105">リレーションシップの削除に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="3fb1e-105">Considerations for Deleting Relationships</span></span>  
 <span data-ttu-id="3fb1e-106">リレーションシップを削除するかどうかを判断する際には、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-106">Keep the following issues in mind when deciding whether to delete a relationship:</span></span>  
  
-   <span data-ttu-id="3fb1e-107">リレーションシップの削除を元に戻す方法はありません。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-107">There is no way to undo the deletion of a relationship.</span></span> <span data-ttu-id="3fb1e-108">リレーションシップを再作成することはできますが、これを行うには、モデル内の数式をすべて再計算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-108">You can re-create the relationship, but this action requires a complete recalculation of formulas in the model.</span></span> <span data-ttu-id="3fb1e-109">そのため、数式で使用されているリレーションシップを削除する場合は、このことを事前にチェックすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-109">Therefore, always check first before deleting a relationship that is used in formulas.</span></span>  
  
-   <span data-ttu-id="3fb1e-110">2 つのテーブル間のリレーションシップを削除すると、それらのテーブルを参照する数式でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-110">Deleting a relationship between two tables can cause errors in formulas that reference these tables.</span></span>  
  
-   <span data-ttu-id="3fb1e-111">Data Analysis Expression (DAX) の RELATED 関数は、テーブル間のリレーションシップを使用して関連する値をもう一方のテーブルで検索します。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-111">The Data Analysis Expression (DAX) RELATED function uses the relationships between tables to look up related values in another table.</span></span> <span data-ttu-id="3fb1e-112">リレーションシップが削除されると、この関数は異なる結果を返します。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-112">It will return different results after the relationship is deleted.</span></span> <span data-ttu-id="3fb1e-113">詳細については、RELATED 関数 (DAX) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-113">For more information, see the RELATED Function (DAX).</span></span>  
  
-   <span data-ttu-id="3fb1e-114">リレーションシップを作成および削除すると、ピボットテーブルと数式の結果が変わるだけでなく、ブックの再計算も実行されます。この処理には、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-114">In addition to changing PivotTable and formula results, both the creation and deletion of relationships will cause the workbook to be recalculated, which can take some time.</span></span>  
  
## <a name="delete-relationships"></a><span data-ttu-id="3fb1e-115">リレーションシップの削除</span><span class="sxs-lookup"><span data-stu-id="3fb1e-115">Delete Relationships</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a><span data-ttu-id="3fb1e-116">ダイアグラム ビューを使用してリレーションシップを削除するには</span><span class="sxs-lookup"><span data-stu-id="3fb1e-116">To delete a relationship by using Diagram View</span></span>  
  
1.  <span data-ttu-id="3fb1e-117">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントして、 **[ダイアグラム ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="3fb1e-118">2 つのテーブルの間のリレーションシップの線を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-118">Right-click a relationship line between two tables, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a><span data-ttu-id="3fb1e-119">[リレーションシップの管理] ダイアログ ボックスを使用してリレーションシップを削除するには</span><span class="sxs-lookup"><span data-stu-id="3fb1e-119">To delete a relationship by using the Manage Relationships dialog box</span></span>  
  
1.  <span data-ttu-id="3fb1e-120">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]** メニューをクリックし、 **[リレーションシップの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-120">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Manage Relationships**.</span></span>  
  
2.  <span data-ttu-id="3fb1e-121">**[リレーションシップの管理]** ダイアログ ボックスで、一覧から 1 つまたは複数のリレーションシップを選択します。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-121">In the **Manage Relationships** dialog box, select one or more relationships from the list.</span></span>  
  
     <span data-ttu-id="3fb1e-122">複数のリレーションシップを選択するには、Ctrl キーを押しながら各リレーションシップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-122">To select multiple relationships, hold down CTRL while you click each relationship.</span></span>  
  
3.  <span data-ttu-id="3fb1e-123">**[リレーションシップの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-123">Click **Delete Relationship**.</span></span>  
  
4.  <span data-ttu-id="3fb1e-124">**[リレーションシップの管理]** ダイアログ ボックスで、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fb1e-124">In the **Manage Relationships** dialog box, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb1e-125">参照</span><span class="sxs-lookup"><span data-stu-id="3fb1e-125">See Also</span></span>  
 <span data-ttu-id="3fb1e-126">[SSAS 表形式のリレーションシップ &#40;&#41;](relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3fb1e-126">[Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="3fb1e-127">2 つのテーブル間のリレーションシップの作成 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="3fb1e-127">Create a Relationship Between Two Tables &#40;SSAS Tabular&#41;</span></span>](create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  

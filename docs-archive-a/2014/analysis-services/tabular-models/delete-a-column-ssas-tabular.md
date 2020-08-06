---
title: 列の削除 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 06af0b7fd9879661db95bb2073cced545bb4eef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641883"
---
# <a name="delete-a-column-ssas-tabular"></a><span data-ttu-id="cf241-102">列の削除 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="cf241-102">Delete a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="cf241-103">このトピックでは、テーブル モデルのテーブルから列を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf241-103">This topic describes how to delete a column from a tabular model table.</span></span>  
  
## <a name="delete-a-model-table-column"></a><span data-ttu-id="cf241-104">モデル テーブルの列の削除</span><span class="sxs-lookup"><span data-stu-id="cf241-104">Delete a Model Table Column</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf241-105">モデル テーブルから列を削除しても、列はパーティションのクエリ定義からは削除されません。</span><span class="sxs-lookup"><span data-stu-id="cf241-105">Deleting a column from a model table does not delete the column from a partition query definition.</span></span> <span data-ttu-id="cf241-106">削除する列がパーティションの一部である場合、パーティションのクエリ定義から手動で列を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf241-106">If the column you are deleting is part of a partition, you must manually delete the column from the partition query definition.</span></span> <span data-ttu-id="cf241-107">パーティションのクエリ定義から列を削除しない場合、列にクエリが実行されてデータが返されますが、モデル テーブルには処理操作時に値が設定されません。</span><span class="sxs-lookup"><span data-stu-id="cf241-107">Failure to delete the column from the partition query definition will cause the column to be queried and data returned, but not populated to the model table, during processing operations.</span></span> <span data-ttu-id="cf241-108">詳細については、「 [パーティション (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf241-108">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-delete-a-model-table-column"></a><span data-ttu-id="cf241-109">モデル テーブルの列を削除するには</span><span class="sxs-lookup"><span data-stu-id="cf241-109">To delete a model table column</span></span>  
  
-   <span data-ttu-id="cf241-110">モデル デザイナーの削除対象の列が含まれるテーブルで列を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf241-110">In the model designer, in the table that contains the column you want to delete, right-click on the column, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a><span data-ttu-id="cf241-111">[テーブルのプロパティ] ダイアログ ボックスを使用してモデル テーブルの列を削除するには</span><span class="sxs-lookup"><span data-stu-id="cf241-111">To delete a model table column by using the Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="cf241-112">モデル デザイナーで削除対象の列が含まれるテーブルをクリックし、 **[テーブル]** メニュー、  **[テーブルのプロパティ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf241-112">In the model designer, click on the table which contains the column you want to delete, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="cf241-113">**[列名の取得元]** で、 **[モデル]** を選択します (*ソースと異なる場合、モデル テーブルの列名を使用します*)。</span><span class="sxs-lookup"><span data-stu-id="cf241-113">In **Column names from**, select **Model** (*to use model table column names, if different from source*).</span></span>  
  
3.  <span data-ttu-id="cf241-114">**[テーブルのプロパティの編集]** ダイアログ ボックスのテーブル プレビュー ウィンドウで、削除する列をオフにしてから、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf241-114">In the **Edit Table Properties** dialog box, in the table preview window, uncheck the column you want to delete, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf241-115">参照</span><span class="sxs-lookup"><span data-stu-id="cf241-115">See Also</span></span>  
 <span data-ttu-id="cf241-116">[SSAS 表形式&#41;&#40;テーブルへの列の追加](add-columns-to-a-table-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="cf241-116">[Add Columns to a Table &#40;SSAS Tabular&#41;](add-columns-to-a-table-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="cf241-117">パーティション (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="cf241-117">Partitions &#40;SSAS Tabular&#41;</span></span>](partitions-ssas-tabular.md)  
  
  

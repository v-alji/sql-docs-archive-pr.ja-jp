---
title: テーブルの削除 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
ms.openlocfilehash: c72fa90426440c1be84318a15cf0d761ef16aca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643479"
---
# <a name="delete-a-table-ssas-tabular"></a><span data-ttu-id="2e69f-102">テーブルの削除 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="2e69f-102">Delete a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="2e69f-103">モデル デザイナーでは、モデル ワークスペース データベース内の不要なテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="2e69f-103">In the model designer, you can delete tables in your model workspace database that you no longer need.</span></span> <span data-ttu-id="2e69f-104">テーブルを削除しても、元のソース データには影響しません。インポートして作業していたデータにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="2e69f-104">Deleting a table does not affect the original source data, only the data that you imported and were working with.</span></span> <span data-ttu-id="2e69f-105">テーブルの削除を元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="2e69f-105">You cannot undo the deletion of a table.</span></span>  
  
### <a name="to-delete-a-table"></a><span data-ttu-id="2e69f-106">テーブルを削除する</span><span class="sxs-lookup"><span data-stu-id="2e69f-106">To delete a table</span></span>  
  
-   <span data-ttu-id="2e69f-107">削除するテーブルのモデル デザイナーの下にあるタブを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e69f-107">Right-click the tab at the bottom of the model designer for the table that you want to delete, and then click **Delete**.</span></span>  
  
## <a name="considerations-when-deleting-tables"></a><span data-ttu-id="2e69f-108">テーブルを削除する際の注意事項</span><span class="sxs-lookup"><span data-stu-id="2e69f-108">Considerations when Deleting Tables</span></span>  
  
-   <span data-ttu-id="2e69f-109">テーブルを削除すると、テーブルを含んでいるタブ全体が削除されます。</span><span class="sxs-lookup"><span data-stu-id="2e69f-109">When you delete a table, the entire tab that the table was on is deleted.</span></span>  
  
-   <span data-ttu-id="2e69f-110">そのテーブルにメジャーが関連付けられている場合、メジャーの定義も削除されます。</span><span class="sxs-lookup"><span data-stu-id="2e69f-110">If any measures were associated with that table, the definition of the measure will also be deleted.</span></span>  
  
-   <span data-ttu-id="2e69f-111">そのテーブルを使用して計算列を作成していた場合、そのテーブルの列も削除されます。削除対象のテーブル列を他のテーブルの計算列で使用している場合は、エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e69f-111">If you created any calculated columns using that table, columns in that table are also deleted; any calculated columns in other tables that use columns from the deleted table will display an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e69f-112">参照</span><span class="sxs-lookup"><span data-stu-id="2e69f-112">See Also</span></span>  
 [<span data-ttu-id="2e69f-113">テーブルと列 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="2e69f-113">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tables-and-columns-ssas-tabular.md)  
  
  

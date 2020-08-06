---
title: マイニング構造からの列の削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ad1de08d57d00fd9798e1ceeddb85d146d7111
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631350"
---
# <a name="remove-columns-from-a-mining-structure"></a><span data-ttu-id="a21e4-102">マイニング構造からの列の削除</span><span class="sxs-lookup"><span data-stu-id="a21e4-102">Remove Columns from a Mining Structure</span></span>
  <span data-ttu-id="a21e4-103">データ マイニング デザイナーを使用して、マイニング構造の作成後に構造から列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="a21e4-103">You can use Data Mining Designer to remove columns from a mining structure after the structure has already been created.</span></span> <span data-ttu-id="a21e4-104">マイニング構造列を削除する理由には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="a21e4-104">Reasons to remove a mining structure column might include the following:</span></span>  
  
-   <span data-ttu-id="a21e4-105">マイニング構造に列の複数のコピーが格納されており、モデルで重複データを使用しないようにする。</span><span class="sxs-lookup"><span data-stu-id="a21e4-105">The mining structure contains multiple copies of a column and you want to avoid the use of duplicate data in a model.</span></span>  
  
-   <span data-ttu-id="a21e4-106">データを保護する必要があるが、ドリルスルーが有効になっている。</span><span class="sxs-lookup"><span data-stu-id="a21e4-106">The data should be protected, but drillthrough has been enabled.</span></span>  
  
-   <span data-ttu-id="a21e4-107">データがモデリングで使用されておらず、処理する必要がない。</span><span class="sxs-lookup"><span data-stu-id="a21e4-107">The data is unused in modeling and should not be processed.</span></span>  
  
 <span data-ttu-id="a21e4-108">マイニング構造から列を削除しても、データ ソース ビュー内の列または外部データ内の列は変更されません。メタデータのみ削除されます。</span><span class="sxs-lookup"><span data-stu-id="a21e4-108">Deleting a column from the mining structure does not change the column in the data source view or in the external data; only metadata is deleted.</span></span> <span data-ttu-id="a21e4-109">ただし、マイニング構造で使用される列を変更する場合は、構造およびその構造に基づくモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a21e4-109">However, when you change the columns used in a mining structure, you must reprocess the structure and any models based on it.</span></span>  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a><span data-ttu-id="a21e4-110">マイニング構造から列を削除するには</span><span class="sxs-lookup"><span data-stu-id="a21e4-110">To remove a column from the mining structure</span></span>  
  
1.  <span data-ttu-id="a21e4-111">データ マイニング デザイナーで **[マイニング構造]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="a21e4-111">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="a21e4-112">マイニング構造のツリーを展開し、すべての列を表示します。</span><span class="sxs-lookup"><span data-stu-id="a21e4-112">Expand the tree for the mining structure, to show all the columns.</span></span>  
  
3.  <span data-ttu-id="a21e4-113">削除する列を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a21e4-113">Right-click the column that you want to delete, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="a21e4-114">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a21e4-114">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a21e4-115">参照</span><span class="sxs-lookup"><span data-stu-id="a21e4-115">See Also</span></span>  
 [<span data-ttu-id="a21e4-116">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="a21e4-116">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  

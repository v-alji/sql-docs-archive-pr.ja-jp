---
title: 入れ子になったテーブルをマイニング構造に追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tables [Analysis Services], nested
- nested tables
- mining structures [Analysis Services], nested tables
- adding nested tables
ms.assetid: 6cf9c701-9cff-4fae-94c2-73796c24ef59
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e61e71d566abc9aae2194cae244f5d4ad8d9ea0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643026"
---
# <a name="add-a-nested-table-to-a-mining-structure"></a><span data-ttu-id="2f7fc-102">マイニング構造への入れ子になったテーブルの追加</span><span class="sxs-lookup"><span data-stu-id="2f7fc-102">Add a Nested Table to a Mining Structure</span></span>
  <span data-ttu-id="2f7fc-103">データ マイニング ウィザードによって作成されたマイニング構造に入れ子になったテーブルを追加するには、データ マイニング デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-103">Use Data Mining Designer to add a nested table to a mining structure after it has been created by the Data Mining Wizard.</span></span>  
  
### <a name="to-add-a-nested-table-to-a-mining-structure"></a><span data-ttu-id="2f7fc-104">入れ子になったテーブルをマイニング構造に追加するには</span><span class="sxs-lookup"><span data-stu-id="2f7fc-104">To add a nested table to a mining structure</span></span>  
  
1.  <span data-ttu-id="2f7fc-105">データ マイニング デザイナーで **[マイニング構造]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-105">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="2f7fc-106">テーブル列の追加先となるマイニング構造を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-106">Right-click the mining structure to which you want to add a table column.</span></span>  
  
3.  <span data-ttu-id="2f7fc-107">**[入れ子になっているテーブルの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-107">Select **Add a Nested Table**.</span></span>  
  
     <span data-ttu-id="2f7fc-108">**[入れ子になったテーブル キー列の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-108">The **Select a Nested Table Key Column** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="2f7fc-109">**[入れ子になったテーブル]** で、マイニング構造で入れ子にするテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-109">Under **Nested table**, select the table that you want to nest in the mining structure.</span></span>  
  
5.  <span data-ttu-id="2f7fc-110">**[基になる列]** で、入れ子になったテーブルのキー列を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-110">Under **Source column**, select the key column for the nested table.</span></span>  
  
6.  <span data-ttu-id="2f7fc-111">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-111">Click **OK**.</span></span>  
  
     <span data-ttu-id="2f7fc-112">キー列を含んでいる新しいテーブル列がマイニング構造に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-112">A new table column that contains the key column is added to the mining structure.</span></span> <span data-ttu-id="2f7fc-113">列を追加する方法については、「 [マイニング構造への列の追加](add-columns-to-a-mining-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f7fc-113">For information about how to add additional columns, see [Add Columns to a Mining Structure](add-columns-to-a-mining-structure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7fc-114">参照</span><span class="sxs-lookup"><span data-stu-id="2f7fc-114">See Also</span></span>  
 [<span data-ttu-id="2f7fc-115">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="2f7fc-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  

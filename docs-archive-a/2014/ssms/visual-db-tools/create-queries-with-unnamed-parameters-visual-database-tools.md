---
title: 無名のパラメーターを使用したクエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ea53afd1fa4d44390f5805d6b28494428608b90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631456"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a><span data-ttu-id="de105-102">無名のパラメーターを使用したクエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="de105-102">Create Queries with Unnamed Parameters (Visual Database Tools)</span></span>
  <span data-ttu-id="de105-103">リテラル値のプレースホルダーとして疑問符 (?) を指定すると、無名のパラメーターを持つクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="de105-103">You can create a query with an unnamed parameter by specifying a question mark (?) as a placeholder for a literal value.</span></span> <span data-ttu-id="de105-104">クエリおよびビュー デザイナーにより、一時的な名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="de105-104">Query and View Designer will give it a temporary name.</span></span> <span data-ttu-id="de105-105">クエリには、必要な数の無名のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="de105-105">You can specify as many unnamed parameters in the query as you need.</span></span>  
  
 <span data-ttu-id="de105-106">クエリおよびビュー デザイナーでクエリを実行すると、一時的な名前と共に [クエリ パラメーター] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="de105-106">When you run the query in the Query and View Designer, the Query Parameters Dialog Box is displayed with the temporary name.</span></span>  
  
### <a name="to-specify-an-unnamed-parameter"></a><span data-ttu-id="de105-107">無名のパラメーターを指定するには</span><span class="sxs-lookup"><span data-stu-id="de105-107">To specify an unnamed parameter</span></span>  
  
1.  <span data-ttu-id="de105-108">検索する列または式を [抽出条件ペイン](visual-database-tools.md)に追加します。</span><span class="sxs-lookup"><span data-stu-id="de105-108">Add the columns or expressions that you want to search to the [Criteria pane](visual-database-tools.md).</span></span> <span data-ttu-id="de105-109">検索列または検索式をクエリ出力に表示しない場合は、出力列から削除します。</span><span class="sxs-lookup"><span data-stu-id="de105-109">If you do not want the search columns or expressions to appear in the query output, remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="de105-110">検索するデータ列または式を含む行を選択し、 **[フィルター]** グリッド列に疑問符 (?) を入力します。</span><span class="sxs-lookup"><span data-stu-id="de105-110">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter a question mark (?).</span></span>  
  
     <span data-ttu-id="de105-111">既定では、"=" 演算子が追加されます。</span><span class="sxs-lookup"><span data-stu-id="de105-111">By default, the Query and View Designer adds the "=" operator.</span></span> <span data-ttu-id="de105-112">ただし、セルを編集して、">"、"<"、または他の SQL 比較演算子にも変更できます。</span><span class="sxs-lookup"><span data-stu-id="de105-112">However, you can edit the cell to substitute ">", "<", or any other SQL comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de105-113">参照</span><span class="sxs-lookup"><span data-stu-id="de105-113">See Also</span></span>  
 [<span data-ttu-id="de105-114">パラメーターを使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="de105-114">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  

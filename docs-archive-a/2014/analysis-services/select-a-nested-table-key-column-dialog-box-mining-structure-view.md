---
title: '[入れ子になったテーブルキー列の選択] ダイアログボックス ([マイニング構造] ビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dc524f6913b7be15e87869355515397a3e0b65c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643530"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a><span data-ttu-id="42a98-102">[入れ子になったテーブル キー列の選択] ダイアログ ボックス ([マイニング構造] ビュー)</span><span class="sxs-lookup"><span data-stu-id="42a98-102">Select a Nested Table Key Column Dialog Box (Mining Structure View)</span></span>
  <span data-ttu-id="42a98-103">**[入れ子になったテーブル キー列の選択]** ダイアログ ボックスを使用すると、新しい入れ子になったテーブルのキーとして動作する列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="42a98-103">Use the **Select a Nested Table Key Column** dialog box to designate a column that will act as the key for the new nested table.</span></span> <span data-ttu-id="42a98-104">ダイアログ ボックスを閉じると、指定したキー列を含む新しいテーブルがマイニング構造に追加されます。</span><span class="sxs-lookup"><span data-stu-id="42a98-104">When you exit the dialog box, a new table is added to the mining structure that contains the designated key column.</span></span> <span data-ttu-id="42a98-105">入れ子になったテーブルに新たに列を追加するには、構造を右クリックして **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42a98-105">You can add additional columns to the nested table by right-clicking the structure and selecting **Add a Column**.</span></span> <span data-ttu-id="42a98-106">このダイアログ ボックスに含まれているオプションは、OLAP マイニング モデルを使用するか、リレーショナル マイニング モデルを使用するかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="42a98-106">The dialog box contains different options depending on whether you are working with an OLAP mining model or a relational mining model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42a98-107">Options</span><span class="sxs-lookup"><span data-stu-id="42a98-107">Options</span></span>  
 <span data-ttu-id="42a98-108">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="42a98-108">**Source table**</span></span>  
 <span data-ttu-id="42a98-109">マイニング モデルの基になるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="42a98-109">The table on which the mining model is based.</span></span>  
  
 <span data-ttu-id="42a98-110">このオプションは、リレーショナル マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="42a98-110">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="42a98-111">**ソース列**</span><span class="sxs-lookup"><span data-stu-id="42a98-111">**Source column**</span></span>  
 <span data-ttu-id="42a98-112">入れ子になったテーブルのキーとして使用できる、基になるテーブル内の使用可能なすべての列の一覧です。</span><span class="sxs-lookup"><span data-stu-id="42a98-112">A list of all the available columns in the source table that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="42a98-113">このオプションは、リレーショナル マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="42a98-113">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="42a98-114">**[列の型を表示]**</span><span class="sxs-lookup"><span data-stu-id="42a98-114">**Show column types**</span></span>  
 <span data-ttu-id="42a98-115">使用できる列のデータ型の一覧です。</span><span class="sxs-lookup"><span data-stu-id="42a98-115">A list of available column data types.</span></span> <span data-ttu-id="42a98-116">データ型を選択または選択解除して、 **[基になる列]** 内の列の一覧をフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="42a98-116">Select or clear data types to filter the list of columns in **Source column**.</span></span> <span data-ttu-id="42a98-117">オンになっているデータ型に一致する列だけが **[基になる列]** の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="42a98-117">Only columns that match the checked data types will be shown in the **Source column** list.</span></span>  
  
 <span data-ttu-id="42a98-118">このオプションは、リレーショナル マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="42a98-118">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="42a98-119">**属性**</span><span class="sxs-lookup"><span data-stu-id="42a98-119">**Attributes**</span></span>  
 <span data-ttu-id="42a98-120">入れ子になったテーブルのキーとして使用できる属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="42a98-120">A list of attributes that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="42a98-121">このオプションは、OLAP マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="42a98-121">This is only used for OLAP mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a98-122">参照</span><span class="sxs-lookup"><span data-stu-id="42a98-122">See Also</span></span>  
 [<span data-ttu-id="42a98-123">マイニング構造ビュー &#40;データマイニングモデルデザイナー&#41;</span><span class="sxs-lookup"><span data-stu-id="42a98-123">Mining Structure View &#40;Data Mining Model Designer&#41;</span></span>](mining-structure-view-data-mining-model-designer.md)  
  
  

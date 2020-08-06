---
title: '[列の選択] ダイアログボックス ([マイニング構造] ビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addacolumn.f1
helpviewer_keywords:
- Select a Column dialog box
ms.assetid: 6f73a7dc-5401-40c3-8f1d-b41fc1dd91c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9f8efedd768ed90c039d2799ef66ff02f7c2f37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633364"
---
# <a name="select-a-column-dialog-box-mining-structure-view"></a><span data-ttu-id="e0eae-102">[列の選択] ダイアログ ボックス ([マイニング構造] ビュー)</span><span class="sxs-lookup"><span data-stu-id="e0eae-102">Select a Column Dialog Box (Mining Structure View)</span></span>
  <span data-ttu-id="e0eae-103">**[列の選択]** ダイアログ ボックスを使用すると、列をマイニング構造に追加できます。</span><span class="sxs-lookup"><span data-stu-id="e0eae-103">Use the **Select a Column** dialog box to add columns to the mining structure.</span></span> <span data-ttu-id="e0eae-104">このダイアログに含まれているオプションは、OLAP マイニング モデルを使用するか、リレーショナル マイニング モデルを使用するかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="e0eae-104">The dialog contains different options depending on whether you are working with an OLAP mining model or a relational mining model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0eae-105">Options</span><span class="sxs-lookup"><span data-stu-id="e0eae-105">Options</span></span>  
 <span data-ttu-id="e0eae-106">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="e0eae-106">**Source table**</span></span>  
 <span data-ttu-id="e0eae-107">マイニング モデルの基になるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="e0eae-107">The table on which the mining model is based.</span></span>  
  
 <span data-ttu-id="e0eae-108">このオプションは、リレーショナル マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0eae-108">This option is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="e0eae-109">**ソース列**</span><span class="sxs-lookup"><span data-stu-id="e0eae-109">**Source column**</span></span>  
 <span data-ttu-id="e0eae-110">マイニング構造に追加できる、基になるテーブル内の使用可能なすべての列の一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0eae-110">A list of all the available columns in the source table that you can add to the mining structure.</span></span>  
  
 <span data-ttu-id="e0eae-111">このオプションは、リレーショナル マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0eae-111">This option is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="e0eae-112">**[列の型を表示]**</span><span class="sxs-lookup"><span data-stu-id="e0eae-112">**Show column types**</span></span>  
 <span data-ttu-id="e0eae-113">使用できる列のデータ型の一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0eae-113">A list of available column data types.</span></span> <span data-ttu-id="e0eae-114">データ型を選択または選択解除して、 **[基になる列]** 内の列の一覧をフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="e0eae-114">Select or clear data types to filter the list of columns in **Source column**.</span></span> <span data-ttu-id="e0eae-115">オンになっているデータ型に一致する列だけが **[基になる列]** の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0eae-115">Only columns that match the checked data types will be shown in the **Source column** list.</span></span>  
  
 <span data-ttu-id="e0eae-116">このオプションは、リレーショナル マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0eae-116">This option is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="e0eae-117">**関連する属性とメジャー**</span><span class="sxs-lookup"><span data-stu-id="e0eae-117">**Related attributes and measures**</span></span>  
 <span data-ttu-id="e0eae-118">マイニング構造に追加できるすべての使用可能なメジャーおよび属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0eae-118">A list of all the available measures and attributes that you can add to the mining structure.</span></span>  
  
 <span data-ttu-id="e0eae-119">このオプションは、OLAP マイニング モデルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0eae-119">This option is only used for OLAP mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0eae-120">参照</span><span class="sxs-lookup"><span data-stu-id="e0eae-120">See Also</span></span>  
 <span data-ttu-id="e0eae-121">[マイニング構造ビュー &#40;データマイニングモデルデザイナー&#41;](mining-structure-view-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e0eae-121">[Mining Structure View &#40;Data Mining Model Designer&#41;](mining-structure-view-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="e0eae-122">マイニング構造への列の追加</span><span class="sxs-lookup"><span data-stu-id="e0eae-122">Add Columns to a Mining Structure</span></span>](data-mining/add-columns-to-a-mining-structure.md)  
  
  

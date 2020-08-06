---
title: '[クエリパラメーター] ダイアログボックス (MDX) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.queryparameters.mdx.f1
ms.assetid: e69b9542-7b54-42bf-b2de-c091e81af7ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1eee07ffefc0b2d7c6115245e12d09c5ac6eb4a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738929"
---
# <a name="query-parameters-dialog-box-mdx"></a><span data-ttu-id="56d80-102">[クエリ パラメーター] ダイアログ ボックス (MDX)</span><span class="sxs-lookup"><span data-stu-id="56d80-102">Query Parameters Dialog Box (MDX)</span></span>
  <span data-ttu-id="56d80-103">**および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [クエリ パラメーター] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、セット、ディメンション、およびサブキューブの定義に使用される MDX クエリにパラメーターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="56d80-103">Use the **Query Parameters** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to add parameters to MDX queries that are used to define sets, dimensions, and subcubes.</span></span> <span data-ttu-id="56d80-104">**[クエリ パラメーター]** ダイアログ ボックスを表示するには、 **[MDX クエリ ビルダー]** ダイアログ ボックスの **[パラメーター]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d80-104">You can display the **Query Parameters** dialog box by clicking the **Parameters** icon in the **MDX query builder** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56d80-105">Options</span><span class="sxs-lookup"><span data-stu-id="56d80-105">Options</span></span>  
 <span data-ttu-id="56d80-106">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="56d80-106">**Parameter**</span></span>  
 <span data-ttu-id="56d80-107">新しいパラメーターを作成するには、パラメーター名を入力するか、または既存のパラメーターの名前を編集します。</span><span class="sxs-lookup"><span data-stu-id="56d80-107">Type a parameter name to begin creating a new parameter, or edit the name of an existing parameter.</span></span>  
  
 <span data-ttu-id="56d80-108">**ディメンション**</span><span class="sxs-lookup"><span data-stu-id="56d80-108">**Dimension**</span></span>  
 <span data-ttu-id="56d80-109">既存のディメンションの一覧から 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="56d80-109">Choose an existing dimension from the list.</span></span>  
  
 <span data-ttu-id="56d80-110">**Hierarchy**</span><span class="sxs-lookup"><span data-stu-id="56d80-110">**Hierarchy**</span></span>  
 <span data-ttu-id="56d80-111">パラメーターが特定の階層に適用される場合は、一覧から階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d80-111">Choose a hierarchy from the list, if the parameter is applied to a specific hierarchy.</span></span>  
  
 <span data-ttu-id="56d80-112">**[複数の値]**</span><span class="sxs-lookup"><span data-stu-id="56d80-112">**Multiple values**</span></span>  
 <span data-ttu-id="56d80-113">説明</span><span class="sxs-lookup"><span data-stu-id="56d80-113">Description</span></span>  
  
 <span data-ttu-id="56d80-114">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="56d80-114">**Default**</span></span>  
 <span data-ttu-id="56d80-115">パラメーターの既定値を指定します (ある場合)。</span><span class="sxs-lookup"><span data-stu-id="56d80-115">Indicate the default value for the parameter, if any.</span></span> <span data-ttu-id="56d80-116">既定では、値は割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="56d80-116">By default, no value is assigned.</span></span>  
  
 <span data-ttu-id="56d80-117">**その他**</span><span class="sxs-lookup"><span data-stu-id="56d80-117">**Other**</span></span>  
 <span data-ttu-id="56d80-118">Del キーまたは [X] ボタンを使用して、今後使用しないパラメーターを削除します。</span><span class="sxs-lookup"><span data-stu-id="56d80-118">Use the Delete key or X button to remove parameters you no long use.</span></span> <span data-ttu-id="56d80-119">方向キーを使用して、強調表示されたパラメーターを一覧内で上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="56d80-119">Use the arrow keys to move the highlighted parameter up or down in the list.</span></span> <span data-ttu-id="56d80-120">パラメーターの順序付けには、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="56d80-120">The following rules apply to ordering of parameters:</span></span>  
  
-   <span data-ttu-id="56d80-121">パラメーターのスコープ</span><span class="sxs-lookup"><span data-stu-id="56d80-121">Parameter scoping.</span></span>  
  
-   <span data-ttu-id="56d80-122">パラメーターの順序</span><span class="sxs-lookup"><span data-stu-id="56d80-122">Parameter order.</span></span>  
  
  

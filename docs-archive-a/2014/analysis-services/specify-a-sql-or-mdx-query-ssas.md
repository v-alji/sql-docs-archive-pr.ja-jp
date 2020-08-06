---
title: SQL または MDX クエリの指定 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.specsqlmdxquery.f1
ms.assetid: e4128221-3b46-48be-b0f1-d82477ce6782
author: minewiskan
ms.author: owend
ms.openlocfilehash: bce5e92aaed7a62311e989d6963e4fa5764028ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736852"
---
# <a name="specify-a-sql-or-mdx-query-ssas"></a><span data-ttu-id="c8946-102">SQL または MDX クエリの指定 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="c8946-102">Specify a SQL or MDX Query (SSAS)</span></span>
  <span data-ttu-id="c8946-103">**テーブルのインポート ウィザード** のこのページを使用すると、SQL クエリまたは MDX クエリでデータをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="c8946-103">This page of the **Table Import Wizard** enables you to import data by using a SQL or MDX query.</span></span> <span data-ttu-id="c8946-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8946-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="c8946-105">クエリでは、インポートするデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="c8946-105">The query can manipulate the data that is imported.</span></span> <span data-ttu-id="c8946-106">たとえば、異なるテーブルからのデータを結合することも、特定の条件を満たす行だけを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="c8946-106">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c8946-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c8946-107">UI element list</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8946-108">期間</span><span class="sxs-lookup"><span data-stu-id="c8946-108">Term</span></span>|<span data-ttu-id="c8946-109">定義</span><span class="sxs-lookup"><span data-stu-id="c8946-109">Definition</span></span>|  
|<span data-ttu-id="c8946-110">**[表示するクエリ名]**</span><span class="sxs-lookup"><span data-stu-id="c8946-110">**Friendly Query Name**</span></span>|<span data-ttu-id="c8946-111">クエリの固有の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c8946-111">Type a unique name for the query.</span></span> <span data-ttu-id="c8946-112">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="c8946-112">This is a required field.</span></span>|  
|<span data-ttu-id="c8946-113">**SQL ステートメント**</span><span class="sxs-lookup"><span data-stu-id="c8946-113">**SQL Statement**</span></span>|<span data-ttu-id="c8946-114">SQL ステートメントを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c8946-114">Type or paste a SQL statement.</span></span>|  
|<span data-ttu-id="c8946-115">**検証**</span><span class="sxs-lookup"><span data-stu-id="c8946-115">**Validate**</span></span>|<span data-ttu-id="c8946-116">SQL ステートメントが有効かどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="c8946-116">Determine if the SQL statement is valid.</span></span>|  
|<span data-ttu-id="c8946-117">**設計**</span><span class="sxs-lookup"><span data-stu-id="c8946-117">**Design**</span></span>|<span data-ttu-id="c8946-118">[クエリ デザイナー] ダイアログ ボックスを使用して、SQL ステートメントを設計します。</span><span class="sxs-lookup"><span data-stu-id="c8946-118">Design a SQL statement by using the query designer dialog box.</span></span> <span data-ttu-id="c8946-119">詳しくは、「[リレーショナル クエリ デザイナー &#40;SSAS&#41;](relational-query-designer-ssas.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c8946-119">For more information, see [Relational Query Designer &#40;SSAS&#41;](relational-query-designer-ssas.md).</span></span>|  
  
  

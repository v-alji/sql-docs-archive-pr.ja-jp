---
title: 名前の一致 (データソースビューウィザード) (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50cc46db7f582e0aea1570dadc956336ef8be074
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641306"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a><span data-ttu-id="6555e-102">[名前の一致] (データ ソース ビュー ウィザード) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6555e-102">Name Matching (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="6555e-103">**[名前の一致]** ページを使用すると、データ ソース ビューに対して選択したテーブルと、スキーマ内の他のテーブルとの間で可能なリレーションシップを検出するための基準を選択できます。</span><span class="sxs-lookup"><span data-stu-id="6555e-103">Use the **Name Matching** page to select the criterion to use for detecting possible relationships between the tables that you select for the data source view and the other tables in the schema.</span></span> <span data-ttu-id="6555e-104">これらのテーブルの間に物理的な外部キー リレーションシップが存在しない場合は、この条件は、関連テーブルを識別してデータ ソース ビューに追加するときに役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="6555e-104">If no physical foreign key relationships exist between the tables, this criterion helps you identify and add related tables to the data source view.</span></span> <span data-ttu-id="6555e-105">また、名前の一致によって識別される論理リレーションシップもデータ ソース ビューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6555e-105">The logical relationships that are identified by name matching are also added to the data source view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6555e-106">このページは、複数のテーブルを持ち、テーブル間に外部キー リレーションシップがないデータ ソースを選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6555e-106">This page appears only if you select a data source that has multiple tables but no foreign key relationships between any one of the tables.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6555e-107">Options</span><span class="sxs-lookup"><span data-stu-id="6555e-107">Options</span></span>  
 <span data-ttu-id="6555e-108">**[列を一致させることにより、論理リレーションシップを作成する]**</span><span class="sxs-lookup"><span data-stu-id="6555e-108">**Create logical relationships by matching columns**</span></span>  
 <span data-ttu-id="6555e-109">オンにした場合、データ ソース ビューに含めるテーブルと、スキーマ内の他のテーブルとの間で可能な論理的依存関係およびリレーションシップを検出するために、名前の一致条件が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6555e-109">Select to use a name-matching criterion to detect possible logical dependencies and relationships between the tables that you select to include in the data source view and the other tables in the schema.</span></span> <span data-ttu-id="6555e-110">このチェック ボックスをオフにすると、データ ソース内のテーブル間の論理リレーションシップを識別する際に名前の一致条件は使用されません。</span><span class="sxs-lookup"><span data-stu-id="6555e-110">If you clear this check box, no name-matching criterion is used to identify logical relationships between tables in the data source.</span></span>  
  
 <span data-ttu-id="6555e-111">**[外部キーの一致]**</span><span class="sxs-lookup"><span data-stu-id="6555e-111">**Foreign key matches**</span></span>  
 <span data-ttu-id="6555e-112">データ ソース内のテーブルおよびビューの間に論理リレーションシップを作成するために使用する条件を選択します。</span><span class="sxs-lookup"><span data-stu-id="6555e-112">Select the criterion to use for creating logical relationships between tables and views in the data source.</span></span> <span data-ttu-id="6555e-113">文字列の照合において、英数字以外の文字は無視されます。</span><span class="sxs-lookup"><span data-stu-id="6555e-113">Non-alphanumeric characters are ignored in matching strings.</span></span> <span data-ttu-id="6555e-114">たとえば、"Customer ID"、"Customer_ID"、"CustomerID" はすべて一致します。</span><span class="sxs-lookup"><span data-stu-id="6555e-114">For example, "Customer ID", "Customer_ID", "CustomerID" all match.</span></span> <span data-ttu-id="6555e-115">次の表に示すいずれかのオプションを選択すると、特定の条件下でリレーションシップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6555e-115">Select one of the options in the following table to create relationships under the specified conditions.</span></span>  
  
|<span data-ttu-id="6555e-116">Select</span><span class="sxs-lookup"><span data-stu-id="6555e-116">Select</span></span>|<span data-ttu-id="6555e-117">作成されるリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="6555e-117">To create</span></span>|  
|------------|---------------|  
|<span data-ttu-id="6555e-118">**[主キーと同一の名前]**</span><span class="sxs-lookup"><span data-stu-id="6555e-118">**Same name as primary key**</span></span>|<span data-ttu-id="6555e-119">選択されたテーブルの主キー列の名前に一致する列名を持つ、任意のテーブルへの論理リレーションシップ。</span><span class="sxs-lookup"><span data-stu-id="6555e-119">A logical relationship to any table with a column name that matches the name of the primary key column in a selected table.</span></span>|  
|<span data-ttu-id="6555e-120">**[対象のテーブル名と同一の名前]**</span><span class="sxs-lookup"><span data-stu-id="6555e-120">**Same name as destination table name**</span></span>|<span data-ttu-id="6555e-121">選択されたテーブルの名前に一致する列名を持つ、任意のテーブルへの論理リレーションシップ。</span><span class="sxs-lookup"><span data-stu-id="6555e-121">A logical relationship to any table with a column name that matches the name of a selected table.</span></span>|  
|<span data-ttu-id="6555e-122">**一致先のテーブル名と主キー名の組み合わせ**</span><span class="sxs-lookup"><span data-stu-id="6555e-122">**Destination table name + primary key name**</span></span>|<span data-ttu-id="6555e-123">"選択されたテーブルの名前" と "選択されたテーブルの主キー列の名前" を連結した名前に一致する列名を持つ、任意のテーブルへの論理リレーションシップ。</span><span class="sxs-lookup"><span data-stu-id="6555e-123">A logical relationship to any table in which a column name matches the selected table name concatenated with the name of the primary key column for the selected table, in that order.</span></span> <span data-ttu-id="6555e-124">連結した名前において、英数字以外の文字は無視されます。たとえば、"Product ID"、"Product_ID"、"ProductID" はすべて一致します。</span><span class="sxs-lookup"><span data-stu-id="6555e-124">Non-alphanumeric characters within the concatenation are ignored (for example, "Product ID", "Product_ID" and "ProductID" all match).</span></span>|  
  
 <span data-ttu-id="6555e-125">**[説明とサンプル]**</span><span class="sxs-lookup"><span data-stu-id="6555e-125">**Description and sample**</span></span>  
 <span data-ttu-id="6555e-126">選択された条件の説明とサンプルを表示します。</span><span class="sxs-lookup"><span data-stu-id="6555e-126">View a description and a sample of the selected criterion.</span></span>  
  
  

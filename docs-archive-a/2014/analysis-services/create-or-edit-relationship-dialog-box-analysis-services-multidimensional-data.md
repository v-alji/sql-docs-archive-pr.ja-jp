---
title: '[リレーションシップの作成] または [リレーションシップの編集] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4edae3f78ac6b764d91e1be97787fe59d49421db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634735"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="187c7-102">[リレーションシップの作成] または [リレーションシップの編集] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="187c7-102">Create or Edit Relationship Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="187c7-103">**の** [リレーションシップの作成]/[リレーションシップの編集] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、データ ソース ビューでリレーションシップを定義または変更できます。</span><span class="sxs-lookup"><span data-stu-id="187c7-103">Use the **Create/Edit Relationship** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a relationship in a data source view.</span></span> <span data-ttu-id="187c7-104">**[リレーションシップの作成]/[リレーションシップの編集]** ダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="187c7-104">You can display the **Create/Edit Relationship** dialog box by:</span></span>  
  
-   <span data-ttu-id="187c7-105">**データ ソース ビュー デザイナー** の **[ツール バー]** ペインで **[新しいリレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187c7-105">Clicking **New Relationship** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="187c7-106">**データ ソース ビュー デザイナー** の **[テーブル]** ペインまたは **[ダイアグラム]** ペインのどちらかで、テーブルを右クリックして **[新しいリレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187c7-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Relationship**.</span></span>  
  
-   <span data-ttu-id="187c7-107">**データ ソース ビュー デザイナー** の **[ダイアグラム]** ペインでリレーションシップを右クリックして **[リレーションシップの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187c7-107">Right-clicking a relationship in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Relationship**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="187c7-108">**データソースビューデザイナー**では、基になるデータソースに存在しないリレーションシップを作成できます。また、**データソースビューデザイナー**によって作成されたリレーションシップを、基になるデータソースの既存の外部キーリレーションシップから削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="187c7-108">You can create relationships in **Data Source View Designer** that do not exist in the underlying data source, and remove relationships created by **Data Source View Designer** from existing foreign key relationships in the underlying data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="187c7-109">Options</span><span class="sxs-lookup"><span data-stu-id="187c7-109">Options</span></span>  
 <span data-ttu-id="187c7-110">**[作成元 (外部キー) テーブル]**</span><span class="sxs-lookup"><span data-stu-id="187c7-110">**Source (foreign key) table**</span></span>  
 <span data-ttu-id="187c7-111">作成先テーブルの 1 つまたは複数の列への参照を含むテーブルまたは名前付きクエリを選択します。</span><span class="sxs-lookup"><span data-stu-id="187c7-111">Select the table or named query that contains the reference to one or more columns in the destination table.</span></span>  
  
 <span data-ttu-id="187c7-112">**[作成先 (主キー) テーブル]**</span><span class="sxs-lookup"><span data-stu-id="187c7-112">**Destination (primary key) table**</span></span>  
 <span data-ttu-id="187c7-113">作成元テーブルによって参照されている 1 つまたは複数の列を含むテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="187c7-113">Select the table that contains one or more columns referenced by the source table.</span></span> <span data-ttu-id="187c7-114">自己結合の場合、 **[作成元 (外部キー) テーブル]** での選択と同じテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="187c7-114">For self-joins, select the same table selected in **Source (foreign key) table**.</span></span>  
  
 <span data-ttu-id="187c7-115">**[基になる列]**</span><span class="sxs-lookup"><span data-stu-id="187c7-115">**Source columns**</span></span>  
 <span data-ttu-id="187c7-116">作成先テーブルの列を参照する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="187c7-116">Select the columns that reference columns in the destination table.</span></span>  
  
 <span data-ttu-id="187c7-117">**[対象になる列]**</span><span class="sxs-lookup"><span data-stu-id="187c7-117">**Destination columns**</span></span>  
 <span data-ttu-id="187c7-118">作成元テーブルの列によって参照されている列を選択します。</span><span class="sxs-lookup"><span data-stu-id="187c7-118">Select the columns that are referenced by columns in the source table.</span></span>  
  
 <span data-ttu-id="187c7-119">**後ろ向き**</span><span class="sxs-lookup"><span data-stu-id="187c7-119">**Reverse**</span></span>  
 <span data-ttu-id="187c7-120">リレーションシップの方向を反転させます。</span><span class="sxs-lookup"><span data-stu-id="187c7-120">Click to reverse the direction of the relationship.</span></span>  
  
 <span data-ttu-id="187c7-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="187c7-121">**Description**</span></span>  
 <span data-ttu-id="187c7-122">リレーションシップの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="187c7-122">Type an optional description for the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187c7-123">参照</span><span class="sxs-lookup"><span data-stu-id="187c7-123">See Also</span></span>  
 <span data-ttu-id="187c7-124">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="187c7-124">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="187c7-125">データ ソース ビュー デザイナー (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="187c7-125">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  

---
title: サブジェクト領域データベーススキーマのオプション (スキーマ生成ウィザード) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98460332478d02de823addcd113fb9c1e87d6958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639679"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="774aa-102">[サブジェクト領域データベース スキーマのオプション] (スキーマ生成ウィザード) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="774aa-102">Subject Area Database Schema Options (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="774aa-103">**[サブジェクト領域データベース スキーマのオプション]** ページを使用すると、スキーマの生成方法を制御したり、データの保存方法を定義したりできます。</span><span class="sxs-lookup"><span data-stu-id="774aa-103">Use the **Subject Area Database Schema Options** page to control how the schema is generated, as well as to define how data is preserved.</span></span>  
  
## <a name="options"></a><span data-ttu-id="774aa-104">Options</span><span class="sxs-lookup"><span data-stu-id="774aa-104">Options</span></span>  
 <span data-ttu-id="774aa-105">**[所有しているスキーマ]**</span><span class="sxs-lookup"><span data-stu-id="774aa-105">**Owning schema**</span></span>  
 <span data-ttu-id="774aa-106">新しいサブジェクト領域データベース内のスキーマの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="774aa-106">Specifies the name of the schema within the new subject area database.</span></span>  
  
 <span data-ttu-id="774aa-107">**[ディメンション テーブルに主キーを作成する]**</span><span class="sxs-lookup"><span data-stu-id="774aa-107">**Create primary keys on dimension tables**</span></span>  
 <span data-ttu-id="774aa-108">生成されたスキーマのディメンション テーブルに主キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="774aa-108">Creates primary keys on the dimension tables in the generated schema.</span></span> <span data-ttu-id="774aa-109">このオプションを選択しない場合、インデックスは作成されません。</span><span class="sxs-lookup"><span data-stu-id="774aa-109">No index is generated if you do not select this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="774aa-110">このオプションを選択しない場合は、参照整合性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="774aa-110">If you do not select this option, referential integrity is enforced.</span></span>  
  
 <span data-ttu-id="774aa-111">**[インデックスを作成する]**</span><span class="sxs-lookup"><span data-stu-id="774aa-111">**Create indexes**</span></span>  
 <span data-ttu-id="774aa-112">生成されたスキーマの外部キー列にインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="774aa-112">Creates indexes on foreign key columns in the generated schema.</span></span>  
  
 <span data-ttu-id="774aa-113">**[参照整合性を適用する]**</span><span class="sxs-lookup"><span data-stu-id="774aa-113">**Enforce referential integrity**</span></span>  
 <span data-ttu-id="774aa-114">生成されたスキーマで参照整合性を適用します。</span><span class="sxs-lookup"><span data-stu-id="774aa-114">Enforces referential integrity within the generated schema.</span></span> <span data-ttu-id="774aa-115">このオプションを選択しない場合、リレーションシップは作成されますが適用されません。</span><span class="sxs-lookup"><span data-stu-id="774aa-115">If you do not select this option, relationships are created but not enforced.</span></span>  
  
 <span data-ttu-id="774aa-116">**[再生成時にデータを保存する]**</span><span class="sxs-lookup"><span data-stu-id="774aa-116">**Preserve data on regeneration**</span></span>  
 <span data-ttu-id="774aa-117">ウィザードの完了時にサブジェクト領域データベースのデータを保持します。</span><span class="sxs-lookup"><span data-stu-id="774aa-117">Retains data in the subject area database when the wizard finishes.</span></span> <span data-ttu-id="774aa-118">このオプションを選択しない場合、サブジェクト領域データベースのすべてのデータは警告なしに消去されます。</span><span class="sxs-lookup"><span data-stu-id="774aa-118">If you do not select this option, all the data in the subject area database may be erased without warning.</span></span>  
  
 <span data-ttu-id="774aa-119">**[Time テーブルの設定]**</span><span class="sxs-lookup"><span data-stu-id="774aa-119">**Populate time table(s)**</span></span>  
 <span data-ttu-id="774aa-120">ウィザードで Time テーブルにデータを設定する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="774aa-120">Specifies how the wizard populates the time tables.</span></span> <span data-ttu-id="774aa-121">このオプションで使用できる値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="774aa-121">The following table describes the possible values for this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="774aa-122">このオプションは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] をプロジェクト モードで使用して [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] からスキーマ生成ウィザードが呼び出された場合だけ有効になります。</span><span class="sxs-lookup"><span data-stu-id="774aa-122">This option is enabled only if Schema Generation Wizard is called from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] in project mode.</span></span>  
  
|<span data-ttu-id="774aa-123">値</span><span class="sxs-lookup"><span data-stu-id="774aa-123">Value</span></span>|<span data-ttu-id="774aa-124">説明</span><span class="sxs-lookup"><span data-stu-id="774aa-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="774aa-125">[設定]</span><span class="sxs-lookup"><span data-stu-id="774aa-125">Populate</span></span>|<span data-ttu-id="774aa-126">サブジェクト領域の Time テーブルにデータが設定されます。</span><span class="sxs-lookup"><span data-stu-id="774aa-126">The subject area time tables are populated.</span></span>|  
|<span data-ttu-id="774aa-127">[設定しない]</span><span class="sxs-lookup"><span data-stu-id="774aa-127">Do not populate</span></span>|<span data-ttu-id="774aa-128">サブジェクト領域の Time テーブルにデータは設定されません。</span><span class="sxs-lookup"><span data-stu-id="774aa-128">The subject area time tables are not populated.</span></span>|  
|<span data-ttu-id="774aa-129">[空の場合のみ設定]</span><span class="sxs-lookup"><span data-stu-id="774aa-129">Populate only if empty</span></span>|<span data-ttu-id="774aa-130">サブジェクト領域の Time テーブルは、空の場合にだけデータが設定されます。</span><span class="sxs-lookup"><span data-stu-id="774aa-130">The subject area time tables are populated only if they are empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="774aa-131">参照</span><span class="sxs-lookup"><span data-stu-id="774aa-131">See Also</span></span>  
 [<span data-ttu-id="774aa-132">スキーマ生成ウィザードの F1 ヘルプ &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="774aa-132">Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;</span></span>](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  

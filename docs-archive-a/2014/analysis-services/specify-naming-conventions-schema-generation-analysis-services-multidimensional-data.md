---
title: 名前付け規則の指定 (スキーマ生成ウィザード) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.namingconventions.f1
ms.assetid: 02d830ea-5b1f-4485-9f94-d64b8bea592b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e9588b49331934041cad888142d29d189fc1a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643519"
---
# <a name="specify-naming-conventions-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="8a1f6-102">[名前付け規則の指定] (スキーマ生成ウィザード) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="8a1f6-102">Specify Naming Conventions (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8a1f6-103">**[名前付け規則の指定]** ページを使用すると、スキーマ オブジェクトの作成時にスキーマ生成ウィザードが使用する名前付けの規則を定義できます。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-103">Use the **Specify Naming Conventions** page to define the naming conventions that the Schema Generation Wizard uses when creating schema objects.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8a1f6-104">Options</span><span class="sxs-lookup"><span data-stu-id="8a1f6-104">Options</span></span>  
 <span data-ttu-id="8a1f6-105">**オプション**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-105">**Option**</span></span>  
 <span data-ttu-id="8a1f6-106">ウィザードが使用する名前付けの規則を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-106">Specify the naming conventions for the wizard to use.</span></span> <span data-ttu-id="8a1f6-107">次の表では、指定できるオプションを説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-107">The following table describes the options you can specify.</span></span>  
  
|<span data-ttu-id="8a1f6-108">オプション</span><span class="sxs-lookup"><span data-stu-id="8a1f6-108">Option</span></span>|<span data-ttu-id="8a1f6-109">説明</span><span class="sxs-lookup"><span data-stu-id="8a1f6-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8a1f6-110">**Separator**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-110">**Separator**</span></span>|<span data-ttu-id="8a1f6-111">オブジェクト名の語句を区切る文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-111">Specifies the character that separates words in an object name.</span></span> <span data-ttu-id="8a1f6-112">**[値]** 列で、 **[アンダースコア]**、 **[スペース]**、または **[なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-112">In the **Value** column, select **Underscore**, **Space**, or **None**.</span></span> <span data-ttu-id="8a1f6-113">既定値は **[アンダースコア]** です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-113">The default is **Underscore**.</span></span>|  
|<span data-ttu-id="8a1f6-114">**[主キー列プレフィックス]**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-114">**Primary key column prefix**</span></span>|<span data-ttu-id="8a1f6-115">各主キー列の名前の前に置く文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-115">Specifies the string to prefix the name of each primary key column.</span></span> <span data-ttu-id="8a1f6-116">既定値は **[PK]** です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-116">The default is **PK**.</span></span>|  
|<span data-ttu-id="8a1f6-117">**[外部キー列プレフィックス]**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-117">**Foreign key column prefix**</span></span>|<span data-ttu-id="8a1f6-118">各外部キー列の名前の前に置く文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-118">Specifies the string to prefix the name of each foreign key column.</span></span> <span data-ttu-id="8a1f6-119">既定値は **[FK]** です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-119">The default is **FK**.</span></span>|  
|<span data-ttu-id="8a1f6-120">**[属性名サフィックス]**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-120">**Attribute name suffix**</span></span>|<span data-ttu-id="8a1f6-121">各属性列の名前に追加される文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-121">Specifies the string to be appended to the name of each attribute column.</span></span> <span data-ttu-id="8a1f6-122">既定値は**Name**です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-122">The default is **Name**.</span></span>|  
|<span data-ttu-id="8a1f6-123">**[カスタム ロールアップ サフィックス]**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-123">**Custom rollup suffix**</span></span>|<span data-ttu-id="8a1f6-124">各ロールアップ列の名前に追加される文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-124">Specifies the string to be appended to the name of each rollup column.</span></span> <span data-ttu-id="8a1f6-125">既定値は **[CustomRollup]** です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-125">The default is **CustomRollup**.</span></span>|  
|<span data-ttu-id="8a1f6-126">**[カスタム ロールアップ プロパティのサフィックス]**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-126">**Custom rollup Properties suffix**</span></span>|<span data-ttu-id="8a1f6-127">各ロールアップ プロパティ列の名前に追加される文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-127">Specifies the string to be appended to the name of each rollup property column.</span></span> <span data-ttu-id="8a1f6-128">既定値は **[CustomRollupProperties]** です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-128">The default is **CustomRollupProperties**.</span></span>|  
|<span data-ttu-id="8a1f6-129">**[単項演算子サフィックス]**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-129">**Unary operator suffix**</span></span>|<span data-ttu-id="8a1f6-130">各単項演算子列の名前に追加される文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-130">Specifies the string to be appended to the name of each unary operator column.</span></span> <span data-ttu-id="8a1f6-131">既定値は **[UnaryOperator]** です。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-131">The default is **UnaryOperator**.</span></span>|  
  
 <span data-ttu-id="8a1f6-132">**Value**</span><span class="sxs-lookup"><span data-stu-id="8a1f6-132">**Value**</span></span>  
 <span data-ttu-id="8a1f6-133">スキーマの生成時に使用する、 **[オプション]** で指定されたオプションの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1f6-133">Specify a value for the option specified in **Option** that you want to use when the schema is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1f6-134">参照</span><span class="sxs-lookup"><span data-stu-id="8a1f6-134">See Also</span></span>  
 <span data-ttu-id="8a1f6-135">[スキーマ生成ウィザードの F1 ヘルプ &#40;Analysis Services-多次元データ&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8a1f6-135">[Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="8a1f6-136">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="8a1f6-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  

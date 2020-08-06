---
title: '[あいまい参照変換エディター] ([参照テーブル] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce51dd64c9c5807ab23ac645694cfec29a36d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632588"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="ffc45-102">[あいまい参照変換エディター] ([参照テーブル] タブ)</span><span class="sxs-lookup"><span data-stu-id="ffc45-102">Fuzzy Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="ffc45-103">**[あいまい参照変換エディター]** ダイアログ ボックスの **[参照テーブル]** タブを使用すると、参照に使用する変換元テーブルとインデックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ffc45-103">Use the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor** dialog box to specify the source table and the index to use for the lookup.</span></span> <span data-ttu-id="ffc45-104">参照データ ソースは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースのテーブルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc45-104">The reference data source must be a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffc45-105">あいまい参照変換では、参照テーブルの作業用コピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ffc45-105">The Fuzzy Lookup transformation creates a working copy of the reference table.</span></span> <span data-ttu-id="ffc45-106">以降に説明するインデックスは、通常の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インデックスではなく、特別なテーブルを使用してこの作業用テーブルに作成されるものです。</span><span class="sxs-lookup"><span data-stu-id="ffc45-106">The indexes described below are created on this working table by using a special table, not an ordinary [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] index.</span></span> <span data-ttu-id="ffc45-107">**[保存されたインデックスを維持する]** を選択しないと、既存の変換元テーブルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="ffc45-107">The transformation does not modify the existing source tables unless you select **Maintain stored index**.</span></span> <span data-ttu-id="ffc45-108">この場合、参照テーブルに加えられた変更に基づいて作業用テーブルと参照インデックス テーブルを更新するトリガーが、参照テーブルに作成されます。</span><span class="sxs-lookup"><span data-stu-id="ffc45-108">In this case, it creates a trigger on the reference table that updates the working table and the lookup index table based on changes to the reference table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffc45-109">`Exhaustive` `MaxMemoryUsage` あいまい参照変換のおよびプロパティは、[**あいまい参照変換エディター**] では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="ffc45-109">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Lookup transformation are not available in the **Fuzzy Lookup Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="ffc45-110">また、の100より大きい値は、 `MaxOutputMatchesPerInput` **詳細エディター**でのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="ffc45-110">In addition, a value greater than 100 for `MaxOutputMatchesPerInput` can be specified only in the **Advanced Editor**.</span></span> <span data-ttu-id="ffc45-111">これらのプロパティの詳細については、「 [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)」の「あいまい参照変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffc45-111">For more information on these properties, see the Fuzzy Lookup Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="ffc45-112">あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffc45-112">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ffc45-113">オプション</span><span class="sxs-lookup"><span data-stu-id="ffc45-113">Options</span></span>  
 <span data-ttu-id="ffc45-114">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-114">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="ffc45-115">一覧から既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-115">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="ffc45-116">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-116">**New**</span></span>  
 <span data-ttu-id="ffc45-117">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-117">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="ffc45-118">**[新しいインデックスを生成する]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-118">**Generate new index**</span></span>  
 <span data-ttu-id="ffc45-119">参照に使用する新しいインデックスを作成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-119">Specify that the transformation should create a new index to use for the lookup.</span></span>  
  
 <span data-ttu-id="ffc45-120">**[参照テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-120">**Reference table name**</span></span>  
 <span data-ttu-id="ffc45-121">参照テーブルとして使用する既存のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-121">Select the existing table to use as the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="ffc45-122">**[新しいインデックスを保存する]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-122">**Store new index**</span></span>  
 <span data-ttu-id="ffc45-123">新しい参照インデックスを保存する場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-123">Select this option if you want to save the new lookup index.</span></span>  
  
 <span data-ttu-id="ffc45-124">**[新しいインデックス名]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-124">**New index name**</span></span>  
 <span data-ttu-id="ffc45-125">新しい参照インデックスを保存するように指定した場合、そのインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-125">If you have chosen to save the new lookup index, type a descriptive name for the index.</span></span>  
  
 <span data-ttu-id="ffc45-126">**[保存されたインデックスを維持する]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-126">**Maintain stored index**</span></span>  
 <span data-ttu-id="ffc45-127">新しい参照インデックスを保存するように指定した場合、そのインデックスを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でも維持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-127">If you have chosen to save the new lookup index, specify whether you also want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to maintain the index.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffc45-128">**[あいまい参照変換エディター]** ダイアログ ボックスの **[参照テーブル]** タブで **[保存されたインデックスを維持する]** を選択すると、変換ではマネージド ストアド プロシージャを使用してインデックスを維持します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-128">When you select **Maintain stored index** on the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor**, the transformation uses managed stored procedures to maintain the index.</span></span> <span data-ttu-id="ffc45-129">これらのマネージド ストアド プロシージャは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の共通言語ランタイム (CLR) 統合機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-129">These managed stored procedures use the common language runtime (CLR) integration feature in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ffc45-130">既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の CLR 統合は無効です。</span><span class="sxs-lookup"><span data-stu-id="ffc45-130">By default, CLR integration in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not enabled.</span></span> <span data-ttu-id="ffc45-131">**[保存されたインデックスを維持する]** 機能を使用するには、CLR 統合を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc45-131">To use the **Maintain stored index** functionality, you must enable CLR integration.</span></span> <span data-ttu-id="ffc45-132">詳細については、「 [CLR 統合の有効化](../relational-databases/clr-integration/clr-integration-enabling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffc45-132">For more information, see [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md).</span></span>  
>   
>  <span data-ttu-id="ffc45-133">**[保存されたインデックスを維持する]** オプションは CLR 統合を必要とするため、この機能を使用できるのは、CLR 統合が有効になっている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスの参照テーブルを選択した場合だけです。</span><span class="sxs-lookup"><span data-stu-id="ffc45-133">Because the **Maintain stored index** option requires CLR integration, this feature works only when you select a reference table on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where CLR integration is enabled.</span></span>  
  
 <span data-ttu-id="ffc45-134">**[既存のインデックスを使用する]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-134">**Use existing index**</span></span>  
 <span data-ttu-id="ffc45-135">参照に既存のインデックスを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-135">Specify that the transformation should use an existing index for the lookup.</span></span>  
  
 <span data-ttu-id="ffc45-136">**[既存のインデックスの名前]**</span><span class="sxs-lookup"><span data-stu-id="ffc45-136">**Name of an existing index**</span></span>  
 <span data-ttu-id="ffc45-137">以前に作成した参照インデックスを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="ffc45-137">Select a previously created lookup index from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc45-138">参照</span><span class="sxs-lookup"><span data-stu-id="ffc45-138">See Also</span></span>  
 <span data-ttu-id="ffc45-139">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ffc45-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ffc45-140">[あいまい参照変換エディター &#40;[列] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ffc45-140">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 <span data-ttu-id="ffc45-141">[[あいまい参照変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)</span><span class="sxs-lookup"><span data-stu-id="ffc45-141">[Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)</span></span>  
  
  

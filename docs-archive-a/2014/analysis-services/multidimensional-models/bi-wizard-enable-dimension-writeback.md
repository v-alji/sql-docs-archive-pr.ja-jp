---
title: ディメンションの書き戻しを有効にする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
author: minewiskan
ms.author: owend
ms.openlocfilehash: cba4a54e8a51d022c6f84a4c81d32f359a95692a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634117"
---
# <a name="enable-dimension-writeback"></a><span data-ttu-id="a6bcd-102">[ディメンションの書き戻しの有効化]</span><span class="sxs-lookup"><span data-stu-id="a6bcd-102">Enable Dimension Writeback</span></span>
  <span data-ttu-id="a6bcd-103">キューブまたはディメンションにディメンション書き戻し拡張機能を追加すると、ユーザーはディメンション構造とメンバーを手動で変更できます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-103">Add the dimension writeback enhancement to a cube or dimension to allow users to manually modify the dimension structure and members.</span></span> <span data-ttu-id="a6bcd-104">書き込みが可能なディメンションに加えた更新は、ディメンション テーブルに直接記録されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-104">Updates to a write-enabled dimension are recorded directly in the dimension table.</span></span> <span data-ttu-id="a6bcd-105">この拡張機能により、ディメンションの `WriteEnabled` プロパティ設定が変更されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-105">This enhancement changes the `WriteEnabled` property setting for a dimension.</span></span>  
  
 <span data-ttu-id="a6bcd-106">ディメンションの書き戻しを追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[ディメンションの書き戻しの有効化]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-106">To add dimension writeback, you use the Business Intelligence Wizard, and select the **Enable dimension writeback** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="a6bcd-107">次に、ウィザードに従って、ディメンションの書き戻しを適用するディメンションを選択し、そのディメンションにこのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension writeback and setting this option for the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6bcd-108">書き戻しは、SQL Server リレーショナル データベースおよびデータ マートでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-108">Writeback is supported for SQL Server relational databases and data marts only.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="a6bcd-109">ディメンションの選択</span><span class="sxs-lookup"><span data-stu-id="a6bcd-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="a6bcd-110">ウィザードの最初の **[ディメンションの書き戻しの有効化]** ページで、ディメンションの書き戻しを適用するディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-110">On the first **Enable Dimension Writeback** page of the wizard, you specify the dimension to which you want to apply dimension writeback.</span></span> <span data-ttu-id="a6bcd-111">選択したこのディメンションに追加されたディメンション書き戻し拡張機能により、ディメンションが変更されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-111">The dimension writeback enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="a6bcd-112">これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="setting-dimension-writeback-capability"></a><span data-ttu-id="a6bcd-113">ディメンションの書き戻し機能の設定</span><span class="sxs-lookup"><span data-stu-id="a6bcd-113">Setting Dimension Writeback Capability</span></span>  
 <span data-ttu-id="a6bcd-114">ウィザードの **[ディメンションの書き戻しの有効化]** の 2 ページ目で、実際に **[ディメンションへの書き戻しを有効にする]** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-114">On the second **Enable Dimension Writeback** page of the wizard, you actually set the **Enable writeback in the dimension** option.</span></span> <span data-ttu-id="a6bcd-115">このオプションを選択すると、ディメンションの `WriteEnabled` プロパティが自動的に `True` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-115">Selecting this option automatically sets the `WriteEnabled` property of the dimension to `True`.</span></span> <span data-ttu-id="a6bcd-116">このオプションの選択を解除すると、このプロパティは自動的に `False` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-116">Clearing this option automatically sets the property to `False`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6bcd-117">解説</span><span class="sxs-lookup"><span data-stu-id="a6bcd-117">Remarks</span></span>  
 <span data-ttu-id="a6bcd-118">新しいメンバーを作成するときは、ディメンションにすべての属性を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-118">When you create a new member, you must include every attribute in a dimension.</span></span> <span data-ttu-id="a6bcd-119">ディメンションのキー属性値を指定せずにメンバーを挿入することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-119">You cannot insert a member without specifying a value for the key attribute of the dimension.</span></span> <span data-ttu-id="a6bcd-120">このため、メンバーの作成は、ディメンション テーブルに定義されている制約 (NULL 以外のキー値など) に拘束されます。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-120">Therefore, creating members is subject to any constraints (such as non-null key values) that are defined on the dimension table.</span></span> <span data-ttu-id="a6bcd-121">必要に応じて、ディメンション プロパティで指定された列 (`CustomRollupColumn`、`CustomRollupPropertiesColumn`、または `UnaryOperatorColumn` ディメンション プロパティで指定した列など) についても考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-121">You should also consider columns optionally specified by dimension properties, such as columns specified in the `CustomRollupColumn`, `CustomRollupPropertiesColumn` or the `UnaryOperatorColumn` dimension properties.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a6bcd-122">SQL Azure をデータ ソースとして使用して Analysis Services データベースへの書き戻しを実行すると、操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-122">If you use SQL Azure as a data source to perform writeback into an Analysis Services database, the operation fails.</span></span> <span data-ttu-id="a6bcd-123">これは仕様による結果です。既定では、複数のアクティブな結果セット (MARS) を有効にするプロバイダー オプションがオンになっていないためです。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-123">This is by design, because the provider option that enables multiple active result sets (MARS) is not turned on by default.</span></span>  
>   
>  <span data-ttu-id="a6bcd-124">これを回避するには、次の設定を接続文字列に追加し、MARS をサポートして書き戻しを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-124">The workaround is to add the following setting in the connection string, to support MARS and to enable writeback:</span></span>  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  <span data-ttu-id="a6bcd-125">詳細については、「 [MARS&#41;&#40;複数のアクティブな結果セットの使用」を](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6bcd-125">For more information see [Using Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bcd-126">参照</span><span class="sxs-lookup"><span data-stu-id="a6bcd-126">See Also</span></span>  
 [<span data-ttu-id="a6bcd-127">書き込み許可ディメンション</span><span class="sxs-lookup"><span data-stu-id="a6bcd-127">Write-Enabled Dimensions</span></span>](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  

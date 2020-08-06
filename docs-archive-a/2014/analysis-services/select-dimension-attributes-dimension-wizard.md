---
title: '[ディメンションの属性の選択] (ディメンションウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4961092517ce1d38cfd4086ec083a939242652d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634099"
---
# <a name="select-dimension-attributes-dimension-wizard"></a><span data-ttu-id="fa888-102">[ディメンション属性の選択] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="fa888-102">Select Dimension Attributes (Dimension Wizard)</span></span>
  <span data-ttu-id="fa888-103">**[ディメンション属性の選択]** ページを使用すると、作成するディメンションの属性を選択したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="fa888-103">Use the **Select Dimension Attributes** page to select and modify the attributes for the dimension to be created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa888-104">列の値を読み取れない場合は、ウィザード ウィンドウを最大化して、値を確認できるように各列の見出しの幅を変更します。</span><span class="sxs-lookup"><span data-stu-id="fa888-104">If you cannot read the values for any column, maximize the wizard window and change the width of each column heading until you can read the values.</span></span>  
  
 <span data-ttu-id="fa888-105">**ディメンション ウィザードを開くには**</span><span class="sxs-lookup"><span data-stu-id="fa888-105">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="fa888-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラー**で、 **プロジェクトの** [ディメンション] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa888-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa888-107">Options</span><span class="sxs-lookup"><span data-stu-id="fa888-107">Options</span></span>  
 <span data-ttu-id="fa888-108">(チェック ボックスのある列)</span><span class="sxs-lookup"><span data-stu-id="fa888-108">(Column with check boxes)</span></span>  
 <span data-ttu-id="fa888-109">ディメンションに属性を含めます。</span><span class="sxs-lookup"><span data-stu-id="fa888-109">Select to include an attribute in the dimension.</span></span>  
  
 <span data-ttu-id="fa888-110">特定の属性を含めるには、その属性のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fa888-110">To include a specific attribute, select the check box for that attribute.</span></span>  
  
 <span data-ttu-id="fa888-111">すべての属性を含めるには、列ヘッダーのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fa888-111">To include all attributes, select the check box in the column header.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa888-112">キー属性のチェック ボックスをオフにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fa888-112">The check box for the key attribute cannot be cleared.</span></span>  
  
 <span data-ttu-id="fa888-113">**属性名**</span><span class="sxs-lookup"><span data-stu-id="fa888-113">**Attribute Name**</span></span>  
 <span data-ttu-id="fa888-114">利用可能な属性を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fa888-114">Lists the available attributes.</span></span>  
  
 <span data-ttu-id="fa888-115">属性の名前を変更するには、属性名をクリックして、属性の新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fa888-115">To change the name of an attribute, click the attribute name and type a new name for the attribute.</span></span>  
  
 <span data-ttu-id="fa888-116">**[参照を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="fa888-116">**Enable Browsing**</span></span>  
 <span data-ttu-id="fa888-117">エンド ユーザーが参照やフィルター選択にその属性を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fa888-117">Select to make the attribute available to the end user for browsing and filtering.</span></span> <span data-ttu-id="fa888-118">キー属性では、**[参照を有効にする]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa888-118">**Enable Browsing** must be selected for the key attribute.</span></span> <span data-ttu-id="fa888-119">非キー属性では、既定で **[参照を有効にする]** は選択されていないので、非キー属性はメンバー プロパティとしてのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa888-119">For non-key attributes, the default is not to have **Enable Browsing** selected, which causes the non-key attributes to be shown only as member properties.</span></span>  
  
 <span data-ttu-id="fa888-120">ほとんどの場合、属性を参照できるようにするには `AttributeHierarchyEnabled` プロパティを `True`、参照できないようにするには `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa888-120">In most cases, the attribute is made available or not available for browsing by setting the `AttributeHierarchyEnabled` property to `True` or `False`, respectively.</span></span> <span data-ttu-id="fa888-121">ただし、次の 3 つの例では、ウィザードで使用される設定が異なります。</span><span class="sxs-lookup"><span data-stu-id="fa888-121">However, in the following three cases, the wizard uses different settings.</span></span>  
  
|<span data-ttu-id="fa888-122">ケース</span><span class="sxs-lookup"><span data-stu-id="fa888-122">Case</span></span>|<span data-ttu-id="fa888-123">設定</span><span class="sxs-lookup"><span data-stu-id="fa888-123">Settings</span></span>|  
|----------|--------------|  
|<span data-ttu-id="fa888-124">ディメンションに親子階層が含まれており、 **[参照を有効にする]** が選択されていない場合</span><span class="sxs-lookup"><span data-stu-id="fa888-124">A dimension contains a parent-child hierarchy and **Enable Browsing** is not selected</span></span>|<span data-ttu-id="fa888-125">ウィザードでは、キー属性の `AttributeHierarchyEnabled` プロパティは `True` に設定されたままになり、`AttributeHierarchyVisible` プロパティを `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa888-125">The wizard leaves the `AttributeHierarchyEnabled` property set to `True`, and sets the `AttributeHierarchyVisible` attribute to `False` for the key attribute.</span></span>|  
|<span data-ttu-id="fa888-126">ディメンション内のテーブルに、ディメンションに存在しないテーブルへの外部キーが含まれている場合</span><span class="sxs-lookup"><span data-stu-id="fa888-126">A table in a dimension contains a foreign key to a table that is not in the dimension</span></span>|<span data-ttu-id="fa888-127">ウィザードでは、属性として含める外部キーが選択されますが、 **[参照を有効にする]** は選択されません。</span><span class="sxs-lookup"><span data-stu-id="fa888-127">The wizard selects the foreign key as an attribute to be included, but will not select **Enable Browsing**.</span></span> <span data-ttu-id="fa888-128">これらの設定をそのまま使用すると、属性の `AttributeHiearchyEnabled` プロパティは `True` に設定され、`AttributeHierarchyVisible` プロパティは `False` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fa888-128">If you keep these settings, the `AttributeHiearchyEnabled` property of the attribute will be set to `True`, and the `AttributeHierarchyVisible` property will be set to `False`.</span></span>|  
|<span data-ttu-id="fa888-129">NULL 値が許容された外部キー列を使用してアクセスできるスノーフレーク テーブルがディメンションに含まれている場合</span><span class="sxs-lookup"><span data-stu-id="fa888-129">A dimension contains snowflake tables that are reached through nullable foreign key columns</span></span><br /><br /> <span data-ttu-id="fa888-130">および</span><span class="sxs-lookup"><span data-stu-id="fa888-130">-and-</span></span><br /><br /> <span data-ttu-id="fa888-131">スノーフレーク テーブルのキーに基づいた属性の [参照を有効にする] が選択されていない場合</span><span class="sxs-lookup"><span data-stu-id="fa888-131">Enable Browsing for the attribute that is based on the key of the snowflake table is not selected</span></span>|<span data-ttu-id="fa888-132">ウィザードでは、`AttributeHiearchyEnabled` プロパティが `True` に設定され、`AttributeHierarchyVisible` プロパティが `False` に設定されている新しい属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="fa888-132">The wizard will create the new attribute that has the `AttributeHiearchyEnabled` property set to `True`, and the `AttributeHierarchyVisible` property set to `False`.</span></span>|  
  
 <span data-ttu-id="fa888-133">**属性の型**</span><span class="sxs-lookup"><span data-stu-id="fa888-133">**Attribute Type**</span></span>  
 <span data-ttu-id="fa888-134">属性の型を設定します (省略可)。</span><span class="sxs-lookup"><span data-stu-id="fa888-134">(Optional) Set the type for the attribute.</span></span> <span data-ttu-id="fa888-135">既定値は **Regular**です。</span><span class="sxs-lookup"><span data-stu-id="fa888-135">The default value is **Regular**.</span></span> <span data-ttu-id="fa888-136">属性の型によって、クライアント アプリケーションは、属性にどのような情報が含まれているかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="fa888-136">The attribute type provides guidance to client applications on what information the attribute might contain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa888-137">参照</span><span class="sxs-lookup"><span data-stu-id="fa888-137">See Also</span></span>  
 <span data-ttu-id="fa888-138">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="fa888-138">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="fa888-139">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa888-139">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fa888-140">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="fa888-140">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  

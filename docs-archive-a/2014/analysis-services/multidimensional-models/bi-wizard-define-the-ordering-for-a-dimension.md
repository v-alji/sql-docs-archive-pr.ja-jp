---
title: ディメンションの順序を定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd5ea148e374c18c530ba0a15c80dbb23983020
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634121"
---
# <a name="define-the-ordering-for-a-dimension"></a><span data-ttu-id="4d352-102">ディメンションの順序の定義</span><span class="sxs-lookup"><span data-stu-id="4d352-102">Define the Ordering for a Dimension</span></span>
  <span data-ttu-id="4d352-103">キューブまたはディメンションに属性の順序指定の拡張機能を追加して、属性のメンバーの順序付け方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d352-103">Add the attribute ordering enhancement to a cube or dimension to specify how the members of an attribute are ordered.</span></span> <span data-ttu-id="4d352-104">メンバーは、属性の名前またはキー、あるいは、属性リレーションシップに基づいた別の属性の名前またはキーによって順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4d352-104">Members can be ordered by the name or the key of the attribute, or by the name or the key of another attribute (based on an attribute relationship).</span></span> <span data-ttu-id="4d352-105">既定では、名前によってメンバーの順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d352-105">By default, members are ordered by the name.</span></span> <span data-ttu-id="4d352-106">この拡張機能により、ディメンション内にある属性の `OrderBy` および `OrderByAttributeID` プロパティ設定が変更されます。</span><span class="sxs-lookup"><span data-stu-id="4d352-106">This enhancement changes the `OrderBy` and `OrderByAttributeID` property settings for attributes in a dimension.</span></span>  
  
 <span data-ttu-id="4d352-107">属性の順序を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[属性の順序の指定]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4d352-107">To add attribute ordering, you use the Business Intelligence Wizard, and select the **Specify attribute ordering** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="4d352-108">このウィザードでは、属性の順序の適用先となるディメンションを選択し、選択したディメンションの属性の順序付け方法を指定する手順が示されます。</span><span class="sxs-lookup"><span data-stu-id="4d352-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply attribute ordering and specifying how to order the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="4d352-109">ディメンションの選択</span><span class="sxs-lookup"><span data-stu-id="4d352-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="4d352-110">ウィザードの最初の **[属性の順序の指定]** ページで、属性の順序の適用先になるディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d352-110">On the first **Specify Attribute Ordering** page of the wizard, you specify the dimension to which you want to apply attribute ordering.</span></span> <span data-ttu-id="4d352-111">選択したこのディメンションに追加された属性の順序指定の拡張機能により、ディメンションが変更されます。</span><span class="sxs-lookup"><span data-stu-id="4d352-111">The attribute ordering enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="4d352-112">これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="4d352-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="specifying-ordering"></a><span data-ttu-id="4d352-113">順序の指定</span><span class="sxs-lookup"><span data-stu-id="4d352-113">Specifying Ordering</span></span>  
 <span data-ttu-id="4d352-114">**[属性の順序の指定]** の 2 ページ目で、ディメンションのすべての属性を順序付ける方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d352-114">On the second **Specify Attribute Ordering** page of the wizard, you specify how all the attributes in the dimension will be ordered.</span></span>  
  
 <span data-ttu-id="4d352-115">**[属性の並べ替え]** 列で、順序付けに使用する属性を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4d352-115">In the **Ordering Attribute** column, you can change the attribute used to do the ordering.</span></span> <span data-ttu-id="4d352-116">メンバーの順序付けに使用する属性が一覧にない場合は、一覧を下にスクロールして [ **\<New attribute...>** **列の選択**] ダイアログボックスを開くと、ディメンションテーブルの列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4d352-116">If the attribute that you want to use to order members is not in the list, scroll down the list, and then select **\<New attribute...>** to open the **Select a Column** dialog box, where you can select a column in a dimension table.</span></span> <span data-ttu-id="4d352-117">**[列の選択]** ダイアログ ボックスを使用して列を選択すると、属性のメンバーを順序付ける追加の属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4d352-117">Selecting a column by using the **Select a Column** dialog box creates an additional attribute with which to order members of an attribute.</span></span>  
  
 <span data-ttu-id="4d352-118">**[条件]** 列で、 **[キー]** または **[名前]** のどちらによって属性のメンバーを順序付けるかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4d352-118">In the **Criteria** column, you can then select whether to order the members of the attribute by either **Key** or **Name**.</span></span>  
  
  

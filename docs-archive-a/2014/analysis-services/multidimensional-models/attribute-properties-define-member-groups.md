---
title: メンバーグループを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95f9516c7a0077e97af348afa863fe15c8d4528b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741437"
---
# <a name="define-member-groups"></a><span data-ttu-id="a18eb-102">メンバー グループを定義する</span><span class="sxs-lookup"><span data-stu-id="a18eb-102">Define Member Groups</span></span>
  <span data-ttu-id="a18eb-103">特定の属性に多数のメンバーが存在する場合は、そのメンバーをバケットにグループ化すると、階層内のデータを参照するときに表示されるメンバーの数を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="a18eb-103">If an attribute has a large number of members, you can choose to group those members into buckets, reducing the number of members that users see when they browse the data in a hierarchy.</span></span> <span data-ttu-id="a18eb-104">メンバーをグループ化するバケットの数を指定したり、バケットの名前付けスキーマを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="a18eb-104">You can also determine the number of buckets in which the members are groups and set a naming scheme for the buckets.</span></span> <span data-ttu-id="a18eb-105">詳細については、[「属性メンバーのグループ化 (分離)](attribute-properties-group-attribute-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a18eb-105">For more information, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
 <span data-ttu-id="a18eb-106">メンバーをグループ化するには、 **DiscretizationMethod** プロパティを設定します。このプロパティには、 **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ウィンドウからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a18eb-106">You group members by setting the **DiscretizationMethod** property, which is accessed through the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a18eb-107">メンバー グループを作成した場合、ディメンションを処理するまで他のユーザーは変更内容を利用できません。</span><span class="sxs-lookup"><span data-stu-id="a18eb-107">When you create member groups, your changes are not available to users until you process the dimension.</span></span> <span data-ttu-id="a18eb-108">詳細については、「[多次元モデルオブジェクトの処理](processing-a-multidimensional-model-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a18eb-108">For more information, see [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-create-member-groups"></a><span data-ttu-id="a18eb-109">メンバー グループを作成するには</span><span class="sxs-lookup"><span data-stu-id="a18eb-109">To create member groups</span></span>  
  
1.  <span data-ttu-id="a18eb-110">作業するディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="a18eb-110">Open the dimension that you want to work with.</span></span> <span data-ttu-id="a18eb-111">既定では、 **[ディメンション構造]** タブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a18eb-111">The **Dimension Structure** tab opens by default.</span></span>  
  
2.  <span data-ttu-id="a18eb-112">**[属性]** で、グループ化するメンバーの属性を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a18eb-112">In **Attributes**, right-click the attribute whose members you want to group, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a18eb-113">**[DiscretizationMethod]** の横のドロップダウン リストから、メンバーのグループ化方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="a18eb-113">From the drop-down list next to **DiscretizationMethod**, select a method by which to group the members.</span></span> <span data-ttu-id="a18eb-114">**[DiscretizationMethod]** の設定の詳細については、「[属性メンバーのグループ化 (分離)](attribute-properties-group-attribute-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a18eb-114">For more information about **DiscretizationMethod** settings, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
  

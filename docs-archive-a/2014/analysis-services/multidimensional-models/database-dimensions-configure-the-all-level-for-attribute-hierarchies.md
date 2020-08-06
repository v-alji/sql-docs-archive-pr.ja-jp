---
title: 属性階層の (All) レベルを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9874a8c8a6861bc7d9e44271b089e8af3a4c0ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714685"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a><span data-ttu-id="45e97-102">属性階層の (All) レベルの構成</span><span class="sxs-lookup"><span data-stu-id="45e97-102">Configure the (All) Level for Attribute Hierarchies</span></span>
  <span data-ttu-id="45e97-103">では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (All) レベルはシステムによって生成されるオプションのレベルです。</span><span class="sxs-lookup"><span data-stu-id="45e97-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the (All) level is an optional, system-generated level.</span></span> <span data-ttu-id="45e97-104">このレベルには 1 つのメンバーが含まれ、その値は直下のレベルに含まれる全メンバーの値の集計です。</span><span class="sxs-lookup"><span data-stu-id="45e97-104">It contains only one member whose value is the aggregation of the values of all members in the immediately subordinate level.</span></span> <span data-ttu-id="45e97-105">このメンバーを All メンバーと呼びます。</span><span class="sxs-lookup"><span data-stu-id="45e97-105">This member is called the All member.</span></span> <span data-ttu-id="45e97-106">All メンバーはシステムによって生成されるメンバーで、ディメンション テーブルには含まれません。</span><span class="sxs-lookup"><span data-stu-id="45e97-106">It is a system-generated member that is not contained in the dimension table.</span></span> <span data-ttu-id="45e97-107">(All) レベルのメンバーは階層の最上位にあるので、このメンバーの値は、階層内の全メンバーの値の集計値です。</span><span class="sxs-lookup"><span data-stu-id="45e97-107">Because the member in the (All) level is at the top of the hierarchy, the member's value is the consolidated aggregation of the values of all members in the hierarchy.</span></span> <span data-ttu-id="45e97-108">通常、All メンバーは階層の既定メンバーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="45e97-108">The All member often serves as the default member of a hierarchy.</span></span>  
  
 <span data-ttu-id="45e97-109">属性階層に (All) レベルがあるかどうかは属性の `IsAggregatable` プロパティ設定によって決まり、ユーザー定義階層に (All) レベルがあるかどうかはユーザー定義階層の最上位レベルに関する属性の `IsAggregatable` プロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="45e97-109">The presence of an (All) level in an attribute hierarchy depends on the `IsAggregatable` property setting for the attribute and the presence of an (All) level in a user-defined hierarchy depends on the `IsAggregatable` property of the attribute at the top-most level of user-defined hierarchy.</span></span> <span data-ttu-id="45e97-110">`IsAggregatable` プロパティが `True` に設定されている場合は、(All) レベルが存在します。</span><span class="sxs-lookup"><span data-stu-id="45e97-110">If the `IsAggregatable` property is set to `True`, an (All) level will exist.</span></span> <span data-ttu-id="45e97-111">`IsAggregatable` プロパティが `False` に設定されている場合は、階層に (All) レベルはありません。</span><span class="sxs-lookup"><span data-stu-id="45e97-111">A hierarchy has no (All) level if the `IsAggregatable` property is set to `False`.</span></span>  
  
## <a name="establishing-the-topmost-level"></a><span data-ttu-id="45e97-112">最上位レベルの設定</span><span class="sxs-lookup"><span data-stu-id="45e97-112">Establishing the Topmost Level</span></span>  
 <span data-ttu-id="45e97-113">階層のレベルのソース属性で `IsAggregatable` プロパティが `False` に設定されている場合には、そのレベルより上の階層に集計レベルを表示できません。</span><span class="sxs-lookup"><span data-stu-id="45e97-113">If the `IsAggregatable` property is set to `False` on the source attribute of a level in a hierarchy, then no aggregatable level can appear in the hierarchy above that level.</span></span> <span data-ttu-id="45e97-114">非集計レベルは任意の階層の最上位レベルであるか、それより上のレベルのソース属性の `IsAggregatable` プロパティも `False` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45e97-114">A non-aggregatable level must be the topmost level of any hierarchy or the `IsAggregatable` property of the source attributes for any levels above it must also be set to `False`.</span></span>  
  
## <a name="all-member-and-all-level"></a><span data-ttu-id="45e97-115">All メンバーと (All) レベル</span><span class="sxs-lookup"><span data-stu-id="45e97-115">All Member and (All) Level</span></span>  
 <span data-ttu-id="45e97-116">(All) レベルの単一のメンバーは、All メンバーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="45e97-116">The single member of the (All) level is called the All member.</span></span> <span data-ttu-id="45e97-117">ディメンションのプロパティは、 `AttributeAllMemberName` ディメンション内の属性の All メンバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="45e97-117">The `AttributeAllMemberName`property on a dimension specifies the name of the All member for attributes in a dimension.</span></span> <span data-ttu-id="45e97-118">階層の `AllMemberName` プロパティにより、階層の All メンバーの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="45e97-118">The `AllMemberName` property on a hierarchy specifies the name of the All member for the hierarchy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e97-119">参照</span><span class="sxs-lookup"><span data-stu-id="45e97-119">See Also</span></span>  
 [<span data-ttu-id="45e97-120">既定のメンバーの定義</span><span class="sxs-lookup"><span data-stu-id="45e97-120">Define a Default Member</span></span>](attribute-properties-define-a-default-member.md)  
  
  

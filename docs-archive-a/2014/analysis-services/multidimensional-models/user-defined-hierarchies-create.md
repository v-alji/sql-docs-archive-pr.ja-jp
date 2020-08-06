---
title: ユーザー定義階層を作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e870a2b20125132342db1845689b7c2481d623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715770"
---
# <a name="create-user-defined-hierarchies"></a><span data-ttu-id="3e10a-102">ユーザー定義階層の作成</span><span class="sxs-lookup"><span data-stu-id="3e10a-102">Create User-Defined Hierarchies</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3e10a-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、ユーザー定義階層を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3e10a-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lets you create user-defined hierarchies.</span></span> <span data-ttu-id="3e10a-104">階層とは、属性に基づいたレベルのコレクションのことです。</span><span class="sxs-lookup"><span data-stu-id="3e10a-104">A hierarchy is a collection of levels based on attributes.</span></span> <span data-ttu-id="3e10a-105">たとえば、時間階層には、年、四半期、月、週、および日の各レベルが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e10a-105">For example, a time hierarchy might contain the Year, Quarter, Month, Week, and Day levels.</span></span> <span data-ttu-id="3e10a-106">階層によっては、各メンバー属性が、その上位にあるメンバー属性を一意に示すことがあります。</span><span class="sxs-lookup"><span data-stu-id="3e10a-106">In some hierarchies, each member attribute uniquely implies the member attribute above it.</span></span> <span data-ttu-id="3e10a-107">これは、自然階層と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="3e10a-107">This is sometimes referred to as a natural hierarchy.</span></span> <span data-ttu-id="3e10a-108">エンド ユーザーは、階層を使用してキューブ データを参照できます。</span><span class="sxs-lookup"><span data-stu-id="3e10a-108">A hierarchy can be used by end users to browse cube data.</span></span> <span data-ttu-id="3e10a-109">階層を定義するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション デザイナーの [階層] ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e10a-109">Define hierarchies by using the Hierarchies pane of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3e10a-110">ユーザー定義階層を作成すると、階層は *不規則*になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e10a-110">When you create a user-defined hierarchy, the hierarchy might become *ragged*.</span></span> <span data-ttu-id="3e10a-111">不規則階層とは、少なくとも 1 つのメンバーの論理上の親メンバーが、そのメンバーのすぐ上のレベルにない階層です。</span><span class="sxs-lookup"><span data-stu-id="3e10a-111">A ragged hierarchy is where the logical parent member of at least one member is not in the level immediately above the member.</span></span> <span data-ttu-id="3e10a-112">不規則階層を使用している場合は、欠落しているメンバーを表示するかどうか、および欠落しているメンバーを表示する方法を制御する設定があります。</span><span class="sxs-lookup"><span data-stu-id="3e10a-112">If you have a ragged hierarchy, there are settings that control whether the missing members are visible and how to display the missing members.</span></span> <span data-ttu-id="3e10a-113">詳細については、「 [不規則階層](user-defined-hierarchies-ragged-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e10a-113">For more information, see [Ragged Hierarchies](user-defined-hierarchies-ragged-hierarchies.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e10a-114">ユーザー定義階層のデザインと構成に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンス ガイド](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e10a-114">For more information about performance issues related to the design and configuration of user-defined hierarchies, see the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e10a-115">参照</span><span class="sxs-lookup"><span data-stu-id="3e10a-115">See Also</span></span>  
 <span data-ttu-id="3e10a-116">[ユーザー階層のプロパティ](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3e10a-116">[User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span></span>  
 <span data-ttu-id="3e10a-117">[レベルプロパティ &#91;準備中 Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3e10a-117">[Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span></span>  
 [<span data-ttu-id="3e10a-118">親子階層</span><span class="sxs-lookup"><span data-stu-id="3e10a-118">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  

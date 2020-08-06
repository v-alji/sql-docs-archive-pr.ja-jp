---
title: グループ式の例 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128e3fa7aed189fd00072c2c3e961b80f8137c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711657"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="01071-102">グループ式の例 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="01071-102">Group Expression Examples (Report Builder and SSRS)</span></span>
  <span data-ttu-id="01071-103">データ領域では、1 つのフィールドでデータをグループ化することも、グループ化の基準となるデータを識別する、より複雑な式を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="01071-103">In a data region, you can group data by a single field, or create more complex expressions that identify the data on which to group.</span></span> <span data-ttu-id="01071-104">複合式には、複数のフィールドやパラメーター、条件ステートメント、またはカスタム コードなどへの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="01071-104">Complex expressions include references to multiple fields or parameters, conditional statements, or custom code.</span></span> <span data-ttu-id="01071-105">データ領域に対してグループを定義する場合、これらの式を **[グループ]** プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="01071-105">When you define a group for a data region, you add these expressions to the **Group** properties.</span></span> <span data-ttu-id="01071-106">詳細については、「 [データ領域でのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01071-106">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="01071-107">簡単なフィールド式に基づく 2 つ以上のグループをマージするには、各フィールドをグループ定義のグループ式一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="01071-107">To merge two or more groups that are based on simple field expressions, add each field to the group expressions list in the group definition.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a><span data-ttu-id="01071-108">グループ式の例</span><span class="sxs-lookup"><span data-stu-id="01071-108">Examples of Group Expressions</span></span>  
 <span data-ttu-id="01071-109">次の表に、グループの定義に使用できるグループ式の例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="01071-109">The following table provides examples of group expressions that you can use to define a group.</span></span>  
  
|<span data-ttu-id="01071-110">説明</span><span class="sxs-lookup"><span data-stu-id="01071-110">Description</span></span>|<span data-ttu-id="01071-111">式</span><span class="sxs-lookup"><span data-stu-id="01071-111">Expression</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="01071-112">`Region` フィールドでグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01071-112">Group by the `Region` field.</span></span>|`=Fields!Region.Value`|  
|<span data-ttu-id="01071-113">姓と名でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01071-113">Group by last name and first name.</span></span>|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|<span data-ttu-id="01071-114">姓の最初の文字でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01071-114">Group by the first letter of the last name.</span></span>|`=Fields!LastName.Value.Substring(0,1)`|  
|<span data-ttu-id="01071-115">ユーザー選択に基づいてパラメーターでグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01071-115">Group by parameter, based on user selection.</span></span><br /><br /> <span data-ttu-id="01071-116">この例では `GroupBy` パラメーターは、グループ化に使用する有効な選択肢を提供する使用可能な値の一覧に基づいている必要があります。</span><span class="sxs-lookup"><span data-stu-id="01071-116">In this example, the parameter `GroupBy` must be based on an available values list that provides a valid choice to group on.</span></span>|`=Fields(Parameters!GroupBy.Value).Value`|  
|<span data-ttu-id="01071-117">3 つの異なるの年齢範囲でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01071-117">Group by three separate age ranges:</span></span><br /><br /> <span data-ttu-id="01071-118">"21 未満"、"21 ～ 50"、および "51 以上"。</span><span class="sxs-lookup"><span data-stu-id="01071-118">"Under 21", "Between 21 and 50", and "Over 50".</span></span>|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|<span data-ttu-id="01071-119">多数の年齢範囲でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01071-119">Group by many age ranges.</span></span> <span data-ttu-id="01071-120">次の例は、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET で記述され、次の範囲に対して文字列を返すカスタム コードを示します。</span><span class="sxs-lookup"><span data-stu-id="01071-120">This example shows custom code, written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, that returns a string for the following ranges:</span></span><br /><br /> <span data-ttu-id="01071-121">25 以下</span><span class="sxs-lookup"><span data-stu-id="01071-121">25 or Under</span></span><br /><br /> <span data-ttu-id="01071-122">26 ～ 50</span><span class="sxs-lookup"><span data-stu-id="01071-122">26 to 50</span></span><br /><br /> <span data-ttu-id="01071-123">51 ～ 75</span><span class="sxs-lookup"><span data-stu-id="01071-123">51 to 75</span></span><br /><br /> <span data-ttu-id="01071-124">76 以上</span><span class="sxs-lookup"><span data-stu-id="01071-124">Over 75</span></span>|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> <span data-ttu-id="01071-125">カスタム コード :</span><span class="sxs-lookup"><span data-stu-id="01071-125">Custom code:</span></span><br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a><span data-ttu-id="01071-126">参照</span><span class="sxs-lookup"><span data-stu-id="01071-126">See Also</span></span>  
 <span data-ttu-id="01071-127">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01071-127">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="01071-128">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01071-128">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="01071-129">レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="01071-129">Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;</span></span>](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  

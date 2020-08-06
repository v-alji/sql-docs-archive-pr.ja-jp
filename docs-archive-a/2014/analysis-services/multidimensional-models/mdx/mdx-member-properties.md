---
title: メンバープロパティの使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b7fdf989fc23ea70be7d7863f5d4c6ac0b61d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714634"
---
# <a name="using-member-properties-mdx"></a><span data-ttu-id="190ca-102">メンバー プロパティの使用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="190ca-102">Using Member Properties (MDX)</span></span>
  <span data-ttu-id="190ca-103">メンバー プロパティは、各組内の各メンバーに関する基本的な情報を対象とします。</span><span class="sxs-lookup"><span data-stu-id="190ca-103">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="190ca-104">基本的な情報には、メンバー名、親レベル、子の数などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="190ca-104">This basic information includes the member name, parent level, the number of children, and so on.</span></span> <span data-ttu-id="190ca-105">メンバー プロパティは特定レベルのすべてのメンバーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="190ca-105">Member properties are available for all members at a given level.</span></span> <span data-ttu-id="190ca-106">編成の点では、メンバー プロパティは 1 つのディメンション上に格納され、ディメンション別に編成されるデータとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="190ca-106">In terms of organization, member properties are treated as dimensionally organized data, stored on a single dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="190ca-107">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、メンバー プロパティを属性リレーションシップと呼んでいます。</span><span class="sxs-lookup"><span data-stu-id="190ca-107">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], member properties are know as attribute relationships.</span></span> <span data-ttu-id="190ca-108">詳細については、「 [属性リレーションシップ](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190ca-108">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="190ca-109">メンバー プロパティには、 *固有* プロパティと *カスタム*プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="190ca-109">Member properties are either *intrinsic* or *custom*:</span></span>  
  
 <span data-ttu-id="190ca-110">固有メンバー プロパティ</span><span class="sxs-lookup"><span data-stu-id="190ca-110">Intrinsic member properties</span></span>  
 <span data-ttu-id="190ca-111">すべてのメンバーで、固有メンバー プロパティ (たとえば書式設定済みのメンバーの値など) がサポートされます。一方、ディメンションやレベルには、追加の固有ディメンション メンバー プロパティや追加の固有レベル メンバー プロパティ (たとえばメンバー ID など) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="190ca-111">All members support intrinsic member properties, such as the formatted value of a member, while dimensions and levels supply additional intrinsic dimension and level member properties, such as the ID of a member.</span></span>  
  
 <span data-ttu-id="190ca-112">詳細については、「[固有メンバー プロパティ (MDX)](mdx-member-properties-intrinsic-member-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190ca-112">For more information, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
 <span data-ttu-id="190ca-113">ユーザー定義メンバー プロパティ</span><span class="sxs-lookup"><span data-stu-id="190ca-113">User-defined member properties</span></span>  
 <span data-ttu-id="190ca-114">多くの場合、メンバーには追加のプロパティが関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="190ca-114">Members often have additional properties associated with them.</span></span> <span data-ttu-id="190ca-115">たとえば、製品レベルには、各製品の SKU、SRP、重さ、および量のプロパティが用意されているかもしれません。</span><span class="sxs-lookup"><span data-stu-id="190ca-115">For example, the Products level may offer the SKU, SRP, Weight, and Volume properties for each product.</span></span> <span data-ttu-id="190ca-116">これらのプロパティはメンバーではありませんが、製品レベルのメンバーに関する追加情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="190ca-116">These properties are not members, but contain additional information about members at the Products level.</span></span>  
  
 <span data-ttu-id="190ca-117">詳細については、「[ユーザー定義メンバー プロパティ (MDX)](mdx-member-properties-user-defined-member-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190ca-117">For more information, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
 <span data-ttu-id="190ca-118">`PROPERTIES`キーワードまたは[properties](/sql/mdx/properties-mdx)関数を使用すると、組み込みメンバープロパティとユーザー定義メンバープロパティの両方を取得できます。</span><span class="sxs-lookup"><span data-stu-id="190ca-118">Both intrinsic and user-defined member properties can be retrieved through the use of the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
## <a name="using-the-properties-keyword"></a><span data-ttu-id="190ca-119">PROPERTIES キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="190ca-119">Using the PROPERTIES Keyword</span></span>  
 <span data-ttu-id="190ca-120">`PROPERTIES` キーワードを使用して、特定の軸ディメンションに対して使用するメンバー プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="190ca-120">The `PROPERTIES` keyword specifies the member properties that are to be used for a given axis dimension.</span></span> <span data-ttu-id="190ca-121">キーワードは、 `PROPERTIES` `<axis specification>` MDX の[SELECT](/sql/mdx/mdx-data-manipulation-select)ステートメントの句の中に埋め込まれています。</span><span class="sxs-lookup"><span data-stu-id="190ca-121">The `PROPERTIES` keyword is buried within the `<axis specification>` clause of the MDX [SELECT](/sql/mdx/mdx-data-manipulation-select) statement:</span></span>  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 <span data-ttu-id="190ca-122">`<axis_specification>` 句には、以下の構文に示すように、オプションの `<dim_props>` 句が含まれています。</span><span class="sxs-lookup"><span data-stu-id="190ca-122">The `<axis_specification>` clause includes an optional `<dim_props>` clause, as shown in the following syntax:</span></span>  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="190ca-123">`<set>` 値と `<axis_name>` 値の詳細については、「[クエリ軸の内容の指定 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190ca-123">For more information about the `<set>` and `<axis_name>` values, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
 <span data-ttu-id="190ca-124">`<dim_props>` 句によって、`PROPERTIES` キーワードを使用したディメンション、レベル、およびメンバー プロパティのクエリが実行可能になります。</span><span class="sxs-lookup"><span data-stu-id="190ca-124">The `<dim_props>` clause lets you query dimension, level, and member properties using the `PROPERTIES` keyword.</span></span> <span data-ttu-id="190ca-125">`<dim_props>` 句の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="190ca-125">The following syntax shows the formatting of the `<dim_props>` clause:</span></span>  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 <span data-ttu-id="190ca-126">`<property>` 構文のブレークダウンは、クエリの対象となるプロパティに応じて変わります。</span><span class="sxs-lookup"><span data-stu-id="190ca-126">The breakdown of the `<property>` syntax varies depending on the property that you are querying:</span></span>  
  
-   <span data-ttu-id="190ca-127">状況に依存する固有メンバー プロパティには、その前にディメンション名またはレベル名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="190ca-127">Context sensitive intrinsic member properties must be preceded with the name of the dimension or level.</span></span> <span data-ttu-id="190ca-128">ただし、状況に依存しない固有メンバー プロパティはディメンション名やレベル名で修飾できません。</span><span class="sxs-lookup"><span data-stu-id="190ca-128">However, non-context sensitive intrinsic member properties cannot be qualified by the dimension or level name.</span></span> <span data-ttu-id="190ca-129">固有メンバープロパティでキーワードを使用する方法の詳細については `PROPERTIES` 、「 [MDX&#41;&#40;固有メンバープロパティ](mdx-member-properties-intrinsic-member-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190ca-129">For more information about how to use the `PROPERTIES` keyword with intrinsic member properties, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
-   <span data-ttu-id="190ca-130">ユーザー定義メンバー プロパティの前には、そのプロパティが存在しているレベルの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="190ca-130">User-defined member properties should be preceded by the name of the level in which they reside.</span></span> <span data-ttu-id="190ca-131">ユーザー定義メンバープロパティでキーワードを使用する方法の詳細については `PROPERTIES` 、「[ユーザー定義メンバープロパティ &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190ca-131">For more information about how to use the `PROPERTIES` keyword with user-defined member properties, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190ca-132">参照</span><span class="sxs-lookup"><span data-stu-id="190ca-132">See Also</span></span>  
 [<span data-ttu-id="190ca-133">プロパティ値の作成および使用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="190ca-133">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)  
  
  

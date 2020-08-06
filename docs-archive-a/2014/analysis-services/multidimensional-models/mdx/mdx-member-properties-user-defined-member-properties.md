---
title: ユーザー定義メンバープロパティ (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75e5df5a0677ee205b5517f4c7ca89a390426971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714637"
---
# <a name="user-defined-member-properties-mdx"></a><span data-ttu-id="40b30-102">ユーザー定義メンバー プロパティ (MDX)</span><span class="sxs-lookup"><span data-stu-id="40b30-102">User-Defined Member Properties (MDX)</span></span>
  <span data-ttu-id="40b30-103">属性リレーションシップとして、ディメンション内の指定されたレベルにユーザー定義メンバー プロパティを追加できます。</span><span class="sxs-lookup"><span data-stu-id="40b30-103">User-defined member properties can be added to a specific named level in a dimension as attribute relationships.</span></span> <span data-ttu-id="40b30-104">ユーザー定義メンバー プロパティは、階層の `(All)` レベル、または階層そのものには追加できません。</span><span class="sxs-lookup"><span data-stu-id="40b30-104">User-defined member properties cannot be added to the `(All)` level of a hierarchy, or to the hierarchy itself.</span></span>  
  
## <a name="creating-user-defined-member-properties"></a><span data-ttu-id="40b30-105">ユーザー定義メンバー プロパティの作成</span><span class="sxs-lookup"><span data-stu-id="40b30-105">Creating User-Defined Member Properties</span></span>  
 <span data-ttu-id="40b30-106">以下のように、ユーザー インターフェイスを使用して、またはプログラムによって、サーバー ベースのディメンションまたはキューブにユーザー定義メンバー プロパティを追加できます。</span><span class="sxs-lookup"><span data-stu-id="40b30-106">User-defined member properties can be added to server-based dimensions or cubes either through the user interface or programmatically:</span></span>  
  
-   <span data-ttu-id="40b30-107">ユーザー インターフェイスを使用してユーザー定義メンバー プロパティを追加するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でディメンション デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="40b30-107">To add user-defined member properties through the user interface, you use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="40b30-108">詳細については、「 [属性リレーションシップの定義](../attribute-relationships-define.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40b30-108">For more information, see [Define Attribute Relationships](../attribute-relationships-define.md).</span></span>  
  
-   <span data-ttu-id="40b30-109">プログラムによってユーザー定義メンバー プロパティを追加するには、アプリケーションで Analysis Manager Objects (AMO) を使用するか、XML for Analysis (XMLA) と Analysis Services Scripting Language (ASSL) を組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="40b30-109">To add user-defined member properties programmatically, your application can use either Analysis Manager Objects (AMO) or a combination of XML for Analysis (XMLA) and Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="40b30-110">詳細については、「 [属性リレーションシップ](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40b30-110">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
## <a name="retrieving-user-defined-member-properties"></a><span data-ttu-id="40b30-111">ユーザー定義メンバー プロパティの取得</span><span class="sxs-lookup"><span data-stu-id="40b30-111">Retrieving User-Defined Member Properties</span></span>  
 <span data-ttu-id="40b30-112">ユーザー定義メンバープロパティを取得するには、 `PROPERTIES` キーワードまたは[properties](/sql/mdx/properties-mdx)関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="40b30-112">You can retrieve user-defined member properties using either the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="40b30-113">PROPERTIES キーワードを使用したユーザー定義メンバー プロパティの取得</span><span class="sxs-lookup"><span data-stu-id="40b30-113">Using the PROPERTIES Keyword to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="40b30-114">次に示すように、ユーザー定義メンバー プロパティを取得する構文は、固有レベル メンバー プロパティを取得する構文と同様です。</span><span class="sxs-lookup"><span data-stu-id="40b30-114">The syntax that retrieves user-defined member properties is similar to that used to retrieve intrinsic level member properties, as shown in the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 <span data-ttu-id="40b30-115">`PROPERTIES` キーワードは、軸を指定するセット式の後に指定します。</span><span class="sxs-lookup"><span data-stu-id="40b30-115">The `PROPERTIES` keyword appears after the set expression of the axis specification.</span></span> <span data-ttu-id="40b30-116">たとえば、次の MDX クエリの `PROPERTIES` キーワードは `List Price` および `Dealer Price` ユーザー定義メンバー プロパティを取得するもので、1 月に販売された製品を示すセット式の後に指定されています。</span><span class="sxs-lookup"><span data-stu-id="40b30-116">For example, the following MDX query the `PROPERTIES` keyword retrieves the `List Price` and `Dealer Price` user-defined member properties and appears after the set expression that identifies the products sold in January:</span></span>  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="40b30-117">Properties 関数を使用したユーザー定義メンバー プロパティの取得</span><span class="sxs-lookup"><span data-stu-id="40b30-117">Using the Properties Function to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="40b30-118">別の方法として、`Properties` 関数を使ってカスタム メンバー プロパティにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="40b30-118">Alternatively, you can access custom member properties with the `Properties` function.</span></span> <span data-ttu-id="40b30-119">たとえば、次の MDX クエリでは、`WITH` キーワードを使用して、`List Price` メンバー プロパティで構成される計算されるメンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="40b30-119">For example, the following MDX query uses the `WITH` keyword to create a calculated member consisting of the `List Price` member property:</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="40b30-120">計算されるメンバーの作成方法の詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40b30-120">For more information about building calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b30-121">参照</span><span class="sxs-lookup"><span data-stu-id="40b30-121">See Also</span></span>  
 <span data-ttu-id="40b30-122">[MDX&#41;&#40;メンバープロパティを使用する](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="40b30-122">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="40b30-123">プロパティ &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="40b30-123">Properties &#40;MDX&#41;</span></span>](/sql/mdx/properties-mdx)  
  
  

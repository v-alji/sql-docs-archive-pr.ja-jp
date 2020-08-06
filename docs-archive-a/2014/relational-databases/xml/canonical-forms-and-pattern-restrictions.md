---
title: 正規の形式とパターン制限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
author: rothja
ms.author: jroth
ms.openlocfilehash: 569e8c4a01ed1eb9ae26ea9e2f6d471b9aad9fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631703"
---
# <a name="canonical-forms-and-pattern-restrictions"></a><span data-ttu-id="0aacf-102">正規の形式とパターン制限</span><span class="sxs-lookup"><span data-stu-id="0aacf-102">Canonical Forms and Pattern Restrictions</span></span>
  <span data-ttu-id="0aacf-103">XSD パターン ファセットを使用すると、単純型の字句空間を制限できます。</span><span class="sxs-lookup"><span data-stu-id="0aacf-103">The XSD pattern facet allows for the restriction of the lexical space of simple types.</span></span> <span data-ttu-id="0aacf-104">複数の字句表現が可能であるような型にパターン制限を適用すると、一部の値が原因で検証時に予想外の動作が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="0aacf-104">When a pattern restriction is put on a type for which there is more than one possible lexical representation, some values could cause unexpected behavior upon validation.</span></span>  
  
 <span data-ttu-id="0aacf-105">このような動作は、その値の字句表現がデータベースに格納されていないために発生します。</span><span class="sxs-lookup"><span data-stu-id="0aacf-105">This behavior occurs because lexical representations of these values are not stored in the database.</span></span> <span data-ttu-id="0aacf-106">したがって、このような値は、出力としてシリアル化される際に、それぞれの正規表現に変換されます。</span><span class="sxs-lookup"><span data-stu-id="0aacf-106">Therefore, the values are converted to their canonical representations when serialized as output.</span></span> <span data-ttu-id="0aacf-107">ドキュメントに含まれる値の正規の形式が型のパターン制限に準拠していない場合に、ユーザーがそのドキュメントの再挿入を試みると、そのドキュメントは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="0aacf-107">If a document contains a value whose canonical form does not comply with the pattern restriction for its type, the document is rejected if a user tries to reinsert it.</span></span>  
  
 <span data-ttu-id="0aacf-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれを回避するために、再挿入できない値を含む XML ドキュメントはすべて、正規の形式がパターン制限に違反しているという理由で拒否します。</span><span class="sxs-lookup"><span data-stu-id="0aacf-108">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any XML document that contains values that cannot be reinserted, because of the violation of pattern restrictions by their canonical forms.</span></span> <span data-ttu-id="0aacf-109">たとえば、値 "33.000" は、"33 **.0+" というパターン制限が指定されている** xs:decimal\\からの派生型に対して有効であると判断されません。</span><span class="sxs-lookup"><span data-stu-id="0aacf-109">For example, the value "33.000" does not validate against a type derived from **xs:decimal** with a pattern restriction of "33\\.0+".</span></span> <span data-ttu-id="0aacf-110">"33.000" はこのパターンに準拠していますが、正規の形式である "33" がパターンに違反しているためです。</span><span class="sxs-lookup"><span data-stu-id="0aacf-110">Although "33.000" complies with this pattern, the canonical form, "33", does not.</span></span>  
  
 <span data-ttu-id="0aacf-111">したがって、プリミティブ型の `boolean`、`decimal`、`float`、`double`、`dateTime`、`time`、`date`、`hexBinary`、および `base64Binary` から派生した型にパターン ファセットを適用する場合は注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="0aacf-111">Therefore, you should be careful when you apply pattern facets to types derived from the following primitive types: `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary`, and `base64Binary`.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0aacf-112">から警告が発行されます。</span><span class="sxs-lookup"><span data-stu-id="0aacf-112">issues a warning when you add any such components to a schema collection.</span></span>  
  
 <span data-ttu-id="0aacf-113">浮動小数点値の不正確なシリアル化にも同様の問題があります。</span><span class="sxs-lookup"><span data-stu-id="0aacf-113">Imprecise serialization of floating-point values has a similar problem.</span></span> <span data-ttu-id="0aacf-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用されている浮動小数点のシリアル化アルゴリズムにより、近い値が同じ正規表現になることがあり得ます。</span><span class="sxs-lookup"><span data-stu-id="0aacf-114">Because of the floating-point serialization algorithm used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible for similar values to share the same canonical form.</span></span> <span data-ttu-id="0aacf-115">ただし、浮動小数点値がシリアル化され、再挿入される際に、その値がわずかに変化することがあります。</span><span class="sxs-lookup"><span data-stu-id="0aacf-115">When a floating-point value is serialized and then reinserted, its value may change slightly.</span></span> <span data-ttu-id="0aacf-116">その結果、再挿入時にその型の **enumeration**、 **minInclusive**、 **minExclusive**、 **maxInclusive**、または **maxExclusive**の各ファセットに違反する値になることがまれにあります。</span><span class="sxs-lookup"><span data-stu-id="0aacf-116">In rare cases, this may result in a value that violates any of the following facets for its type on reinsertion: **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**, or **maxExclusive**.</span></span> <span data-ttu-id="0aacf-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれを回避するために、シリアル化や再挿入を行えない `xs:float` または `xs:double` から派生した値を拒否します。</span><span class="sxs-lookup"><span data-stu-id="0aacf-117">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any values of types derived from `xs:float` or `xs:double` that cannot be serialized and reinserted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aacf-118">参照</span><span class="sxs-lookup"><span data-stu-id="0aacf-118">See Also</span></span>  
 [<span data-ttu-id="0aacf-119">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="0aacf-119">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

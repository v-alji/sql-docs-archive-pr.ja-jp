---
title: 一意のパーティクル属性の制約 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
f1_keywords:
- unique particle attribution
helpviewer_keywords:
- schema collections [SQL Server], unique particle attribution
- XML schema collections [SQL Server], unique particle attribution
- UPA constraint rule
- unique particle attribution constraint rule
ms.assetid: 6bb879e9-a5ee-402e-94e4-fe8cec5966b0
author: rothja
ms.author: jroth
ms.openlocfilehash: 7416aa4ea14539f3bf633207768783aa439ec818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711778"
---
# <a name="unique-particle-attribution-constraint"></a><span data-ttu-id="190d9-102">一意のパーティクル属性の制約</span><span class="sxs-lookup"><span data-stu-id="190d9-102">Unique Particle Attribution Constraint</span></span>
  <span data-ttu-id="190d9-103">XSD では、UPA (一意のパーティクル属性) 制約の規則によって、複雑なコンテンツ モデルが制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="190d9-103">In XSD, complex content models are constrained by the unique particle attribution (UPA) constraint rule.</span></span> <span data-ttu-id="190d9-104">この規則では、あいまいさを排除し、インスタンス ドキュメント内の各要素が、その親のコンテンツ モデル内の `<xsd:element>` パーティクルまたは `<xsd:any>` パーティクルの 1 つに正確に対応することが必要です。</span><span class="sxs-lookup"><span data-stu-id="190d9-104">This rule requires that each element in an instance document correspond unambiguously to exactly one `<xsd:element>` or `<xsd:any>` particle in its parent's content model.</span></span> <span data-ttu-id="190d9-105">あいまいなコンテンツ モデルになる可能性のある型を含むスキーマは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="190d9-105">Any schema that contains a type with a potentially ambiguous content model is rejected.</span></span>  
  
 <span data-ttu-id="190d9-106">あいまいさの最も一般的な原因は、`<xsd:any>` のワイルドカード文字や、minOccurs < maxOccurs のような可変の出現範囲を持つパーティクルです。</span><span class="sxs-lookup"><span data-stu-id="190d9-106">The most common causes of ambiguity are `<xsd:any>` wildcard characters and particles that have variable occurrence ranges, such as minOccurs < maxOccurs.</span></span> <span data-ttu-id="190d9-107">たとえば、次のコンテンツ モデルでは、<`e1`> 要素は `<xsd:element>` 要素または `<xsd:any>` 要素のどちらにも一致するので、あいまいになります。</span><span class="sxs-lookup"><span data-stu-id="190d9-107">For example, the following content model is ambiguous, because an <`e1`> element could match either the `<xsd:element>` or the `<xsd:any>` element.</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
            <xsd:element name="e1"/>  
            <xsd:any namespace="##any"/>  
        </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="190d9-108">また、次のコンテンツ モデルもあいまいです。</span><span class="sxs-lookup"><span data-stu-id="190d9-108">The following content model is also ambiguous:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:sequence>  
            <xsd:element name="e1" maxOccurs="2"/>  
            <xsd:element name="e2" minOccurs="0"/>  
            <xsd:element name="e1"/>  
        </xsd:sequence>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="190d9-109">`<root><e1/><e2/><e1/></root>` などのドキュメントは明確に検証できますが、 `<root><e1/><e1/></root>` などのドキュメントは明確に検証できません。これは、2 番目の `<xsd:element>` がどの `<e1/>` に対応するかが明確でないためです。</span><span class="sxs-lookup"><span data-stu-id="190d9-109">Although a document such as `<root><e1/><e2/><e1/></root>` can be validated unambiguously, a document such as `<root><e1/><e1/></root>` cannot, because it is not clear to which `<xsd:element>` the second `<e1/>` corresponds.</span></span> <span data-ttu-id="190d9-110">一部のドキュメントを明確に検証できても、あいまいさが残る可能性があるため、スキーマは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="190d9-110">Even though some documents can be validated unambiguously, the schema will be rejected, because of the potential for ambiguity.</span></span>  
  
 <span data-ttu-id="190d9-111">コンテンツ モデルが有効であるためには、先行読み取りを行わなくても、インスタンスを明確に検証できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="190d9-111">Note that for a content model to be valid, it must be possible to validate any instance unambiguously without looking ahead.</span></span> <span data-ttu-id="190d9-112">たとえば、次のコンテンツ モデルについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="190d9-112">For example, consider the following content model:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e2"/>  
           </xsd:sequence>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e3"/>  
           </xsd:sequence>  
       </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="190d9-113">`<root><e1/><e3/></root>`などのドキュメントの場合、シーケンス `<e1/><e3/>` が 2 番目の `<xsd:sequence>`に明確に一致します。</span><span class="sxs-lookup"><span data-stu-id="190d9-113">For a document such as `<root><e1/><e3/></root>`, the sequence `<e1/><e3/>` unambiguously matches the second `<xsd:sequence>`.</span></span> <span data-ttu-id="190d9-114">ただし、 `<xsd:element>` を先行読み取りしないと、 `<e1/>` が対応する `<e3/>`を決定できないので、コンテンツ モデルは UPA 制約規則に違反することになります。</span><span class="sxs-lookup"><span data-stu-id="190d9-114">However, because the `<xsd:element>` to which `<e1/>` corresponds cannot be determined without looking ahead to `<e3/>`, the content model violates the UPA constraint rule.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="190d9-115">詳細情報</span><span class="sxs-lookup"><span data-stu-id="190d9-115">Finding More Information</span></span>  
 <span data-ttu-id="190d9-116">次のドキュメントは W3C (World Wide Web Consortium) が発行したもので、一意のパーティクル属性の制約に関する技術的な説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="190d9-116">The following document is published by the World Wide Web Consortium (W3C) and contains the technical description of the unique particle attribution constraint:</span></span>  
  
 <span data-ttu-id="190d9-117">"XML Schema Part 1: Structures Second Edition, W3C Proposed Edited Recommendation":</span><span class="sxs-lookup"><span data-stu-id="190d9-117">"XML Schema Part 1: Structures Second Edition, W3C Proposed Edited Recommendation":</span></span>  
  
-   <span data-ttu-id="190d9-118">Section 3.8.6: Constraints on Model Group Schema Components</span><span class="sxs-lookup"><span data-stu-id="190d9-118">Section 3.8.6: Constraints on Model Group Schema Components</span></span>  
  
-   <span data-ttu-id="190d9-119">Appendix H: Analysis of the Unique Particle Attribution Constraint (non-normative)</span><span class="sxs-lookup"><span data-stu-id="190d9-119">Appendix H: Analysis of the Unique Particle Attribution Constraint (non-normative)</span></span>  
  
 <span data-ttu-id="190d9-120">ドキュメントを表示するには、[http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="190d9-120">To see the document, visit [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190d9-121">参照</span><span class="sxs-lookup"><span data-stu-id="190d9-121">See Also</span></span>  
 [<span data-ttu-id="190d9-122">XML スキーマ コレクション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="190d9-122">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  

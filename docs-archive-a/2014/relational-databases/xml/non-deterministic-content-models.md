---
title: 非決定的コンテンツ モデル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: rothja
ms.author: jroth
ms.openlocfilehash: 6182ff4a5ee0c9c109f6880c7d3337fb6dd20749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712830"
---
# <a name="non-deterministic-content-models"></a><span data-ttu-id="c9ca2-102">非決定的コンテンツ モデル</span><span class="sxs-lookup"><span data-stu-id="c9ca2-102">Non-Deterministic Content Models</span></span>
  <span data-ttu-id="c9ca2-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) よりも前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、非決定的コンテンツ モデルを含む XML スキーマは拒否されていました。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-103">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejected XML schemas that had non-deterministic content models.</span></span>  
  
 <span data-ttu-id="c9ca2-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1 以降では、オカレンス制約が 0、1、または unbounded の場合、非決定的コンテンツ モデルが許容されます。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1, however, non-deterministic content models are accepted if the occurrence constraints are 0,1, or unbounded.</span></span>  
  
## <a name="example-non-deterministic-content-model-rejected"></a><span data-ttu-id="c9ca2-105">例: 拒否される非決定的コンテンツ モデル</span><span class="sxs-lookup"><span data-stu-id="c9ca2-105">Example: Non-deterministic content model rejected</span></span>  
 <span data-ttu-id="c9ca2-106">次の例では、非決定的コンテンツ モデルを含む XML スキーマの作成を試みています。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-106">The following example attempts to create an XML schema with a non-deterministic content model.</span></span> <span data-ttu-id="c9ca2-107">このコードは、 `<root>` 要素には 2 つの `<a>` 要素で構成されたシーケンスが 1 つ必要なのか、 `<root>` 要素にはそれぞれ `<a>` 要素を含む 2 つのシーケンスが必要なのかが明確ではないので失敗します。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-107">The code fails because it is not clear whether the `<root>` element should have a sequence of two `<a>` elements or if the `<root>` element should have two sequences, each with an `<a>` element.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 <span data-ttu-id="c9ca2-108">このスキーマは、オカレンス制約を固有の位置に移動することにより修正できます。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-108">The schema can be fixed by moving the occurrence constraint to a unique location.</span></span> <span data-ttu-id="c9ca2-109">たとえば、親要素であるシーケンス パーティクルに制約を移動できます。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-109">For example, the constraint can be moved to the containing sequence particle:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 <span data-ttu-id="c9ca2-110">または、子要素に制約を移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-110">Or the constraint can be moved to the contained element:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a><span data-ttu-id="c9ca2-111">例: 許容される非決定的コンテンツ モデル</span><span class="sxs-lookup"><span data-stu-id="c9ca2-111">Example: Non-deterministic content model accepted</span></span>  
 <span data-ttu-id="c9ca2-112">次のスキーマは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 よりも前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では拒否されます。</span><span class="sxs-lookup"><span data-stu-id="c9ca2-112">The following schema would be rejected in versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9ca2-113">参照</span><span class="sxs-lookup"><span data-stu-id="c9ca2-113">See Also</span></span>  
 [<span data-ttu-id="c9ca2-114">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="c9ca2-114">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

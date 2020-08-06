---
title: Xs:QName 型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: rothja
ms.author: jroth
ms.openlocfilehash: 79aaf992243e665738f97c7ee1858528d6fb867c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719736"
---
# <a name="the-xsqname-type"></a><span data-ttu-id="5e8fa-102">The xs:QName Type</span><span class="sxs-lookup"><span data-stu-id="5e8fa-102">The xs:QName Type</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5e8fa-103">では、XML スキーマ制約要素を使用する **xs:QName** から派生した型はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="5e8fa-103">does not support types derived from **xs:QName** by the use of an XML Schema restriction element.</span></span> <span data-ttu-id="5e8fa-104">また、現在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、メンバー型に **QName** を指定した共用体型をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="5e8fa-104">Also, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] currently does not support union types with **QName** as a member type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e8fa-105">例</span><span class="sxs-lookup"><span data-stu-id="5e8fa-105">Example</span></span>  
 <span data-ttu-id="5e8fa-106">次の `CREATE XML SCHEMA COLLECTION` ステートメントでは、共用体のメンバー型に `xs:QName` 型を指定しているため、XML スキーマを読み込めません。</span><span class="sxs-lookup"><span data-stu-id="5e8fa-106">The following `CREATE XML SCHEMA COLLECTION` statements cannot load the XML schema, because they specify the `xs:QName` type as a member type of the union:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 <span data-ttu-id="5e8fa-107">これらのステートメントはどちらも、エラーが発生して失敗します。</span><span class="sxs-lookup"><span data-stu-id="5e8fa-107">Both statements fail with an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8fa-108">参照</span><span class="sxs-lookup"><span data-stu-id="5e8fa-108">See Also</span></span>  
 [<span data-ttu-id="5e8fa-109">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="5e8fa-109">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

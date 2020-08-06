---
title: '&lt;xsd:redefine&gt; 要素 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce439e81cf87e97b4afe6e25a201e1ab0cb2a458
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719731"
---
# <a name="the-ltxsdredefinegt-element"></a><span data-ttu-id="5e475-102">&lt;xsd:redefine&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="5e475-102">The &lt;xsd:redefine&gt; Element</span></span>
  <span data-ttu-id="5e475-103">W3C XSD の **redefine** 要素は、スキーマ コンポーネントの再定義をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5e475-103">The W3C XSD **redefine** element provides support for redefining schema components.</span></span> <span data-ttu-id="5e475-104">ただし、このディレクティブのサポートはパフォーマンスが低下する可能性があり、再定義された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` スキーマに関連付けられているデータ型のすべてのインスタンスを再検証する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="5e475-104">However, support for this directive is potentially costly to performance and also requires that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revalidate all instances of the `xml` data type associated with the redefined schema.</span></span> <span data-ttu-id="5e475-105">このため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれらの要素をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="5e475-105">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support this element.</span></span> <span data-ttu-id="5e475-106">**\<xsd:redefine>** 要素を含む XML スキーマは、サーバーに拒否されます。</span><span class="sxs-lookup"><span data-stu-id="5e475-106">XML schemas that include the **\<xsd:redefine>** element are rejected by the server.</span></span>  
  
 <span data-ttu-id="5e475-107">スキーマまたはスキーマ コンポーネントを更新するには、代わりに次の方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5e475-107">To update a schema or its components, you can do the following instead:</span></span>  
  
1.  <span data-ttu-id="5e475-108">変更されたスキーマ コンポーネントを使用して新しい XML スキーマ コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e475-108">Create a new XML Schema collection with the modified schema components.</span></span>  
  
2.  <span data-ttu-id="5e475-109">`xml`新しい Xml スキーマコレクションを使用するように、再定義する Xml スキーマコレクションを使用するすべてのデータ型 (XML DT) を再入力します。</span><span class="sxs-lookup"><span data-stu-id="5e475-109">Retype all `xml` data types (XML DT) that use the XML Schema collection to be redefined to use the new XML Schema collection instead.</span></span> <span data-ttu-id="5e475-110">そのためには、ALTER TABLE コマンドの ALTER COLUMN オプションを使用して列の型を再指定するか、変数やパラメーターの XML スキーマ コレクション制約を変更します。</span><span class="sxs-lookup"><span data-stu-id="5e475-110">To do this, use the ALTER COLUMN option of the ALTER TABLE command for retyping columns, or change the XML Schema collection constraints on variables or parameters.</span></span>  
  
3.  <span data-ttu-id="5e475-111">古いバージョンの XML スキーマ コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="5e475-111">Drop the old version of the XML Schema collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e475-112">参照</span><span class="sxs-lookup"><span data-stu-id="5e475-112">See Also</span></span>  
 [<span data-ttu-id="5e475-113">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="5e475-113">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

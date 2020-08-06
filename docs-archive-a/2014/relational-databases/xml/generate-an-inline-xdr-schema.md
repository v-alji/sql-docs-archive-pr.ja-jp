---
title: インライン XDR スキーマの生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e2bb7b4b482b79ab5550540dd5b24ffdd8d6636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743074"
---
# <a name="generate-an-inline-xdr-schema"></a><span data-ttu-id="f29b7-102">インライン XDR スキーマの生成</span><span class="sxs-lookup"><span data-stu-id="f29b7-102">Generate an Inline XDR Schema</span></span>
  <span data-ttu-id="f29b7-103">FOR XML の **XMLDATA** ディレクティブは、クエリの結果と合わせてインライン XDR スキーマを返します。</span><span class="sxs-lookup"><span data-stu-id="f29b7-103">The **XMLDATA** directive in FOR XML returns an inline XDR schema together with the query result.</span></span> <span data-ttu-id="f29b7-104">ただし、XDR スキーマは、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンで導入された新しいデータ型や拡張のすべてをサポートしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f29b7-104">However, the XDR schema does not support all the new data types and other enhancements introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="f29b7-105">代わりに、 [XMLSCHEMA ディレクティブ](generate-an-inline-xsd-schema.md)を使用してインライン XSD スキーマを要求できます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-105">Instead, you can request an inline XSD schema by using [the XMLSCHEMA directive](generate-an-inline-xsd-schema.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f29b7-106">FOR XML オプションに対する XMLDATA ディレクティブは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-106">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="f29b7-107">RAW モードと AUTO モードの場合は、XSD 世代を使用してください。</span><span class="sxs-lookup"><span data-stu-id="f29b7-107">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="f29b7-108">EXPLICIT モードでは、XMLDATA ディレクティブに代わる機能はありません。</span><span class="sxs-lookup"><span data-stu-id="f29b7-108">There is no replacement for the XMLDATA directive in EXPLICIT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="f29b7-109">また、インライン XDR スキーマのサポートについては、次の点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="f29b7-109">Also note the following about the inline XDR schema support:</span></span>  
  
-   <span data-ttu-id="f29b7-110">FOR XML クエリの結果に **xml** 型の列が含まれている場合にインライン XDR スキーマを要求すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-110">If the FOR XML query result includes columns of **xml** type and you request an inline XDR schema, an error is returned.</span></span> <span data-ttu-id="f29b7-111">インライン XDR は、xml 型をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f29b7-111">Inline XDR does not support these types.</span></span>  
  
-   <span data-ttu-id="f29b7-112">**(n)varchar(max)** 型と **(n)varbinary(max)** 型は、それぞれ **(n)varchar(n)** 型と **varbinary(n)** 型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-112">The **(n)varchar(max)** and **(n)varbinary(max)** types will be mapped to **(n)varchar(n)** and **varbinary(n)**, respectively.</span></span>  
  
-   <span data-ttu-id="f29b7-113">互換性モードが 90 以上に設定されている場合、 **timestamp** 型の値は **varbinary(8)** 型のデータと見なされてバイナリ データとして扱われ、次のように結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-113">When compatibility mode is set to 90 or higher, **timestamp** values are considered as **varbinary(8)** data, are treated like binary data, and are returned in the result as follows:</span></span>  
  
    -   <span data-ttu-id="f29b7-114">**binary base64** が指定されている場合は、Base64 エンコード形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-114">Base 64 encoding is used when **binary base64** is specified.</span></span>  
  
    -   <span data-ttu-id="f29b7-115">**binary base64** が指定されていない場合、AUTO モードでは URL エンコード形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f29b7-115">URL encoding is used in AUTO mode when **binary base64** is not specified.</span></span>  
  
  

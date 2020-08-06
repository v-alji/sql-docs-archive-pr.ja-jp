---
title: データ型と XML 一括読み込みの動作 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b03423f3bb88166d0d9ce5b0df450d4455e7ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642713"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a><span data-ttu-id="3d516-102">データ型と XML 一括読み込みの動作 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3d516-102">Data Types and XML Bulk Load Behavior (SQLXML 4.0)</span></span>
  <span data-ttu-id="3d516-103">マッピング スキーマで指定されるデータ型 (XSD または XDR 型と `sql:datatype`) は、次の場合を除いて、通常は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3d516-103">The data types that are specified in the mapping schema (XSD or XDR type and `sql:datatype`) are generally ignored, except in the following cases:</span></span>  
  
 <span data-ttu-id="3d516-104">XSD では、次の場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3d516-104">In XSD:</span></span>  
  
-   <span data-ttu-id="3d516-105">XML 一括読み込みではデータ変換が実行されてから Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信されるため、型が `dateTime` または `time` の場合は、`sql:datatype` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d516-105">If the type is `dateTime` or `time`, you must specify the `sql:datatype` because XML Bulk Load performs data conversion before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3d516-106">の型の列に一括読み込みを実行するときに、 `uniqueidentifier` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XSD 値が中かっこ ({および}) を含む GUID である場合、 **sql: datatype = "uniqueidentifier"** を指定して、列に値を挿入する前に中かっこを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d516-106">When you are bulk loading into a column of `uniqueidentifier` type in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and the XSD value is a GUID that includes braces ({ and }), you must specify **sql:datatype="uniqueidentifier"** to remove the braces before the value is inserted into the column.</span></span> <span data-ttu-id="3d516-107">`sql:datatype` を指定しない場合、値はかっこ付きで送られ、挿入は失敗します。</span><span class="sxs-lookup"><span data-stu-id="3d516-107">If `sql:datatype` is not specified, the value is sent with the braces and the insert fails.</span></span>  
  
 <span data-ttu-id="3d516-108">の詳細については `sql:datatype` 、「[データ型の強制型変換」および「sql: datatype 注釈 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d516-108">For more information about `sql:datatype`, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="3d516-109">XDR では、次の場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3d516-109">In XDR:</span></span>  
  
-   <span data-ttu-id="3d516-110">XML 一括読み込みではデータ変換が実行されてから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信されるため、`dt:type` が `datetime`、`time`、`dateTime.tz`、または `time.tz` の場合は、`dt:type` と `sql:datatype` データ型の両方を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d516-110">If the `dt:type` is `datetime`, `time`, `dateTime.tz`, or `time.tz`, you must specify both the `dt:type` and `sql:datatype` data types because XML Bulk Load performs data conversion before it sends the data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3d516-111">XML データの型がである場合は `uuid` 、を `sql:datatype` 指定する必要があります。データが文字列データの場合を除き、 **dt: type = "uuid"** も必要です。</span><span class="sxs-lookup"><span data-stu-id="3d516-111">If your XML data is of type `uuid`, `sql:datatype` must be specified; **dt:type="uuid"** is also required, unless the data is string data.</span></span> <span data-ttu-id="3d516-112">`dt:uuid` を指定しない場合、XML 一括読み込みでは中かっこ付きの文字列が読み込まれ、必要に応じて削除されます。</span><span class="sxs-lookup"><span data-stu-id="3d516-112">If you do not specify `dt:uuid`, XML Bulk Load accepts strings with braces (and removes them if needed).</span></span>  
  
-   <span data-ttu-id="3d516-113">XML データが `bin.base64` または `bin.hex` の場合は、`dt:type` で XML データ型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d516-113">If the XML data is `bin.base64` or `bin.hex`, you must specify the XML data type with `dt:type`.</span></span> <span data-ttu-id="3d516-114">指定すると、XML 一括読み込みではデータを 16 進数表記として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3d516-114">XML Bulk Load then loads the data into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a hexadecimal representation of the data.</span></span>  
  
  

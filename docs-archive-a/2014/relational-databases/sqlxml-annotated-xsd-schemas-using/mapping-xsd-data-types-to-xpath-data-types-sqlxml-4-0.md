---
title: XSD データ型から XPath データ型へのマッピング (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a3bd0b100dd935b5cea0d9ee4565633a9cb80e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644394"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a><span data-ttu-id="10134-102">XSD データ型から XPath データ型へのマッピング (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="10134-102">Mapping XSD Data Types to XPath Data Types (SQLXML 4.0)</span></span>
  <span data-ttu-id="10134-103">XSD スキーマに対して XPath クエリを実行するときに、`xsd:type` 属性に XSD のデータ型が指定されている場合は、XPath でクエリが処理されるときに、指定のデータ型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="10134-103">When an XPath query is executed against an XSD schema and the XSD type is specified in the `xsd:type` attribute, XPath uses the data type specified when it processes the query.</span></span>  
  
 <span data-ttu-id="10134-104">ノードの XPath データ型は、次の表に示すように、スキーマ内に指定されている XSD データ型から派生します。</span><span class="sxs-lookup"><span data-stu-id="10134-104">The XPath data type of a node is derived from the XSD data type in the schema, as shown in the following table.</span></span> <span data-ttu-id="10134-105">ここでは説明のため、EmployeeID というノードを使用します。</span><span class="sxs-lookup"><span data-stu-id="10134-105">(The EmployeeID node is used for the purpose of illustration.)</span></span>  
  
|<span data-ttu-id="10134-106">XSD データ型</span><span class="sxs-lookup"><span data-stu-id="10134-106">XSD data type</span></span>|<span data-ttu-id="10134-107">XDR データ型</span><span class="sxs-lookup"><span data-stu-id="10134-107">XDR data type</span></span>|<span data-ttu-id="10134-108">同等の</span><span class="sxs-lookup"><span data-stu-id="10134-108">Equivalent</span></span><br /><br /> <span data-ttu-id="10134-109">XPath データ型</span><span class="sxs-lookup"><span data-stu-id="10134-109">XPath data type</span></span>|<span data-ttu-id="10134-110">SQL Server</span><span class="sxs-lookup"><span data-stu-id="10134-110">SQL Server</span></span><br /><br /> <span data-ttu-id="10134-111">SQL Server 変換</span><span class="sxs-lookup"><span data-stu-id="10134-111">conversion that is used</span></span>|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|`Base64Binary`<br /><br /> `HexBinary`|`None`<br /><br /> `bin.base64bin.hex`|`Not applicable`|<span data-ttu-id="10134-112">なし</span><span class="sxs-lookup"><span data-stu-id="10134-112">None</span></span><br /><br /> <span data-ttu-id="10134-113">EmployeeID</span><span class="sxs-lookup"><span data-stu-id="10134-113">EmployeeID</span></span>|  
|`Boolean`|`boolean`|`boolean`|<span data-ttu-id="10134-114">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="10134-114">CONVERT(bit, EmployeeID)</span></span>|  
|`Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong`|`number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8`|`number`|<span data-ttu-id="10134-115">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="10134-115">CONVERT(float(53), EmployeeID)</span></span>|  
|`id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI`|`id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid`|`string`|<span data-ttu-id="10134-116">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="10134-116">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|`decimal`|`fixed14.4`|`Not applicable (There is no data type in XPath that is equivalent to the fixed14.4 XDR data type.)`|<span data-ttu-id="10134-117">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="10134-117">CONVERT(money, EmployeeID)</span></span>|  
|`date`|`date`|`string`|<span data-ttu-id="10134-118">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="10134-118">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|`time`|`time`<br /><br /> `time.tz`|`string`|<span data-ttu-id="10134-119">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="10134-119">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
  

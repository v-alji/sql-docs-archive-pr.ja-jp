---
title: CLR でのラージオブジェクト (LOB) パラメーターの処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: ee791c73a6610761c2086723f9e41c2351b37dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742277"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a><span data-ttu-id="f3ead-102">CLR での LOB (ラージ オブジェクト) パラメーターの処理</span><span class="sxs-lookup"><span data-stu-id="f3ead-102">Handling Large Object (LOB) Parameters in the CLR</span></span>
  <span data-ttu-id="f3ead-103">`SqlBytes` と `SqlChars` は、それぞれ、LOB (ラージ オブジェクト) バイナリ型 (`varbinary(max)`) パラメーターと LOB 文字型 (`nvarchar(max)`) パラメーターを渡すために使用します。</span><span class="sxs-lookup"><span data-stu-id="f3ead-103">Use `SqlBytes` and `SqlChars` to pass large object (LOB) binary type (`varbinary(max)`) and LOB character type (`nvarchar(max)`) parameters, respectively.</span></span> <span data-ttu-id="f3ead-104">これらの型を使用すると、マネージド領域に LOB 値全体をコピーするのではなく、データベースから CLR (共通言語ランタイム) ルーチンに LOB 値をストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="f3ead-104">These types allow streaming the LOB values from the database to the common language runtime (CLR) routine, instead of copying the entire value into managed space.</span></span> <span data-ttu-id="f3ead-105">`SqlBinary` と `SqlString` は、小さなバイナリ値や文字列値のみに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3ead-105">`SqlBinary` and `SqlString` should be used only for small binary and character string values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ead-106">参照</span><span class="sxs-lookup"><span data-stu-id="f3ead-106">See Also</span></span>  
 [<span data-ttu-id="f3ead-107">.NET Framework での SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="f3ead-107">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  

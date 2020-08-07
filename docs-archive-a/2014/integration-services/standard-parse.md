---
title: 標準解析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- standard parse [Integration Services]
- locales [Integration Services]
ms.assetid: dfe835b1-ea52-4e18-a23a-5188c5b6f013
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cacff710870d372d6bbf8345e05397857c13a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718495"
---
# <a name="standard-parse"></a><span data-ttu-id="f46b9-102">標準解析</span><span class="sxs-lookup"><span data-stu-id="f46b9-102">Standard Parse</span></span>
  <span data-ttu-id="f46b9-103">標準解析は、ロケール依存型の解析ルーチンのセットであり、Oleaut32.dll と Ole2dsip.dll で使用できるオートメーション データ型変換の API が提供する、すべてのデータ型変換がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f46b9-103">Standard parse is a locale-sensitive set of parsing routines that support all the data type conversions provided by the Automation data type conversion APIs that are available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="f46b9-104">標準解析は、OLE DB 解析 API に相当します。</span><span class="sxs-lookup"><span data-stu-id="f46b9-104">Standard parse is equivalent to the OLE DB parsing APIs.</span></span>  
  
 <span data-ttu-id="f46b9-105">標準解析は、各言語のデータのデータ型変換をサポートしており、データ形式が高速解析でサポートされていない場合に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f46b9-105">Standard parse provides support for data type conversion of international data, and it should be used if the data format is not supported by Fast parse.</span></span> <span data-ttu-id="f46b9-106">オートメーション データ型変換 API の詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/?LinkId=79427)にある「データ型変換 API」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f46b9-106">For more information about the Automation data type conversion API, see "Data Type Conversion APIs" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=79427).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f46b9-107">参照</span><span class="sxs-lookup"><span data-stu-id="f46b9-107">See Also</span></span>  
 [<span data-ttu-id="f46b9-108">高速解析</span><span class="sxs-lookup"><span data-stu-id="f46b9-108">Fast Parse</span></span>](../../2014/integration-services/fast-parse.md)  
  
  

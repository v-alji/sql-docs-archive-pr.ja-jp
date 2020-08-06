---
title: データの解析 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bd34cd83351e31313ae96ff5709ec999a60f2f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633934"
---
# <a name="parsing-data"></a><span data-ttu-id="ff497-102">データの解析</span><span class="sxs-lookup"><span data-stu-id="ff497-102">Parsing Data</span></span>
  <span data-ttu-id="ff497-103">パッケージ内のデータ フローは、異種データ ストア間でデータの抽出や読み込みを行います。データ ストアでは、標準およびカスタムのさまざまなデータ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff497-103">Data flows in packages extract and load data between heterogeneous data stores, which may use a variety of standard and custom data types.</span></span> <span data-ttu-id="ff497-104">データ フローでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の変換元は、データの抽出、文字列データの解析、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型へのデータ変換を行います。</span><span class="sxs-lookup"><span data-stu-id="ff497-104">In a data flow, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources do the work of extracting data, parsing string data, and converting data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="ff497-105">次に続く変換で、データを解析して別のデータ型に変換したり、列のコピーを別のデータ型で作成することもあります。</span><span class="sxs-lookup"><span data-stu-id="ff497-105">Subsequent transformations may parse data to convert it to a different data type, or create column copies with different data types.</span></span> <span data-ttu-id="ff497-106">コンポーネントで使用する式で、引数やオペランドを別のデータ型にキャストする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ff497-106">Expressions used in components may also cast arguments and operands to different data types.</span></span> <span data-ttu-id="ff497-107">さらに、データがデータ ストアに読み込まれるとき、変換先でデータを解析して、変換先が使用するデータ型に変換する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ff497-107">Finally, when the data is loaded into a data store, the destination may parse the data to convert it to a data type that the destination uses.</span></span> <span data-ttu-id="ff497-108">詳細については、「 [Integration Services Data Types](integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff497-108">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="types-of-parsing"></a><span data-ttu-id="ff497-109">解析の種類</span><span class="sxs-lookup"><span data-stu-id="ff497-109">Types of Parsing</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="ff497-110">では、データ変換用に、高速解析と標準解析の、2 種類の解析が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ff497-110">provides two types of parsing for converting data: Fast parse and Standard parse.</span></span>  
  
-   <span data-ttu-id="ff497-111">高速解析は、高速で単純な解析ルーチンのセットで、ロケール固有のデータ型の変換はサポートされません。最も頻繁に使用される日付と時間の形式のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ff497-111">Fast parse is a fast, simple set of parsing routines that does not support locale-specific data type conversions, and supports only the most frequently used date and time formats.</span></span> <span data-ttu-id="ff497-112">詳細については、「 [高速解析](../fast-parse.md)」参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff497-112">For more information, see [Fast Parse](../fast-parse.md).</span></span>  
  
-   <span data-ttu-id="ff497-113">標準解析は、解析ルーチンの大規模なセットで、Oleaut32.dll と Ole2dsip.dll で使用できるオートメーション データ型変換 API で提供される、すべてのデータ型の変換がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff497-113">Standard parse is a rich set of parsing routines that supports all the data type conversions that are provided by the Automation data type conversion APIs available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="ff497-114">詳細については、「 [標準解析](../standard-parse.md)」参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff497-114">For more information, see [Standard Parse](../standard-parse.md).</span></span>  
  
  

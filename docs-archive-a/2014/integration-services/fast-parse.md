---
title: 高速解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- fast parse [Integration Services]
ms.assetid: 6688707d-3c5b-404e-aa2f-e13092ac8d95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 343b8b8b74338512dbf29b3d2efd436df1ffa8ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720252"
---
# <a name="fast-parse"></a><span data-ttu-id="056af-102">高速解析</span><span class="sxs-lookup"><span data-stu-id="056af-102">Fast Parse</span></span>
  <span data-ttu-id="056af-103">高速解析は、データを解析するための高速で単純なルーチンのセットです。</span><span class="sxs-lookup"><span data-stu-id="056af-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="056af-104">これらのルーチンはロケール依存型ではなく、日付、時刻、および整数形式のサブセットのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="056af-104">These routines are not locale-sensitive and they support only a subset of date, time, and integer formats.</span></span>  
  
## <a name="requirements-and-limitations"></a><span data-ttu-id="056af-105">要件と制限</span><span class="sxs-lookup"><span data-stu-id="056af-105">Requirements and Limitations</span></span>  
 <span data-ttu-id="056af-106">パッケージに高速解析を実装することで、ロケール固有の形式と頻繁に使用される ISO 8601 の基本形式や拡張形式では、日付、時刻、および数値データを解釈できなくなりますが、パッケージのパフォーマンスは向上します。</span><span class="sxs-lookup"><span data-stu-id="056af-106">By implementing fast parse, a package forfeits its ability to interpret date, time, and numeric data in locale-specific formats and many frequently used ISO 8601 basic and extended formats, but the package enhances its performance.</span></span> <span data-ttu-id="056af-107">たとえば、高速解析では、YYYYMMDD や YYYY-MM-DD など、通常使用される日付形式表記のみがサポートされます。ロケール固有の解析の実行や、通貨データ内の特殊文字の認識は行いません。また、整数の 16 進数表記と科学的表記は変換できません。</span><span class="sxs-lookup"><span data-stu-id="056af-107">For example, fast parse supports only the most commonly used date format representations such as YYYYMMDD and YYYY-MM-DD, does not perform locale-specific parsing, does not recognize special characters in currency data, and cannot convert hexadecimal or scientific representation of integers.</span></span>  
  
 <span data-ttu-id="056af-108">フラット ファイル ソースまたはデータ変換の変換を使用する場合のみ、高速解析を使用できます。</span><span class="sxs-lookup"><span data-stu-id="056af-108">Fast parse is available only when you use the Flat File source or the Data Conversion transformation.</span></span> <span data-ttu-id="056af-109">著しくパフォーマンスが向上する可能性があるので、可能な限りこれらのデータ フロー コンポーネントで高速解析を使用するよう検討してください。</span><span class="sxs-lookup"><span data-stu-id="056af-109">The increase in performance can be significant, and you should consider using fast parse in these data flow components if you can.</span></span>  
  
 <span data-ttu-id="056af-110">パッケージ内のデータ フローでロケール依存型の解析が必要な場合は、高速解析ではなく、標準的な解析を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="056af-110">If the data flow in the package requires locale-sensitive parsing, standard parse is recommended instead of fast parse.</span></span> <span data-ttu-id="056af-111">たとえば、高速解析では、コンマなど 10 進数の記号が含まれるロケール依存型のデータ、年 - 月 - 日形式以外の日付形式、および通貨記号は認識されません。</span><span class="sxs-lookup"><span data-stu-id="056af-111">For example, fast parse does not recognize locale-sensitive data that includes decimal symbols such as the comma, date formats other than year-month-date formats, and currency symbols.</span></span>  
  
 <span data-ttu-id="056af-112">高速解析では、世紀、年、月など、1 つ以上の日付の部分を暗黙で表記する切り捨て表記は認識されません。</span><span class="sxs-lookup"><span data-stu-id="056af-112">Truncated representations that imply one or more date parts, such as a century, a year, or a month, are not recognized by fast parse.</span></span> <span data-ttu-id="056af-113">たとえば、高速解析は、世紀を暗黙で示して年月を表記する '**-YYMM**' 形式と、年を暗黙で示して月を表記する '**--MM**' 形式の、どちらも認識しません。</span><span class="sxs-lookup"><span data-stu-id="056af-113">For example, fast parse recognizes neither the '**-YYMM**' format, which specifies a year and month in an implied century, nor '**--MM**', which specifies a month in an implied year.</span></span> <span data-ttu-id="056af-114">ただし、有効桁数を減らした表記の一部は認識されます。</span><span class="sxs-lookup"><span data-stu-id="056af-114">However, some representations with reduced precision are recognized.</span></span> <span data-ttu-id="056af-115">たとえば、高速解析では、時間と分のみを示す 'hhmm;' 形式と、年のみを示す '**YYYY**' 形式は認識されます。</span><span class="sxs-lookup"><span data-stu-id="056af-115">For example, fast parse recognizes the 'hhmm;' format, which indicates hour and minute only, and '**YYYY**', which indicates year only.</span></span>  
  
 <span data-ttu-id="056af-116">高速解析は、列レベルで指定されます。</span><span class="sxs-lookup"><span data-stu-id="056af-116">Fast parse is specified at the column level.</span></span> <span data-ttu-id="056af-117">フラット ファイル ソースおよびデータ変換の変換では、出力列で高速解析を指定できます。</span><span class="sxs-lookup"><span data-stu-id="056af-117">In the Flat File source and the Data Conversion transformation, you can specify Fast parse on output columns.</span></span> <span data-ttu-id="056af-118">入力と出力には、ロケール依存型の列およびロケール非依存型の列の、両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="056af-118">Inputs and outputs can include both locale-sensitive and locale-insensitive columns.</span></span>  
  
 <span data-ttu-id="056af-119">高速解析がサポートするデータ形式の詳細については、「 [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) 」および「 [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="056af-119">For more information about the data formats that Fast parse supports, see [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) and [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="056af-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="056af-120">Related Tasks</span></span>  
 [<span data-ttu-id="056af-121">高速解析を設定する</span><span class="sxs-lookup"><span data-stu-id="056af-121">Set Fast Parse</span></span>](../../2014/integration-services/set-fast-parse.md)  
  
  

---
title: 数値データ形式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc54a331c3762e31ba9d9a431aaca7eda6374d8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641054"
---
# <a name="numeric-data-formats"></a><span data-ttu-id="78032-102">数値データ形式</span><span class="sxs-lookup"><span data-stu-id="78032-102">Numeric Data Formats</span></span>
  <span data-ttu-id="78032-103">高速解析は、データを解析するための、高速で単純なロケール非依存型のルーチンのセットです。</span><span class="sxs-lookup"><span data-stu-id="78032-103">Fast parse provides a fast, simple, locale-insensitive set of routines for parsing data.</span></span> <span data-ttu-id="78032-104">高速解析でサポートされているデータ型は、整数データ型の限定された形式のセットのみです。</span><span class="sxs-lookup"><span data-stu-id="78032-104">Fast parse supports only a limited set of formats for integer data types.</span></span>  
  
## <a name="integer-data-types"></a><span data-ttu-id="78032-105">整数データ型</span><span class="sxs-lookup"><span data-stu-id="78032-105">Integer Data Types</span></span>  
 <span data-ttu-id="78032-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で用意されている整数データ型は、DT_I1、DT_UI1、DT_I2、DT_UI2、DT_I4、DT_UI4、DT_I8、および DT_UI8 です。</span><span class="sxs-lookup"><span data-stu-id="78032-106">The integer data types that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides are DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8, and DT_UI8.</span></span> <span data-ttu-id="78032-107">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78032-107">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="78032-108">高速解析では、次の形式の整数データ型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="78032-108">Fast parse supports the following formats for integer data types:</span></span>  
  
-   <span data-ttu-id="78032-109">0 以上の先頭および末尾のスペース、またはタブ ストップ。</span><span class="sxs-lookup"><span data-stu-id="78032-109">Zero or more leading and trailing spaces or tab stops.</span></span> <span data-ttu-id="78032-110">たとえば、値 "  123  " は有効です。</span><span class="sxs-lookup"><span data-stu-id="78032-110">For example, the value "  123  " is valid.</span></span> <span data-ttu-id="78032-111">値がすべてスペースの場合は、0 に評価されます。</span><span class="sxs-lookup"><span data-stu-id="78032-111">A value that is all spaces evaluates to zero.</span></span>  
  
-   <span data-ttu-id="78032-112">先頭の正符号、負符号、または符号なし。</span><span class="sxs-lookup"><span data-stu-id="78032-112">A leading plus sign, minus sign, or neither.</span></span> <span data-ttu-id="78032-113">たとえば、値 +123、-123、および 123 は有効です。</span><span class="sxs-lookup"><span data-stu-id="78032-113">For example, the values +123, -123, and 123 are valid.</span></span>  
  
-   <span data-ttu-id="78032-114">1 つ以上のアラビア数字 (0 ～ 9)。</span><span class="sxs-lookup"><span data-stu-id="78032-114">One or more Hindu-Arabic numerals (0-9).</span></span> <span data-ttu-id="78032-115">たとえば、値 345 は有効です。</span><span class="sxs-lookup"><span data-stu-id="78032-115">For example, the value 345 is valid.</span></span> <span data-ttu-id="78032-116">他の言語の数値はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="78032-116">Other language numerals are not supported.</span></span>  
  
 <span data-ttu-id="78032-117">次の形式を含むデータ形式はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="78032-117">Non-supported data formats include the following:</span></span>  
  
-   <span data-ttu-id="78032-118">特殊文字。</span><span class="sxs-lookup"><span data-stu-id="78032-118">Special characters.</span></span> <span data-ttu-id="78032-119">たとえば、通貨文字 $ はサポートされないため、値 $20 は解析できません。</span><span class="sxs-lookup"><span data-stu-id="78032-119">For example, the currency character $ is not supported, and the value $20 cannot be parsed.</span></span>  
  
-   <span data-ttu-id="78032-120">ライン フィード、キャリッジ リターン、改行なしスペースなどの空白文字。</span><span class="sxs-lookup"><span data-stu-id="78032-120">White-space characters such as line feed, carriage returns, and non-breaking spaces.</span></span> <span data-ttu-id="78032-121">たとえば、値 " 123" は解析できません。</span><span class="sxs-lookup"><span data-stu-id="78032-121">For example, the value " 123" cannot be parsed.</span></span>  
  
-   <span data-ttu-id="78032-122">整数の 16 進表記。</span><span class="sxs-lookup"><span data-stu-id="78032-122">Hexadecimal representations of integers.</span></span> <span data-ttu-id="78032-123">たとえば、値 2EE は解析できません。</span><span class="sxs-lookup"><span data-stu-id="78032-123">For example, the value 2EE cannot be parsed.</span></span>  
  
-   <span data-ttu-id="78032-124">整数の科学的表記法。</span><span class="sxs-lookup"><span data-stu-id="78032-124">Scientific notation representation of integers.</span></span> <span data-ttu-id="78032-125">たとえば、値 1E+10 は解析できません。</span><span class="sxs-lookup"><span data-stu-id="78032-125">For example, the value 1E+10 cannot be parsed.</span></span>  
  
 <span data-ttu-id="78032-126">次の形式は、整数の出力データ形式です。</span><span class="sxs-lookup"><span data-stu-id="78032-126">The following formats are output data formats for integers:</span></span>  
  
-   <span data-ttu-id="78032-127">負の数値を表す負符号、および正の数値を表す符号なし。</span><span class="sxs-lookup"><span data-stu-id="78032-127">A minus sign for negative numbers and nothing for positive ones.</span></span>  
  
-   <span data-ttu-id="78032-128">空白なし。</span><span class="sxs-lookup"><span data-stu-id="78032-128">No white spaces.</span></span>  
  
-   <span data-ttu-id="78032-129">1 つ以上のアラビア数字 (0 ～ 9)。</span><span class="sxs-lookup"><span data-stu-id="78032-129">One or more Hindu-Arabic numerals (0-9).</span></span>  
  
  

---
title: データの切り捨て (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0c4280c9eacd22ebf84bf1570d485de51cab09b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645191"
---
# <a name="data-truncation-ssis"></a><span data-ttu-id="e4896-102">データの切り捨て (SSIS)</span><span class="sxs-lookup"><span data-stu-id="e4896-102">Data Truncation (SSIS)</span></span>
  <span data-ttu-id="e4896-103">式により誤ってデータが切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e4896-103">An expression may inadvertently cause data to be truncated.</span></span> <span data-ttu-id="e4896-104">データの切り捨ては次の環境で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e4896-104">Truncation can occur under the following circumstances:</span></span>  
  
-   <span data-ttu-id="e4896-105">文字列。</span><span class="sxs-lookup"><span data-stu-id="e4896-105">Strings.</span></span> <span data-ttu-id="e4896-106">たとえば、DT_WSTR データ型の文字列データを、文字長単位で同じ長さの文字列に変換する場合、DT_STR データ型に変換すると、元の文字列に 2 バイト文字が含まれている場合にデータが失われます。</span><span class="sxs-lookup"><span data-stu-id="e4896-106">For example, translating string data with a DT_WSTR data type to the same length string, measured in characters, with a DT_STR data type causes data loss if the original string contains double-byte characters.</span></span>  
  
-   <span data-ttu-id="e4896-107">有効桁。</span><span class="sxs-lookup"><span data-stu-id="e4896-107">Significant digits.</span></span> <span data-ttu-id="e4896-108">たとえば、整数値を DT_I4 データ型から DT_I2 データ型にキャストする場合、または符号なし整数を符号付き整数にキャストする場合などです。</span><span class="sxs-lookup"><span data-stu-id="e4896-108">For example, casting an integer from a DT_I4 data type to a DT_I2 data type or an unsigned integer to a signed integer.</span></span>  
  
-   <span data-ttu-id="e4896-109">有効桁以外の桁。</span><span class="sxs-lookup"><span data-stu-id="e4896-109">Insignificant digits.</span></span> <span data-ttu-id="e4896-110">たとえば、実数を DT_R8 データ型から DT_R4 データ型にキャストする場合、または整数を DT_I4 データ型から DT_R4 データ型にキャストする場合などです。</span><span class="sxs-lookup"><span data-stu-id="e4896-110">For example, casting a real number from a DT_R8 to a DT_R4 or an integer from a DT_I4 data type to a DT_R4 data type.</span></span>  
  
 <span data-ttu-id="e4896-111">式エバリュエーターは切り捨てが発生する可能性のある明示的なキャストを識別し、式が解析されるときに警告を発生します。</span><span class="sxs-lookup"><span data-stu-id="e4896-111">The expression evaluator identifies explicit casts that may cause truncation and issues a warning when the expression is parsed.</span></span> <span data-ttu-id="e4896-112">たとえば、30 文字の文字列が 20 文字の文字列にキャストされる場合、式エバリュエーターで警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="e4896-112">For example, the expression evaluator warns you if a 30-character string is cast into a 20-character string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4896-113">切り捨ては実行時にはチェックされません。データは警告なしで切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="e4896-113">Truncation is not checked at run time; data is truncated without warning.</span></span> <span data-ttu-id="e4896-114">ただし、ほとんどのデータ アダプターおよび変換では、エラー行の処理を実行できるエラー出力がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e4896-114">However, most data adapters and transformations support error outputs that can handle the disposition of error rows.</span></span> <span data-ttu-id="e4896-115">データの切り捨て処理の詳細については、「[データのエラー処理](../data-flow/error-handling-in-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4896-115">For more information about handling truncation of data, see [Error Handling in Data](../data-flow/error-handling-in-data.md).</span></span>  
  
  

---
title: Cast (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CAST function
- cast operator
- converting data types [Integration Services]
- data types [Integration Services], expressions
- data types [Integration Services], converting
ms.assetid: d4e915cc-1c7b-4b2e-93b0-13a8b0cb9242
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65d60eca4340b65b8a82855c3f2b29a6cda56e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736666"
---
# <a name="cast-ssis-expression"></a><span data-ttu-id="e5114-102">Cast (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e5114-102">Cast (SSIS Expression)</span></span>
  <span data-ttu-id="e5114-103">式のあるデータ型を別のデータ型に明示的に変換します。</span><span class="sxs-lookup"><span data-stu-id="e5114-103">Explicitly converts an expression from one data type to a different data type.</span></span> <span data-ttu-id="e5114-104">キャスト演算子は、切り捨て演算子としても機能できます。</span><span class="sxs-lookup"><span data-stu-id="e5114-104">The cast operator can also function as a truncation operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5114-105">構文</span><span class="sxs-lookup"><span data-stu-id="e5114-105">Syntax</span></span>

```

(type_spec) expression

```

## <a name="arguments"></a><span data-ttu-id="e5114-106">引数</span><span class="sxs-lookup"><span data-stu-id="e5114-106">Arguments</span></span>
 <span data-ttu-id="e5114-107">*type_spec*有効な [!INCLUDE[ssIS](../../includes/ssis-md.md)] データ型です。</span><span class="sxs-lookup"><span data-stu-id="e5114-107">*type_spec* Is a valid [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span>

 <span data-ttu-id="e5114-108">*式*有効な式です。</span><span class="sxs-lookup"><span data-stu-id="e5114-108">*expression* Is a valid expression.</span></span>

## <a name="result-types"></a><span data-ttu-id="e5114-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="e5114-109">Result Types</span></span>
 <span data-ttu-id="e5114-110">*type_spec*のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="e5114-110">The data type of *type_spec*.</span></span> <span data-ttu-id="e5114-111">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5114-111">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="e5114-112">解説</span><span class="sxs-lookup"><span data-stu-id="e5114-112">Remarks</span></span>
 <span data-ttu-id="e5114-113">次の図は、有効なキャスト演算を示しています。</span><span class="sxs-lookup"><span data-stu-id="e5114-113">The following diagram shows legal cast operations.</span></span>

 <span data-ttu-id="e5114-114">![データ型間の有効および無効なキャスト](../media/data-conversion.gif "データ型間の有効および無効なキャスト")</span><span class="sxs-lookup"><span data-stu-id="e5114-114">![Legal and not legal casts between data types](../media/data-conversion.gif "Legal and not legal casts between data types")</span></span>

 <span data-ttu-id="e5114-115">一部のデータ型にキャストする場合、パラメーターが必要となります。</span><span class="sxs-lookup"><span data-stu-id="e5114-115">Casting to some data types requires parameters.</span></span> <span data-ttu-id="e5114-116">次の表に、パラメーターが必要なデータ型とそのパラメーターの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="e5114-116">The following table lists these data types and their parameters.</span></span>

|<span data-ttu-id="e5114-117">データ型</span><span class="sxs-lookup"><span data-stu-id="e5114-117">Data type</span></span>|<span data-ttu-id="e5114-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5114-118">Parameter</span></span>|<span data-ttu-id="e5114-119">例</span><span class="sxs-lookup"><span data-stu-id="e5114-119">Example</span></span>|
|---------------|---------------|-------------|
|<span data-ttu-id="e5114-120">DT_STR</span><span class="sxs-lookup"><span data-stu-id="e5114-120">DT_STR</span></span>|<span data-ttu-id="e5114-121">*charcount*</span><span class="sxs-lookup"><span data-stu-id="e5114-121">*charcount*</span></span><br /><br /> <span data-ttu-id="e5114-122">*コードページ*</span><span class="sxs-lookup"><span data-stu-id="e5114-122">*codepage*</span></span>|<span data-ttu-id="e5114-123">(DT_STR,30,1252) は、1252 コード ページを使用して、30 バイトまたは 30 文字を DT_STR データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-123">(DT_STR,30,1252) casts 30 bytes, or 30 single characters, to the DT_STR data type using the 1252 code page.</span></span>|
|<span data-ttu-id="e5114-124">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="e5114-124">DT_WSTR</span></span>|<span data-ttu-id="e5114-125">*Charcount*</span><span class="sxs-lookup"><span data-stu-id="e5114-125">*Charcount*</span></span>|<span data-ttu-id="e5114-126">(DT_WSTR,20) は、20 バイト ペアまたは 20 Unicode 文字を DT_WSTR データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-126">(DT_WSTR,20) casts 20 byte pairs, or 20 Unicode characters, to the DT_WSTR data type.</span></span>|
|<span data-ttu-id="e5114-127">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="e5114-127">DT_BYTES</span></span>|<span data-ttu-id="e5114-128">*Bytecount*</span><span class="sxs-lookup"><span data-stu-id="e5114-128">*Bytecount*</span></span>|<span data-ttu-id="e5114-129">(DT_BYTES,50) は、50 バイトを DT_BYTES データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-129">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|
|<span data-ttu-id="e5114-130">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="e5114-130">DT_DECIMAL</span></span>|<span data-ttu-id="e5114-131">*スケール*</span><span class="sxs-lookup"><span data-stu-id="e5114-131">*Scale*</span></span>|<span data-ttu-id="e5114-132">(DT_DECIMAL,2) は、数値を小数点以下 2 桁の DT_DECIMAL データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-132">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|
|<span data-ttu-id="e5114-133">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="e5114-133">DT_NUMERIC</span></span>|<span data-ttu-id="e5114-134">*[精度]*</span><span class="sxs-lookup"><span data-stu-id="e5114-134">*Precision*</span></span><br /><br /> <span data-ttu-id="e5114-135">*スケール*</span><span class="sxs-lookup"><span data-stu-id="e5114-135">*Scale*</span></span>|<span data-ttu-id="e5114-136">(DT_NUMERIC,10,3) は、数値を有効桁数 10 桁で小数点以下 3 桁の DT_NUMERIC データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-136">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|
|<span data-ttu-id="e5114-137">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="e5114-137">DT_TEXT</span></span>|<span data-ttu-id="e5114-138">*コードページ*</span><span class="sxs-lookup"><span data-stu-id="e5114-138">*Codepage*</span></span>|<span data-ttu-id="e5114-139">(DT_TEXT,1252) は、1252 コード ページを使用して、値を DT_TEXT データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-139">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|

 <span data-ttu-id="e5114-140">文字列を DT_DATE にキャストする場合、またはその逆のキャストを行う場合、変換のロケールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e5114-140">When a string is cast to a DT_DATE, or vice versa, the locale of the transformation is used.</span></span> <span data-ttu-id="e5114-141">ただし、ロケール設定で ISO 形式を使用するかどうかにかかわらず、日付は YYYY-MM-DD の ISO 形式となります。</span><span class="sxs-lookup"><span data-stu-id="e5114-141">However, the date is in the ISO format of YYYY-MM-DD, regardless of whether the locale preference uses the ISO format.</span></span>

> [!NOTE]
>  <span data-ttu-id="e5114-142">文字列を DT_DATE 以外の日付データ型に変換するには、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5114-142">To convert a string to a date data type other than DT_DATE, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="e5114-143">コード ページがマルチバイト文字の場合、バイト数と文字数は異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5114-143">If the code page is a multibyte character code page, the number of bytes and characters may differ.</span></span> <span data-ttu-id="e5114-144">DT_WSTR データ型から同じ *charcount* 値の DT_STR データ型にキャストすると、変換された文字列で最後の文字が切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5114-144">Casting from a DT_WSTR to a DT_STR with the same *charcount* value may cause truncation of the final characters in the converted string.</span></span> <span data-ttu-id="e5114-145">変換先のテーブルの列で十分なストレージが使用できる場合、 *charcount* パラメーターの値は、マルチバイト コード ページで必要となるバイト数を反映するように設定します。</span><span class="sxs-lookup"><span data-stu-id="e5114-145">If sufficient storage is available in the column of the destination table, set the value of the *charcount* parameter to reflect the number of bytes that the multibyte code page requires.</span></span> <span data-ttu-id="e5114-146">たとえば、936 コード ページを使用して、文字データを DT_STR データ型にキャストする場合、データに含まれると考えられる文字数の 2 倍の値を *charcount* に設定する必要があります。また、UTF-8 コード ページを使用して文字データをキャストする場合、 *charcount* は、予想される文字数の 4 倍の値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5114-146">For example, if you cast character data to a DT_STR data type using the 936 code page, you should set *charcount* to a value up to two times greater than the number of characters that you expect the data to contain; if you cast character data using the UTF-8 code page, you should set *charcount* to a value up to four times greater.</span></span>

 <span data-ttu-id="e5114-147">日付データ型の構造の詳細については、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5114-147">For more information about the structure of date data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="ssis-expression-examples"></a><span data-ttu-id="e5114-148">SSIS 式の例</span><span class="sxs-lookup"><span data-stu-id="e5114-148">SSIS Expression Examples</span></span>
 <span data-ttu-id="e5114-149">この例では、数値を整数にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-149">This example casts a numeric value to an integer.</span></span>

```
(DT_I4) 3.57
```

 <span data-ttu-id="e5114-150">この例では、1252 コード ページを使用して整数を文字列にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-150">This example casts an integer to a character string using the 1252 code page.</span></span>

```
(DT_STR,1,1252)5
```

 <span data-ttu-id="e5114-151">この例では、3 文字の文字列を 2 バイト文字にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-151">This example casts a three-character string to double-byte characters.</span></span>

```
(DT_WSTR,3)"Cat"
```

 <span data-ttu-id="e5114-152">この例では、整数を小数点以下 2 桁の 10 進数にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-152">This example casts an integer to a decimal with a scale of two.</span></span>

```
(DT_DECIMAl,2)500
```

 <span data-ttu-id="e5114-153">この例では、整数を有効桁数 7 桁で小数点以下 3 桁の数値にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-153">This example casts an integer to a numeric with a precision of seven and scale of three.</span></span>

```
(DT_NUMERIC,7,3)4000
```

 <span data-ttu-id="e5114-154">この例では、 **nvarchar** データ型で定義され、長さが 50 の **FirstName** 列の値を、1252 コード ページを使用して文字列にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-154">This example casts values in the **FirstName** column, defined with an **nvarchar** data type and a length of 50, to a character string using the 1252 code page.</span></span>

```
(DT_STR,50,1252)FirstName
```

 <span data-ttu-id="e5114-155">この例では、DT_DBDATE 型の **DateFirstPurchase** 列の値を、長さ 20 の Unicode 文字列にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-155">This example casts values in the **DateFirstPurchase** column of type DT_DBDATE, to a Unicode character string with a length of 20.</span></span>

```
(DT_WSTR,20)DateFirstPurchase
```

 <span data-ttu-id="e5114-156">この例は、文字リテラル "True" をブール型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-156">This example casts the string literal "True" to a Boolean.</span></span>

```
(DT_BOOL)"True"
```

 <span data-ttu-id="e5114-157">この例では、文字列リテラルを DT_DBDATE にキャストします。</span><span class="sxs-lookup"><span data-stu-id="e5114-157">This example casts a string literal to DT_DBDATE.</span></span>

```
(DT_DBDATE) "1999-10-11"
```

 <span data-ttu-id="e5114-158">この例では、秒の小数部に 5 桁を使用する DT_DBTIME2 データ型に文字列リテラルをキャストします</span><span class="sxs-lookup"><span data-stu-id="e5114-158">This example casts a string literal to the DT_DBTIME2 data type that uses 5 digits for fractional seconds.</span></span> <span data-ttu-id="e5114-159">(DT_DBTIME2 データ型では、秒の小数部に 0 ～ 7 桁まで指定できます)。</span><span class="sxs-lookup"><span data-stu-id="e5114-159">(The DT_DBTIME2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIME2, 5) "16:34:52.12345"
```

 <span data-ttu-id="e5114-160">この例では、秒の小数部に 4 桁を使用する DT_DBTIMESTAMP2 データ型に文字列リテラルをキャストします</span><span class="sxs-lookup"><span data-stu-id="e5114-160">This example casts a string literal to the DT_DBTIMESTAMP2 data type that uses 4 digits for fractional seconds.</span></span> <span data-ttu-id="e5114-161">(DT_DBTIMESTAMP2 データ型では、秒の小数部に 0 ～ 7 桁まで指定できます)。</span><span class="sxs-lookup"><span data-stu-id="e5114-161">(The DT_DBTIMESTAMP2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMP2, 4) "1999-10-11 16:34:52.1234"
```

 <span data-ttu-id="e5114-162">この例では、秒の小数部に 7 桁を使用する DT_DBTIMESTAMPOFFSET データ型に文字列リテラルをキャストします</span><span class="sxs-lookup"><span data-stu-id="e5114-162">This example casts a string literal to the DT_DBTIMESTAMPOFFSET data type that uses 7 digits for fractional seconds.</span></span> <span data-ttu-id="e5114-163">(DT_DBTIMESTAMPOFFSET データ型では、秒の小数部に 0 ～ 7 桁まで指定できます)。</span><span class="sxs-lookup"><span data-stu-id="e5114-163">(The DT_DBTIMESTAMPOFFSET data typecan have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMPOFFSET, 7) "1999-10-11 16:34:52.1234567 + 5:35"
```

## <a name="see-also"></a><span data-ttu-id="e5114-164">参照</span><span class="sxs-lookup"><span data-stu-id="e5114-164">See Also</span></span>
 <span data-ttu-id="e5114-165">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md)[演算子 &#40;ssis 式&#41;](operators-ssis-expression.md) [Integration Services &#40;Ssis&#41; 式](integration-services-ssis-expressions.md)[でのデータ型 Integration Services](integration-services-data-types-in-expressions.md)式</span><span class="sxs-lookup"><span data-stu-id="e5114-165">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)</span></span>



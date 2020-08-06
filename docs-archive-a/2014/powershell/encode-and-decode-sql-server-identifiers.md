---
title: SQL Server 識別子のエンコードとデコード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88e7ebbc81d9c3cb91b1bf678075c5b5d0884890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713229"
---
# <a name="encode-and-decode-sql-server-identifiers"></a><span data-ttu-id="e13c0-102">SQL Server 識別子のエンコードとデコード</span><span class="sxs-lookup"><span data-stu-id="e13c0-102">Encode and Decode SQL Server Identifiers</span></span>
  <span data-ttu-id="e13c0-103">SQL Server の区切られた識別子には、Windows PowerShell パスでサポートされない文字が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e13c0-103">SQL Server delimited identifiers sometimes contain characters not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="e13c0-104">これらの文字は、16 進数値にエンコードすることによって指定できます。</span><span class="sxs-lookup"><span data-stu-id="e13c0-104">These characters can be specified by encoding their hexadecimal values.</span></span>  
  
1.  <span data-ttu-id="e13c0-105">**作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="e13c0-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="e13c0-106">**特殊文字を処理する方法:**  [識別子のエンコード](#EncodeIdent)、 [識別子のデコード](#DecodeIdent)</span><span class="sxs-lookup"><span data-stu-id="e13c0-106">**To process special characters:**  [Encoding an Identifier](#EncodeIdent), [Decoding an Identifier](#DecodeIdent)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e13c0-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="e13c0-107">Before You Begin</span></span>  
 <span data-ttu-id="e13c0-108">Windows PowerShell のパス名でサポートされていない文字は、"xx" のように、"%" 文字の後に文字を表すビットパターンの16進数値として表すか、エンコードすることができ **%** ます。</span><span class="sxs-lookup"><span data-stu-id="e13c0-108">Characters that are not supported in Windows PowerShell path names can be represented, or encoded, as the "%" character followed by the hexadecimal value for the bit pattern that represents the character, as in "**%** xx".</span></span> <span data-ttu-id="e13c0-109">エンコードは、Windows PowerShell パスでサポートされない文字を処理する場合にいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e13c0-109">Encoding can always be used to handle characters that are not supported in Windows PowerShell paths.</span></span>  
  
 <span data-ttu-id="e13c0-110">**Encode-SqlName** コマンドレットは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子を入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e13c0-110">The **Encode-SqlName** cmdlet takes as input a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier.</span></span> <span data-ttu-id="e13c0-111">また、Windows PowerShell 言語ではサポートされないすべての文字が "%xx" でエンコードされた文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-111">It outputs a string with all the characters that are not supported by the Windows PowerShell language encoded with "%xx".</span></span> <span data-ttu-id="e13c0-112">**Decode-SqlName** コマンドレットは、エンコードされた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子を入力として受け取り、元の識別子を返します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-112">The **Decode-SqlName** cmdlet takes as input an encoded [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier and returns the original identifier.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e13c0-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e13c0-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e13c0-114">`Encode-Sqlname` コマンドレットと `Decode-Sqlname` コマンドレットでエンコードまたはデコードできるのは、SQL Server の区切られた識別子ではサポートされるが PowerShell パスではサポートされない文字のみです。</span><span class="sxs-lookup"><span data-stu-id="e13c0-114">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets only encode or decode the characters that are allowed in SQL Server delimited identifiers, but are not supported in PowerShell paths.</span></span> <span data-ttu-id="e13c0-115">**Encode-SqlName** によってエンコードされ、 **Decode-sqlname**によってデコードされる文字を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-115">These are the characters encoded by **Encode-SqlName** and decoded by **Decode-SqlName**:</span></span>  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="e13c0-116">**文字**</span><span class="sxs-lookup"><span data-stu-id="e13c0-116">**Character**</span></span>|\ |/|<span data-ttu-id="e13c0-117">:</span><span class="sxs-lookup"><span data-stu-id="e13c0-117">:</span></span>|%|\<|>|*|<span data-ttu-id="e13c0-118">?</span><span class="sxs-lookup"><span data-stu-id="e13c0-118">?</span></span>|<span data-ttu-id="e13c0-119">[</span><span class="sxs-lookup"><span data-stu-id="e13c0-119">[</span></span>|<span data-ttu-id="e13c0-120">]</span><span class="sxs-lookup"><span data-stu-id="e13c0-120">]</span></span>|<span data-ttu-id="e13c0-121">&#124;</span><span class="sxs-lookup"><span data-stu-id="e13c0-121">&#124;</span></span>|  
|<span data-ttu-id="e13c0-122">**16 進エンコード**</span><span class="sxs-lookup"><span data-stu-id="e13c0-122">**Hexadecimal Encoding**</span></span>|<span data-ttu-id="e13c0-123">%5C</span><span class="sxs-lookup"><span data-stu-id="e13c0-123">%5C</span></span>|<span data-ttu-id="e13c0-124">%2F</span><span class="sxs-lookup"><span data-stu-id="e13c0-124">%2F</span></span>|<span data-ttu-id="e13c0-125">%3A</span><span class="sxs-lookup"><span data-stu-id="e13c0-125">%3A</span></span>|<span data-ttu-id="e13c0-126">%25</span><span class="sxs-lookup"><span data-stu-id="e13c0-126">%25</span></span>|<span data-ttu-id="e13c0-127">%3C</span><span class="sxs-lookup"><span data-stu-id="e13c0-127">%3C</span></span>|<span data-ttu-id="e13c0-128">%3E</span><span class="sxs-lookup"><span data-stu-id="e13c0-128">%3E</span></span>|<span data-ttu-id="e13c0-129">%2A</span><span class="sxs-lookup"><span data-stu-id="e13c0-129">%2A</span></span>|<span data-ttu-id="e13c0-130">%3F</span><span class="sxs-lookup"><span data-stu-id="e13c0-130">%3F</span></span>|<span data-ttu-id="e13c0-131">%5B</span><span class="sxs-lookup"><span data-stu-id="e13c0-131">%5B</span></span>|<span data-ttu-id="e13c0-132">%5D</span><span class="sxs-lookup"><span data-stu-id="e13c0-132">%5D</span></span>|<span data-ttu-id="e13c0-133">%7C</span><span class="sxs-lookup"><span data-stu-id="e13c0-133">%7C</span></span>|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a> <span data-ttu-id="e13c0-134">識別子のエンコード</span><span class="sxs-lookup"><span data-stu-id="e13c0-134">Encoding an Identifier</span></span>  
 <span data-ttu-id="e13c0-135">**PowerShell パス内で SQL Server 識別子をエンコードするには**</span><span class="sxs-lookup"><span data-stu-id="e13c0-135">**To encode a SQL Server identifier in a PowerShell path**</span></span>  
  
-   <span data-ttu-id="e13c0-136">SQL Server 識別子をエンコードするには、次の 2 つの方法のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-136">Use one of two methods to encode a SQL Server identifier:</span></span>  
  
    -   <span data-ttu-id="e13c0-137">サポートされていない文字の 16 進数コードを、%XX という構文 (XX は 16 進数コード) を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-137">Specify the hexadecimal code for the unsupported character using the syntax %XX, where XX is the hexadecimal code.</span></span>  
  
    -   <span data-ttu-id="e13c0-138">識別子を引用符で囲まれた文字列として `Encode-Sqlname` コマンドレットに渡します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-138">Pass the identifier as a quoted string to the `Encode-Sqlname` cmdlet</span></span>  
  
### <a name="examples-encoding"></a><span data-ttu-id="e13c0-139">例 (エンコード)</span><span class="sxs-lookup"><span data-stu-id="e13c0-139">Examples (Encoding)</span></span>  
 <span data-ttu-id="e13c0-140">この例では、":" 文字のエンコードされたバージョン (%3A) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-140">This example specifies the encoded version of the ":" character (%3A):</span></span>  
  
```  
Set-Location Table%3ATest  
```  
  
 <span data-ttu-id="e13c0-141">あるいは、 **Encode-SqlName** を使用して Windows PowerShell でサポートされる名前を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e13c0-141">Alternatively, you can use **Encode-SqlName** to build a name supported by Windows PowerShell:</span></span>  
  
```powershell
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a> <span data-ttu-id="e13c0-142">識別子のデコード</span><span class="sxs-lookup"><span data-stu-id="e13c0-142">Decoding an Identifier</span></span>  
 <span data-ttu-id="e13c0-143">**PowerShell パスの SQL Server 識別子をデコードするには**</span><span class="sxs-lookup"><span data-stu-id="e13c0-143">**To decode a SQL Server identifier from a PowerShell path**</span></span>  
  
 <span data-ttu-id="e13c0-144">16 進数エンコードを、そのエンコードが表す文字に置換するには、`Decode-Sqlname` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-144">Use the `Decode-Sqlname` cmdlet to replace the hexadecimal encodings with the characters represented by the encoding.</span></span>  
  
### <a name="examples-decoding"></a><span data-ttu-id="e13c0-145">例 (デコード)</span><span class="sxs-lookup"><span data-stu-id="e13c0-145">Examples (Decoding)</span></span>  
 <span data-ttu-id="e13c0-146">次の例では、"Table:Test" を返します。</span><span class="sxs-lookup"><span data-stu-id="e13c0-146">This example returns "Table:Test":</span></span>  
  
```powershell
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a><span data-ttu-id="e13c0-147">参照</span><span class="sxs-lookup"><span data-stu-id="e13c0-147">See Also</span></span>  
 <span data-ttu-id="e13c0-148">[PowerShell での SQL Server 識別子](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="e13c0-148">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="e13c0-149">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="e13c0-149">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="e13c0-150">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="e13c0-150">SQL Server PowerShell</span></span>](sql-server-powershell.md)  

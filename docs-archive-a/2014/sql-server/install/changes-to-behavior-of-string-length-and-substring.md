---
title: 文字列長と substring | の動作の変更Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1188823a877b4c5dc9cef13431492dfe3b303e23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640478"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a><span data-ttu-id="f202d-102">string-length および substring の動作の変更</span><span class="sxs-lookup"><span data-stu-id="f202d-102">Changes to behavior of string-length and substring</span></span>
  <span data-ttu-id="f202d-103">[文字列長関数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length)と[Substring 関数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-substring)関数は、サロゲート文字を含む XML データベースと共に使用すると、異なる結果を返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="f202d-103">The [string-length Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) and [substring Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-substring) functions may return different results when used with XML databases that contain surrogate characters.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f202d-104">説明</span><span class="sxs-lookup"><span data-stu-id="f202d-104">Description</span></span>  
 <span data-ttu-id="f202d-105">データベースがと互換性があるように設定されている場合 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、[文字列長関数 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length)および[Substring 関数](/sql/xquery/functions-on-string-values-substring)は、Unicode 補助文字を処理するときに、xquery&#41;関数の変更を &#40;ます。</span><span class="sxs-lookup"><span data-stu-id="f202d-105">When a database is set to be compatible with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the behavior of the [string-length Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) and [substring Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-substring) functions changes when dealing with Unicode supplementary characters.</span></span> <span data-ttu-id="f202d-106">U+FFFF より大きいコード ポイントで定義された各 Unicode 補助文字は、これらの関数では 1 文字としてカウントされます。前のバージョンでは 2 文字としてカウントされていました。</span><span class="sxs-lookup"><span data-stu-id="f202d-106">Each Unicode supplementary character, which is defined by having a code point larger than U+FFFF, is counted as one character by these functions rather than two, as it was in previous versions.</span></span>  
  
 <span data-ttu-id="f202d-107">サロゲート文字の詳細については、「[サロゲートと補助文字](https://go.microsoft.com/fwlink/?LinkId=178317)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f202d-107">For more information about surrogate characters, see [Surrogates and Supplementary Characters](https://go.microsoft.com/fwlink/?LinkId=178317).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f202d-108">参照</span><span class="sxs-lookup"><span data-stu-id="f202d-108">See Also</span></span>  
 <span data-ttu-id="f202d-109">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="f202d-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="f202d-110">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="f202d-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

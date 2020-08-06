---
title: 結果セットの情報の取得 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634500"
---
# <a name="retrieve-result-set-information-odbc"></a><span data-ttu-id="e4038-102">結果セットの情報の取得 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="e4038-102">Retrieve Result Set Information (ODBC)</span></span>
    
### <a name="to-get-information-about-a-result-set"></a><span data-ttu-id="e4038-103">結果セットに関する情報を取得するには</span><span class="sxs-lookup"><span data-stu-id="e4038-103">To get information about a result set</span></span>  
  
1.  <span data-ttu-id="e4038-104">[Sqlnumresultcols](../native-client-odbc-api/sqlnumresultcols.md)を呼び出して、結果セット内の列の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4038-104">Call [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns in the result set.</span></span>  
  
2.  <span data-ttu-id="e4038-105">結果セット内の各列に対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e4038-105">For each column in the result set:</span></span>  
  
    -   <span data-ttu-id="e4038-106">[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)を呼び出して、結果列に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4038-106">Call [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to get information about the result column.</span></span>  
  
     <span data-ttu-id="e4038-107">または</span><span class="sxs-lookup"><span data-stu-id="e4038-107">Or</span></span>  
  
    -   <span data-ttu-id="e4038-108">[Sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md)を呼び出して、結果列に関する特定の記述子情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4038-108">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) to get specific descriptor information about the result column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4038-109">参照</span><span class="sxs-lookup"><span data-stu-id="e4038-109">See Also</span></span>  
 <span data-ttu-id="e4038-110">[結果の処理方法に関するトピック &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="e4038-110">[Processing Results How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="e4038-111">ODBC&#41;&#40;結果セットの特性の決定</span><span class="sxs-lookup"><span data-stu-id="e4038-111">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  

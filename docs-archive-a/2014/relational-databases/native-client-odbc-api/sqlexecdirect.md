---
title: SQLExecDirect |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: rothja
ms.author: jroth
ms.openlocfilehash: 68188506546e7b4a5dd4c05bc9a94cbf34300001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639955"
---
# <a name="sqlexecdirect"></a><span data-ttu-id="9aa89-102">SQLExecDirect</span><span class="sxs-lookup"><span data-stu-id="9aa89-102">SQLExecDirect</span></span>
  <span data-ttu-id="9aa89-103">ステートメント属性 SQL_SOPT_SS_PARAM_FOCUS が0でない場合、SQLExecDirect は SQL_ERROR を返し、SQLSTATE = HY024 の診断レコードと、"無効な属性値、SQL_SOPT_SS_PARAM_FOCUS (実行時にはゼロでなければなりません)" というメッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="9aa89-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not 0, SQLExecDirect will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="9aa89-104">SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aa89-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="9aa89-105">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aa89-105">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa89-106">参照</span><span class="sxs-lookup"><span data-stu-id="9aa89-106">See Also</span></span>  
 <span data-ttu-id="9aa89-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709) </span><span class="sxs-lookup"><span data-stu-id="9aa89-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709) </span></span>  
 [<span data-ttu-id="9aa89-108">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="9aa89-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  

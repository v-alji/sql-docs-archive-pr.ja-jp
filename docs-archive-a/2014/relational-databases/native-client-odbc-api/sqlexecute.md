---
title: SQLExecute |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: rothja
ms.author: jroth
ms.openlocfilehash: 514436c65ef103cafae2189a03b560255b447eda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639946"
---
# <a name="sqlexecute"></a><span data-ttu-id="0d050-102">SQLExecute</span><span class="sxs-lookup"><span data-stu-id="0d050-102">SQLExecute</span></span>
  <span data-ttu-id="0d050-103">ステートメント属性 SQL_SOPT_SS_PARAM_FOCUS が0に設定されていない場合、SQLExecute は SQL_ERROR を返し、SQLSTATE = HY024、メッセージ "無効な属性値、SQL_SOPT_SS_PARAM_FOCUS (実行時にゼロである必要があります)" を含む診断レコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0d050-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not set to 0, SQLExecute will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="0d050-104">SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d050-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d050-105">解説</span><span class="sxs-lookup"><span data-stu-id="0d050-105">Remarks</span></span>  
 <span data-ttu-id="0d050-106">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d050-106">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d050-107">参照</span><span class="sxs-lookup"><span data-stu-id="0d050-107">See Also</span></span>  
 <span data-ttu-id="0d050-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span><span class="sxs-lookup"><span data-stu-id="0d050-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span></span>  
 [<span data-ttu-id="0d050-109">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="0d050-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  

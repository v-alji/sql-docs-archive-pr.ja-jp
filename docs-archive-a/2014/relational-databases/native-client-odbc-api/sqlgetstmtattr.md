---
title: SQLGetStmtAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: rothja
ms.author: jroth
ms.openlocfilehash: f1f9b6a0c0668540b566c9b3d7ede781c97a1dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641638"
---
# <a name="sqlgetstmtattr"></a><span data-ttu-id="b913a-102">SQLGetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="b913a-102">SQLGetStmtAttr</span></span>
  <span data-ttu-id="b913a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、ドライバー固有のステートメント属性を公開するために、SQLGetStmtAttr を拡張します。</span><span class="sxs-lookup"><span data-stu-id="b913a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver extends SQLGetStmtAttr to expose driver-specific statement attributes.</span></span>  
  
 <span data-ttu-id="b913a-104">[SQLSetStmtAttr](sqlsetstmtattr.md)には、読み取りと書き込みの両方のステートメント属性が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="b913a-104">[SQLSetStmtAttr](sqlsetstmtattr.md) lists statement attributes that are both read and write.</span></span> <span data-ttu-id="b913a-105">ここでは、読み取り専用のステートメント属性のみを示します。</span><span class="sxs-lookup"><span data-stu-id="b913a-105">This topic lists the read only statement attributes.</span></span>  
  
## <a name="sql_sopt_ss_current_command"></a><span data-ttu-id="b913a-106">SQL_SOPT_SS_CURRENT_COMMAND</span><span class="sxs-lookup"><span data-stu-id="b913a-106">SQL_SOPT_SS_CURRENT_COMMAND</span></span>  
 <span data-ttu-id="b913a-107">コマンド バッチの現在のコマンドを公開します。</span><span class="sxs-lookup"><span data-stu-id="b913a-107">The SQL_SOPT_SS_CURRENT_COMMAND attribute exposes the current command of a command batch.</span></span> <span data-ttu-id="b913a-108">バッチ内のコマンドの位置を表す整数を返します。</span><span class="sxs-lookup"><span data-stu-id="b913a-108">The return is an integer that specifies the location of the command in the batch.</span></span> <span data-ttu-id="b913a-109">*Valueptr*値の型は SQLLEN です。</span><span class="sxs-lookup"><span data-stu-id="b913a-109">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
## <a name="sql_sopt_ss_nocount_status"></a><span data-ttu-id="b913a-110">SQL_SOPT_SS_NOCOUNT_STATUS</span><span class="sxs-lookup"><span data-stu-id="b913a-110">SQL_SOPT_SS_NOCOUNT_STATUS</span></span>  
 <span data-ttu-id="b913a-111">SQL_SOPT_SS_NOCOUNT_STATUS 属性は、NOCOUNT オプションの現在の設定を示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。これは、 [SQLRowCount](sqlrowcount.md)が呼び出されたときに、がステートメントの影響を受ける行の数をレポートするかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="b913a-111">The SQL_SOPT_SS_NOCOUNT_STATUS attribute indicates the current setting of the NOCOUNT option, which controls whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reports the numbers of rows affected by a statement when [SQLRowCount](sqlrowcount.md) is called.</span></span> <span data-ttu-id="b913a-112">*Valueptr*値の型は SQLLEN です。</span><span class="sxs-lookup"><span data-stu-id="b913a-112">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
|<span data-ttu-id="b913a-113">値</span><span class="sxs-lookup"><span data-stu-id="b913a-113">Value</span></span>|<span data-ttu-id="b913a-114">説明</span><span class="sxs-lookup"><span data-stu-id="b913a-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b913a-115">SQL_NC_OFF</span><span class="sxs-lookup"><span data-stu-id="b913a-115">SQL_NC_OFF</span></span>|<span data-ttu-id="b913a-116">NOCOUNT を OFF にします。</span><span class="sxs-lookup"><span data-stu-id="b913a-116">NOCOUNT is OFF.</span></span> <span data-ttu-id="b913a-117">SQLRowCount は、影響を受けた行数を返します。</span><span class="sxs-lookup"><span data-stu-id="b913a-117">SQLRowCount returns number of rows affected.</span></span>|  
|<span data-ttu-id="b913a-118">SQL_NC_ON</span><span class="sxs-lookup"><span data-stu-id="b913a-118">SQL_NC_ON</span></span>|<span data-ttu-id="b913a-119">NOCOUNT を ON にします。</span><span class="sxs-lookup"><span data-stu-id="b913a-119">NOCOUNT is ON.</span></span> <span data-ttu-id="b913a-120">影響を受ける行の数は SQLRowCount によって返されず、戻り値は0です。</span><span class="sxs-lookup"><span data-stu-id="b913a-120">The number of rows affected is not returned by SQLRowCount and the returned value is 0.</span></span>|  
  
 <span data-ttu-id="b913a-121">SQLRowCount が0を返す場合、アプリケーションは SQL_SOPT_SS_NOCOUNT_STATUS をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b913a-121">If SQLRowCount returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="b913a-122">SQL_NC_ON が返された場合、SQLRowCount の値が0の場合は、によって行数が返されなかったことを示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b913a-122">If SQL_NC_ON is returned, the value of 0 from SQLRowCount only indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has not returned a row count.</span></span> <span data-ttu-id="b913a-123">SQL_NC_OFF が返される場合、NOCOUNT が無効になっており、SQLRowCount から返される値が 0 であると、ステートメントで処理された行がなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="b913a-123">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from SQLRowCount indicates that the statement did not affect any rows.</span></span>  
  
 <span data-ttu-id="b913a-124">SQL_SOPT_SS_NOCOUNT_STATUS が SQL_NC_OFF のときは、アプリケーションでは、SQLRowCount の値を表示しないでください。</span><span class="sxs-lookup"><span data-stu-id="b913a-124">Applications should not display the value of SQLRowCount when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="b913a-125">大きなバッチやストアド プロシージャには、複数の SET NOCOUNT ステートメントが含まれていることがあるので、SQL_SOPT_SS_NOCOUNT_STATUS が一定であると想定することはできません。</span><span class="sxs-lookup"><span data-stu-id="b913a-125">Large batches or stored procedures can contain multiple SET NOCOUNT statements, so it cannot be assumed that SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="b913a-126">このオプションは、SQLRowCount が0を返すたびにテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b913a-126">This option should be tested each time SQLRowCount returns 0.</span></span>  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a><span data-ttu-id="b913a-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="b913a-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
 <span data-ttu-id="b913a-128">クエリ通知要求のメッセージ テキストを返します。</span><span class="sxs-lookup"><span data-stu-id="b913a-128">The SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT attribute returns the message text for the query notification request.</span></span>  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a><span data-ttu-id="b913a-129">SQLGetStmtAttr とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="b913a-129">SQLGetStmtAttr and Table-valued Parameters</span></span>  
 <span data-ttu-id="b913a-130">SQLGetStmtAttr を呼び出すと、テーブル値パラメーターを操作するときに、アプリケーションパラメーター記述子 (APD) の SQL_SOPT_SS_PARAM_FOCUS の値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b913a-130">SQLGetStmtAttr can be called to get the value of SQL_SOPT_SS_PARAM_FOCUS in the application parameter descriptor (APD) when working with table-valued parameters.</span></span> <span data-ttu-id="b913a-131">SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b913a-131">For more information on SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="b913a-132">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b913a-132">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b913a-133">参照</span><span class="sxs-lookup"><span data-stu-id="b913a-133">See Also</span></span>  
 <span data-ttu-id="b913a-134">[SQLSetStmtAttr 関数](https://go.microsoft.com/fwlink/?LinkId=59370) </span><span class="sxs-lookup"><span data-stu-id="b913a-134">[SQLSetStmtAttr Function](https://go.microsoft.com/fwlink/?LinkId=59370) </span></span>  
 [<span data-ttu-id="b913a-135">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="b913a-135">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  

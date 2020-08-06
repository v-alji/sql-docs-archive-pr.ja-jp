---
title: Microsoft 分散トランザクションコーディネーターの使用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: rothja
ms.author: jroth
ms.openlocfilehash: f7b7da33066a9f4edd01037738ed91155340e6ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639943"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a><span data-ttu-id="3db22-102">Microsoft 分散トランザクション コーディネーターの使用 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="3db22-102">Use Microsoft Distributed Transaction Coordinator (ODBC)</span></span>
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a><span data-ttu-id="3db22-103">MS DTC を使用して複数の SQL Server を更新するには</span><span class="sxs-lookup"><span data-stu-id="3db22-103">To update two or more SQL Servers by using MS DTC</span></span>  
  
1.  <span data-ttu-id="3db22-104">MS DTC の OLE DtcGetTransactionManager 関数を使用して、MS DTC に接続します。</span><span class="sxs-lookup"><span data-stu-id="3db22-104">Connect to MS DTC by using the MS DTC OLE DtcGetTransactionManager function.</span></span> <span data-ttu-id="3db22-105">MS DTC の詳細については、Microsoft 分散トランザクション コーディネーターを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3db22-105">For information about MS DTC, see Microsoft Distributed Transaction Coordinator.</span></span>  
  
2.  <span data-ttu-id="3db22-106">確立する Microsoft SQL Server 接続ごとに1回、SQL DriverConnect を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3db22-106">Call SQL DriverConnect once for each Microsoft SQL Server connection you want to establish.</span></span>  
  
3.  <span data-ttu-id="3db22-107">MS DTC の OLE ITransactionDispenser::BeginTransaction 関数を呼び出して、MS DTC トランザクションを開始し、トランザクションを表すトランザクション オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="3db22-107">Call the MS DTC OLE ITransactionDispenser::BeginTransaction function to begin an MS DTC transaction and obtain a Transaction object that represents the transaction.</span></span>  
  
4.  <span data-ttu-id="3db22-108">MS DTC トランザクションに参加させる ODBC 接続ごとに、[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) を 1 回以上呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3db22-108">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) one or more times for each ODBC connection you want to enlist in the MS DTC transaction.</span></span> <span data-ttu-id="3db22-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) の 2 番目のパラメーターは SQL_ATTR_ENLIST_IN_DTC、3 番目のパラメーターは (手順 3. で取得した) トランザクション オブジェクトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="3db22-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) second parameter must be SQL_ATTR_ENLIST_IN_DTC and third parameter must be the Transaction object (obtained in Step 3).</span></span>  
  
5.  <span data-ttu-id="3db22-110">更新する SQL Server ごとに 1 回ずつ [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3db22-110">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) once for each SQL Server you want to update.</span></span>  
  
6.  <span data-ttu-id="3db22-111">MS DTC の OLE ITransaction::Commit 関数を呼び出して、MS DTC トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="3db22-111">Call the MS DTC OLE ITransaction::Commit function to commit the MS DTC transaction.</span></span> <span data-ttu-id="3db22-112">トランザクション オブジェクトは無効になります。</span><span class="sxs-lookup"><span data-stu-id="3db22-112">The Transaction object is no longer valid.</span></span>  
  
 <span data-ttu-id="3db22-113">一連の MS DTC トランザクションを実行するには、手順 3. から手順 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3db22-113">To perform a series of MS DTC transactions, repeat Steps 3 through 6.</span></span>  
  
 <span data-ttu-id="3db22-114">トランザクション オブジェクトへの参照を解放するには、MS DTC の OLE ITransaction::Return 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3db22-114">To release the reference to the Transaction object, call the MS DTC OLE ITransaction::Return function.</span></span>  
  
 <span data-ttu-id="3db22-115">MS DTC トランザクションで ODBC 接続を使用し、この接続をローカルの SQL Server トランザクションでも使用するには、[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) に SQL_DTC_DONE を指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3db22-115">To use an ODBC connection with an MS DTC transaction, and then use the same connection with a local SQL Server transaction, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_DTC_DONE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3db22-116">手順 4. と手順 5. で示した呼び出し方法の代わりに、SQL Server ごとに [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) と [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) を続けて呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3db22-116">You can also call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) and [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) in turn for each SQL Server instead of calling them as suggested earlier in Steps 4 and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db22-117">参照</span><span class="sxs-lookup"><span data-stu-id="3db22-117">See Also</span></span>  
 [<span data-ttu-id="3db22-118">ODBC&#41;&#40;のトランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="3db22-118">Performing Transactions &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  

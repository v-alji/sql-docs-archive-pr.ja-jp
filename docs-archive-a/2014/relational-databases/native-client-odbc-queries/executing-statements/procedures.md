---
title: プロシージャ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: rothja
ms.author: jroth
ms.openlocfilehash: a7ae4678d324ba7d07ae429793b1f75b57bb15e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631861"
---
# <a name="procedures"></a><span data-ttu-id="c664c-102">手順</span><span class="sxs-lookup"><span data-stu-id="c664c-102">Procedures</span></span>
  <span data-ttu-id="c664c-103">ストアド プロシージャは、1 つ以上の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含むプリコンパイルされた実行可能オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c664c-103">A stored procedure is a precompiled executable object that contains one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="c664c-104">ストアド プロシージャは、入力パラメーターと出力パラメーターを使用でき、整数のリターン コードを出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="c664c-104">Stored procedures can have input and output parameters and can also put out an integer return code.</span></span> <span data-ttu-id="c664c-105">アプリケーションは、カタログ関数を使用することで、使用可能なストアド プロシージャを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="c664c-105">An application can enumerate available stored procedures by using catalog functions.</span></span>  
  
 <span data-ttu-id="c664c-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を対象とする ODBC アプリケーションからストアド プロシージャを呼び出す場合、直接実行だけを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c664c-106">ODBC applications that target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should only use direct execution to call a stored procedure.</span></span> <span data-ttu-id="c664c-107">以前のバージョンのに接続している場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーは、一時ストアドプロシージャを作成することによって[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を実装します。このストアドプロシージャは、 **sqlexecute**で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c664c-107">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver implements [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) by creating a temporary stored procedure, which is then called on **SQLExecute**.</span></span> <span data-ttu-id="c664c-108">**SQLPrepare**によって、対象のストアドプロシージャを呼び出すだけでなく、対象のストアドプロシージャを直接実行する一時ストアドプロシージャを作成することにより、オーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="c664c-108">It adds overhead to have **SQLPrepare** create a temporary stored procedure that only calls the target stored procedure versus directly executing the target stored procedure.</span></span> <span data-ttu-id="c664c-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続している場合でも、呼び出しの準備には、ネットワーク経由のやり取りが増え、ストアド プロシージャ実行プランを呼び出すだけの実行プランの構築が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c664c-109">Even when connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], preparing a call requires an extra round trip across the network and the building of an execution plan that just calls the stored procedure execution plan.</span></span>  
  
 <span data-ttu-id="c664c-110">ODBC アプリケーションでは、ストアド プロシージャの実行時に ODBC CALL 構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c664c-110">ODBC applications should use the ODBC CALL syntax when executing a stored procedure.</span></span> <span data-ttu-id="c664c-111">ドライバーは、ODBC CALL 構文の使用時に、リモート プロシージャ コールのメカニズムを使用してプロシージャを呼び出すように最適化されます。</span><span class="sxs-lookup"><span data-stu-id="c664c-111">The driver is optimized to use a remote procedure call mechanism to call the procedure when the ODBC CALL syntax is used.</span></span> <span data-ttu-id="c664c-112">これは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE ステートメントをサーバーに送信するときに使用するメカニズムよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="c664c-112">This is more efficient than the mechanism used to send a [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE statement to the server.</span></span>  
  
 <span data-ttu-id="c664c-113">詳細については、「[ストアドプロシージャの実行](../../native-client-odbc-stored-procedures/running-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c664c-113">For more information, see [Running Stored Procedures](../../native-client-odbc-stored-procedures/running-stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c664c-114">参照</span><span class="sxs-lookup"><span data-stu-id="c664c-114">See Also</span></span>  
 [<span data-ttu-id="c664c-115">ODBC&#41;&#40;のステートメントの実行</span><span class="sxs-lookup"><span data-stu-id="c664c-115">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  

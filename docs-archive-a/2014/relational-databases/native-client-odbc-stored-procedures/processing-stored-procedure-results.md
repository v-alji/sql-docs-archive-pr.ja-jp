---
title: ストアドプロシージャの結果を処理しています |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f37a6d8beff88748fa944293bd67f449d29eff2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741957"
---
# <a name="processing-stored-procedure-results"></a><span data-ttu-id="973f5-102">ストアド プロシージャの結果の処理</span><span class="sxs-lookup"><span data-stu-id="973f5-102">Processing Stored Procedure Results</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="973f5-103">ストアド プロシージャには、データを返す際に使用する次の 4 つのメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="973f5-103">stored procedures have four mechanisms used to return data:</span></span>  
  
-   <span data-ttu-id="973f5-104">プロシージャ内の各 SELECT ステートメントで結果セットを生成する。</span><span class="sxs-lookup"><span data-stu-id="973f5-104">Each SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="973f5-105">プロシージャが出力パラメーターによってデータを返すことができる。</span><span class="sxs-lookup"><span data-stu-id="973f5-105">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="973f5-106">カーソルの出力パラメーターから、[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルを返すことができる。</span><span class="sxs-lookup"><span data-stu-id="973f5-106">A cursor output parameter can pass back a [!INCLUDE[tsql](../../includes/tsql-md.md)] server cursor.</span></span>  
  
-   <span data-ttu-id="973f5-107">プロシージャに整数のリターン コードを含めることができる。</span><span class="sxs-lookup"><span data-stu-id="973f5-107">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="973f5-108">アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="973f5-108">Applications must be able to handle all these outputs from stored procedures.</span></span> <span data-ttu-id="973f5-109">CALL ステートメントや EXECUTE ステートメントには、リターン コードと出力パラメーター用のパラメーター マーカーを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="973f5-109">The CALL or EXECUTE statement should include parameter markers for the return code and output parameters.</span></span> <span data-ttu-id="973f5-110">[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)を使用してすべてを出力パラメーターとしてバインドすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、バインドされた変数に出力値を転送します。</span><span class="sxs-lookup"><span data-stu-id="973f5-110">Use [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) to bind them all as output parameters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will transfer the output values to the bound variables.</span></span> <span data-ttu-id="973f5-111">出力パラメーターとリターンコードは、によってクライアントに返される最後の項目であり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Sqlmoreresults](../native-client-odbc-api/sqlmoreresults.md)が SQL_NO_DATA を返すまでアプリケーションに返されません。</span><span class="sxs-lookup"><span data-stu-id="973f5-111">Output parameters and return codes are the last items returned to the client by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they are not returned to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="973f5-112">ODBC は、[!INCLUDE[tsql](../../includes/tsql-md.md)] カーソル パラメーターのバインドをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="973f5-112">ODBC does not support binding [!INCLUDE[tsql](../../includes/tsql-md.md)] cursor parameters.</span></span> <span data-ttu-id="973f5-113">プロシージャの実行前にすべての出力パラメーターをバインドしておく必要があるので、出力カーソル パラメーターを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを ODBC アプリケーションから呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="973f5-113">Because all output parameters must be bound before executing a procedure, any [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that contains an output cursor parameter cannot be called by ODBC applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="973f5-114">参照</span><span class="sxs-lookup"><span data-stu-id="973f5-114">See Also</span></span>  
 [<span data-ttu-id="973f5-115">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="973f5-115">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  

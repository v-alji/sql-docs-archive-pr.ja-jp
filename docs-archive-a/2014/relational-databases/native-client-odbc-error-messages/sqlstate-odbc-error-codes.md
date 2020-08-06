---
title: SQLSTATE (ODBC エラーコード) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: rothja
ms.author: jroth
ms.openlocfilehash: ff3ec0a5cdc8f24f34e42849f7c8f6d1d9d41478
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630998"
---
# <a name="sqlstate-odbc-error-codes"></a><span data-ttu-id="d48c8-102">SQLSTATE (ODBC エラー コード)</span><span class="sxs-lookup"><span data-stu-id="d48c8-102">SQLSTATE (ODBC Error Codes)</span></span>
  <span data-ttu-id="d48c8-103">SQLSTATE は、警告やエラーの原因についての詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d48c8-103">SQLSTATE provides detailed information about the cause of a warning or error.</span></span> <span data-ttu-id="d48c8-104">によって検出され、によって返されるデータソースで発生したエラーの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーは、返されたネイティブエラー番号を適切な SQLSTATE にマップします。</span><span class="sxs-lookup"><span data-stu-id="d48c8-104">For errors that occur in the data source detected and returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps the returned native error number to the appropriate SQLSTATE.</span></span> <span data-ttu-id="d48c8-105">ネイティブエラー番号にマップする ODBC エラーコードがない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは SQLSTATE 42000 ("構文エラーまたはアクセス違反") を返します。</span><span class="sxs-lookup"><span data-stu-id="d48c8-105">If a native error number does not have an ODBC error code to map to, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQLSTATE 42000 ("syntax error or access violation").</span></span> <span data-ttu-id="d48c8-106">ドライバーによって検出されたエラーについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーによって適切な SQLSTATE が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d48c8-106">For errors that are detected by the driver, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates the appropriate SQLSTATE.</span></span>  
  
 <span data-ttu-id="d48c8-107">状態エラー コードの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d48c8-107">For more information about the state error codes, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d48c8-108">付録 A: ODBC エラー コード</span><span class="sxs-lookup"><span data-stu-id="d48c8-108">Appendix A: ODBC Error Codes</span></span>](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [<span data-ttu-id="d48c8-109">SQLSTATE マッピング</span><span class="sxs-lookup"><span data-stu-id="d48c8-109">SQLSTATE Mappings</span></span>](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a><span data-ttu-id="d48c8-110">参照</span><span class="sxs-lookup"><span data-stu-id="d48c8-110">See Also</span></span>  
 [<span data-ttu-id="d48c8-111">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="d48c8-111">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  

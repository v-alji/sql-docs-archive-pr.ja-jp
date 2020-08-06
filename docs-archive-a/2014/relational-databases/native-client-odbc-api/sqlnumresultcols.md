---
title: SQLNumResultCols |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: rothja
ms.author: jroth
ms.openlocfilehash: 45e72165eef621dc377b02ed3d2e7e1e3cf7ab8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645026"
---
# <a name="sqlnumresultcols"></a><span data-ttu-id="0aa40-102">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="0aa40-102">SQLNumResultCols</span></span>
  <span data-ttu-id="0aa40-103">実行されたステートメントの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーはサーバーにアクセスせず、結果セットの列数を報告しません。</span><span class="sxs-lookup"><span data-stu-id="0aa40-103">For executed statements, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not visit the server to report the number of columns in a result set.</span></span> <span data-ttu-id="0aa40-104">この場合、 `SQLNumResultCols` はサーバーのラウンドトリップを発生させません。</span><span class="sxs-lookup"><span data-stu-id="0aa40-104">In this case, `SQLNumResultCols` does not cause a server roundtrip.</span></span> <span data-ttu-id="0aa40-105">[SQLDescribeCol](sqldescribecol.md)や[sqlcolattribute](sqlcolattribute.md)と同様、 `SQLNumResultCols` 準備済みで実行されていないステートメントを呼び出すと、サーバーのラウンドトリップが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0aa40-105">Like [SQLDescribeCol](sqldescribecol.md) and [SQLColAttribute](sqlcolattribute.md), calling `SQLNumResultCols` on prepared but not executed statements generates a server roundtrip.</span></span>  
  
 <span data-ttu-id="0aa40-106">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0aa40-106">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statement batch returns multiple result row sets, it is possible for the number of result set columns to change from one set to another.</span></span> <span data-ttu-id="0aa40-107">`SQLNumResultCols`各セットに対してを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aa40-107">`SQLNumResultCols` should be called for each set.</span></span> <span data-ttu-id="0aa40-108">列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aa40-108">When the number of columns changes, the application should rebind data values prior to fetching row results.</span></span> <span data-ttu-id="0aa40-109">複数の結果セットを返す処理の詳細については、「 [Sqlmoreresults](sqlmoreresults.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0aa40-109">For more information about handling multiple result set returns, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="0aa40-110">以降のデータベースエンジンの機能強化により [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、SQLNumResultCols は、予期される結果についてより正確な説明を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="0aa40-110">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLNumResultCols to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="0aa40-111">これらのより正確な結果は、以前のバージョンの SQLNumResultCols によって返される値とは異なる場合があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="0aa40-111">These more accurate results may differ from the values returned by SQLNumResultCols in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0aa40-112">詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0aa40-112">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa40-113">参照</span><span class="sxs-lookup"><span data-stu-id="0aa40-113">See Also</span></span>  
 <span data-ttu-id="0aa40-114">[SQLNumResultCols 関数](https://go.microsoft.com/fwlink/?LinkId=59359) </span><span class="sxs-lookup"><span data-stu-id="0aa40-114">[SQLNumResultCols Function](https://go.microsoft.com/fwlink/?LinkId=59359) </span></span>  
 [<span data-ttu-id="0aa40-115">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="0aa40-115">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  

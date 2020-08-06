---
title: ODBC API による機能強化された日付と時刻のサポート |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], API support
ms.assetid: 430c029d-f8c1-4de7-a9dd-330e9b6bfc20
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b5225850b427e411e1e9e15e9fcd7780f473440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738352"
---
# <a name="odbc-api-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="631fd-102">ODBC API による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="631fd-102">ODBC API Support for Enhanced Date and Time Features</span></span>
  <span data-ttu-id="631fd-103">次の ODBC API は、機能強化された日付と時刻をサポートします。</span><span class="sxs-lookup"><span data-stu-id="631fd-103">The following ODBC APIs support enhanced date and time functionality:</span></span>  
  
-   [<span data-ttu-id="631fd-104">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="631fd-104">SQLBindCol</span></span>](../native-client-odbc-api/sqlbindcol.md)  
  
-   [<span data-ttu-id="631fd-105">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="631fd-105">SQLBindParameter</span></span>](../native-client-odbc-api/sqlbindparameter.md)  
  
-   [<span data-ttu-id="631fd-106">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="631fd-106">SQLColAttribute</span></span>](../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="631fd-107">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="631fd-107">SQLColumns</span></span>](../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="631fd-108">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="631fd-108">SQLDescribeCol</span></span>](../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="631fd-109">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="631fd-109">SQLDescribeParam</span></span>](../native-client-odbc-api/sqldescribeparam.md)  
  
-   [<span data-ttu-id="631fd-110">SQLFetch</span><span class="sxs-lookup"><span data-stu-id="631fd-110">SQLFetch</span></span>](../native-client-odbc-api/sqlfetch.md)  
  
-   [<span data-ttu-id="631fd-111">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="631fd-111">SQLFetchScroll</span></span>](../native-client-odbc-api/sqlfetchscroll.md)  
  
-   [<span data-ttu-id="631fd-112">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="631fd-112">SQLGetData</span></span>](../native-client-odbc-api/sqlgetdata.md)  
  
-   [<span data-ttu-id="631fd-113">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="631fd-113">SQLGetDescField</span></span>](../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [<span data-ttu-id="631fd-114">SQLGetDescRec</span><span class="sxs-lookup"><span data-stu-id="631fd-114">SQLGetDescRec</span></span>](../native-client-odbc-api/sqlgetdescrec.md)  
  
-   [<span data-ttu-id="631fd-115">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="631fd-115">SQLGetTypeInfo</span></span>](../native-client-odbc-api/sqlgettypeinfo.md)  
  
-   [<span data-ttu-id="631fd-116">SQLProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="631fd-116">SQLProcedureColumns</span></span>](../native-client-odbc-api/sqlprocedurecolumns.md)  
  
-   [<span data-ttu-id="631fd-117">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="631fd-117">SQLPutData</span></span>](../native-client-odbc-api/sqlputdata.md)  
  
-   [<span data-ttu-id="631fd-118">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="631fd-118">SQLSetDescField</span></span>](../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [<span data-ttu-id="631fd-119">SQLSetDescRec</span><span class="sxs-lookup"><span data-stu-id="631fd-119">SQLSetDescRec</span></span>](../native-client-odbc-api/sqlsetdescrec.md)  
  
-   [<span data-ttu-id="631fd-120">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="631fd-120">SQLSpecialColumns</span></span>](../native-client-odbc-api/sqlspecialcolumns.md)  
  
 <span data-ttu-id="631fd-121">次の一括コピー API は、機能強化された日付と時刻をサポートします。</span><span class="sxs-lookup"><span data-stu-id="631fd-121">The following bulk copy APIs support enhanced date and time functionality:</span></span>  
  
-   [<span data-ttu-id="631fd-122">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="631fd-122">bcp_bind</span></span>](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)  
  
-   [<span data-ttu-id="631fd-123">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="631fd-123">bcp_colfmt</span></span>](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)  
  
-   [<span data-ttu-id="631fd-124">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="631fd-124">bcp_getcolfmt</span></span>](../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="631fd-125">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="631fd-125">bcp_gettypename</span></span>](../native-client-odbc-extensions-bulk-copy-functions/bcp-gettypename.md)  
  
-   [<span data-ttu-id="631fd-126">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="631fd-126">bcp_setcolfmt</span></span>](../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
## <a name="see-also"></a><span data-ttu-id="631fd-127">参照</span><span class="sxs-lookup"><span data-stu-id="631fd-127">See Also</span></span>  
 [<span data-ttu-id="631fd-128">ODBC&#41;&#40;の日付と時刻の改善</span><span class="sxs-lookup"><span data-stu-id="631fd-128">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  

---
title: 一括コピー関数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dba8cf4d510d2ec5f20e600302bb692c749f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642061"
---
# <a name="bulk-copy-functions"></a><span data-ttu-id="ff73a-102">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="ff73a-102">Bulk Copy Functions</span></span>
  <span data-ttu-id="ff73a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 専用の一括コピー API 拡張機能を使用すると、クライアント アプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルへのデータ行の追加や、テーブルからのデータ行の抽出をすばやく行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ff73a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy API extension of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver allows client applications to rapidly add data rows to, or extract data rows from, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="ff73a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用している場合は、SQLNCLI11.LIB と SQLNCLI.H 内にある一括コピー関数 (BCP) を参照できます。</span><span class="sxs-lookup"><span data-stu-id="ff73a-104">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, you can reference the bulk copy functions (BCP) in SQLNCLI11.LIB and SQLNCLI.H.</span></span>  
  
 <span data-ttu-id="ff73a-105">アプリケーションで BCP API 関数呼び出しを使用する場合は、アプリケーションで使用するドライバー (.dll) に付属するライブラリ (.lib) とアプリケーションをリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff73a-105">An application that uses BCP API function calls should link with the library (.lib) that shipped with the driver (.dll) used by the application.</span></span> <span data-ttu-id="ff73a-106">BCP アプリケーションを複数のドライバー ライブラリとリンクしないでください。</span><span class="sxs-lookup"><span data-stu-id="ff73a-106">A BCP application should not link with more than one driver library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff73a-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ff73a-107">In This Section</span></span>  
  
-   [<span data-ttu-id="ff73a-108">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="ff73a-108">bcp_batch</span></span>](bcp-batch.md)  
  
-   [<span data-ttu-id="ff73a-109">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="ff73a-109">bcp_bind</span></span>](bcp-bind.md)  
  
-   [<span data-ttu-id="ff73a-110">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="ff73a-110">bcp_colfmt</span></span>](bcp-colfmt.md)  
  
-   [<span data-ttu-id="ff73a-111">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="ff73a-111">bcp_collen</span></span>](bcp-collen.md)  
  
-   [<span data-ttu-id="ff73a-112">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="ff73a-112">bcp_colptr</span></span>](bcp-colptr.md)  
  
-   [<span data-ttu-id="ff73a-113">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="ff73a-113">bcp_columns</span></span>](bcp-columns.md)  
  
-   [<span data-ttu-id="ff73a-114">bcp_control</span><span class="sxs-lookup"><span data-stu-id="ff73a-114">bcp_control</span></span>](bcp-control.md)  
  
-   [<span data-ttu-id="ff73a-115">bcp_done</span><span class="sxs-lookup"><span data-stu-id="ff73a-115">bcp_done</span></span>](bcp-done.md)  
  
-   [<span data-ttu-id="ff73a-116">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="ff73a-116">bcp_exec</span></span>](bcp-exec.md)  
  
-   [<span data-ttu-id="ff73a-117">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="ff73a-117">bcp_getcolfmt</span></span>](bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="ff73a-118">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="ff73a-118">bcp_gettypename</span></span>](bcp-gettypename.md)  
  
-   [<span data-ttu-id="ff73a-119">bcp_init</span><span class="sxs-lookup"><span data-stu-id="ff73a-119">bcp_init</span></span>](bcp-init.md)  
  
-   [<span data-ttu-id="ff73a-120">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="ff73a-120">bcp_moretext</span></span>](bcp-moretext.md)  
  
-   [<span data-ttu-id="ff73a-121">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="ff73a-121">bcp_readfmt</span></span>](bcp-readfmt.md)  
  
-   [<span data-ttu-id="ff73a-122">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="ff73a-122">bcp_sendrow</span></span>](bcp-sendrow.md)  
  
-   [<span data-ttu-id="ff73a-123">bcp_setbulkmode</span><span class="sxs-lookup"><span data-stu-id="ff73a-123">bcp_setbulkmode</span></span>](bcp-setbulkmode.md)  
  
-   [<span data-ttu-id="ff73a-124">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="ff73a-124">bcp_setcolfmt</span></span>](bcp-setcolfmt.md)  
  
-   [<span data-ttu-id="ff73a-125">bcp_writefmt</span><span class="sxs-lookup"><span data-stu-id="ff73a-125">bcp_writefmt</span></span>](bcp-writefmt.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff73a-126">参照</span><span class="sxs-lookup"><span data-stu-id="ff73a-126">See Also</span></span>  
 <span data-ttu-id="ff73a-127">[SQL Server ドライバーの拡張機能](../../database-engine/dev-guide/sql-server-driver-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="ff73a-127">[SQL Server Driver Extensions](../../database-engine/dev-guide/sql-server-driver-extensions.md) </span></span>  
 [<span data-ttu-id="ff73a-128">ODBC&#41;&#40;の一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="ff73a-128">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  

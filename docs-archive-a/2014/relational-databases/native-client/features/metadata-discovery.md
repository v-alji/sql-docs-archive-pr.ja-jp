---
title: メタデータの検出 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
ms.openlocfilehash: 571df9f21ab46a53c8aba7907039ce02afd6ad05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714266"
---
# <a name="metadata-discovery"></a><span data-ttu-id="55172-102">メタデータの検出</span><span class="sxs-lookup"><span data-stu-id="55172-102">Metadata Discovery</span></span>
  <span data-ttu-id="55172-103">のメタデータ検出の [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 機能強化により、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ネイティブクライアントアプリケーションでは、クエリの実行によって返される列またはパラメーターのメタデータが、クエリを実行する前に指定したメタデータ形式と同じか、または互換性があるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="55172-103">The metadata discovery improvement in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] allows [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client applications to ensure that column or parameter metadata returned from the execution of a query is identical to or compatible with the metadata format you specified before you executed the query.</span></span> <span data-ttu-id="55172-104">クエリの実行後に返されたメタデータにクエリの実行前に指定したメタデータ形式との互換性がない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="55172-104">You will receive an error if the metadata returned after query execution is not compatible with the metadata format you specified before query execution.</span></span>  
  
 <span data-ttu-id="55172-105">bcp 関数と ODBC 関数、および IBCPSession インターフェイスと IBCPSession2 インターフェイスでは、遅延読み取り (遅延メタデータ検出) を指定して、クエリ出力操作でメタデータ検出を回避できます。</span><span class="sxs-lookup"><span data-stu-id="55172-105">In bcp and ODBC functions, and IBCPSession and IBCPSession2 interfaces, you can now specify a delayed read (delayed metadata discovery) to avoid metadata discovery for query out operations.</span></span> <span data-ttu-id="55172-106">その結果、パフォーマンスが向上し、メタデータ検出のエラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="55172-106">This improves performance and eliminates metadata discovery failures.</span></span>  
  
 <span data-ttu-id="55172-107">で Native Client を使用しているアプリケーションを開発している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] が、より前のサーバーバージョンに接続している場合 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 、メタデータ検出機能はサーバーのバージョンに対応します。</span><span class="sxs-lookup"><span data-stu-id="55172-107">If you develop an application using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] but connect to a server version earlier than [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], metadata discovery functionality will correspond to the version of the server.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55172-108">解説</span><span class="sxs-lookup"><span data-stu-id="55172-108">Remarks</span></span>  
 <span data-ttu-id="55172-109">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の bcp 関数が機能強化され、メタデータ検出機能が向上しています。</span><span class="sxs-lookup"><span data-stu-id="55172-109">The following bcp functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="55172-110">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="55172-110">bcp_columns</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [<span data-ttu-id="55172-111">bcp_control</span><span class="sxs-lookup"><span data-stu-id="55172-111">bcp_control</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [<span data-ttu-id="55172-112">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="55172-112">bcp_getcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="55172-113">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="55172-113">bcp_readfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [<span data-ttu-id="55172-114">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="55172-114">bcp_setcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 <span data-ttu-id="55172-115">[Bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)を使用してメタデータ形式を指定すると、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="55172-115">You will also see a performance improvement when specifying metadata format using [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).</span></span>  
  
 <span data-ttu-id="55172-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)には、bcp_readfmt の動作を制御する新しい*eOption*があり `BCPDELAYREADFMT` ます。</span><span class="sxs-lookup"><span data-stu-id="55172-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) has a new *eOption* to control the behavior of bcp_readfmt: `BCPDELAYREADFMT`.</span></span>  
  
 <span data-ttu-id="55172-117">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の ODBC 関数が機能強化され、メタデータ検出機能が向上しています。</span><span class="sxs-lookup"><span data-stu-id="55172-117">The following ODBC functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="55172-118">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="55172-118">SQLNumResultCols</span></span>](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [<span data-ttu-id="55172-119">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="55172-119">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="55172-120">SQLNumParams</span><span class="sxs-lookup"><span data-stu-id="55172-120">SQLNumParams</span></span>](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [<span data-ttu-id="55172-121">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="55172-121">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
 <span data-ttu-id="55172-122">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の OLE DB メンバー関数が機能強化され、メタデータ検出機能が向上しています。</span><span class="sxs-lookup"><span data-stu-id="55172-122">The following OLE DB member functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   <span data-ttu-id="55172-123">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="55172-123">IColumnsInfo::GetColumnInfo</span></span>  
  
-   <span data-ttu-id="55172-124">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="55172-124">IColumnsRowset::GetColumnsRowset</span></span>  
  
-   <span data-ttu-id="55172-125">ICommandWithParameters::GetParameterInfo (詳細は「[ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md)」を参照)</span><span class="sxs-lookup"><span data-stu-id="55172-125">ICommandWithParameters::GetParameterInfo (see [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) for more information)</span></span>  
  
 <span data-ttu-id="55172-126">IBCPSession::BCPSetBulkMode を使用してメタデータ形式を指定したときのパフォーマンスも向上しています。</span><span class="sxs-lookup"><span data-stu-id="55172-126">You will also see a performance improvement when specifying metadata format using IBCPSession::BCPSetBulkMode</span></span>  
  
 <span data-ttu-id="55172-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でのメタデータ検出機能の強化は、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] への次の 2 つのストアド プロシージャの追加により実現されました。</span><span class="sxs-lookup"><span data-stu-id="55172-127">The improved metadata discovery in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is possible because of the addition of two stored procedures in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="55172-128">sp_describe_first_result_set</span><span class="sxs-lookup"><span data-stu-id="55172-128">sp_describe_first_result_set</span></span>  
  
-   <span data-ttu-id="55172-129">sp_describe_undeclared_parameters</span><span class="sxs-lookup"><span data-stu-id="55172-129">sp_describe_undeclared_parameters</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55172-130">参照</span><span class="sxs-lookup"><span data-stu-id="55172-130">See Also</span></span>  
 [<span data-ttu-id="55172-131">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="55172-131">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  

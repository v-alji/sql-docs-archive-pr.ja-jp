---
title: SQL Server Native Client (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: rothja
ms.author: jroth
ms.openlocfilehash: 16c73966e318ed1e7d326fa77f56195ebbd830df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718075"
---
# <a name="sql-server-native-client-odbc"></a><span data-ttu-id="7f3d8-102">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="7f3d8-102">SQL Server Native Client (ODBC)</span></span>
  <span data-ttu-id="7f3d8-103">ODBC は、リレーショナル データベースまたは索引順次アクセス方式 (ISAM) データベースのデータへのアクセスに使用するアプリケーション プログラミング インターフェイス (API) の標準的な定義です。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-103">ODBC is a standard definition of an application programming interface (API) used to access data in relational or indexed sequential access method (ISAM) databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="7f3d8-104">は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と通信する C および C++ アプリケーションの作成に使用されるネイティブ API の 1 つとして、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを介して ODBC をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-104">supports ODBC, via the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, as one of the native APIs for writing C and C++ applications that communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="7f3d8-105">Native Client ODBC ドライバーを使用して作成された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プログラムは、C 関数の呼び出しによって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と通信します。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-105">programs that are written using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through C function calls.</span></span> <span data-ttu-id="7f3d8-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の ODBC 関数が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに実装されています。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-106">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific versions of the ODBC functions are implemented in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="7f3d8-107">ドライバーは、SQL ステートメントを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に渡し、ステートメントの結果をアプリケーションに返します。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-107">The driver passes SQL statements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and returns the results of the statements to the application.</span></span>  
  
 <span data-ttu-id="7f3d8-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは Microsoft Win32 ODBC 3.51 仕様に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-108">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with the Microsoft Win32 ODBC 3.51 specification.</span></span> <span data-ttu-id="7f3d8-109">以前のバージョンの ODBC を使用して作成されているアプリケーションは、ODBC 3.51 仕様で定義されている方法に従ってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7f3d8-109">The driver supports applications written using earlier versions of ODBC in the manner defined in the ODBC 3.51 specification.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f3d8-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7f3d8-110">In This Section</span></span>  
  
-   [<span data-ttu-id="7f3d8-111">データ ソース名と 64 ビット オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="7f3d8-111">Data Source Names and 64-Bit Operating Systems</span></span>](data-source-names-and-64-bit-operating-systems.md)  
  
-   [<span data-ttu-id="7f3d8-112">SQL Server Native Client ODBC ドライバー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="7f3d8-112">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
-   [<span data-ttu-id="7f3d8-113">ODBC&#41;&#40;SQL Server との通信</span><span class="sxs-lookup"><span data-stu-id="7f3d8-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-114">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="7f3d8-114">Executing Queries &#40;ODBC&#41;</span></span>](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-115">ODBC&#41;&#40;結果の処理</span><span class="sxs-lookup"><span data-stu-id="7f3d8-115">Processing Results &#40;ODBC&#41;</span></span>](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-116">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="7f3d8-116">Using Cursors &#40;ODBC&#41;</span></span>](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-117">ODBC&#41;&#40;のトランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="7f3d8-117">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-118">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="7f3d8-118">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [<span data-ttu-id="7f3d8-119">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="7f3d8-119">Running Stored Procedures</span></span>](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [<span data-ttu-id="7f3d8-120">カタログ関数の使用</span><span class="sxs-lookup"><span data-stu-id="7f3d8-120">Using Catalog Functions</span></span>](using-catalog-functions.md)  
  
-   [<span data-ttu-id="7f3d8-121">ODBC&#41;&#40;の一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="7f3d8-121">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-122">text 列と image 列の管理</span><span class="sxs-lookup"><span data-stu-id="7f3d8-122">Managing Text and Image Columns</span></span>](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [<span data-ttu-id="7f3d8-123">ODBC ドライバーのパフォーマンスのプロファイル</span><span class="sxs-lookup"><span data-stu-id="7f3d8-123">Profiling ODBC Driver Performance</span></span>](profiling-odbc-driver-performance.md)  
  
-   [<span data-ttu-id="7f3d8-124">テーブル値パラメーター &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="7f3d8-124">Table-Valued Parameters &#40;ODBC&#41;</span></span>](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-125">ODBC&#41;&#40;の日付と時刻の改善</span><span class="sxs-lookup"><span data-stu-id="7f3d8-125">Date and Time Improvements &#40;ODBC&#41;</span></span>](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-126">大きな CLR ユーザー定義型 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="7f3d8-126">Large CLR User-Defined Types &#40;ODBC&#41;</span></span>](large-clr-user-defined-types-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-127">FILESTREAM のサポート &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="7f3d8-127">FILESTREAM Support &#40;ODBC&#41;</span></span>](filestream-support-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-128">クライアント接続 &#40;ODBC&#41; でのサービス プリンシパル名 &#40;SPNs&#41;</span><span class="sxs-lookup"><span data-stu-id="7f3d8-128">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;</span></span>](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-129">スパース列は &#40;ODBC&#41;をサポートしています</span><span class="sxs-lookup"><span data-stu-id="7f3d8-129">Sparse Columns Support &#40;ODBC&#41;</span></span>](sparse-columns-support-odbc.md)  
  
-   [<span data-ttu-id="7f3d8-130">SQL Server Native Client &#40;ODBC&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="7f3d8-130">SQL Server Native Client &#40;ODBC&#41; Reference</span></span>](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [<span data-ttu-id="7f3d8-131">ODBC の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="7f3d8-131">ODBC How-to Topics</span></span>](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="7f3d8-132">参照</span><span class="sxs-lookup"><span data-stu-id="7f3d8-132">See Also</span></span>  
 <span data-ttu-id="7f3d8-133">[SQL Server Native Client プログラミング](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="7f3d8-133">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 [<span data-ttu-id="7f3d8-134">SQL Server Native Client のインストール</span><span class="sxs-lookup"><span data-stu-id="7f3d8-134">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  

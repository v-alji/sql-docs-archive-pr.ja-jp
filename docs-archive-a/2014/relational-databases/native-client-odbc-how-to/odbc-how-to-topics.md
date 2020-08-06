---
title: ODBC の操作方法に関するトピック |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 151f2066-1c37-410f-88f4-b27dfca66031
author: rothja
ms.author: jroth
ms.openlocfilehash: cfeb120b9fa1fedb5358b5e12dabed7835f9a6b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738305"
---
# <a name="odbc-how-to-topics"></a><span data-ttu-id="51e01-102">ODBC の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="51e01-102">ODBC How-to Topics</span></span>
  <span data-ttu-id="51e01-103">Odbc ドライバーを使用するに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、odbc データソースを作成し、サーバーに正しいバージョンのカタログストアドプロシージャがあることを確認できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="51e01-103">To use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver, you must be able to create ODBC data sources and ensure that the server has the correct version of the catalog stored procedures.</span></span> <span data-ttu-id="51e01-104">SQL Server を使用する ODBC アプリケーションをコーディングするには、ODBC ハンドルの割り当て方法、属性の設定方法、SQL Server インスタンスへの接続方法、クエリの実行方法、および結果の処理方法を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="51e01-104">To code an ODBC application that uses SQL Server, you must know how to allocate ODBC handles, set attributes, connect to an instance of SQL Server, execute queries, and process results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51e01-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="51e01-105">In This Section</span></span>  
  
-   [<span data-ttu-id="51e01-106">SQL Server ODBC ドライバーを構成する方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="51e01-106">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
-   [<span data-ttu-id="51e01-107">ハンドルを割り当てて SQL Server &#40;ODBC&#41;に接続する</span><span class="sxs-lookup"><span data-stu-id="51e01-107">Allocate Handles and Connect to SQL Server &#40;ODBC&#41;</span></span>](allocate-handles-and-connect-to-sql-server-odbc.md)  
  
-   [<span data-ttu-id="51e01-108">クエリの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-108">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](execute-queries/executing-queries-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="51e01-109">結果の処理方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-109">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="51e01-110">カーソルの使用方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-110">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](cursors/using-cursors-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="51e01-111">Microsoft 分散トランザクションコーディネーター &#40;ODBC&#41;を使用する</span><span class="sxs-lookup"><span data-stu-id="51e01-111">Use Microsoft Distributed Transaction Coordinator &#40;ODBC&#41;</span></span>](use-microsoft-distributed-transaction-coordinator-odbc.md)  
  
-   [<span data-ttu-id="51e01-112">ストアドプロシージャの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-112">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="51e01-113">Text 列と image 列の管理方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-113">Managing text and image Columns How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/managing-text-and-image-columns-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="51e01-114">Odbc&#41;&#40;ODBC ドライバーのパフォーマンスのプロファイル方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="51e01-114">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
-   [<span data-ttu-id="51e01-115">Odbc&#41;&#40;odbc エラーの処理</span><span class="sxs-lookup"><span data-stu-id="51e01-115">Process ODBC Errors &#40;ODBC&#41;</span></span>](process-odbc-errors-odbc.md)  
  
-   [<span data-ttu-id="51e01-116">SQL Server ODBC ドライバーを使用した一括コピーの操作方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-116">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copy/bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="51e01-117">参照</span><span class="sxs-lookup"><span data-stu-id="51e01-117">See Also</span></span>  
 [<span data-ttu-id="51e01-118">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="51e01-118">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  

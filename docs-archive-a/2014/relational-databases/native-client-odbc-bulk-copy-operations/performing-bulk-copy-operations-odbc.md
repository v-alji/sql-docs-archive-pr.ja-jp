---
title: 一括コピー操作の実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: rothja
ms.author: jroth
ms.openlocfilehash: f2647ebca703eab46d7be0e1cfc2490a65384ee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740926"
---
# <a name="performing-bulk-copy-operations-odbc"></a><span data-ttu-id="165c7-102">一括コピー操作の実行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="165c7-102">Performing Bulk Copy Operations (ODBC)</span></span>
  <span data-ttu-id="165c7-103">ODBC 標準では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一括コピー操作が直接サポートされません。</span><span class="sxs-lookup"><span data-stu-id="165c7-103">The ODBC standard does not directly support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="165c7-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降のインスタンスに接続するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一括コピー操作を実行する DB-Library 関数がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="165c7-104">When connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the DB-Library functions that perform [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="165c7-105">このドライバー固有の拡張機能では、一括コピー関数を使用する既存の DB-Library アプリケーションを簡単にアップグレードできる手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="165c7-105">This driver-specific extension provides an easy upgrade path for existing DB-Library applications that use bulk copy functions.</span></span> <span data-ttu-id="165c7-106">次のファイルには、一括コピー専用のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="165c7-106">The specialized bulk copy support is in the following files:</span></span>  
  
-   <span data-ttu-id="165c7-107">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="165c7-107">sqlncli.h</span></span>  
  
     <span data-ttu-id="165c7-108">一括コピー関数の関数プロトタイプと定数定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="165c7-108">Includes function prototypes and constant definitions for bulk copy functions.</span></span> <span data-ttu-id="165c7-109">一括コピー操作を実行する ODBC アプリケーションでは、sqlncli.h をインクルードする必要があります。このファイルは、コンパイル時にアプリケーションのインクルード パスに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="165c7-109">sqlncli.h must be included in the ODBC application performing bulk copy operations and must be in the application's include path when it is compiled.</span></span>  
  
-   <span data-ttu-id="165c7-110">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="165c7-110">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="165c7-111">リンカーのライブラリ パスに存在し、リンクされるファイルとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="165c7-111">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="165c7-112">sqlncli11.lib は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。</span><span class="sxs-lookup"><span data-stu-id="165c7-112">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="165c7-113">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="165c7-113">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="165c7-114">実行時に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="165c7-114">Must be present at execution time.</span></span> <span data-ttu-id="165c7-115">sqlncli11.dll は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。</span><span class="sxs-lookup"><span data-stu-id="165c7-115">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="165c7-116">ODBC **Sqlbulkoperations**関数には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一括コピー関数との関係はありません。</span><span class="sxs-lookup"><span data-stu-id="165c7-116">The ODBC **SQLBulkOperations** function has no relationship to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy functions.</span></span> <span data-ttu-id="165c7-117">アプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の一括コピー関数を使用して、一括コピー操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="165c7-117">Applications must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy functions to perform bulk copy operations.</span></span>  
  
## <a name="minimally-logging-bulk-copies"></a><span data-ttu-id="165c7-118">一括コピーの最小ログ記録</span><span class="sxs-lookup"><span data-stu-id="165c7-118">Minimally Logging Bulk Copies</span></span>  
 <span data-ttu-id="165c7-119">完全復旧モデルでは、一括読み込みで実行されたすべての行挿入操作が、トランザクション ログに完全に記録されます。</span><span class="sxs-lookup"><span data-stu-id="165c7-119">With the Full Recovery model, all row-insert operations performed by bulk load are fully logged in the transaction log.</span></span> <span data-ttu-id="165c7-120">ただし大量のデータを読み込むと、トランザクション ログがすぐにいっぱいになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="165c7-120">For large data loads, this can cause the transaction log to fill rapidly.</span></span> <span data-ttu-id="165c7-121">特定の条件下では、最小ログ記録が可能になります。</span><span class="sxs-lookup"><span data-stu-id="165c7-121">Under certain conditions, minimally logging is possible.</span></span> <span data-ttu-id="165c7-122">最小ログ記録を行うことで、一括読み込み操作によってログ領域がいっぱいになる可能性が少なくなります。また、これは完全なログ記録よりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="165c7-122">Minimal logging reduces the possibility of a bulk load operation filling the log space and is also more efficient than full logging.</span></span>  
  
 <span data-ttu-id="165c7-123">最小ログ記録の使用の詳細については、「[一括インポートで最小ログ記録を行うための前提条件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="165c7-123">For information on using minimal logging, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="165c7-124">解説</span><span class="sxs-lookup"><span data-stu-id="165c7-124">Remarks</span></span>  
 <span data-ttu-id="165c7-125">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で bcp.exe を使用すると、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは発生しなかった状況でエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="165c7-125">When using bcp.exe in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, you might see errors in situations where there were no errors prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="165c7-126">これは、新しいバージョンでは bcp.exe でデータ型が暗黙的に変換されなくなったためです。</span><span class="sxs-lookup"><span data-stu-id="165c7-126">This is because in the later versions, bcp.exe no longer performs implicit data type conversion.</span></span> <span data-ttu-id="165c7-127">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは、対象テーブルのデータ型が money データ型の場合、bcp.exe で数値データが money データ型に変換されました。</span><span class="sxs-lookup"><span data-stu-id="165c7-127">Prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], bcp.exe converted numeric data to a money data type, if the target table had a money data type.</span></span> <span data-ttu-id="165c7-128">ただし、その際には、余分なフィールドは単純に切り捨てられていました。</span><span class="sxs-lookup"><span data-stu-id="165c7-128">However, in that situation, bcp.exe simply truncated extra fields.</span></span> <span data-ttu-id="165c7-129">以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、データ型がファイルと対象テーブルの間で一致しない場合、対象テーブルに合わせて切り捨てが必要なデータがあると、bcp.exe によってエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="165c7-129">Beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if data types do not match between the file and the target table, bcp.exe will raise an error if there is any data that would have to be truncated to fit into the target table.</span></span> <span data-ttu-id="165c7-130">このエラーを解決するには、対象のデータ型に合わせてデータを修正します。</span><span class="sxs-lookup"><span data-stu-id="165c7-130">To resolve this error, fix the data to match the target data type.</span></span> <span data-ttu-id="165c7-131">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のリリースの bcp.exe を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="165c7-131">Optionally, use bcp.exe from a release prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="165c7-132">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="165c7-132">In This Section</span></span>  
  
-   [<span data-ttu-id="165c7-133">データ ファイルとフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="165c7-133">Using Data Files and Format Files</span></span>](using-data-files-and-format-files.md)  
  
-   [<span data-ttu-id="165c7-134">プログラム変数からの一括コピー</span><span class="sxs-lookup"><span data-stu-id="165c7-134">Bulk Copying from Program Variables</span></span>](bulk-copying-from-program-variables.md)  
  
-   [<span data-ttu-id="165c7-135">一括コピー バッチ サイズの管理</span><span class="sxs-lookup"><span data-stu-id="165c7-135">Managing Bulk Copy Batch Sizes</span></span>](managing-bulk-copy-batch-sizes.md)  
  
-   [<span data-ttu-id="165c7-136">テキスト データと画像データの一括コピー</span><span class="sxs-lookup"><span data-stu-id="165c7-136">Bulk Copying Text and Image Data</span></span>](bulk-copying-text-and-image-data.md)  
  
-   [<span data-ttu-id="165c7-137">DB-Library から ODBC への一括コピーの変換</span><span class="sxs-lookup"><span data-stu-id="165c7-137">Converting from DB-Library to ODBC Bulk Copy</span></span>](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a><span data-ttu-id="165c7-138">参照</span><span class="sxs-lookup"><span data-stu-id="165c7-138">See Also</span></span>  
 <span data-ttu-id="165c7-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="165c7-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="165c7-140">データの一括インポートと一括エクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="165c7-140">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  

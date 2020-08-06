---
title: ODBC ドライバーのパフォーマンスのプロファイルに関するトピック (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: rothja
ms.author: jroth
ms.openlocfilehash: d27547862138b511a4defaa3cae80f48f69fdc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631885"
---
# <a name="profiling-odbc-driver-performance-how-to-topics-odbc"></a><span data-ttu-id="38c0e-102">ODBC ドライバーのパフォーマンスをプロファイルする方法に関するトピック (ODBC)</span><span class="sxs-lookup"><span data-stu-id="38c0e-102">Profiling ODBC Driver Performance How-to Topics (ODBC)</span></span>
  <span data-ttu-id="38c0e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバーには、ドライバーのパフォーマンスをプロファイルするための、ドライバー固有の 2 つのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="38c0e-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver has two driver-specific options for profiling the performance of the driver.</span></span>  
  
 <span data-ttu-id="38c0e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC ドライバーは、パフォーマンスの統計情報をファイルに記録できます。</span><span class="sxs-lookup"><span data-stu-id="38c0e-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver can log performance statistics in file.</span></span> <span data-ttu-id="38c0e-105">ログ ファイルはタブで区切られており、Microsoft Excel など、タブ区切りのファイルをサポートする任意のスプレッドシートで分析できます。</span><span class="sxs-lookup"><span data-stu-id="38c0e-105">The log file is a tab-delimited file that can be analyzed in any spreadsheet supporting tab-delimited files, such as Microsoft Excel.</span></span>  
  
 <span data-ttu-id="38c0e-106">ドライバーは、実行時間の長いクエリ (指定した時間内にサーバーから応答が得られないクエリ) もログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="38c0e-106">The driver can also log long-running queries (queries that do not get a response from the server in a specified length of time).</span></span> <span data-ttu-id="38c0e-107">プログラマとデータベース管理者は、これらのクエリを後で分析できます。</span><span class="sxs-lookup"><span data-stu-id="38c0e-107">These queries can later be analyzed by programmers and database administrators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38c0e-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="38c0e-108">In This Section</span></span>  
  
-   [<span data-ttu-id="38c0e-109">ODBC&#41;&#40;プロファイルドライバーのパフォーマンスデータ</span><span class="sxs-lookup"><span data-stu-id="38c0e-109">Profile Driver Performance Data &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data.md)  
  
-   [<span data-ttu-id="38c0e-110">実行時間の長いクエリをログに記録 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="38c0e-110">Log Long-Running Queries &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a><span data-ttu-id="38c0e-111">参照</span><span class="sxs-lookup"><span data-stu-id="38c0e-111">See Also</span></span>  
 [<span data-ttu-id="38c0e-112">ODBC の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="38c0e-112">ODBC How-to Topics</span></span>](odbc-how-to-topics.md)  
  
  

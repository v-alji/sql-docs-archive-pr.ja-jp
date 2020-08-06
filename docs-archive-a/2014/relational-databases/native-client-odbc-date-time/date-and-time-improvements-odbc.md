---
title: 日付と時刻の強化 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ce8f906fc1949a80bfa8e5a541ecf1e83878775
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640902"
---
# <a name="date-and-time-improvements-odbc"></a><span data-ttu-id="ac47e-102">日付と時刻の強化機能 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ac47e-102">Date and Time Improvements (ODBC)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="ac47e-103">では、新しい日付と時刻のデータ型が導入されました。</span><span class="sxs-lookup"><span data-stu-id="ac47e-103">introduced new date and time data types.</span></span> <span data-ttu-id="ac47e-104">このセクションでは、これらの新しい型がネイティブクライアントで拡張として公開されるしくみについて説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ac47e-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="ac47e-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client による新しい日付と時刻のデータ型のサポートの概要については、「[日付と時刻の機能強化](../native-client/features/date-and-time-improvements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac47e-105">For an overview of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="ac47e-106">ODBC の日付と時刻のサポートを示すサンプルについては、「[日付と時刻の型の使用](../native-client-odbc-how-to/use-date-and-time-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac47e-106">For a sample demonstrating ODBC date/time support, see [Use Date and Time Types](../native-client-odbc-how-to/use-date-and-time-types.md).</span></span>  
  
 <span data-ttu-id="ac47e-107">日付と時刻のデータ型に関する一般的な情報については、「[datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac47e-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac47e-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ac47e-108">In This Section</span></span>  
 [<span data-ttu-id="ac47e-109">ODBC の日付/時刻の強化に対するデータ型のサポート</span><span class="sxs-lookup"><span data-stu-id="ac47e-109">Data Type Support for ODBC Date and Time Improvements</span></span>](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 <span data-ttu-id="ac47e-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付と時刻のデータ型をサポートする ODBC 型について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-110">Provides information about ODBC types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="ac47e-111">ODBC&#41;&#40;メタデータ</span><span class="sxs-lookup"><span data-stu-id="ac47e-111">Metadata &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/metadata-odbc.md)  
 <span data-ttu-id="ac47e-112">実装パラメーター記述子 (IPD) フィールドと実装行記述子 (IRD) フィールドに返される情報、および `SQLColumns` と `SQLProcedureColumns` によって返される列のメタデータについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-112">Describes information returned in the implementation parameter descriptor (IPD) and implementation row descriptor (IRD) fields, as well as column metadata returned by `SQLColumns` and `SQLProcedureColumns`.</span></span> <span data-ttu-id="ac47e-113">また、`SQLGetTypeInfo` によって返される、データ型のメタデータについても説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-113">Also describes data type metadata returned by `SQLGetTypeInfo`.</span></span>  
  
 [<span data-ttu-id="ac47e-114">ODBC&#41;&#40;の datetime データ型の変換</span><span class="sxs-lookup"><span data-stu-id="ac47e-114">datetime Data Type Conversions &#40;ODBC&#41;</span></span>](datetime-data-type-conversions-odbc.md)  
 <span data-ttu-id="ac47e-115">datetime 値と datetimeoffset 値の間で変換を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-115">Describes how to convert between datetime and datetimeoffset values.</span></span>  
  
 [<span data-ttu-id="ac47e-116">sql_variant による日付型と時刻型のサポート</span><span class="sxs-lookup"><span data-stu-id="ac47e-116">sql_variant Support for Date and Time Types</span></span>](sql-variant-support-for-date-and-time-types.md)  
 <span data-ttu-id="ac47e-117">SQL_VARIANT 関数による機能強化された日付と時刻のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-117">Describes SQL_VARIANT function support for enhanced date and time functionality.</span></span>  
  
 [<span data-ttu-id="ac47e-118">OLE DB および ODBC の &#40;、強化された日付/時刻型に対する一括コピーの変更&#41;</span><span class="sxs-lookup"><span data-stu-id="ac47e-118">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="ac47e-119">一括コピー操作をサポートする日付または時刻の機能強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-119">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="ac47e-120">以前の SQL Server バージョン &#40;ODBC&#41;の日付と時刻の型の動作の強化</span><span class="sxs-lookup"><span data-stu-id="ac47e-120">Enhanced Date and Time Type Behavior with Previous SQL Server Versions &#40;ODBC&#41;</span></span>](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 <span data-ttu-id="ac47e-121">機能強化された日付と時刻を使用するクライアントアプリケーションが古いバージョンのと通信する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および以前のバージョンの Native client でコンパイルされたクライアントが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能強化された日付と時刻の機能をサポートするサーバーにコマンドを送信する場合に想定される動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-121">Describes the expected behavior when a client application using enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
 [<span data-ttu-id="ac47e-122">ODBC API による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="ac47e-122">ODBC API Support for Enhanced Date and Time Features</span></span>](odbc-api-support-for-enhanced-date-and-time-features.md)  
 <span data-ttu-id="ac47e-123">機能強化された日付と時刻をサポートする ODBC 関数の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ac47e-123">Lists the ODBC functions that support enhanced date and time functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac47e-124">参照</span><span class="sxs-lookup"><span data-stu-id="ac47e-124">See Also</span></span>  
 [<span data-ttu-id="ac47e-125">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="ac47e-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  

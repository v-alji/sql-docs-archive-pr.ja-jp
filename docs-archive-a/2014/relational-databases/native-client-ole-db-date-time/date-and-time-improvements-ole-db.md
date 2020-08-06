---
title: 日付と時刻の機能強化 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: rothja
ms.author: jroth
ms.openlocfilehash: 16bb9e98691aea829eb71a16ddabddb371d7bcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739859"
---
# <a name="date-and-time-improvements-ole-db"></a><span data-ttu-id="0353d-102">日付と時刻の強化機能 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="0353d-102">Date and Time Improvements (OLE DB)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="0353d-103">では、新しい日付と時刻のデータ型が導入されています。</span><span class="sxs-lookup"><span data-stu-id="0353d-103">introduces new date and time data types.</span></span> <span data-ttu-id="0353d-104">このセクションでは、これらの新しい型がネイティブクライアントで拡張として公開されるしくみについて説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="0353d-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="0353d-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しい日付と時刻のデータ型の Native Client のサポートの概要については、「[日付と時刻の機能強化](../native-client/features/date-and-time-improvements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0353d-105">For an overview of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="0353d-106">サンプルについては、「[強化された日付/時刻機能の使用 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0353d-106">For a sample, see [Use Enhanced Date and Time Features &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).</span></span>  
  
 <span data-ttu-id="0353d-107">日付と時刻のデータ型に関する一般的な情報については、「[datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0353d-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0353d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0353d-108">In This Section</span></span>  
 [<span data-ttu-id="0353d-109">OLE DB の日付/時刻の強化に対するデータ型のサポート</span><span class="sxs-lookup"><span data-stu-id="0353d-109">Data Type Support for OLE DB Date and Time Improvements</span></span>](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 <span data-ttu-id="0353d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付と時刻のデータ型をサポートする OLE DB (Native Client) 型に関する情報を提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="0353d-110">Provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="0353d-111">メタデータ &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0353d-111">Metadata &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/metadata-ole-db.md)  
 <span data-ttu-id="0353d-112">DBBINDING 構造体、、、、および I に関する情報を格納し `ICommandWithParameters::GetParameterInfo` `ICommandWithParameters::SetParameterInfo` `IColumnsRowset::GetColumnsRowset` `ColumnsInfo::GetColumnInfo` ます。また、OLE DB スキーマ行セットの更新に関する情報も提供します。</span><span class="sxs-lookup"><span data-stu-id="0353d-112">Contains information about the DBBINDING structure, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset`, and I`ColumnsInfo::GetColumnInfo`. Also provides information about updates to OLE DB schema rowsets.</span></span>  
  
 [<span data-ttu-id="0353d-113">バインドと変換 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0353d-113">Bindings and Conversions &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 <span data-ttu-id="0353d-114">既存の日付型と新しい日付型の両方を対象とした、サーバーとクライアント間における変換の規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="0353d-114">Describes the rules for conversion between server and client for both existing and new date types.</span></span>  
  
 [<span data-ttu-id="0353d-115">OLE DB および ODBC の &#40;、強化された日付/時刻型に対する一括コピーの変更&#41;</span><span class="sxs-lookup"><span data-stu-id="0353d-115">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="0353d-116">一括コピー操作をサポートする日付または時刻の機能強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="0353d-116">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="0353d-117">OLE DB API による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="0353d-117">OLE DB API Support for Date and Time Enhancements</span></span>](ole-db-api-support-for-date-and-time-enhancements.md)  
 <span data-ttu-id="0353d-118">機能強化された日付や時刻をサポートする OLE DB API について説明します。</span><span class="sxs-lookup"><span data-stu-id="0353d-118">Describes the OLE DB APIs that support enhanced date/time features.</span></span>  
  
 [<span data-ttu-id="0353d-119">IRowsetFind での比較</span><span class="sxs-lookup"><span data-stu-id="0353d-119">Comparability for IRowsetFind</span></span>](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 <span data-ttu-id="0353d-120">日付型または時刻型、および `IRowsetFind` について説明します。</span><span class="sxs-lookup"><span data-stu-id="0353d-120">Describes date/time types and `IRowsetFind`.</span></span>  
  
 [<span data-ttu-id="0353d-121">以前の SQL Server バージョン &#40;OLE DB の新しい日付と時刻の機能&#41;</span><span class="sxs-lookup"><span data-stu-id="0353d-121">New Date and Time Features with Previous SQL Server Versions &#40;OLE DB&#41;</span></span>](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 <span data-ttu-id="0353d-122">機能強化された日付や時刻を使用するクライアント アプリケーションが以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と通信する場合、および以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でコンパイルされたクライアントから、機能強化された日付や時刻をサポートするサーバーにコマンドを送信する場合に想定される動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="0353d-122">Describes the expected behavior when a client application that uses enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0353d-123">参照</span><span class="sxs-lookup"><span data-stu-id="0353d-123">See Also</span></span>  
 [<span data-ttu-id="0353d-124">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0353d-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  

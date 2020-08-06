---
title: SQL Server Native Client (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: rothja
ms.author: jroth
ms.openlocfilehash: 46b948eb1d075edc6000849dcb2d18ea372809d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639475"
---
# <a name="sql-server-native-client-ole-db"></a><span data-ttu-id="1db6c-102">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1db6c-102">SQL Server Native Client (OLE DB)</span></span>
  <span data-ttu-id="1db6c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、データへのアクセスに使用する低レベルの COM API です。</span><span class="sxs-lookup"><span data-stu-id="1db6c-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a low-level COM API that is used for accessing data.</span></span> <span data-ttu-id="1db6c-104">高いパフォーマンスが必要なツール、ユーティリティ、または低レベルのコンポーネントを開発する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1db6c-104">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is recommended for developing tools, utilities, or low-level components that need high performance.</span></span> <span data-ttu-id="1db6c-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の表形式のデータ ストリーム (TDS) プロトコルに直接アクセスするパフォーマンスの高いネイティブ プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="1db6c-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a native, high performance provider that accesses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabular Data Stream (TDS) protocol directly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1db6c-106">Native Client は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続するアプリケーションに OLE DB サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="1db6c-106">Native Client provides OLE DB support to applications connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1db6c-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、OLE DB バージョン2.0 に準拠しているプロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="1db6c-107">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is an OLE DB version 2.0-compliant provider.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1db6c-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1db6c-108">In This Section</span></span>  
  
-   [<span data-ttu-id="1db6c-109">SQL Server Native Client OLE DB プロバイダー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="1db6c-109">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](../../native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [<span data-ttu-id="1db6c-110">データ ソース オブジェクト &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-110">Data Source Objects &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-111">コマンド</span><span class="sxs-lookup"><span data-stu-id="1db6c-111">Commands</span></span>](../../native-client-ole-db-commands/commands.md)  
  
-   [<span data-ttu-id="1db6c-112">行セット</span><span class="sxs-lookup"><span data-stu-id="1db6c-112">Rowsets</span></span>](../../native-client-ole-db-rowsets/rowsets.md)  
  
-   [<span data-ttu-id="1db6c-113">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1db6c-113">Stored Procedures</span></span>](stored-procedures.md)  
  
-   [<span data-ttu-id="1db6c-114">BLOB と OLE オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1db6c-114">BLOBs and OLE Objects</span></span>](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [<span data-ttu-id="1db6c-115">テーブルとインデックス</span><span class="sxs-lookup"><span data-stu-id="1db6c-115">Tables and Indexes</span></span>](../../native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [<span data-ttu-id="1db6c-116">データ型 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-116">Data Types &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-117">スキーマ行セットのサポート &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-117">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-118">テーブル値パラメーター &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-118">Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-119">日付と時刻の強化機能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-119">Date and Time Improvements &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-120">大きな CLR ユーザー定義型 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-120">Large CLR User-Defined Types &#40;OLE DB&#41;</span></span>](large-clr-user-defined-types-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-121">FILESTREAM サポート &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-121">FILESTREAM Support &#40;OLE DB&#41;</span></span>](filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-122">トランザクション</span><span class="sxs-lookup"><span data-stu-id="1db6c-122">Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
  
-   [<span data-ttu-id="1db6c-123">エラー</span><span class="sxs-lookup"><span data-stu-id="1db6c-123">Errors</span></span>](../../native-client-ole-db-errors/errors.md)  
  
-   [<span data-ttu-id="1db6c-124">クライアント接続 &#40;OLE DB&#41; でのサービス プリンシパル名 &#40;SPNs&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-124">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;</span></span>](service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-125">スパース列のサポート &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1db6c-125">Sparse Columns Support &#40;OLE DB&#41;</span></span>](sparse-columns-support-ole-db.md)  
  
-   [<span data-ttu-id="1db6c-126">SQL Server Native Client &#40;OLE DB&#41; 参照</span><span class="sxs-lookup"><span data-stu-id="1db6c-126">SQL Server Native Client &#40;OLE DB&#41; Reference</span></span>](../../native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [<span data-ttu-id="1db6c-127">OLE DB の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="1db6c-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="1db6c-128">参照</span><span class="sxs-lookup"><span data-stu-id="1db6c-128">See Also</span></span>  
 [<span data-ttu-id="1db6c-129">SQL Server Native Client プログラミング</span><span class="sxs-lookup"><span data-stu-id="1db6c-129">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  

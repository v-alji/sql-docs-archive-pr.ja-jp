---
title: その他の SQL Server 以外のサブスクライバー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3849ca717e82bcf1bed5769190c9f898209a454a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630904"
---
# <a name="other-non-sql-server-subscribers"></a><span data-ttu-id="0a95d-102">その他の SQL Server 以外のサブスクライバー</span><span class="sxs-lookup"><span data-stu-id="0a95d-102">Other Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="0a95d-103">でサポートされている以外のサブスクライバーの一覧につい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ては、「 [SQL Server 以外のサブスクライバー](non-sql-server-subscribers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a95d-103">For a list of non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers supported by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span> <span data-ttu-id="0a95d-104">ここでは、ODBC ドライバーと OLE DB プロバイダーの要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a95d-104">This topic includes information about requirements for ODBC drivers and OLE DB providers.</span></span>  
  
## <a name="odbc-driver-requirements"></a><span data-ttu-id="0a95d-105">ODBC ドライバーの要件</span><span class="sxs-lookup"><span data-stu-id="0a95d-105">ODBC Driver Requirements</span></span>  
 <span data-ttu-id="0a95d-106">ODBC ドライバーは、以下の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a95d-106">The ODBC driver:</span></span>  
  
-   <span data-ttu-id="0a95d-107">ODBC Level-1 に準拠している</span><span class="sxs-lookup"><span data-stu-id="0a95d-107">Must be ODBC level-1 compliant.</span></span>  
  
-   <span data-ttu-id="0a95d-108">スレッドセーフで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターが実行されているプロセッサ アーキテクチャ (Intel または Alpha) およびプラットフォーム (32 ビットまたは 64 ビット) に対応している</span><span class="sxs-lookup"><span data-stu-id="0a95d-108">Must be thread-safe, and for the processor architecture (Intel or Alpha) and platform (32 bit or 64 bit) on which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor runs.</span></span>  
  
-   <span data-ttu-id="0a95d-109">トランザクションの実行が可能である</span><span class="sxs-lookup"><span data-stu-id="0a95d-109">Must be transaction capable.</span></span>  
  
-   <span data-ttu-id="0a95d-110">データ定義言語 (DDL) をサポートする</span><span class="sxs-lookup"><span data-stu-id="0a95d-110">Must support the Data Definition Language (DDL).</span></span>  
  
-   <span data-ttu-id="0a95d-111">読み取り専用にはできない</span><span class="sxs-lookup"><span data-stu-id="0a95d-111">Cannot be read-only.</span></span>  
  
-   <span data-ttu-id="0a95d-112">**MSreplication_subscriptions**などの長いテーブル名をサポートしている</span><span class="sxs-lookup"><span data-stu-id="0a95d-112">Must support long table names such as **MSreplication_subscriptions**.</span></span>  
  
## <a name="replicating-using-ole-db-interfaces"></a><span data-ttu-id="0a95d-113">OLE DB インターフェイスを使用するレプリケーション</span><span class="sxs-lookup"><span data-stu-id="0a95d-113">Replicating Using OLE DB Interfaces</span></span>  
 <span data-ttu-id="0a95d-114">トランザクション レプリケーションを行うには、OLE DB プロバイダーが以下のオブジェクトをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a95d-114">OLE DB providers must support these objects for transactional replication:</span></span>  
  
-   <span data-ttu-id="0a95d-115">**DataSource** オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0a95d-115">**DataSource** object</span></span>  
  
-   <span data-ttu-id="0a95d-116">**Session** オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0a95d-116">**Session** object</span></span>  
  
-   <span data-ttu-id="0a95d-117">**Command** オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0a95d-117">**Command** object</span></span>  
  
-   <span data-ttu-id="0a95d-118">**Rowset** オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0a95d-118">**Rowset** object</span></span>  
  
-   <span data-ttu-id="0a95d-119">**Error** オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0a95d-119">**Error** object</span></span>  
  
### <a name="datasource-object-interfaces"></a><span data-ttu-id="0a95d-120">DataSource オブジェクト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a95d-120">DataSource Object Interfaces</span></span>  
 <span data-ttu-id="0a95d-121">データ ソースに接続するためには、以下のインターフェイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a95d-121">The following interfaces are required to connect to a data source:</span></span>  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 <span data-ttu-id="0a95d-122">プロバイダーが **IDBInfo** インターフェイスをサポートしている場合、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はこのインターフェイスを使用して、引用符で囲まれた識別子の文字、SQL ステートメントの最大長、テーブル名と列名の最大文字数などの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a95d-122">If the provider supports the **IDBInfo** interface, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses the interface to retrieve information such as the quoted identifier character, maximum SQL statement length, and maximum number of characters in table and column names.</span></span>  
  
### <a name="session-object-interfaces"></a><span data-ttu-id="0a95d-123">Session オブジェクト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a95d-123">Session Object Interfaces</span></span>  
 <span data-ttu-id="0a95d-124">以下のインターフェイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a95d-124">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="0a95d-125">**IDBCreateCommand**</span><span class="sxs-lookup"><span data-stu-id="0a95d-125">**IDBCreateCommand**</span></span>  
  
-   <span data-ttu-id="0a95d-126">**ITransaction**</span><span class="sxs-lookup"><span data-stu-id="0a95d-126">**ITransaction**</span></span>  
  
-   <span data-ttu-id="0a95d-127">**ITransactionLocal**</span><span class="sxs-lookup"><span data-stu-id="0a95d-127">**ITransactionLocal**</span></span>  
  
-   <span data-ttu-id="0a95d-128">**IDBSchemaRowset**</span><span class="sxs-lookup"><span data-stu-id="0a95d-128">**IDBSchemaRowset**</span></span>  
  
### <a name="command-object-interfaces"></a><span data-ttu-id="0a95d-129">Command オブジェクト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a95d-129">Command Object Interfaces</span></span>  
 <span data-ttu-id="0a95d-130">以下のインターフェイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a95d-130">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="0a95d-131">**ICommand**</span><span class="sxs-lookup"><span data-stu-id="0a95d-131">**ICommand**</span></span>  
  
-   <span data-ttu-id="0a95d-132">**ICommandProperties**</span><span class="sxs-lookup"><span data-stu-id="0a95d-132">**ICommandProperties**</span></span>  
  
-   <span data-ttu-id="0a95d-133">**ICommandText**</span><span class="sxs-lookup"><span data-stu-id="0a95d-133">**ICommandText**</span></span>  
  
-   <span data-ttu-id="0a95d-134">**ICommandPrepare**</span><span class="sxs-lookup"><span data-stu-id="0a95d-134">**ICommandPrepare**</span></span>  
  
-   <span data-ttu-id="0a95d-135">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="0a95d-135">**IColumnsInfo**</span></span>  
  
-   <span data-ttu-id="0a95d-136">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="0a95d-136">**IAccessor**</span></span>  
  
-   <span data-ttu-id="0a95d-137">**ICommandWithParameters**</span><span class="sxs-lookup"><span data-stu-id="0a95d-137">**ICommandWithParameters**</span></span>  
  
 <span data-ttu-id="0a95d-138">**IAccessor** は、パラメーター アクセサーを作成するために必要です。</span><span class="sxs-lookup"><span data-stu-id="0a95d-138">**IAccessor** is necessary to create parameter accessors.</span></span> <span data-ttu-id="0a95d-139">プロバイダーが**IColumnRowset**をサポートしている場合、は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのインターフェイスを使用して、列が id 列であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="0a95d-139">If the provider supports **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses that interface to determine whether a column is an identity column.</span></span>  
  
### <a name="rowset-object-interfaces"></a><span data-ttu-id="0a95d-140">Rowset オブジェクト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a95d-140">Rowset Object Interfaces</span></span>  
 <span data-ttu-id="0a95d-141">以下のインターフェイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a95d-141">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="0a95d-142">**IRowset**</span><span class="sxs-lookup"><span data-stu-id="0a95d-142">**IRowset**</span></span>  
  
-   <span data-ttu-id="0a95d-143">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="0a95d-143">**IAccessor**</span></span>  
  
-   <span data-ttu-id="0a95d-144">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="0a95d-144">**IColumnsInfo**</span></span>  
  
 <span data-ttu-id="0a95d-145">アプリケーションは、サブスクリプション データベース内に作成された、レプリケートされるテーブル上の行セットを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a95d-145">An application should open a rowset on a replicated table that is created in the subscription database.</span></span> <span data-ttu-id="0a95d-146">**IColumnsInfo** と **IAccessor** は、その行セット内のデータにアクセスするために必要です。</span><span class="sxs-lookup"><span data-stu-id="0a95d-146">**IColumnsInfo** and **IAccessor** are needed to access data in the rowset.</span></span>  
  
### <a name="error-object-interfaces"></a><span data-ttu-id="0a95d-147">Error オブジェクト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a95d-147">Error Object Interfaces</span></span>  
 <span data-ttu-id="0a95d-148">エラーの管理には、以下のインターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0a95d-148">Use the following interfaces to manage errors:</span></span>  
  
-   <span data-ttu-id="0a95d-149">**IErrorRecords**</span><span class="sxs-lookup"><span data-stu-id="0a95d-149">**IErrorRecords**</span></span>  
  
-   <span data-ttu-id="0a95d-150">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="0a95d-150">**IErrorInfo**</span></span>  
  
 <span data-ttu-id="0a95d-151">**ISQLErrorInfo** は、OLE DB プロバイダーが ISQLErrorInfo をサポートしている場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="0a95d-151">Use **ISQLErrorInfo** if it is supported by the OLE DB provider.</span></span>  
  
 <span data-ttu-id="0a95d-152">OLE DB プロバイダーの詳細については、OLE DB プロバイダー付属のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a95d-152">For more information about the OLE DB provider, see the documentation supplied with your OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a95d-153">参照</span><span class="sxs-lookup"><span data-stu-id="0a95d-153">See Also</span></span>  
 [<span data-ttu-id="0a95d-154">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="0a95d-154">Non-SQL Server Subscribers</span></span>](non-sql-server-subscribers.md)  
  
  

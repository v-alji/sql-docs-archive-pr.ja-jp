---
title: リンク サーバー (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB, linked servers
- OLE DB provider, linked servers
- server management [SQL Server], linked servers
- linked servers [SQL Server]
- distributed queries [SQL Server], linked servers
- servers [SQL Server], linked
- remote servers [SQL Server], linked servers
- linked servers [SQL Server], about linked servers
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1de70882cdeb87ccc0ae42aa23a9b6c8b3248e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631894"
---
# <a name="linked-servers-database-engine"></a><span data-ttu-id="31b6a-102">リンク サーバー (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="31b6a-102">Linked Servers (Database Engine)</span></span>
  <span data-ttu-id="31b6a-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスの外に存在する OLE DB データ ソースに対し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]からコマンドを実行できるようにするには、リンク サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-103">Configure a linked server to enable the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to execute commands against OLE DB data sources outside of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31b6a-104">通常、リンク サーバーを構成する目的は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の別のインスタンスまたは別のデータベース製品 (Oracle など) のテーブルを含んだ [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]から実行できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="31b6a-104">Typically linked servers are configured to enable the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that includes tables in another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or another database product such as Oracle.</span></span> <span data-ttu-id="31b6a-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] の Access や Excel など、さまざまな種類の OLE DB データ ソースをリンク サーバーとして構成できます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-105">Many types OLE DB data sources can be configured as linked servers, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access and Excel.</span></span> <span data-ttu-id="31b6a-106">リンク サーバーには次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="31b6a-106">Linked servers offer the following advantages:</span></span>

-   <span data-ttu-id="31b6a-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の外部のデータにアクセスできる。</span><span class="sxs-lookup"><span data-stu-id="31b6a-107">The ability to access data from outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

-   <span data-ttu-id="31b6a-108">企業内のさまざまなデータ ソースに対して分散クエリ、更新、コマンド、およびトランザクションを実行できる。</span><span class="sxs-lookup"><span data-stu-id="31b6a-108">The ability to issue distributed queries, updates, commands, and transactions on heterogeneous data sources across the enterprise.</span></span>

-   <span data-ttu-id="31b6a-109">さまざまなデータ ソースを同じように処理できる。</span><span class="sxs-lookup"><span data-stu-id="31b6a-109">The ability to address diverse data sources similarly.</span></span>

 <span data-ttu-id="31b6a-110">リンク サーバーの構成は、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) ステートメントを使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-110">You can configure a linked server by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or by using the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) statement.</span></span> <span data-ttu-id="31b6a-111">各 OLE DB プロバイダーは、必要なパラメーターの数と型という点で大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="31b6a-111">OLE DB providers vary greatly in the type and number of parameters required.</span></span> <span data-ttu-id="31b6a-112">たとえば、プロバイダーによっては、 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)からコマンドを実行できるようにするには、リンク サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-112">For example some providers require you to provide a security context for the connection using [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql).</span></span> <span data-ttu-id="31b6a-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から OLE DB ソース上のデータを更新できる OLE DB プロバイダーもあれば、</span><span class="sxs-lookup"><span data-stu-id="31b6a-113">Some OLE DB providers allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to update data on the OLE DB source.</span></span> <span data-ttu-id="31b6a-114">読み取り専用データ アクセスに特化したものも存在します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-114">Others provide only read-only data access.</span></span> <span data-ttu-id="31b6a-115">各 OLE DB プロバイダーの詳細については、該当する OLE DB プロバイダーのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="31b6a-115">For information about each OLE DB provider, consult documentation for that OLE DB provider.</span></span>

## <a name="linked-server-components"></a><span data-ttu-id="31b6a-116">リンク サーバーのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="31b6a-116">Linked Server Components</span></span>
 <span data-ttu-id="31b6a-117">リンク サーバーの定義では、次のオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-117">A linked server definition specifies the following objects:</span></span>

-   <span data-ttu-id="31b6a-118">OLE DB プロバイダー</span><span class="sxs-lookup"><span data-stu-id="31b6a-118">An OLE DB provider</span></span>

-   <span data-ttu-id="31b6a-119">OLE DB データ ソース</span><span class="sxs-lookup"><span data-stu-id="31b6a-119">An OLE DB data source</span></span>

 <span data-ttu-id="31b6a-120">*OLE DB プロバイダー* は、特定のデータ ソースを管理し、相互運用する DLL です。</span><span class="sxs-lookup"><span data-stu-id="31b6a-120">An *OLE DB provider* is a DLL that manages and interacts with a specific data source.</span></span> <span data-ttu-id="31b6a-121">*OLE DB データ ソース* は、OLE DB を使用してアクセスできる特定のデータベースを識別します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-121">An *OLE DB data source* identifies the specific database that can be accessed through OLE DB.</span></span> <span data-ttu-id="31b6a-122">リンク サーバーの定義を使用してクエリが行われるデータ ソースは通常はデータベースですが、さまざまなファイルやファイル形式用の OLE DB プロバイダーが存在します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-122">Although data sources queried through linked server definitions are ordinarily databases, OLE DB providers exist for a variety of files and file formats.</span></span> <span data-ttu-id="31b6a-123">これには、テキスト ファイル、ワークシートのデータ、およびフルテキスト検索の結果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-123">These include text files, spreadsheet data, and the results of full-text content searches.</span></span>

 <span data-ttu-id="31b6a-124">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー (PROGID: SQLNCLI11) は、の公式 OLE DB プロバイダーです [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="31b6a-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider (PROGID: SQLNCLI11) is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="31b6a-125">分散クエリは、必要な OLE DB インターフェイスを実装しているすべての OLE DB プロバイダーで処理できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="31b6a-125">distributed queries are designed to work with any OLE DB provider that implements the required OLE DB interfaces.</span></span> <span data-ttu-id="31b6a-126">ただし、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーなど、特定のプロバイダーに対してのみテストが行われています。</span><span class="sxs-lookup"><span data-stu-id="31b6a-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been tested against only the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider and certain other providers.</span></span>

## <a name="linked-server-details"></a><span data-ttu-id="31b6a-127">リンク サーバーの詳細</span><span class="sxs-lookup"><span data-stu-id="31b6a-127">Linked Server Details</span></span>
 <span data-ttu-id="31b6a-128">次の図に、基本的なリンク サーバー構成を示します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-128">The following illustration shows the basics of a linked server configuration.</span></span>

 <span data-ttu-id="31b6a-129">![クライアント層、サーバー層、データベース サーバー層](../../database-engine/media/lsvr.gif "クライアント層、サーバー層、データベース サーバー層")</span><span class="sxs-lookup"><span data-stu-id="31b6a-129">![Client tier, server tier, and database server tier](../../database-engine/media/lsvr.gif "Client tier, server tier, and database server tier")</span></span>

 <span data-ttu-id="31b6a-130">リンク サーバーは、通常は分散クエリの処理に使用します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-130">Typically, linked servers are used to handle distributed queries.</span></span> <span data-ttu-id="31b6a-131">クライアント アプリケーションからリンク サーバー経由で分散クエリが実行されるときは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でコマンドが解析され、OLE DB に要求が送信されます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-131">When a client application executes a distributed query through a linked server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] parses the command and sends requests to OLE DB.</span></span> <span data-ttu-id="31b6a-132">行セット要求は、プロバイダーに対するクエリの実行や、プロバイダーのベース テーブルを開くなどの形式をとります。</span><span class="sxs-lookup"><span data-stu-id="31b6a-132">The rowset request may be in the form of executing a query against the provider or opening a base table from the provider.</span></span>

 <span data-ttu-id="31b6a-133">データ ソースがリンク サーバー経由でデータを返すには、そのデータ ソースの OLE DB プロバイダー (DLL) が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスと同じサーバー上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31b6a-133">For a data source to return data through a linked server, the OLE DB provider (DLL) for that data source must be present on the same server as the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="31b6a-134">サード パーティの OLE DB プロバイダーを使用しているときは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを実行しているアカウントに、プロバイダーがインストールされているディレクトリとそのすべてのサブディレクトリの読み取り権限と実行権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="31b6a-134">When a third-party OLE DB provider is used, the account under which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service runs must have read and execute permissions for the directory, and all subdirectories, in which the provider is installed.</span></span>

## <a name="managing-providers"></a><span data-ttu-id="31b6a-135">プロバイダーの管理</span><span class="sxs-lookup"><span data-stu-id="31b6a-135">Managing Providers</span></span>
 <span data-ttu-id="31b6a-136">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が OLE DB プロバイダーを読み込んで使用する方法を制御する一連のオプションは、レジストリで指定されます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-136">There is a set of options that control how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads and uses OLE DB providers that are specified in the registry.</span></span>

## <a name="managing-linked-server-definitions"></a><span data-ttu-id="31b6a-137">リンク サーバー定義の管理</span><span class="sxs-lookup"><span data-stu-id="31b6a-137">Managing Linked Server Definitions</span></span>
 <span data-ttu-id="31b6a-138">リンク サーバーをセットアップするときは、接続情報とデータ ソース情報を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に登録します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-138">When you are setting up a linked server, register the connection information and data source information with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31b6a-139">登録後、1 つの論理名でデータ ソースを参照できます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-139">After registered, that data source can be referred to with a single logical name.</span></span>

 <span data-ttu-id="31b6a-140">ストアド プロシージャとカタログ ビューを使用して、リンク サーバーの定義を管理できます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-140">You can use stored procedures and catalog views to manage linked server definitions:</span></span>

-   <span data-ttu-id="31b6a-141">**sp_addlinkedserver**を実行して、リンク サーバーの定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-141">Create a linked server definition by running **sp_addlinkedserver**.</span></span>

-   <span data-ttu-id="31b6a-142">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sys.servers **システム カタログ ビューに対してクエリを実行して、** の特定のインスタンスに定義されたリンク サーバーに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-142">View information about the linked servers defined in a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by running a query against the **sys.servers** system catalog views.</span></span>

-   <span data-ttu-id="31b6a-143">**sp_dropserver**を実行して、リンク サーバーの定義を削除します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-143">Delete a linked server definition by running **sp_dropserver**.</span></span> <span data-ttu-id="31b6a-144">このストアド プロシージャを使用して、リモート サーバーを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-144">You can also use this stored procedure to remove a remote server.</span></span>

 <span data-ttu-id="31b6a-145">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を使用して、リンク サーバーを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-145">You can also define linked servers by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="31b6a-146">オブジェクト エクスプローラーで **[サーバー オブジェクト]** を右クリックし、 **[新規作成]** をポイントして、 **[リンク サーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31b6a-146">In the Object Explorer, right-click **Server Objects**, select **New**, and select **Linked Server**.</span></span> <span data-ttu-id="31b6a-147">リンク サーバー名を右クリックして **[削除]** をクリックすると、リンク サーバーの定義を削除できます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-147">You can delete a linked server definition by right-clicking the linked server name and selecting **Delete**.</span></span>

 <span data-ttu-id="31b6a-148">リンク サーバーに対して分散クエリを実行する場合は、クエリを実行するデータ ソースごとに 4 つの部分で構成される完全修飾テーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="31b6a-148">When you execute a distributed query against a linked server, include a fully qualified, four-part table name for each data source to query.</span></span> <span data-ttu-id="31b6a-149">この4部構成の名前は、linked_server_name. _catalog_. という形式にする必要があります。\*\* _`schema`_ \*\*_object_name_。</span><span class="sxs-lookup"><span data-stu-id="31b6a-149">This four-part name should be in the form _linked_server_name.catalog_**._`schema`_.**_object_name_.</span></span>

> [!NOTE]
>  <span data-ttu-id="31b6a-150">リンク サーバーは、どのサーバーで定義されたかを示す (ループ バックする) ように定義することができます。</span><span class="sxs-lookup"><span data-stu-id="31b6a-150">Linked servers can be defined to point back (loop back) to the server on which they are defined.</span></span> <span data-ttu-id="31b6a-151">ループバック サーバーは、単一のサーバー ネットワークで分散クエリを使用するアプリケーションをテストする際に最も有効です。</span><span class="sxs-lookup"><span data-stu-id="31b6a-151">Loopback servers are most useful when testing an application that uses distributed queries on a single server network.</span></span> <span data-ttu-id="31b6a-152">ループバック リンク サーバーはテスト用であり、分散トランザクションなどの多くの操作ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="31b6a-152">Loopback linked servers are intended for testing and are not supported for many operations, such as distributed transactions.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="31b6a-153">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="31b6a-153">Related Tasks</span></span>
 [<span data-ttu-id="31b6a-154">リンク サーバーの作成 &#40;SQL Server データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="31b6a-154">Create Linked Servers &#40;SQL Server Database Engine&#41;</span></span>](create-linked-servers-sql-server-database-engine.md)

 [<span data-ttu-id="31b6a-155">sp_addlinkedserver &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31b6a-155">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)

 [<span data-ttu-id="31b6a-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31b6a-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)

 [<span data-ttu-id="31b6a-157">sp_dropserver &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31b6a-157">sp_dropserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql)

## <a name="related-content"></a><span data-ttu-id="31b6a-158">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="31b6a-158">Related Content</span></span>
 [<span data-ttu-id="31b6a-159">sys.servers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31b6a-159">sys.servers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql)

 [<span data-ttu-id="31b6a-160">sp_linkedservers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31b6a-160">sp_linkedservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)



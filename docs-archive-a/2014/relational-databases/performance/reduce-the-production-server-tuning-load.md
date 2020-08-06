---
title: 実稼動サーバーのチューニング負荷の軽減 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- overhead [Database Engine Tuning Advisor]
- tuning overhead [SQL Server]
- reducing production server tuning load
- Database Engine Tuning Advisor [SQL Server], test servers
- test servers [Database Engine Tuning Advisor]
- production servers [SQL Server]
- offload tuning overhead [SQL Server]
ms.assetid: bb95ecaf-444a-4771-a625-e0a91c8f0709
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53a61b17793a50d6b819f7c1684afdc4de4377f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642744"
---
# <a name="reduce-the-production-server-tuning-load"></a><span data-ttu-id="f63bb-102">実稼動サーバーのチューニング負荷の軽減</span><span class="sxs-lookup"><span data-stu-id="f63bb-102">Reduce the Production Server Tuning Load</span></span>
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="f63bb-103">チューニング アドバイザーは、ワークロードの分析とチューニング推奨設定の生成をクエリ オプティマイザーに依存します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-103">Tuning Advisor relies on the query optimizer to analyze a workload and to make tuning recommendations.</span></span> <span data-ttu-id="f63bb-104">実稼働サーバー上でこの分析を実行すると、サーバーの負荷が増し、チューニング セッション中のサーバーのパフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="f63bb-104">Performing this analysis on the production server adds to the server load and can hurt server performance during the tuning session.</span></span> <span data-ttu-id="f63bb-105">実稼働サーバーに加えてテスト サーバーを使用することで、チューニング セッション中のサーバーの負荷への影響を小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-105">You can reduce the impact to the server load during a tuning session by using a test server in addition to the production server.</span></span>

## <a name="how-database-engine-tuning-advisor-uses-a-test-server"></a><span data-ttu-id="f63bb-106">データベース エンジン チューニング アドバイザーでテスト サーバーを使用する方法</span><span class="sxs-lookup"><span data-stu-id="f63bb-106">How Database Engine Tuning Advisor Uses a Test Server</span></span>
 <span data-ttu-id="f63bb-107">これまでは、テスト サーバーを使用するために、実稼働サーバーからテスト サーバーにすべてのデータをコピーし、テスト サーバーをチューニングして、実稼働サーバーに推奨設定を実装する方法を使用してきました。</span><span class="sxs-lookup"><span data-stu-id="f63bb-107">The traditional way to use a test server is to copy all of the data from your production server to your test server, tune the test server, and then implement the recommendation on your production server.</span></span> <span data-ttu-id="f63bb-108">この処理により、実稼働サーバーのパフォーマンスに影響が及ぶことはありませんが、これは最善の解決策ではありません。</span><span class="sxs-lookup"><span data-stu-id="f63bb-108">This process eliminates the performance impact on your production server, but nevertheless is not the optimal solution.</span></span> <span data-ttu-id="f63bb-109">たとえば、大量のデータを実稼働サーバーからテスト サーバーにコピーする場合、非常に時間がかかり、多量のリソースが使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f63bb-109">For example, copying large amounts of data from the production to the test server can consume substantial amounts of time and resources.</span></span> <span data-ttu-id="f63bb-110">また、テスト サーバーのハードウェアが、実稼働サーバーに配置されているハードウェアほど優れていることはめったにありません。</span><span class="sxs-lookup"><span data-stu-id="f63bb-110">In addition, test server hardware is seldom as powerful as the hardware that is deployed for production servers.</span></span> <span data-ttu-id="f63bb-111">チューニング処理は、クエリ オプティマイザーに依存し、生成される推奨設定は基になるハードウェアに部分的に基づきます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-111">The tuning process relies on the query optimizer, and the recommendations it generates are based in part on the underlying hardware.</span></span> <span data-ttu-id="f63bb-112">テスト サーバーと実稼働サーバーのハードウェアが異なる場合、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーの推奨設定の特性が低下します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-112">If the test and production server hardware are not identical, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor recommendation quality is diminished.</span></span>

 <span data-ttu-id="f63bb-113">このような問題を防ぐために、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーでは、大部分のチューニング負荷をテスト サーバーにオフロードして、実稼働サーバー上のデータベースをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="f63bb-113">To avoid these problems, [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor tunes a database on a production server by offloading most of the tuning load onto a test server.</span></span> <span data-ttu-id="f63bb-114">このチューニングは、実際には実稼働サーバーからテスト サーバーにデータがコピーされずに、実稼働サーバーのハードウェア構成情報を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-114">It does this by using the production server hardware configuration information and without actually copying the data from the production server to the test server.</span></span> [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="f63bb-115">チューニング アドバイザーでは、実稼働サーバーからテスト サーバーに実際のデータがコピーされることはありません。</span><span class="sxs-lookup"><span data-stu-id="f63bb-115">Tuning Advisor does not copy actual data from the production server to the test server.</span></span> <span data-ttu-id="f63bb-116">メタデータと必要な統計だけがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-116">It only copies the metadata and necessary statistics.</span></span>

 <span data-ttu-id="f63bb-117">次の手順は、テスト サーバーでの実稼働データベースのチューニング処理の概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="f63bb-117">The following steps outline the process for tuning a production database on a test server:</span></span>

1.  <span data-ttu-id="f63bb-118">テスト サーバーを使用するユーザーが、両方のサーバーに存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-118">Make sure that the user who wants to use the test server exists on both servers.</span></span>

     <span data-ttu-id="f63bb-119">開始する前に、テスト サーバーを使用して実稼働サーバー上のデータベースをチューニングするユーザーが、両方のサーバーに存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-119">Before you start, make sure that the user who wants to use the test server to tune a database on the production server exists on both servers.</span></span> <span data-ttu-id="f63bb-120">このためには、テスト サーバーにユーザーとそのユーザーのログインを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f63bb-120">This requires that you create the user and his or her login on the test server.</span></span> <span data-ttu-id="f63bb-121">使用者が両方のコンピューターの **sysadmin** 固定サーバー ロールのメンバーであれば、この手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="f63bb-121">If you are a member of the **sysadmin** fixed server role on both computers, this step is not necessary.</span></span>

2.  <span data-ttu-id="f63bb-122">テスト サーバーでワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="f63bb-122">Tune the workload on the test server.</span></span>

     <span data-ttu-id="f63bb-123">テスト サーバーでワークロードをチューニングするには、XML 入力ファイルと **dta** コマンド ライン ユーティリティを併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f63bb-123">To tune a workload on a test server, you must use an XML input file with the **dta** command-line utility.</span></span> <span data-ttu-id="f63bb-124">XML 入力ファイルで、 **TestServer** サブ要素にテスト サーバーの名前を指定し、 **TuningOptions** 親要素の下の他のサブ要素の値も指定します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-124">In the XML input file, specify the name of your test server with the **TestServer** subelement in addition to specifying the values for the other subelements under the **TuningOptions** parent element.</span></span>

     <span data-ttu-id="f63bb-125">チューニング処理中、データベース エンジン チューニング アドバイザーによって、テスト サーバーにシェル データベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-125">During the tuning process, Database Engine Tuning Advisor creates a shell database on the test server.</span></span> <span data-ttu-id="f63bb-126">データベース エンジン チューニング アドバイザーでは、このシェル データベースを作成してチューニングするために、次の目的で実稼働サーバーに呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-126">To create this shell database and tune it, Database Engine Tuning Advisor makes calls to the production server for the following:</span></span>

    1.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="f63bb-127">チューニング アドバイザーは、実稼働データベースからテスト サーバーのシェル データベースにメタデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="f63bb-127">Tuning Advisor imports metadata from the production database to the test server shell database.</span></span> <span data-ttu-id="f63bb-128">このメタデータには、空のテーブル、インデックス、ビュー、ストアド プロシージャ、トリガーなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-128">This metadata includes empty tables, indexes, views, stored procedures, triggers, and so on.</span></span> <span data-ttu-id="f63bb-129">これにより、テスト サーバーのシェル データベースに対してワークロード クエリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f63bb-129">This makes it possible for the workload queries to execute against the test server shell database.</span></span>

    2.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="f63bb-130">チューニング アドバイザーは、クエリ オプティマイザーでテスト サーバーのクエリを正確に最適化できるように、実稼働サーバーから統計をインポートします。</span><span class="sxs-lookup"><span data-stu-id="f63bb-130">Tuning Advisor imports statistics from the production server so the query optimizer can accurately optimize queries on the test server.</span></span>

    3.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="f63bb-131">チューニング アドバイザーは、プロセッサ数と使用可能なメモリを指定するハードウェア パラメーターを実稼働サーバーからインポートし、クエリ プランの生成に必要な情報をクエリ オプティマイザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-131">Tuning Advisor imports hardware parameters specifying the number of processors and available memory from the production server to provide the query optimizer with the information it needs to generate a query plan.</span></span>

3.  <span data-ttu-id="f63bb-132">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーでは、テスト サーバーのシェル データベースのチューニング完了後、チューニングの推奨設定が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-132">After [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor finishes tuning the test server shell database, it generates a tuning recommendation.</span></span>

4.  <span data-ttu-id="f63bb-133">テスト サーバーのチューニングによって作成された推奨設定を実稼働サーバーに適用します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-133">Apply the recommendation received from tuning the test server to the production server.</span></span>

 <span data-ttu-id="f63bb-134">次の図は、テスト サーバーと実稼働サーバーのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="f63bb-134">The following illustration shows the test server and production server scenario:</span></span>

 <span data-ttu-id="f63bb-135">![データベース エンジン チューニング アドバイザーでのテスト サーバーの使用法](../../database-engine/media/testsvr.gif "データベース エンジン チューニング アドバイザーでのテスト サーバーの使用法")</span><span class="sxs-lookup"><span data-stu-id="f63bb-135">![Database Engine Tuning Advisor test server usage](../../database-engine/media/testsvr.gif "Database Engine Tuning Advisor test server usage")</span></span>

> [!NOTE]
>  <span data-ttu-id="f63bb-136">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーのグラフィカル ユーザー インターフェイス (GUI) では、テスト サーバーのチューニング機能はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f63bb-136">The test server tuning feature is not supported in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor graphical user interface (GUI).</span></span>

## <a name="example"></a><span data-ttu-id="f63bb-137">例</span><span class="sxs-lookup"><span data-stu-id="f63bb-137">Example</span></span>
 <span data-ttu-id="f63bb-138">最初に、チューニングを実行するユーザーが、テスト サーバーと実稼働サーバーの両方に存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f63bb-138">First, make sure that the user who wants to perform the tuning exists on both the test and production servers.</span></span>

 <span data-ttu-id="f63bb-139">ユーザー情報をテスト サーバーにコピーした後、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルでテスト サーバーのチューニング セッションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-139">After the user information is copied over to your test server, you can define your test server tuning session in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor XML input file.</span></span> <span data-ttu-id="f63bb-140">次の XML 入力ファイルの例は、テスト サーバーを指定して、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーを使用してデータベースをチューニングする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f63bb-140">The following example XML input file illustrates how to specify a test server to tune a database with [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor.</span></span>

 <span data-ttu-id="f63bb-141">この例では、 `MyDatabaseName` データベースが `MyServerName`でチューニングされています。</span><span class="sxs-lookup"><span data-stu-id="f63bb-141">In this example, the `MyDatabaseName` database is being tuned on `MyServerName`.</span></span> <span data-ttu-id="f63bb-142">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトの `MyWorkloadScript.sql`をワークロードとして使用しています。</span><span class="sxs-lookup"><span data-stu-id="f63bb-142">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script, `MyWorkloadScript.sql`, is used as the workload.</span></span> <span data-ttu-id="f63bb-143">このワークロードには、 `MyDatabaseName`に対して実行するイベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f63bb-143">This workload contains events that execute against `MyDatabaseName`.</span></span> <span data-ttu-id="f63bb-144">このデータベースに対し、クエリ オプティマイザーによって行われるほとんどの呼び出しは、チューニング処理の一部として行われ、 `MyTestServerName`に存在するシェル データベースによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-144">Most of the query optimizer calls to this database, which occur as part of the tuning process, are handled by the shell database that resides on `MyTestServerName`.</span></span> <span data-ttu-id="f63bb-145">シェル データベースは、メタデータと統計で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-145">The shell database is composed of metadata and statistics.</span></span> <span data-ttu-id="f63bb-146">この処理により、チューニングのオーバーヘッドがテスト サーバーにオフロードされます。</span><span class="sxs-lookup"><span data-stu-id="f63bb-146">This process results in the tuning overhead being offloaded to the test server.</span></span> <span data-ttu-id="f63bb-147">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] チューニング アドバイザーでは、この XML 入力ファイルを使用してチューニングの推奨設定を生成するとき、インデックスのみ (`<FeatureSet>IDX</FeatureSet>`) を考慮し、パーティション分割を行わず、 `MyDatabaseName`に既存の物理デザイン構造を保持する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f63bb-147">When [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor generates its tuning recommendation using this XML input file, it should consider indexes only (`<FeatureSet>IDX</FeatureSet>`), no partitioning, and need not keep any of the existing physical design structures in `MyDatabaseName`.</span></span>

```
<?xml version="1.0" encoding="utf-16" ?>
<DTAXML xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">
  <DTAInput>
    <Server>
      <Name>MyServerName</Name>
      <Database>
        <Name>MyDatabaseName</Name>
      </Database>
    </Server>
    <Workload>
      <File>MyWorkloadScript.sql</File>
    </Workload>
    <TuningOptions>
      <TestServer>MyTestServerName</TestServer>
      <FeatureSet>IDX</FeatureSet>
      <Partitioning>NONE</Partitioning>
      <KeepExisting>NONE</KeepExisting>
    </TuningOptions>
  </DTAInput>
</DTAXML>
```

## <a name="see-also"></a><span data-ttu-id="f63bb-148">参照</span><span class="sxs-lookup"><span data-stu-id="f63bb-148">See Also</span></span>
 <span data-ttu-id="f63bb-149">[テストサーバーの XML 入力ファイル参照を使用する場合の考慮事項](considerations-for-using-test-servers.md) [&#40;データベースエンジンチューニングアドバイザー&#41;](database-engine-tuning-advisor.md)</span><span class="sxs-lookup"><span data-stu-id="f63bb-149">[Considerations for Using Test Servers](considerations-for-using-test-servers.md) [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](database-engine-tuning-advisor.md)</span></span>



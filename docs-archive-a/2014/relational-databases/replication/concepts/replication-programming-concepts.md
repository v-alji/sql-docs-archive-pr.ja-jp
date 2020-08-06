---
title: レプリケーションのプログラミング概念 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- replication [SQL Server], planning
- programming [SQL Server replication], planning
- programming [SQL Server replication]
ms.assetid: 2cd846e7-5bf3-4144-8772-703c4f439a2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db4ab6196c138eaf21de08afc27731225df398e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640880"
---
# <a name="replication-programming-concepts"></a><span data-ttu-id="0373b-102">レプリケーションのプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="0373b-102">Replication Programming Concepts</span></span>
  <span data-ttu-id="0373b-103">レプリケーション機能を利用するアプリケーションを開発する前に、次に示す一般的な計画手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="0373b-103">Before developing an application that uses replication functionalities, you should follow the following general planning steps:</span></span>  
  
1.  <span data-ttu-id="0373b-104">レプリケーション トポロジを定義します。</span><span class="sxs-lookup"><span data-stu-id="0373b-104">Define your replication topology.</span></span>  
  
2.  <span data-ttu-id="0373b-105">アプリケーションの機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="0373b-105">Define application functionality.</span></span>  
  
3.  <span data-ttu-id="0373b-106">セキュリティを計画します。</span><span class="sxs-lookup"><span data-stu-id="0373b-106">Plan for security.</span></span>  
  
4.  <span data-ttu-id="0373b-107">開発環境を選択します。</span><span class="sxs-lookup"><span data-stu-id="0373b-107">Choose a development environment.</span></span>  
  
5.  <span data-ttu-id="0373b-108">適切なレプリケーション プログラミング インターフェイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="0373b-108">Choose the appropriate replication programming interface.</span></span>  
  
 <span data-ttu-id="0373b-109">以下に、この手順の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="0373b-109">The rest of this topic describes these steps in more detail.</span></span> <span data-ttu-id="0373b-110">計画のプロセスについてわかりやすく説明するために、例も示します。</span><span class="sxs-lookup"><span data-stu-id="0373b-110">To help illustrate the planning process, an example has been included.</span></span>  
  
## <a name="defining-the-replication-topology"></a><span data-ttu-id="0373b-111">レプリケーション トポロジの定義</span><span class="sxs-lookup"><span data-stu-id="0373b-111">Defining the Replication Topology</span></span>  
 <span data-ttu-id="0373b-112">レプリケーションのプログラミングの最初の手順は、アプリケーションのレプリケーション トポロジを定義することです。</span><span class="sxs-lookup"><span data-stu-id="0373b-112">The first step in programming replication is to define the replication topology for your application.</span></span> <span data-ttu-id="0373b-113">既存のサブスクライバー上のデータにアクセスするクライアント アプリケーションなど、既存のレプリケーション トポロジを使用するアプリケーションを作成する場合は、次の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="0373b-113">If you are writing an application that will use an existing replication topology, such as a client application that accesses data at an existing subscriber, you should move onto the next step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0373b-114">レプリケーション トポロジの配置だけがアプリケーションの目的である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0373b-114">In some cases, deploying the replication topology will be the sole purpose of the application.</span></span>  
  
 <span data-ttu-id="0373b-115">レプリケーション トポロジの定義は、次のような多くの要因によって決まります。</span><span class="sxs-lookup"><span data-stu-id="0373b-115">The replication topology that you define depends on many factors, including the following:</span></span>  
  
-   <span data-ttu-id="0373b-116">レプリケートされたデータの更新が必要か、まただれが更新するか。</span><span class="sxs-lookup"><span data-stu-id="0373b-116">Whether or not replicated data needs to be updated, and by whom.</span></span>  
  
-   <span data-ttu-id="0373b-117">データ ディストリビューションでは、関連する一貫性、自律性、待機時間を必要とするか。</span><span class="sxs-lookup"><span data-stu-id="0373b-117">Your data distribution needs regarding consistency, autonomy, and latency.</span></span>  
  
-   <span data-ttu-id="0373b-118">ビジネス ユーザー、技術的なインフラストラクチャ、ネットワークとセキュリティ、データ特性などのレプリケーション環境。</span><span class="sxs-lookup"><span data-stu-id="0373b-118">The replication environment, including business users, technical infrastructure, network and security, and data characteristics.</span></span>  
  
-   <span data-ttu-id="0373b-119">レプリケーションの種類とレプリケーション オプション。</span><span class="sxs-lookup"><span data-stu-id="0373b-119">The types of replication and replication options.</span></span>  
  
-   <span data-ttu-id="0373b-120">レプリケーション トポロジと、そのレプリケーションの種類との対応。</span><span class="sxs-lookup"><span data-stu-id="0373b-120">The replication topologies and how they align with the types of replication.</span></span>  
  
 <span data-ttu-id="0373b-121">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションを初めて使用する場合は、「[レプリケーションの種類](../types-of-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0373b-121">If you are new to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication, see [Types of Replication](../types-of-replication.md).</span></span>  
  
## <a name="defining-application-functionality"></a><span data-ttu-id="0373b-122">アプリケーションの機能の定義</span><span class="sxs-lookup"><span data-stu-id="0373b-122">Defining Application Functionality</span></span>  
 <span data-ttu-id="0373b-123">レプリケーション トポロジを定義した後で、アプリケーションに備える機能を決定します。</span><span class="sxs-lookup"><span data-stu-id="0373b-123">Once the replication topology has been defined, you should decide on the functionalities that your application will offer.</span></span> <span data-ttu-id="0373b-124">サブスクリプションをアプリケーションに同期させるスクリプトから、レプリケーションを構成するためのユーザー インターフェイスを備えたアプリケーションまで、幅広い機能を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0373b-124">These functionalities can range from a script that synchronizes a subscription to an application with a user interface to configure replication.</span></span> <span data-ttu-id="0373b-125">レプリケーションでは次の一般的なプログラミング作業がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="0373b-125">Replication supports the following general programming tasks:</span></span>  
  
-   <span data-ttu-id="0373b-126">レプリケーションのセットアップ</span><span class="sxs-lookup"><span data-stu-id="0373b-126">Setting up replication.</span></span>  
  
-   <span data-ttu-id="0373b-127">サブスクライバーの同期</span><span class="sxs-lookup"><span data-stu-id="0373b-127">Synchronizing Subscribers.</span></span>  
  
-   <span data-ttu-id="0373b-128">レプリケーション トポロジの保持</span><span class="sxs-lookup"><span data-stu-id="0373b-128">Maintaining a replication topology.</span></span>  
  
-   <span data-ttu-id="0373b-129">レプリケーション トポロジの監視</span><span class="sxs-lookup"><span data-stu-id="0373b-129">Monitoring a replication topology.</span></span>  
  
-   <span data-ttu-id="0373b-130">レプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0373b-130">Troubleshooting replication.</span></span>  
  
 <span data-ttu-id="0373b-131">レプリケーション機能と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の他の機能を組み合わせることで、アプリケーションを拡張することもよく行われます。</span><span class="sxs-lookup"><span data-stu-id="0373b-131">It is also common extend your application by combining replication functionalities with other functionalities provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0373b-132">次の表に、レプリケーション アプリケーションで提供できる拡張機能の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="0373b-132">The following table highlights some extended functionalities that you might provide in your replication application.</span></span>  
  
|<span data-ttu-id="0373b-133">機能</span><span class="sxs-lookup"><span data-stu-id="0373b-133">Functionality</span></span>|<span data-ttu-id="0373b-134">例</span><span class="sxs-lookup"><span data-stu-id="0373b-134">Example</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="0373b-135">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) を使用したサーバー管理</span><span class="sxs-lookup"><span data-stu-id="0373b-135">Server administration using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)</span></span>|<span data-ttu-id="0373b-136">管理者がレプリケーション トポロジ内でデータベースをパブリッシャーとしてアタッチし、構成できるアプリケーション</span><span class="sxs-lookup"><span data-stu-id="0373b-136">An application that enables an administrator to attach and configure a database as a Publisher in a replication topology.</span></span>|  
|<span data-ttu-id="0373b-137">ADO.NET を使用したデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="0373b-137">Data access using ADO.NET</span></span>|<span data-ttu-id="0373b-138">ユーザーがオフライン時にローカル サブスクライバー データベース内のレプリケート済み販売データにプログラムからアクセスして変更でき、さらにボタンをクリックすることでプル サブスクリプションに接続して同期できるアプリケーション</span><span class="sxs-lookup"><span data-stu-id="0373b-138">An application that enables users to programmatically access and change replicated sales data in a local Subscriber database while offline and then connect and synchronize the pull subscription by clicking a button.</span></span>|  
  
## <a name="planning-for-security"></a><span data-ttu-id="0373b-139">セキュリティの計画</span><span class="sxs-lookup"><span data-stu-id="0373b-139">Planning for Security</span></span>  
 <span data-ttu-id="0373b-140">セキュリティはどのようなアプリケーションでも重要です。セキュリティの計画は、コードを作成する前に完成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-140">Security is important in any application, and planning for security should be completed before writing any code.</span></span> <span data-ttu-id="0373b-141">アプリケーションのセキュリティは、データベースのセキュリティ保護、レプリケーションのセキュリティ保護、安全なコードの作成の 3 つに大きく分類されます。</span><span class="sxs-lookup"><span data-stu-id="0373b-141">Application security can be divided into three main parts: securing the database, securing replication, and writing secure code.</span></span>  
  
 <span data-ttu-id="0373b-142">セキュリティの詳細については、次のトピックで解説します。</span><span class="sxs-lookup"><span data-stu-id="0373b-142">The following topics provide information on security:</span></span>  
  
-   [<span data-ttu-id="0373b-143">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="0373b-143">SQL Server Replication Security</span></span>](../security/view-and-modify-replication-security-settings.md)  
  
-   [<span data-ttu-id="0373b-144">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="0373b-144">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
## <a name="choosing-a-development-environment"></a><span data-ttu-id="0373b-145">開発環境の選択</span><span class="sxs-lookup"><span data-stu-id="0373b-145">Choosing a Development Environment</span></span>  
 <span data-ttu-id="0373b-146">レプリケーション アプリケーションの開発時に検討する基本開発環境は、3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="0373b-146">When developing a replication application, there are three basic development environments to consider.</span></span> <span data-ttu-id="0373b-147">どの開発環境からもほぼ同じレプリケーション機能を利用できますが、いくつか例外があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-147">Each development environment has access to the same replication functionalities with some exceptions.</span></span> <span data-ttu-id="0373b-148">レプリケーション アプリケーションは、次の環境で開発できます。</span><span class="sxs-lookup"><span data-stu-id="0373b-148">Replication applications can be developed in each of the following environments.</span></span>  
  
-   <span data-ttu-id="0373b-149">**マネージド コード**</span><span class="sxs-lookup"><span data-stu-id="0373b-149">**Managed code**</span></span>  
  
     <span data-ttu-id="0373b-150">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] プログラミングと .NET 共通言語ランタイム (CLR) を利用できる、オブジェクト指向開発環境です。</span><span class="sxs-lookup"><span data-stu-id="0373b-150">Object oriented development environment that leverages the benefits of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programming and the .NET common language runtime (CLR).</span></span> <span data-ttu-id="0373b-151">マネージド コードは、.NET 開発と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アプリケーションのどちらにも推奨されるプログラミング環境です。</span><span class="sxs-lookup"><span data-stu-id="0373b-151">Managed code is the recommended programming environment for both .NET development and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applications.</span></span> <span data-ttu-id="0373b-152">マネージド レプリケーション インターフェイスを利用することで、[!INCLUDE[tsql](../../../includes/tsql-md.md)] がわからなくてもオブジェクト指向の方法でレプリケーション管理をプログラミングできます。さらに、スクリプトから使用できないレプリケーション エージェントを実行する場合に、コールバック機能も提供できます。</span><span class="sxs-lookup"><span data-stu-id="0373b-152">Managed replication interfaces enable the programming of replication administration in an object-oriented manner without having to know [!INCLUDE[tsql](../../../includes/tsql-md.md)], and it also provides some callback functionalities when running replication agents that are not available from scripts.</span></span> <span data-ttu-id="0373b-153">マネージド コードは、再利用可能なコンポーネントおよびユーザー インターフェイス アプリケーションの開発に最適な環境です。</span><span class="sxs-lookup"><span data-stu-id="0373b-153">Managed code is the best environment for developing reusable components and user interface applications.</span></span>  
  
-   <span data-ttu-id="0373b-154">**スクリプトの作成**</span><span class="sxs-lookup"><span data-stu-id="0373b-154">**Scripting**</span></span>  
  
     <span data-ttu-id="0373b-155">一連のコマンドを [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトでレプリケーション システムのストアド プロシージャとして実行するか、バッチ ファイル内のコマンドを実行する単純なアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="0373b-155">Simple applications that execute a series of commands as either replication system stored procedures in [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts or commands in batch files.</span></span> <span data-ttu-id="0373b-156">プロセス内で管理される [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロバイダーを使用して、管理対象の環境でスクリプトを実行できますが、管理対象のレプリケーション インターフェイスを使用することで同じ機能を利用できます。さらに、コールバック機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="0373b-156">While you can execute scripts in a managed environment using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in-process managed provider, the same functionality can obtained by using managed replication interfaces, which also provide callback functionalities.</span></span> <span data-ttu-id="0373b-157">スクリプトは、たとえばレプリケーション サーバーのインストールなど、数回のみ実行されるタスクを実行する場合や、コールバック機能が不要な場合に最適な環境です。</span><span class="sxs-lookup"><span data-stu-id="0373b-157">Scripting is the best environment for executing tasks that will run only a few times and where callback functionalities are not required, such as installing a replication server.</span></span>  
  
-   <span data-ttu-id="0373b-158">**ネイティブ コード**</span><span class="sxs-lookup"><span data-stu-id="0373b-158">**Native code**</span></span>  
  
     <span data-ttu-id="0373b-159">コードが CLR によって管理されない、システム オブジェクトや COM オブジェクトへの直接アクセスを利用するオブジェクト指向開発環境です。</span><span class="sxs-lookup"><span data-stu-id="0373b-159">Object-oriented development environment that utilizes direct access to the system or COM objects such that code is not managed by the CLR.</span></span> <span data-ttu-id="0373b-160">ネイティブ コード レプリケーション インターフェイスは、非推奨または廃止になりました。</span><span class="sxs-lookup"><span data-stu-id="0373b-160">Native code replication interfaces are deprecated or discontinued.</span></span> <span data-ttu-id="0373b-161">詳細については、「[SQL Server レプリケーションの非推奨の機能](../deprecated-features-in-sql-server-replication.md)」または「[レプリケーションの旧バージョンとの互換性](../replication-backward-compatibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0373b-161">For more information, see [Deprecated Features in SQL Server Replication](../deprecated-features-in-sql-server-replication.md) or [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
## <a name="choose-the-appropriate-replication-programming-interface"></a><span data-ttu-id="0373b-162">適切なレプリケーション プログラミング インターフェイスの選択</span><span class="sxs-lookup"><span data-stu-id="0373b-162">Choose the Appropriate Replication Programming Interface</span></span>  
 <span data-ttu-id="0373b-163">計画の最後の手順は、選択した開発環境で目的のレプリケーション機能を実装するためのレプリケーション プログラミング インターフェイスを適切に選択することです。</span><span class="sxs-lookup"><span data-stu-id="0373b-163">The final planning step is choosing the appropriate replication programming interface that implements the desired replication functionality for the chosen development environment.</span></span> <span data-ttu-id="0373b-164">次の表に、使用できるレプリケーション プログラミング インターフェイスを示します。</span><span class="sxs-lookup"><span data-stu-id="0373b-164">The following table shows the replication programming interfaces available.</span></span>  
  
|<span data-ttu-id="0373b-165">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0373b-165">Interface</span></span>|<span data-ttu-id="0373b-166">環境</span><span class="sxs-lookup"><span data-stu-id="0373b-166">Environment</span></span>|<span data-ttu-id="0373b-167">用途</span><span class="sxs-lookup"><span data-stu-id="0373b-167">Uses</span></span>|  
|---------------|-----------------|----------|  
|[<span data-ttu-id="0373b-168">レプリケーション管理オブジェクトの概念</span><span class="sxs-lookup"><span data-stu-id="0373b-168">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)|<span data-ttu-id="0373b-169">マネージド コード</span><span class="sxs-lookup"><span data-stu-id="0373b-169">Managed code</span></span>|<span data-ttu-id="0373b-170">管理、監視、同期</span><span class="sxs-lookup"><span data-stu-id="0373b-170">Administration, monitoring, and synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication>|<span data-ttu-id="0373b-171">マネージド コード</span><span class="sxs-lookup"><span data-stu-id="0373b-171">Managed code</span></span>|<span data-ttu-id="0373b-172">同期</span><span class="sxs-lookup"><span data-stu-id="0373b-172">Synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|<span data-ttu-id="0373b-173">マネージド コード</span><span class="sxs-lookup"><span data-stu-id="0373b-173">Managed code</span></span>|<span data-ttu-id="0373b-174">カスタム ロジックとマージ同期プロセスを統合するためのビジネス ロジック ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="0373b-174">Creation of business logic handlers to integrate custom logic with the merge synchronization process.</span></span>|  
|[<span data-ttu-id="0373b-175">レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0373b-175">Replication Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)|<span data-ttu-id="0373b-176">スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="0373b-176">Scripting</span></span>|<span data-ttu-id="0373b-177">管理と監視。</span><span class="sxs-lookup"><span data-stu-id="0373b-177">Administration and monitoring.</span></span>|  
|[<span data-ttu-id="0373b-178">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="0373b-178">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)|<span data-ttu-id="0373b-179">スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="0373b-179">Scripting</span></span>|<span data-ttu-id="0373b-180">同期</span><span class="sxs-lookup"><span data-stu-id="0373b-180">Synchronization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0373b-181">例</span><span class="sxs-lookup"><span data-stu-id="0373b-181">Example</span></span>  
 <span data-ttu-id="0373b-182">[!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] では、データを世界中の 200 人の販売担当者にパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-182">At [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)], data needs to be published for 200 sales representatives around the world.</span></span> <span data-ttu-id="0373b-183">販売担当者は頻繁に出張するため、ラップトップ コンピューターや携帯情報端末 (PDA) を使用して顧客データを変更したり、新しい発注を追加したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-183">The sales representatives travel often and will need to use laptop computers or personal digital assistants (PDAs) to change customer data and add new orders.</span></span> <span data-ttu-id="0373b-184">販売担当者がラップトップ コンピューターをネットワークに接続したときに、このような変更をパブリッシャーと同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-184">The changes will then need to be synchronized with the Publisher when the sales representative connects the laptop to the network.</span></span>  
  
 <span data-ttu-id="0373b-185">このアプリケーションの場合、計画手順は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0373b-185">For this application, the planning steps might look like the following:</span></span>  
  
1.  <span data-ttu-id="0373b-186">このアプリケーションのレプリケーション トポロジは既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="0373b-186">The replication topology for this application already exists.</span></span> <span data-ttu-id="0373b-187">しかし、クライアントで新しいプル サブスクリプションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-187">However, a new pull subscription must be created at the client.</span></span> <span data-ttu-id="0373b-188">パブリケーションではパラメーター化されたフィルターを使用して、一意なデータのセットを各販売担当者にレプリケートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-188">The publication should use parameterized filters to replicate a unique set of data to each sales representative.</span></span>  
  
2.  <span data-ttu-id="0373b-189">販売アプリケーションに必要な一般的なデータ アクセスに加えて、このアプリケーションでは販売担当者が必要なときにボタンをクリックしてプル サブスクリプションを同期できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-189">In addition to the typical data access required for a sales application, this application should enable a salesperson to synchronize the pull subscription on demand by clicking a button.</span></span> <span data-ttu-id="0373b-190">さらに、販売担当者がこのアプリケーションをインストールして実行するため、クライアント側でサブスクリプションを構成し、初期スナップショットを適用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0373b-190">Since a sales representative will install and run the application, it also needs to be able to configure a subscription and apply the initial snapshot at the client.</span></span> <span data-ttu-id="0373b-191">場合によっては、このアプリケーションは Windows で提供されているインフラストラクチャを利用してワイヤレス接続を探し、接続が検出された場合はサブスクリプションを自動的に同期します。</span><span class="sxs-lookup"><span data-stu-id="0373b-191">Optionally, the application will use the infrastructure provided by Windows for sensing wireless connectivity to automatically synchronize the subscription when a connection is detected.</span></span>  
  
3.  <span data-ttu-id="0373b-192">パブリッシャーに接続するときには、Windows 認証と仮想プライベート ネットワークの使用を含む、レプリケーションのセキュリティ ガイドラインすべてに従います。</span><span class="sxs-lookup"><span data-stu-id="0373b-192">Follow all of the security guidelines for replication, including using Windows Authentication and a virtual private network (VPN) when connecting to the publisher.</span></span> <span data-ttu-id="0373b-193">Web 同期を実行する場合は、SSL (Secure Sockets Layer) 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="0373b-193">If implementing Web synchronization, use a secure sockets layer (SSL) connection.</span></span> <span data-ttu-id="0373b-194">詳しくは、「 [Configure Web Synchronization](../configure-web-synchronization.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0373b-194">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md).</span></span>  
  
4.  <span data-ttu-id="0373b-195">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の機能を利用するには、マネージド コード言語を使用してアプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="0373b-195">In order to take advantage of the features of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], the application is developed using a managed code language.</span></span>  
  
5.  <span data-ttu-id="0373b-196">このような要件に基づき、このアプリケーションに必要なレプリケーション機能はレプリケーション管理オブジェクト (RMO) 管理インターフェイスによってすべて提供できます。</span><span class="sxs-lookup"><span data-stu-id="0373b-196">Based on these requirements, the Replication Management Objects (RMO) managed interface can provide all of the needed replication functionality for this application.</span></span>  
  
 <span data-ttu-id="0373b-197">次の例は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に付属するサンプル アプリケーションに実装されています。</span><span class="sxs-lookup"><span data-stu-id="0373b-197">This example scenario has been implemented in a sample application that ships with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  

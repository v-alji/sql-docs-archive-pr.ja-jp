---
title: Change Data Capture Service for Oracle by Attunity のシステム アーキテクチャ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1db6c737-3c60-4066-a0a3-3611e1c83e4e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c78cf38f64abf31fe22392ab7c7bafe90a2e6b11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641826"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a><span data-ttu-id="28b1c-102">Change Data Capture Service for Oracle by Attunity のシステム アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="28b1c-102">Change Data Capture Service for Oracle by Attunity System Architecture</span></span>
  <span data-ttu-id="28b1c-103">CDC Service for Oracle は、1 つ以上のソース Oracle データベースの選択したテーブルに加えられた変更を、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスにある [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC データベースにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="28b1c-103">The CDC Service for Oracle captures changes made to selected tables in one or more source Oracle databases into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC databases located on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="28b1c-104">次の図に、CDC Service for Oracle を構成するコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="28b1c-104">The following diagram shows the components that make up the CDC Service for Oracle.</span></span>  
  
 <span data-ttu-id="28b1c-105">![サービス アーキテクチャ](../media/service-architecture.gif "サービス アーキテクチャ")</span><span class="sxs-lookup"><span data-stu-id="28b1c-105">![Service Architecture](../media/service-architecture.gif "Service Architecture")</span></span>  
  
 <span data-ttu-id="28b1c-106">この図は、使用される 4 つのプラットフォームを示しています。</span><span class="sxs-lookup"><span data-stu-id="28b1c-106">This figure illustrates four platforms that are used.</span></span> <span data-ttu-id="28b1c-107">多くの場合、これらのプラットフォームは重複させることができますが、この図では標準的なユース ケースを示しています。</span><span class="sxs-lookup"><span data-stu-id="28b1c-107">In many cases, these platforms can overlap, however this diagram represents a standard use case.</span></span> <span data-ttu-id="28b1c-108">たとえば、Oracle データベースと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースのそれぞれを独立したコンピューターで実行し、Oracle CDC Service プラットフォームまたは CDC Service の設計元であるプラットフォームと共有しないようにするのが適切です。</span><span class="sxs-lookup"><span data-stu-id="28b1c-108">For example, it makes sense that the Oracle and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases each run on a separate computer and are not shared with the Oracle CDC Service platform or the platform from which the CDC Service is designed.</span></span> <span data-ttu-id="28b1c-109">この図に示すプラットフォームは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-109">The platforms illustrated in this figure are:</span></span>  
  
-   <span data-ttu-id="28b1c-110">Oracle CDC Service: Oracle CDC Service がインストールされて実行される、任意のサポート対象 Windows コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-110">The Oracle CDC Service: This can be any supported Windows computer where the Oracle CDC Service is installed and run.</span></span> <span data-ttu-id="28b1c-111">このプラットフォームは、Microsoft フェールオーバー クラスターのクラスター ノードを表す場合もあります (高可用性構成については、このドキュメントで後ほど説明します)。</span><span class="sxs-lookup"><span data-stu-id="28b1c-111">This platform may also represent a cluster node in a Microsoft failover cluster (high availability configurations are discussed later in this document).</span></span>  
  
-   <span data-ttu-id="28b1c-112">Oracle データベース: Oracle データベースのサポート対象バージョンが実行される任意のコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-112">The Oracle Database: This can be any computer where a supported version of the Oracle database runs.</span></span> <span data-ttu-id="28b1c-113">これには、Windows、Linux、またはインストールされた Oracle データベースのバージョンがサポートする他の任意のオペレーティング システムを実行するコンピューターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="28b1c-113">This includes any computer running Windows, Linux, or any other operating system supported by the version of the Oracle database installed.</span></span> <span data-ttu-id="28b1c-114">このプラットフォームは図で複数示されています。これは、単一の Oracle CDC Service で複数のソース Oracle データベースの変更をキャプチャできるためです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-114">Note that the diagram shows this platform in plural because a single Oracle CDC Service can capture changes from multiple source Oracle databases.</span></span>  
  
-   <span data-ttu-id="28b1c-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: 対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース ( [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のサポート対象の SKU) が実行される任意のコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-115">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: This can be any computer where the target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database (a supported SKU of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]) runs.</span></span> <span data-ttu-id="28b1c-116">Oracle CDC Service は、変更テーブルおよびサービス構成を格納する 1 つの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ターゲットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="28b1c-116">An Oracle CDC Service supports one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] target where it stores change tables and service configuration.</span></span> <span data-ttu-id="28b1c-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プラットフォームは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のクラスター化されたインスタンスまたは [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の **AlwaysOn** 機能を使用してミラー化されたインスタンスを表す場合もあります。</span><span class="sxs-lookup"><span data-stu-id="28b1c-117">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Platform may also represent a clustered instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] or a mirrored instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] using the **AlwaysOn** feature.</span></span>  
  
-   <span data-ttu-id="28b1c-118">Oracle CDC デザイナー: ソースの Oracle データベースと対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースにアクセスできる任意のサポート対象 Windows コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-118">The Oracle CDC Designer: This can be any supported Windows computer that can access the source Oracle database and the target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="28b1c-119">次の表に、上記の 4 つのプラットフォームで実行されるコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="28b1c-119">The following table describes the components that run on the four platforms described above.</span></span>  
  
|<span data-ttu-id="28b1c-120">コンポーネント/説明</span><span class="sxs-lookup"><span data-stu-id="28b1c-120">Component/Description</span></span>|<span data-ttu-id="28b1c-121">コンポーネントの構成要素</span><span class="sxs-lookup"><span data-stu-id="28b1c-121">Component consists of:</span></span>|  
|----------------------------|----------------------------|  
|<span data-ttu-id="28b1c-122">Oracle CDC Service: 変更データ キャプチャ操作が実行される Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-122">Oracle CDC Service: This is a Windows service where the change data capture activity takes place.</span></span>|<span data-ttu-id="28b1c-123">Oracle CDC インスタンス: 単一のソース Oracle データベースに対する変更データ キャプチャ操作を処理する、Oracle CDC Service のサブプロセスです (ソース Oracle データベースごとに 1 つの Oracle CDC インスタンスが存在します)。</span><span class="sxs-lookup"><span data-stu-id="28b1c-123">Oracle CDC Instance: A sub-process of the Oracle CDC Service that handles change data capture activity for a single source Oracle database (there is one Oracle CDC instance per source Oracle database).</span></span><br /><br /> <span data-ttu-id="28b1c-124">Oracle ログ リーダー: Oracle クライアントを使用して Oracle トランザクション ログを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="28b1c-124">Oracle Log Reader: Reads Oracle transaction logs using the Oracle Client.</span></span><br /><br /> <span data-ttu-id="28b1c-125">Oracle クライアント: Oracle との通信に使用される Oracle Instant Client です。</span><span class="sxs-lookup"><span data-stu-id="28b1c-125">Oracle Client: The Oracle Instant Client used for communication with Oracle.</span></span> <span data-ttu-id="28b1c-126">これは、Oracle CDC Service をインストールする前に Oracle から入手してインストールする必要がある必須ソフトウェアです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-126">This is a prerequisite that should be obtained from Oracle and installed before installing the Oracle CDC Service.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="28b1c-127">変更ライター: キャプチャされた Oracle テーブルに加えられたコミット済みの変更を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]変更テーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="28b1c-127">Change Writer: This writes committed changes made to the captured Oracle table to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]change tables.</span></span> <span data-ttu-id="28b1c-128">また、このコンポーネントはキャプチャ状態を対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内に維持します。</span><span class="sxs-lookup"><span data-stu-id="28b1c-128">This component also maintains that capture state within the target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="28b1c-129">ODBC クライアント: [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]用のマイクロソフトのネイティブ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-129">ODBC Client: The Microsoft Native Client for [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="28b1c-130">これは、Oracle CDC Service をインストールする前にマイクロソフトから入手してインストールする必要がある必須コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-130">This is a prerequisite component that should be obtained from Microsoft and installed before installing the Oracle CDC Service.</span></span>|  
|<span data-ttu-id="28b1c-131">Oracle CDC Service 構成: Windows サービスを作成してその構成を設定する Microsoft 管理コンソール スナップインです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-131">Oracle CDC Service Configuration: This is a Microsoft Management Console snap-in that creates the Windows service and sets up its configuration.</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="28b1c-132">クライアント: .NET Framework Version 4 に付属する SQL ADO.NET クライアントです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-132">Client: The SQL ADO.NET client that ships with version 4 of the .NET framework.</span></span>|  
|<span data-ttu-id="28b1c-133">Oracle データベース: 選択したテーブルへの変更をキャプチャするソース Oracle データベースです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-133">Oracle Database: A source Oracle database from which changes to select tables are captured.</span></span>|<span data-ttu-id="28b1c-134">ログ マイナー: Oracle トランザクション ログの読み取りに使用される Oracle コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-134">Log Miner: An Oracle component through which the Oracle transaction logs are read.</span></span><br /><br /> <span data-ttu-id="28b1c-135">トランザクション ログ: データベースでトランザクションをロールバックし、障害から復元できるようにするために (この場合、Oracle データベースをアーカイブログ モードで運用する必要があります)、Oracle によって使用されるオンラインまたはアーカイブされた Oracle 再実行ログです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-135">Transaction Logs: The online and archived Oracle Redo Logs that are used by Oracle to ensure that the database can roll back transactions and recover from failures (in this case, the Oracle database must operate in archive-log mode).</span></span>|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="28b1c-136">インスタンス: CDC データベースがホストされる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-136">Instance: A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where the CDC databases are hosted.</span></span> <span data-ttu-id="28b1c-137">これはクラスター化された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス (フェールオーバー クラスター) またはミラー化されたデータベース (AlwaysOn) です。</span><span class="sxs-lookup"><span data-stu-id="28b1c-137">This may be a clustered [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance (failover cluster) or a mirrored database (AlwaysOn).</span></span>|<span data-ttu-id="28b1c-138">MSXDBCDC データベース: この [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスと連動する CDC Service に関する情報が保持されるデータベースです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-138">The MSXDBCDC Database: A database where information about the CDC Services working with this [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance is kept.</span></span> <span data-ttu-id="28b1c-139">また、各 CDC Service によって処理される Oracle CDC インスタンスの情報も保持されます。</span><span class="sxs-lookup"><span data-stu-id="28b1c-139">It also keeps information on the Oracle CDC Instances handled by each CDC Service.</span></span> <span data-ttu-id="28b1c-140">このデータベースは、CDC Service 作成プロセスの一環として作成されます。</span><span class="sxs-lookup"><span data-stu-id="28b1c-140">This database is created as part of the CDC Service creation process.</span></span><br /><br /> <span data-ttu-id="28b1c-141">CDC データベース: いずれかのソース Oracle データベースに加えられた変更を格納する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-141">The CDC Databases: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases that store changes made to one of the source Oracle databases.</span></span> <span data-ttu-id="28b1c-142">CDC データベースは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC に対して有効になります。そのため、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC のテーブルおよび機能を含み、Oracle からの変更を簡単に処理できます。</span><span class="sxs-lookup"><span data-stu-id="28b1c-142">The CDC Databases are enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC so they have the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC tables and functions, making it easy to consume changes originating from Oracle.</span></span>|  
|<span data-ttu-id="28b1c-143">Oracle CDC デザイナー: Oracle CDC インスタンスの作成を支援する Microsoft 管理コンソール スナップインです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-143">Oracle CDC Designer: A Microsoft Management Console snap-in that helps create Oracle CDC Instances.</span></span> <span data-ttu-id="28b1c-144">このスナップインを使用して、キャプチャするテーブルおよび列を選択し、Oracle 接続情報を提供し、CDC インスタンスのライフ サイクルを管理します。</span><span class="sxs-lookup"><span data-stu-id="28b1c-144">Use this to select the tables and columns to be captured, provide Oracle connection information and manage the life cycle of CDC Instances.</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="28b1c-145">クライアント: .NET Framework Version 4 に付属する SQL ADO.NET クライアントです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-145">Client: The SQL ADO.NET client that ships with version 4 of the .NET framework.</span></span><br /><br /> <span data-ttu-id="28b1c-146">Oracle クライアント: Oracle との通信に使用される Oracle Instant Client です。</span><span class="sxs-lookup"><span data-stu-id="28b1c-146">Oracle Client: The Oracle Instant Client used for communication with Oracle.</span></span> <span data-ttu-id="28b1c-147">これは、Oracle CDC Service をインストールする前に Oracle から入手してインストールする必要がある必須コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="28b1c-147">This is a prerequisite component that should be obtained from Oracle and installed before installing the Oracle CDC Service.</span></span>|  
  
 <span data-ttu-id="28b1c-148">Oracle CDC Service とその子である Oracle CDC インスタンスは、ソース Oracle データベースおよびクライアントである対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのみと通信できます。</span><span class="sxs-lookup"><span data-stu-id="28b1c-148">The Oracle CDC Service and its child Oracle CDC Instances can communicate only with the source Oracle database(s) and the target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance as clients.</span></span> <span data-ttu-id="28b1c-149">ネットワーク プロトコルやその他のプロトコルの積極的なリッスンは行いません。</span><span class="sxs-lookup"><span data-stu-id="28b1c-149">They do not actively listen on any network and other protocols.</span></span> <span data-ttu-id="28b1c-150">Oracle CDC Service は、CDC データベースを監視して構成の変更を検出し、更新された構成に基づいて操作を更新します。</span><span class="sxs-lookup"><span data-stu-id="28b1c-150">The Oracle CDC Service monitors the CDC databases for configuration changes and updates its operation based on the updated configuration.</span></span>  
  
  
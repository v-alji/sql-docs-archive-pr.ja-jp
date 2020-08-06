---
title: OLE DB 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5431de956a1039c2978688982792f190b0abc544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642228"
---
# <a name="ole-db-connection-manager"></a><span data-ttu-id="934bb-102">OLE DB 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="934bb-102">OLE DB Connection Manager</span></span>
  <span data-ttu-id="934bb-103">OLE DB 接続マネージャーを使用すると、パッケージは OLE DB プロバイダーを使用してデータ ソースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="934bb-103">An OLE DB connection manager enables a package to connect to a data source by using an OLE DB provider.</span></span> <span data-ttu-id="934bb-104">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する OLE DB 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用できます。</span><span class="sxs-lookup"><span data-stu-id="934bb-104">For example, an OLE DB connection manager that connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934bb-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB プロバイダーでは、マルチサブネット フェールオーバー クラスタリングの新しい接続文字列キーワード (MultiSubnetFailover=True) はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="934bb-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB provider does not support the new connection string key words (MultiSubnetFailover=True) for Multi-Subnet Failover Clustering.</span></span> <span data-ttu-id="934bb-106">詳細については、www.mattmasson.com の[リリースノート](https://go.microsoft.com/fwlink/?LinkId=247824)と、の[AlwaysOn マルチサブネットフェールオーバーおよび SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)に関するブログ記事を参照し SQL Server てください。</span><span class="sxs-lookup"><span data-stu-id="934bb-106">For more information, see the [SQL Server Release  Notes](https://go.microsoft.com/fwlink/?LinkId=247824) and the blog post, [AlwaysOn Multi-Subnet Failover and SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/), on www.mattmasson.com.</span></span>  
  
 <span data-ttu-id="934bb-107">いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] タスクとデータフローコンポーネントでは、OLE DB 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="934bb-107">Several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and data flow components use an OLE DB connection manager.</span></span> <span data-ttu-id="934bb-108">たとえば、OLE DB ソースと OLE DB 変換先は、この接続マネージャーを使用してデータの抽出と読み込みを行います。また、SQL 実行タスクは、この接続マネージャーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="934bb-108">For example, the OLE DB source and OLE DB destination use this connection manager to extract and load data, and the Execute SQL task can use this connection manager to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to run queries.</span></span>  
  
 <span data-ttu-id="934bb-109">OLE DB 接続マネージャーは、C++ などの言語を使用するアンマネージ コードで記述されたカスタム タスク内で、OLE DB データ ソースにアクセスするためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="934bb-109">The OLE DB connection manager is also used to access OLE DB data sources in custom tasks written in unmanaged code that uses a language such as C++.</span></span>  
  
 <span data-ttu-id="934bb-110">OLE DB 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に OLE DB 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="934bb-110">When you add an OLE DB connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an OLE DB connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="934bb-111">接続マネージャーの `ConnectionManagerType` プロパティは、`OLEDB` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="934bb-111">The `ConnectionManagerType` property of the connection manager is set to `OLEDB`.</span></span>  
  
 <span data-ttu-id="934bb-112">OLE DB 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="934bb-112">The OLE DB connection manager can be configured in the following ways:</span></span>  
  
-   <span data-ttu-id="934bb-113">選択したプロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="934bb-113">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="934bb-114">プロパイダによっては、接続先のデータ ソースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="934bb-114">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="934bb-115">選択したプロバイダーに適したセキュリティ資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="934bb-115">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="934bb-116">接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="934bb-116">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="934bb-117">ログの記録</span><span class="sxs-lookup"><span data-stu-id="934bb-117">Logging</span></span>  
 <span data-ttu-id="934bb-118">OLE DB 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="934bb-118">You can log the calls that the OLE DB connection manager makes to external data providers.</span></span> <span data-ttu-id="934bb-119">このログ機能を使用すると、OLE DB 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="934bb-119">You can use this logging capability to troubleshoot the connections that the OLE DB connection manager makes to external data sources.</span></span> <span data-ttu-id="934bb-120">OLE DB 接続マネージャーが外部データプロバイダーに対して行う呼び出しをログに記録するには、パッケージログ記録を有効にし、パッケージレベルで**Diagnostic**イベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="934bb-120">To log the calls that the OLE DB connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="934bb-121">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934bb-121">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuration-of-the-oledb-connection-manager"></a><span data-ttu-id="934bb-122">OLEDB 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="934bb-122">Configuration of the OLEDB Connection Manager</span></span>  
 <span data-ttu-id="934bb-123">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="934bb-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="934bb-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [OLE DB 接続マネージャーの構成](../configure-ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934bb-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Configure OLE DB Connection Manager](../configure-ole-db-connection-manager.md).</span></span> <span data-ttu-id="934bb-125">プログラムによって接続マネージャーを構成する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** クラスのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="934bb-125">For information about configuring a connection manager programmatically, see the documentation for **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** class in the Developer Guide.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="934bb-126">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="934bb-126">Related Content</span></span>  
  
-   <span data-ttu-id="934bb-127">Wiki の記事「 [SSIS With Oracle connector with](https://go.microsoft.com/fwlink/?LinkId=220670) social.technet.microsoft.com」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="934bb-127">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) on social.technet.microsoft.com.</span></span>  
  
-   <span data-ttu-id="934bb-128">carlprothman.net の [OLE DB プロバイダー用接続文字列](https://go.microsoft.com/fwlink/?LinkId=220744)に関する技術記事</span><span class="sxs-lookup"><span data-stu-id="934bb-128">Technical article, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744), on carlprothman.net.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934bb-129">参照</span><span class="sxs-lookup"><span data-stu-id="934bb-129">See Also</span></span>  
 <span data-ttu-id="934bb-130">[OLE DB ソース](../data-flow/ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="934bb-130">[OLE DB Source](../data-flow/ole-db-source.md) </span></span>  
 <span data-ttu-id="934bb-131">[OLE DB 変換先](../data-flow/ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="934bb-131">[OLE DB Destination](../data-flow/ole-db-destination.md) </span></span>  
 <span data-ttu-id="934bb-132">[SQL 実行タスク](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="934bb-132">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="934bb-133">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="934bb-133">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  

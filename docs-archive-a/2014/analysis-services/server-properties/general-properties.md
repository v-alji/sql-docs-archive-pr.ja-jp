---
title: 全般プロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- IdleConnectionTimeout property
- InstanceVisible property
- TempDir property
- AdminTimeout property
- MinIdleSessionTimeout property
- MaxIdleSessionTimeout property
- IdleOrphanSessionTimeout property
- BackupDir property
- CommitTimeout property
- ExternalCommandTimeout property
- Enabled property
- ForceCommitTimeout property
- Port property
- CoordinatorShutdownMode property
- ServerTimeout property
- AllowedBrowsingFolders property
- CoordinatorCancelCount property
- DataDir property
- CoordinatorQueryMaxThreads property
- CoordinatorExecutionMode property
- ExternalConnectionTimeout property
- CollationName property
- EnableFast1033Locale property
- CoordinatorBuildMaxThreads property
- Language property
- StatisticsStoreSize property
- RepositoryConnectionString property
ms.assetid: 88a8117c-396a-469f-a62d-c6f262504021
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca746a1bb57e84cf0f6a8f47622b118c7180eb1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743498"
---
# <a name="general-properties"></a><span data-ttu-id="7ee7e-102">全般プロパティ</span><span class="sxs-lookup"><span data-stu-id="7ee7e-102">General Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="7ee7e-103">では、次の表に示すサーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="7ee7e-104">このトピックでは、Security、Network、ThreadPool など、個別のセクションで取り上げることのできなかった、msmdsrv.ini ファイル内のサーバー プロパティについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-104">This topic documents those server properties in the msmdsrv.ini file that are not otherwise included in a specific section, such as Security, Network, or ThreadPool.</span></span> <span data-ttu-id="7ee7e-105">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="7ee7e-106">**適用対象:** 特に記載のない限り、多次元サーバー モードおよびテーブル サーバー モードが対象となります。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-106">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="7ee7e-107">不特定カテゴリ</span><span class="sxs-lookup"><span data-stu-id="7ee7e-107">Non-Specific Category</span></span>  
 `AdminTimeout`  
 <span data-ttu-id="7ee7e-108">管理者のタイムアウトを秒単位で定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-108">A signed 32-bit integer property that defines the administrator timeout in seconds.</span></span> <span data-ttu-id="7ee7e-109">これは詳細プロパティなので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-109">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="7ee7e-110">このプロパティの既定値は 0 であり、タイムアウトがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-110">The default value for this property is zero (0), which indicates there is no timeout.</span></span>  
  
 `AllowedBrowsingFolders`  
 <span data-ttu-id="7ee7e-111">Analysis Services のダイアログ ボックスでファイルを保存、開く、および検索するときに参照できるフォルダーを区切り記号で区切った一覧で指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-111">A string property that specifies in a delimited list the folders that can be browsed when saving, opening, and finding files in Analysis Services dialog boxes.</span></span> <span data-ttu-id="7ee7e-112">Analysis Services のサービス アカウントには、リストに追加するすべてのフォルダーの読み取り権限と書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-112">The Analysis Services service account must have read and write permissions to any folders that you add to the list.</span></span>  
  
 `BackupDir`  
 <span data-ttu-id="7ee7e-113">Backup コマンドの一部としてパスが指定されていない場合に、既定でバックアップファイルが格納されるディレクトリの名前を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-113">A string property that identifies the name of the directory where backup files are stored by default, in the event a path is not specified as part of the Backup command.</span></span>  
  
 `CollationName`  
 <span data-ttu-id="7ee7e-114">サーバーの照合順序を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-114">A string property that identifies the server collation.</span></span> <span data-ttu-id="7ee7e-115">詳細については、「[言語および照合順序 &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-115">For more information, see [Languages and Collations &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md).</span></span>  
  
 `CommitTimeout`  
 <span data-ttu-id="7ee7e-116">サーバーがトランザクションをコミットする目的で書き込みロックの取得を待機する時間 (ミリ秒単位) を指定する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-116">An integer property that specifies how long (in milliseconds) the server will wait to acquire a write lock for the purpose of committing a transaction.</span></span> <span data-ttu-id="7ee7e-117">サーバーはトランザクションをコミットする書き込みロックを取得する前に他のロックが解放されるのを待機する必要があるため、待機期間が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-117">A waiting period is often required because the server must wait for other locks to be released before it can take a write lock that commits the transaction.</span></span>  
  
 <span data-ttu-id="7ee7e-118">このプロパティの既定値は 0 であり、サーバーで無限に待機することを示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-118">The default value for this property is zero (0), which indicates that the server will wait indefinitely.</span></span> <span data-ttu-id="7ee7e-119">ロックに関連したプロパティの詳細については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-119">For more information about lock-related properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorBuildMaxThreads`  
 <span data-ttu-id="7ee7e-120">パーティション インデックスの作成に割り当てられるスレッドの最大数を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-120">A signed 32-bit integer property that defines the maximum number of threads allocated to building partition indexes.</span></span> <span data-ttu-id="7ee7e-121">パーティション インデックスの作成時間を短縮するには、この値を大きくしてください。ただし、メモリの使用量は増えます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-121">Increase this value in order to speed-up partition indexing, at the cost of memory usage.</span></span> <span data-ttu-id="7ee7e-122">このプロパティの詳細については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-122">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorCancelCount`  
 <span data-ttu-id="7ee7e-123">キャンセル イベントが発生したかどうかを内部反復カウントに基づいてサーバーがチェックする頻度を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-123">A signed 32-bit integer property that defines how frequently the server should check whether a Cancel event occurred (based on internal iteration count).</span></span> <span data-ttu-id="7ee7e-124">キャンセルのチェック頻度を多くするには、この値を小さくしてください。ただし、全体的なパフォーマンスは低下します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-124">Decrease this number in order to check for Cancel more frequently, at the expense of general performance.</span></span>  
  
 <span data-ttu-id="7ee7e-125">表形式サーバー モードでは、`CoordinatorCancelCount` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-125">`CoordinatorCancelCount` is ignored in tabular server mode.</span></span>  
  
 `CoordinatorExecutionMode`  
 <span data-ttu-id="7ee7e-126">処理操作やクエリ操作など、サーバーによって試行される並列操作の最大数を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-126">A signed 32-bit integer property that defines the maximum number of parallel operations the server will attempt, including processing and querying operations.</span></span> <span data-ttu-id="7ee7e-127">0 を指定すると、サーバーの内部アルゴリズムに基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-127">Zero (0) indicates that the server will decide, based on an internal algorithm.</span></span> <span data-ttu-id="7ee7e-128">正の数値は、操作の最大総数を示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-128">A positive number indicates the maximum number of operations in total.</span></span> <span data-ttu-id="7ee7e-129">負の数値 (反対の符号) は、プロセッサあたりの操作の最大数を示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-129">A negative number, with the sign reversed, indicates the maximum number of operations per processor.</span></span>  
  
 <span data-ttu-id="7ee7e-130">表形式サーバー モードでは、`CoordinatorExecutionMode` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-130">`CoordinatorExecutionMode` is ignored in tabular server mode.</span></span>  
  
 <span data-ttu-id="7ee7e-131">このプロパティの既定値は -4 であり、サーバーのプロセッサあたりの並列操作が 4 に制限されることを示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-131">The default value for this property is -4, which indicates the server is limited to 4 parallel operations per processor.</span></span> <span data-ttu-id="7ee7e-132">このプロパティの詳細については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-132">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorQueryMaxThreads`  
 <span data-ttu-id="7ee7e-133">クエリ解決時のパーティション セグメントあたりの最大スレッド数を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-133">A signed 32-bit integer property that defines the maximum number of threads per partition segment during query resolution.</span></span> <span data-ttu-id="7ee7e-134">同時ユーザーの数が少なくなるほど大きい値を設定できますが、値を大きくするとメモリの使用量が増えます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-134">The fewer the number of concurrent users, the higher this value can be, at the cost of memory.</span></span> <span data-ttu-id="7ee7e-135">逆に、同時ユーザーが多い場合は、この値を小さくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-135">Conversely, it may need to be lowered if there are a large number of concurrent users.</span></span>  
  
 `CoordinatorShutdownMode`  
 <span data-ttu-id="7ee7e-136">コーディネーターのシャットダウン モードを定義するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-136">A Boolean property that defines coordinator shutdown mode.</span></span> <span data-ttu-id="7ee7e-137">これは詳細プロパティなので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-137">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataDir`  
 <span data-ttu-id="7ee7e-138">データを保存するディレクトリの名前を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-138">A string property that identifies the name of the directory where data is stored.</span></span>  
  
 `DeploymentMode`  
 <span data-ttu-id="7ee7e-139">Analysis Services サーバー インスタンスの操作コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-139">Determines the operational context of an Analysis Services server instance.</span></span> <span data-ttu-id="7ee7e-140">このプロパティは、ダイアログボックス、メッセージ、およびドキュメントでは "サーバーモード" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-140">This property is referred to as 'server mode' in dialog boxes, messages, and documentation.</span></span> <span data-ttu-id="7ee7e-141">このプロパティは、Analysis Services のインストール時に選択したサーバー モードに基づいて、SQL Server セットアップによって構成されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-141">This property is configured by SQL Server Setup based on the server mode you selected when installing Analysis Services.</span></span> <span data-ttu-id="7ee7e-142">このプロパティは内部使用のみと見なしてください。常にセットアップによって指定された値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-142">This property should be considered internal only, always using the value specified by Setup.</span></span>  
  
 <span data-ttu-id="7ee7e-143">このプロパティの有効値を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-143">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="7ee7e-144">値</span><span class="sxs-lookup"><span data-stu-id="7ee7e-144">Value</span></span>|<span data-ttu-id="7ee7e-145">[説明]</span><span class="sxs-lookup"><span data-stu-id="7ee7e-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ee7e-146">0</span><span class="sxs-lookup"><span data-stu-id="7ee7e-146">0</span></span>|<span data-ttu-id="7ee7e-147">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-147">This is the default value.</span></span> <span data-ttu-id="7ee7e-148">MOLAP、HOLAP、ROLAP の各ストレージ、およびデータ マイニング モデルを使用する多次元データベースの処理に使用される多次元モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-148">It specifies multidimensional mode, used to service multidimensional databases that use MOLAP, HOLAP, and ROLAP storage, as well as data mining models.</span></span>|  
|<span data-ttu-id="7ee7e-149">1</span><span class="sxs-lookup"><span data-stu-id="7ee7e-149">1</span></span>|<span data-ttu-id="7ee7e-150">PowerPivot for SharePoint 配置の一部としてインストールされた Analysis Services インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-150">Specifies Analysis Services instances that were installed as part of a PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="7ee7e-151">PowerPivot for SharePoint インストールの一部である Analysis Services インスタンスの配置モード プロパティは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-151">Do not change the deployment mode property of Analysis Services instance that is part of a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="7ee7e-152">モードを変更すると、PowerPivot データがサーバー上で実行されなくなります。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-152">PowerPivot data will no longer run on the server if you change the mode.</span></span>|  
|<span data-ttu-id="7ee7e-153">2</span><span class="sxs-lookup"><span data-stu-id="7ee7e-153">2</span></span>|<span data-ttu-id="7ee7e-154">インメモリ ストレージまたは DirectQuery ストレージを使用するテーブル モデル データベースをホストするために使用するテーブル モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-154">Specifies Tabular mode used for hosting tabular model databases that use in-memory storage or DirectQuery storage.</span></span>|  
  
 <span data-ttu-id="7ee7e-155">各モードは、他のモードと相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-155">Each mode is exclusive of the other.</span></span> <span data-ttu-id="7ee7e-156">テーブル モード用に構成されたサーバーでは、キューブおよびディメンションを含む Analysis Services データベースを実行できません。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-156">A server that is configured for tabular mode cannot run Analysis Services databases that contain cubes and dimensions.</span></span> <span data-ttu-id="7ee7e-157">基になるコンピューターのハードウェアでサポートできる場合は、Analysis Services の複数のインスタンスを同じコンピューターにインストールし、さまざまな配置モードを使用するように各インスタンスを構成できます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-157">If the underlying computer hardware can support it, you can install multiple instances of Analysis Services on the same computer and configure each instance to use a different deployment mode.</span></span> <span data-ttu-id="7ee7e-158">Analysis Services はリソースを大量に消費するアプリケーションであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-158">Remember that Analysis Services is a resource intensive application.</span></span> <span data-ttu-id="7ee7e-159">同じシステム上に複数のインスタンスを配置する構成は、ハイエンド サーバーの場合のみお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-159">Deploying multiple instances on the same system is recommended only for high-end servers.</span></span>  
  
 `EnableFast1033Locale`  
 <span data-ttu-id="7ee7e-160">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-160">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ExternalCommandTimeout`  
 <span data-ttu-id="7ee7e-161">リレーショナル データ ソースや外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーなど、外部サーバーに対して発行されたコマンドのタイムアウトを秒単位で定義する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-161">An integer property that defines the timeout, in seconds, for commands issued to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="7ee7e-162">このプロパティの既定値は 3600 (秒) です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-162">The default value for this property is 3600 (seconds).</span></span>  
  
 `ExternalConnectionTimeout`  
 <span data-ttu-id="7ee7e-163">リレーショナル データ ソースや外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーなど、外部サーバーへの接続確立のタイムアウトを秒単位で定義する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-163">An integer property that defines the timeout, in seconds, for creating connections to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span> <span data-ttu-id="7ee7e-164">このプロパティは、接続のタイムアウトが接続文字列に指定されている場合に無視されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-164">This property is ignored if a connection timeout is specified on the connection string.</span></span>  
  
 <span data-ttu-id="7ee7e-165">このプロパティの既定値は 60 (秒) です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-165">The default value for this property is 60 (seconds).</span></span>  
  
 `ForceCommitTimeout`  
 <span data-ttu-id="7ee7e-166">処理中のクエリなど、現在のコマンドに先行する他のコマンドを取り消す前に書き込みコミット操作が待機する必要のある時間をミリ秒単位で指定する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-166">An integer property that specifies how long, in milliseconds, a write commit operation should wait before canceling other commands that preceded the current command, including queries in progress.</span></span> <span data-ttu-id="7ee7e-167">これにより、クエリなどの優先順位の低い操作を取り消すことでコミット トランザクションを続行できます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-167">This allows the commit transaction to proceed by canceling lower priority operations, such as queries.</span></span>  
  
 <span data-ttu-id="7ee7e-168">このプロパティの既定値は 30 秒 (30,000 ミリ秒) であり、コミット トランザクションが 30 秒間待機するまで他のコマンドはタイムアウトにならないことを示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-168">The default value for this property is 30 seconds (30000 milliseconds), which indicates that other commands will not be forced to timeout until the commit transaction has been waiting for 30 seconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ee7e-169">このイベントによってクエリやプロセスが取り消されると、"`Server: The operation has been cancelled`" というエラー メッセージが報告されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-169">Queries and processes cancelled by this event will report the following error message: "`Server: The operation has been cancelled`"</span></span>  
  
 <span data-ttu-id="7ee7e-170">このプロパティの詳細については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-170">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ee7e-171">`ForceCommitTimeout` は、キューブ処理コマンドと書き戻し操作に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-171">`ForceCommitTimeout` applies to cube processing commands and to writeback operations.</span></span>  
  
 `IdleConnectionTimeout`  
 <span data-ttu-id="7ee7e-172">アクティブでない接続のタイムアウトを秒単位で指定する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-172">An integer property that specifies a timeout, in seconds, for connections that are inactive.</span></span>  
  
 <span data-ttu-id="7ee7e-173">このプロパティの既定値は 0 であり、アイドル状態の接続がタイムアウトにならないことを示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-173">The default value for this property is zero (0), which indicates that idle connections will not be timed out.</span></span>  
  
 `IdleOrphanSessionTimeout`  
 <span data-ttu-id="7ee7e-174">孤立したセッションをサーバー メモリに保持しておく時間を秒単位で定義する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-174">An integer property that defines how long, in seconds, orphaned sessions will be retained in server memory.</span></span> <span data-ttu-id="7ee7e-175">孤立セッションとは、関連付けられている接続がなくなったセッションです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-175">An orphaned session is one that no longer has an associated connection.</span></span> <span data-ttu-id="7ee7e-176">既定値は 120 秒です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-176">The default is 120 seconds.</span></span>  
  
 `InstanceVisible`  
 <span data-ttu-id="7ee7e-177">SQL Server Browser サービスからのインスタンス要求を検出するためにサーバー インスタンスを表示するかどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-177">A Boolean property that indicates whether the server instance is visible to discover instance requests from SQL Server Browser service.</span></span> <span data-ttu-id="7ee7e-178">既定値は True です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-178">The default is True.</span></span> <span data-ttu-id="7ee7e-179">false に設定した場合、インスタンスは SQL Server Browser に表示されません。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-179">If you set it to false, the instance is not visible to SQL Server Browser.</span></span>  
  
 `Language`  
 <span data-ttu-id="7ee7e-180">エラー メッセージや数値書式などの言語を定義する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-180">A string property that defines the language, including error messages and number formatting.</span></span> <span data-ttu-id="7ee7e-181">このプロパティは CollationName プロパティをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-181">This property overrides the CollationName property.</span></span>  
  
 <span data-ttu-id="7ee7e-182">このプロパティの既定値は空白であり、CollationName プロパティによって言語が定義されることを示します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-182">The default value for this property is blank, which indicates that the CollationName property defines the language.</span></span>  
  
 `LogDir`  
 <span data-ttu-id="7ee7e-183">サーバー ログを保存するディレクトリの名前を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-183">A string property that identifies the name of the directory that contains server logs.</span></span> <span data-ttu-id="7ee7e-184">このプロパティは、データベース テーブル (既定の動作) ではなく、ディスク ファイルがログ記録に使用される場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-184">This property only applies when disk files are used for logging, as opposed to database tables (the default behavior).</span></span>  
  
 `MaxIdleSessionTimeout`  
 <span data-ttu-id="7ee7e-185">アイドル状態のセッションの最大タイムアウトを秒単位で定義する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-185">An integer property that defines the maximum idle session timeout, in seconds.</span></span> <span data-ttu-id="7ee7e-186">既定値はゼロ (0) で、セッションがタイムアウトしないことを示します。ただし、サーバーがリソースの制約を受けている場合でも、アイドル状態のセッションは削除されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-186">The default is zero (0), indicating that sessions are never timed out. However, idle sessions will still be removed if the server is under resource constraints.</span></span>  
  
 `MinIdleSessionTimeout`  
 <span data-ttu-id="7ee7e-187">アイドル状態のセッションがタイムアウトになるまでの最短時間を秒単位で定義する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-187">An integer property that defines the minimum time, in seconds, that idle sessions will timeout.</span></span> <span data-ttu-id="7ee7e-188">既定値は 2700 秒です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-188">The default is 2700 seconds.</span></span> <span data-ttu-id="7ee7e-189">この時間を経過すると、メモリが必要な場合に限り、アイドル状態のセッションがサーバーによって終了されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-189">After this time expires, the server is permitted to end the idle session, but will only do so as memory is needed.</span></span>  
  
 `Port`  
 <span data-ttu-id="7ee7e-190">サーバーがクライアント接続をリッスンするポート番号を定義する整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-190">An integer property that defines the port number on which server will listen for client connections.</span></span> <span data-ttu-id="7ee7e-191">このプロパティを設定しない場合、サーバーは最初の未使用ポートを動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-191">If not set, server dynamically finds first unused port.</span></span>  
  
 <span data-ttu-id="7ee7e-192">このプロパティの既定値は 0 であり、ポート 2383 が既定により使用されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-192">The default value for this property is zero (0), which in turn defaults to port 2383.</span></span> <span data-ttu-id="7ee7e-193">ポートの構成の詳細については、「 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-193">For more information about port configuration, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
 `ServerTimeout`  
 <span data-ttu-id="7ee7e-194">クエリのタイムアウトを秒単位で定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-194">An integer that defines the timeout, in seconds, for queries.</span></span> <span data-ttu-id="7ee7e-195">既定値は 3600 秒 (60 分) です。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-195">The default is 3600 seconds (or 60 minutes).</span></span> <span data-ttu-id="7ee7e-196">ゼロ (0) はクエリがタイムアウトにならないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-196">Zero (0) specifies that no queries will timeout.</span></span>  
  
 `TempDir`  
 <span data-ttu-id="7ee7e-197">処理、復元、その他の操作時に使用する一時ファイルの格納場所を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-197">A string property that specifies the location for storing temporary files used during processing, restoring, and other operations.</span></span> <span data-ttu-id="7ee7e-198">このプロパティの既定値は、セットアップによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-198">The default value for this property is determined by setup.</span></span> <span data-ttu-id="7ee7e-199">このプロパティを指定しない場合、既定値は Data ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-199">If not specified, the default is the Data directory.</span></span>  
  
## <a name="requestprioritization-category"></a><span data-ttu-id="7ee7e-200">要求の優先順位付けカテゴリ</span><span class="sxs-lookup"><span data-stu-id="7ee7e-200">RequestPrioritization Category</span></span>  
 `Enabled`  
 <span data-ttu-id="7ee7e-201">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-201">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `StatisticsStoreSize`  
 <span data-ttu-id="7ee7e-202">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ee7e-202">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee7e-203">参照</span><span class="sxs-lookup"><span data-stu-id="7ee7e-203">See Also</span></span>  
 <span data-ttu-id="7ee7e-204">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7ee7e-204">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="7ee7e-205">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="7ee7e-205">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  

---
title: SQL Server オブジェクトの転送タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjectstask.f1
helpviewer_keywords:
- Transfer SQL Server Objects task [Integration Services]
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 281acb189e8f4dcfde9dc7ad1d2a74525236d28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631167"
---
# <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="6ef63-102">SQL Server オブジェクトの転送タスク</span><span class="sxs-lookup"><span data-stu-id="6ef63-102">Transfer SQL Server Objects Task</span></span>
  <span data-ttu-id="6ef63-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内の 1 つ以上の種類のオブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス間で転送します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-103">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers one or more types of objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6ef63-104">たとえば、このタスクを使用して、テーブルやストアド プロシージャをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-104">For example, the task can copy tables and stored procedures.</span></span> <span data-ttu-id="6ef63-105">転送元として使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンに応じて、コピーできるオブジェクトの種類が異なります。</span><span class="sxs-lookup"><span data-stu-id="6ef63-105">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is used as a source, different types of objects are available to copy.</span></span> <span data-ttu-id="6ef63-106">たとえば、スキーマとユーザー定義集計は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースだけに含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-106">For example, only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database includes schemas and user-defined aggregates.</span></span>  
  
## <a name="objects-to-transfer"></a><span data-ttu-id="6ef63-107">転送するオブジェクト</span><span class="sxs-lookup"><span data-stu-id="6ef63-107">Objects to Transfer</span></span>  
 <span data-ttu-id="6ef63-108">転送するオブジェクトの権限に加えて、指定したデータベースのサーバー ロール、ロール、およびユーザーもコピーできます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-108">Server roles, roles, and users from the specified database can be copied, as well as the permissions for the transferred objects.</span></span> <span data-ttu-id="6ef63-109">関連付けられているユーザー、ロール、および権限をオブジェクトと一緒にコピーすることで、転送したオブジェクトを転送先サーバー上ですぐに利用できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-109">By copying the associated users, roles, and permissions together with the objects, you can make the transferred objects immediately operable on the destination server.</span></span>  
  
 <span data-ttu-id="6ef63-110">次の表に、コピーできるオブジェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-110">The following table lists the type of objects that can be copied.</span></span>  
  
|<span data-ttu-id="6ef63-111">Object</span><span class="sxs-lookup"><span data-stu-id="6ef63-111">Object</span></span>|  
|------------|  
|<span data-ttu-id="6ef63-112">テーブル</span><span class="sxs-lookup"><span data-stu-id="6ef63-112">Tables</span></span>|  
|<span data-ttu-id="6ef63-113">ビュー</span><span class="sxs-lookup"><span data-stu-id="6ef63-113">Views</span></span>|  
|<span data-ttu-id="6ef63-114">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="6ef63-114">Stored Procedures</span></span>|  
|<span data-ttu-id="6ef63-115">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="6ef63-115">User-Defined Functions</span></span>|  
|<span data-ttu-id="6ef63-116">デフォルト</span><span class="sxs-lookup"><span data-stu-id="6ef63-116">Defaults</span></span>|  
|<span data-ttu-id="6ef63-117">ユーザー定義のデータ型</span><span class="sxs-lookup"><span data-stu-id="6ef63-117">User-Defined Data Types</span></span>|  
|<span data-ttu-id="6ef63-118">パーティション関数</span><span class="sxs-lookup"><span data-stu-id="6ef63-118">Partition Functions</span></span>|  
|<span data-ttu-id="6ef63-119">パーティション構成</span><span class="sxs-lookup"><span data-stu-id="6ef63-119">Partition Schemes</span></span>|  
|<span data-ttu-id="6ef63-120">スキーマ</span><span class="sxs-lookup"><span data-stu-id="6ef63-120">Schemas</span></span>|  
|<span data-ttu-id="6ef63-121">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="6ef63-121">Assemblies</span></span>|  
|<span data-ttu-id="6ef63-122">ユーザー定義集計</span><span class="sxs-lookup"><span data-stu-id="6ef63-122">User-Defined Aggregates</span></span>|  
|<span data-ttu-id="6ef63-123">ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="6ef63-123">User-Defined Types</span></span>|  
|<span data-ttu-id="6ef63-124">XML スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="6ef63-124">XML Schema Collection</span></span>|  
  
 <span data-ttu-id="6ef63-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで作成されたユーザー定義型 (UDT) には、共通言語ランタイム (CLR) アセンブリに対する依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="6ef63-125">User-defined types (UDTs) that were created in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have dependencies on common language runtime (CLR) assemblies.</span></span> <span data-ttu-id="6ef63-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクを使用して UDT を転送する場合、依存オブジェクトを転送するタスクを構成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="6ef63-126">If you use the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to transfer UDTs, you must also configure the task to transfer dependent objects.</span></span> <span data-ttu-id="6ef63-127">依存オブジェクトを転送するには、`IncludeDependentObjects` プロパティを `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-127">To transfer dependent objects, set the `IncludeDependentObjects` property to `True`.</span></span>  
  
### <a name="table-options"></a><span data-ttu-id="6ef63-128">テーブル オプション</span><span class="sxs-lookup"><span data-stu-id="6ef63-128">Table Options</span></span>  
 <span data-ttu-id="6ef63-129">テーブルをコピーする際には、コピー プロセスに含めるテーブル関連のアイテムの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-129">When copying tables, you can indicate the types of table-related items to include in the copy process.</span></span> <span data-ttu-id="6ef63-130">次の種類のアイテムは、関連するテーブルと共にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-130">The following types of items can be copied together with the related table:</span></span>  
  
-   <span data-ttu-id="6ef63-131">インデックス</span><span class="sxs-lookup"><span data-stu-id="6ef63-131">Indexes</span></span>  
  
-   <span data-ttu-id="6ef63-132">トリガー</span><span class="sxs-lookup"><span data-stu-id="6ef63-132">Triggers</span></span>  
  
-   <span data-ttu-id="6ef63-133">フルテキスト インデックス</span><span class="sxs-lookup"><span data-stu-id="6ef63-133">Full-text indexes</span></span>  
  
-   <span data-ttu-id="6ef63-134">主キー</span><span class="sxs-lookup"><span data-stu-id="6ef63-134">Primary keys</span></span>  
  
-   <span data-ttu-id="6ef63-135">外部キー</span><span class="sxs-lookup"><span data-stu-id="6ef63-135">Foreign keys</span></span>  
  
 <span data-ttu-id="6ef63-136">また、タスクで生成するスクリプトを Unicode 形式にするかどうかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-136">You can also indicate whether the script that the task generates is in Unicode format.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="6ef63-137">転送先に関するオプション</span><span class="sxs-lookup"><span data-stu-id="6ef63-137">Destination Options</span></span>  
 <span data-ttu-id="6ef63-138">転送するオブジェクトのスキーマ名、データ、拡張プロパティ、および依存オブジェクトを転送に含めるように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクを構成できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-138">You can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="6ef63-139">データをコピーする場合、置換するか、既存のデータを追加できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-139">If data is copied, it can replace or append existing data.</span></span>  
  
 <span data-ttu-id="6ef63-140">一部のオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-140">Some options apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6ef63-141">たとえば、スキーマは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-141">For example, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports schemas.</span></span>  
  
## <a name="security-options"></a><span data-ttu-id="6ef63-142">セキュリティ オプション</span><span class="sxs-lookup"><span data-stu-id="6ef63-142">Security Options</span></span>  
 <span data-ttu-id="6ef63-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクでは、転送元の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースレベルのユーザーとロール、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン、および転送するオブジェクトの権限を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-143">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database-level users and roles from the source, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, and the permissions for transferred objects.</span></span> <span data-ttu-id="6ef63-144">たとえば、転送するテーブルの権限を転送に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-144">For example, the transfer can include the permissions on the transferred tables.</span></span>  
  
## <a name="transfer-objects-between-instances-of-sql-server"></a><span data-ttu-id="6ef63-145">SQL Server のインスタンス間でのオブジェクトの転送</span><span class="sxs-lookup"><span data-stu-id="6ef63-145">Transfer Objects Between Instances of SQL Server</span></span>  
 <span data-ttu-id="6ef63-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の転送元および転送先をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6ef63-146">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="6ef63-147">events</span><span class="sxs-lookup"><span data-stu-id="6ef63-147">Events</span></span>  
 <span data-ttu-id="6ef63-148">このタスクは、転送されたオブジェクトを報告する情報イベントを生成する以外に、オブジェクトが上書きされたときに警告イベントを生成します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-148">The task raises an information event that reports the object transferred and a warning event when an object is overwritten.</span></span> <span data-ttu-id="6ef63-149">情報イベントは、データベース テーブルの切り捨てなどのアクションに対しても生成されます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-149">An information event is also raised for actions such as the truncation of database tables.</span></span>  
  
 <span data-ttu-id="6ef63-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクでは、オブジェクト転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-150">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task does not report incremental progress of the object transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="6ef63-151">実行値</span><span class="sxs-lookup"><span data-stu-id="6ef63-151">Execution Value</span></span>  
 <span data-ttu-id="6ef63-152">このタスクの `ExecutionValue` プロパティに格納される実行値は、転送されたオブジェクトの数を返します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-152">The execution value, stored in the `ExecutionValue` property of the task, returns the number of objects transferred.</span></span> <span data-ttu-id="6ef63-153">SQL Server オブジェクトの転送タスクの `ExecValueVariable` プロパティにユーザー定義変数を割り当てると、オブジェクト転送に関する情報をパッケージの他のオブジェクトで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6ef63-153">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer SQL Server Objects task, information about the object transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="6ef63-154">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ef63-154">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="6ef63-155">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="6ef63-155">Log Entries</span></span>  
 <span data-ttu-id="6ef63-156">SQL Server オブジェクトの転送タスクには、次のようなカスタム ログ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="6ef63-156">The Transfer SQL Server Objects task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="6ef63-157">TransferSqlServerObjectsTaskStartTransferringObjects   転送が開始されたことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="6ef63-157">TransferSqlServerObjectsTaskStartTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="6ef63-158">ログ エントリには、開始時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-158">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="6ef63-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    転送が完了したことを報告このログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="6ef63-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    This log entry reports that the transfer has completed.</span></span> <span data-ttu-id="6ef63-160">ログ エントリには、終了時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-160">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="6ef63-161">また、`OnInformation` イベントのログ エントリは、転送対象として選択された種類のオブジェクトの数、転送されたオブジェクトの数、およびテーブルと一緒にデータが転送されたときはテーブルの切り捨てなどのアクションを報告します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-161">In addition, a log entry for an `OnInformation` event reports the number of objects of the object types that have been selected for transfer, the number of objects that were transferred, and actions such as the truncation of tables when data is transferred with tables.</span></span> <span data-ttu-id="6ef63-162">`OnWarning` イベントのログ エントリは転送先でオブジェクトが上書きされると書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-162">A log entry for the `OnWarning` event is written for each object on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="6ef63-163">セキュリティとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="6ef63-163">Security and Permissions</span></span>  
 <span data-ttu-id="6ef63-164">ユーザーは、転送元サーバー上でオブジェクトを参照する権限、および転送先サーバー上でオブジェクトを削除および作成する権限を持っていることに加えて、指定したデータベースおよびデータベース オブジェクトにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef63-164">The user must have permission to browse objects on the source server, and must have permission to drop and create objects on the destination server; moreover, the user must have access to the specified database and database objects.</span></span>  
  
## <a name="configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="6ef63-165">SQL Server オブジェクトの転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="6ef63-165">Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="6ef63-166">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクを構成して、すべてのオブジェクト、特定の種類のすべてのオブジェクト、または特定の種類の指定したオブジェクトを転送の対象とすることができます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-166">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can be configured to transfer all objects, all objects of a type, or only specified objects of a type.</span></span> <span data-ttu-id="6ef63-167">たとえば、AdventureWorks データベース内の選択したテーブルのみをコピーするように指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-167">For example, you can choose to copy only selected tables in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="6ef63-168">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクを使用してテーブルを転送する場合は、テーブルと一緒にコピーする、テーブルに関連するオブジェクトの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-168">If the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers tables, you can specify the types of table-related objects to copy with the tables.</span></span> <span data-ttu-id="6ef63-169">たとえば、テーブルと一緒に主キーをコピーするように指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-169">For example, you can specify that primary keys are copied with tables.</span></span>  
  
 <span data-ttu-id="6ef63-170">転送するオブジェクトの機能をさらに強化するため、転送するオブジェクトのスキーマ名、データ、拡張プロパティ、および依存オブジェクトを転送に含めるように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクを構成できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-170">To further enhance functionality of transferred objects, you can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="6ef63-171">データをコピーする場合は、既存のデータを置き換えるかまたは追加するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef63-171">When copying data, you can specify whether to replace or append existing data.</span></span>  
  
 <span data-ttu-id="6ef63-172">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクは実行時、2 つの SMO 接続マネージャーを使用して、転送元サーバーおよび転送先サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-172">At run time, the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="6ef63-173">SMO 接続マネージャーの構成は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクとは別に行い、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクは SMO 接続マネージャーを参照します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-173">The SMO connection managers are configured separately from the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task, and then referenced in the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task.</span></span> <span data-ttu-id="6ef63-174">SMO 接続マネージャーは、サーバーと、サーバーに接続する際に使用する認証モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-174">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="6ef63-175">詳細については、「 [SMO 接続マネージャー](../connection-manager/smo-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ef63-175">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="6ef63-176">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="6ef63-176">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="6ef63-177">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ef63-177">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="6ef63-178">[[SQL Server オブジェクトの転送タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="6ef63-178">[Transfer SQL Server Objects Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="6ef63-179">[[SQL Server オブジェクトの転送タスク エディター] &#40;[オブジェクト] ページ&#41;](../transfer-sql-server-objects-task-editor-objects-page.md)</span><span class="sxs-lookup"><span data-stu-id="6ef63-179">[Transfer SQL Server Objects Task Editor &#40;Objects Page&#41;](../transfer-sql-server-objects-task-editor-objects-page.md)</span></span>  
  
-   <span data-ttu-id="6ef63-180">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="6ef63-180">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="6ef63-181">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ef63-181">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="6ef63-182">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="6ef63-182">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="6ef63-183">プログラムによる SQL Server オブジェクトの転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="6ef63-183">Programmatic Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="6ef63-184">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ef63-184">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask>  
  
  

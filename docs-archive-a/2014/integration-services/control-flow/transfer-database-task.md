---
title: データベース転送タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.f1
helpviewer_keywords:
- Transfer Database task [Integration Services]
ms.assetid: b9a2e460-cdbc-458f-8df8-06b8b2de3d67
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85123eaff3e274bb4a96908ea99aef02c328ba23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631178"
---
# <a name="transfer-database-task"></a><span data-ttu-id="939d1-102">データベース転送タスク</span><span class="sxs-lookup"><span data-stu-id="939d1-102">Transfer Database Task</span></span>
  <span data-ttu-id="939d1-103">データベース転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つのインスタンスの間で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを転送します。</span><span class="sxs-lookup"><span data-stu-id="939d1-103">The Transfer Database task transfers a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="939d1-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトをコピーして転送するだけの他のタスクに対し、データベース転送タスクでは、データベースをコピーまたは移動できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-104">In contrast to the other tasks that only transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects by copying them, the Transfer Database task can either copy or move a database.</span></span> <span data-ttu-id="939d1-105">このタスクを使用して、同じサーバー内でデータベースをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="939d1-105">This task can also be used to copy a database within the same server.</span></span>  
  
## <a name="offline-and-online-modes"></a><span data-ttu-id="939d1-106">オフライン モードとオンライン モード</span><span class="sxs-lookup"><span data-stu-id="939d1-106">Offline and Online Modes</span></span>  
 <span data-ttu-id="939d1-107">データベースは、オンライン モードまたはオフライン モードで転送できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-107">The database can be transferred by using online or offline mode.</span></span> <span data-ttu-id="939d1-108">オンライン モードでは、データベースがアタッチされたまま、SQL 管理オブジェクト (SMO) を使用して転送され、データベース オブジェクトがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="939d1-108">When you use online mode, the database remains attached and it is transferred by using SQL Management Object (SMO) to copy the database objects.</span></span> <span data-ttu-id="939d1-109">オフライン モードでは、データベースがデタッチされた後、データベース ファイルがコピーまたは移動されます。転送が正常に完了した後、データベースが転送先にアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="939d1-109">When you use offline mode, the database is detached, the database files are copied or moved, and the database is attached at the destination after the transfer finishes successfully.</span></span> <span data-ttu-id="939d1-110">データベースのコピーの場合、コピーが正常に完了するとデータベースは転送元に再びアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="939d1-110">If the database is copied, it is automatically reattached at the source if the copy is successful.</span></span> <span data-ttu-id="939d1-111">オフライン モードでは、データベースは短時間にコピーされますが、転送が行われている間はデータベースを利用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="939d1-111">In offline mode, the database is copied more quickly, but the database is unavailable to users during the transfer.</span></span>  
  
 <span data-ttu-id="939d1-112">オフライン モードを使用する場合は、転送元サーバーと転送先サーバー上でデータベース ファイルを格納するネットワーク ファイル共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-112">Offline mode requires that you specify the network file shares on the source and destination servers that contain the database files.</span></span> <span data-ttu-id="939d1-113">このフォルダーが共有されていてユーザーがフォルダーにアクセスできる場合、 \\\computername\Program Files\myfolder\\という構文を使用してネットワーク共有を参照できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-113">If the folder is shared and can be accessed by the user, you can reference the network share using the syntax \\\computername\Program Files\myfolder\\.</span></span> <span data-ttu-id="939d1-114">それ以外の場合は、 \\\computername\c$\Program Files\myfolder\\という構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-114">Otherwise, you must use the syntax \\\computername\c$\Program Files\myfolder\\.</span></span> <span data-ttu-id="939d1-115">後者の構文を使用するには、転送元と転送先のネットワーク共有に対する書き込みアクセスがユーザーに許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-115">To use the latter syntax, the user must have write access to the source and destination network shares.</span></span>  
  
## <a name="transfer-of-databases-between-versions-of-sql-server"></a><span data-ttu-id="939d1-116">SQL Server のバージョン間でのデータベースの転送</span><span class="sxs-lookup"><span data-stu-id="939d1-116">Transfer of Databases Between Versions of SQL Server</span></span>  
 <span data-ttu-id="939d1-117">データベース転送タスクは、異なるバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間でデータベースを転送できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-117">The Transfer Database task can transfer a database between instances of different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span>  
  
## <a name="events"></a><span data-ttu-id="939d1-118">events</span><span class="sxs-lookup"><span data-stu-id="939d1-118">Events</span></span>  
 <span data-ttu-id="939d1-119">データベース転送タスクでは、エラー メッセージ転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-119">The Transfer Database task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="939d1-120">実行値</span><span class="sxs-lookup"><span data-stu-id="939d1-120">Execution Value</span></span>  
 <span data-ttu-id="939d1-121">タスクの `ExecutionValue` プロパティで定義される実行値は、値 1 を返します。これは、他の転送タスクとは異なり、データベース転送タスクでは 1 つのデータベースしか転送できないためです。</span><span class="sxs-lookup"><span data-stu-id="939d1-121">The execution value, defined in the `ExecutionValue` property of the task, returns the value 1, because in contrast to other transfer tasks, the Transfer Database task can transfer only one database.</span></span>  
  
 <span data-ttu-id="939d1-122">データベース転送タスクの `ExecValueVariable` プロパティにユーザー定義変数を割り当てると、エラー メッセージ転送に関する情報をパッケージ内の他のオブジェクトで利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="939d1-122">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Database task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="939d1-123">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="939d1-123">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="939d1-124">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="939d1-124">Log Entries</span></span>  
 <span data-ttu-id="939d1-125">データベース転送タスクには、次のカスタム ログ エントリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="939d1-125">The Transfer Database task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="939d1-126">SourceSQLServer: このログ エントリは、転送元サーバーの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="939d1-126">SourceSQLServer    This log entry lists the name of the source server.</span></span>  
  
-   <span data-ttu-id="939d1-127">DestSQLServer: このログ エントリは、転送先サーバーの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="939d1-127">DestSQLServer    This log entry lists the name of the destination server.</span></span>  
  
-   <span data-ttu-id="939d1-128">SourceDB: このログ エントリは、転送されたデータベースの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="939d1-128">SourceDB    This log entry lists the name of the database that is transferred.</span></span>  
  
 <span data-ttu-id="939d1-129">さらに、転送先データベースが上書きされたときに、`OnInformation` イベントのログ エントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="939d1-129">In addition, a log entry for the `OnInformation` event is written when the destination database is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="939d1-130">セキュリティとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="939d1-130">Security and Permissions</span></span>  
 <span data-ttu-id="939d1-131">オフライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが sysadmin サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-131">To transfer a database using offline mode, the user who runs the package must be a member of the sysadmin server role.</span></span>  
  
 <span data-ttu-id="939d1-132">オンライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが sysadmin サーバー ロールのメンバーであるか、または選択されたデータベースのデータベース所有者 (dbo) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-132">To transfer a database using online mode, the user who runs the package must be a member of the sysadmin server role or the database owner (dbo) of the selected database.</span></span>  
  
## <a name="configuration-of-the-transfer-database-task"></a><span data-ttu-id="939d1-133">データベース転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="939d1-133">Configuration of the Transfer Database Task</span></span>  
 <span data-ttu-id="939d1-134">データベースの転送が失敗した場合に転送元データベースへの再アタッチを試行するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-134">You can specify whether the task tries to reattach the source database if the database transfer fails.</span></span>  
  
 <span data-ttu-id="939d1-135">さらに、データベース転送タスクでは、転送先に同じ名前のデータベースが存在する場合にそのデータベースを上書きするように構成できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-135">The Transfer Database task can also be configured to permit overwriting a destination database that has the same name, replacing the destination database.</span></span>  
  
 <span data-ttu-id="939d1-136">転送プロセスの一部として、転送元データベースの名前を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="939d1-136">The source database can also be renamed as part of the transfer process.</span></span> <span data-ttu-id="939d1-137">転送先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに同じ名前のデータベースが存在する場合にデータベースを転送するには、転送元データベースの名前を変更することでデータベースを転送できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-137">If you want to transfer a database to a destination instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that already contains a database that has the same name, renaming the source database allows the database to be transferred.</span></span> <span data-ttu-id="939d1-138">ただし、データベース ファイルの名前も異なっている必要があります。同じ名前のデータベース ファイルが転送先に既に存在すると、タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="939d1-138">However, the database file names must also be different; if database files that have the same names already exist at the destination, the task fails.</span></span>  
  
 <span data-ttu-id="939d1-139">データベースをコピーする場合、データベースのサイズは、コピー先サーバーの **model** データベースのサイズより小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="939d1-139">When you copy a database, the database cannot be smaller than the size of the **model** database on the destination server.</span></span> <span data-ttu-id="939d1-140">コピーするデータベースのサイズを大きくするか、 **model**データベースのサイズを小さくできます。</span><span class="sxs-lookup"><span data-stu-id="939d1-140">You can either increase the size of the database to copy, or reduce the size of **model**.</span></span>  
  
 <span data-ttu-id="939d1-141">実行時、データベース転送タスクは、1 つまたは 2 つの SMO 接続マネージャーを使用して、転送元サーバーと転送先サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="939d1-141">At run time, the Transfer Database task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="939d1-142">同じサーバー上にデータベースのコピーを作成する場合は、SMO 接続マネージャーが 1 つだけ必要です。</span><span class="sxs-lookup"><span data-stu-id="939d1-142">When you create a copy of a database on the same server, only one SMO connection manager is required.</span></span> <span data-ttu-id="939d1-143">これらの SMO 接続マネージャーはデータベース転送タスクとは別に構成され、データベース転送タスクで参照されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-143">The SMO connection managers are configured separately from the Transfer Database task, and then are referenced in the Transfer Database task.</span></span> <span data-ttu-id="939d1-144">SMO 接続マネージャーは、サーバーと、タスクがこのサーバーにアクセスするときに使用する認証モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="939d1-144">The SMO connection managers specify the server and the authentication mode to use when the task accesses the server.</span></span> <span data-ttu-id="939d1-145">詳細については、「 [SMO 接続マネージャー](../connection-manager/smo-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="939d1-145">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="939d1-146">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="939d1-146">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="939d1-147">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="939d1-147">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="939d1-148">[[データベース転送タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="939d1-148">[Transfer Database Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="939d1-149">[データベース転送タスク エディター ([データベース] ページ)](../transfer-database-task-editor-databases-page.md)</span><span class="sxs-lookup"><span data-stu-id="939d1-149">[Transfer Database Task Editor &#40;Databases Page&#41;](../transfer-database-task-editor-databases-page.md)</span></span>  
  
-   <span data-ttu-id="939d1-150">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="939d1-150">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="939d1-151">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="939d1-151">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="939d1-152">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="939d1-152">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-database-task"></a><span data-ttu-id="939d1-153">プログラムによるデータベース転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="939d1-153">Programmatic Configuration of the Transfer Database Task</span></span>  
 <span data-ttu-id="939d1-154">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="939d1-154">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferDatabaseTask.TransferDatabaseTask>  
  
  

---
title: データ コレクターのセキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- security [data collector]
- data collector [SQL Server], security
ms.assetid: e75d6975-641e-440a-a642-cb39a583359a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c89f1658f6ae1b5bd79de96f20222b0b19529df2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633166"
---
# <a name="data-collector-security"></a><span data-ttu-id="9de84-102">データ コレクターのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="9de84-102">Data Collector Security</span></span>
  <span data-ttu-id="9de84-103">データ コレクターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって実装されるロールベースのセキュリティ モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9de84-103">The data collector uses the role-based security model implemented by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="9de84-104">このモデルを使用すると、データベース管理者は、データ コレクターのさまざまなタスクをそのタスクの実行に必要な権限だけがあるセキュリティ コンテキスト内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9de84-104">This model lets the database administrator run the various data collector tasks in a security context that has only the permissions required to perform that task.</span></span> <span data-ttu-id="9de84-105">この方法は、ストアド プロシージャかビューを使用しないとアクセスできない内部テーブルに関係する操作に対しても使用されます。</span><span class="sxs-lookup"><span data-stu-id="9de84-105">This approach is also used for operations involving internal tables, which can only be accessed by using a stored procedure or view.</span></span> <span data-ttu-id="9de84-106">内部テーブルに対する権限は与えられず、</span><span class="sxs-lookup"><span data-stu-id="9de84-106">No permissions are granted to internal tables.</span></span> <span data-ttu-id="9de84-107">テーブルへのアクセスに使用されるストアド プロシージャやビューのユーザーに対して権限がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="9de84-107">Instead, permissions are checked on the user of the stored procedure or view that is used to access a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9de84-108">このセキュリティ モデルのもう 1 つの重要な側面は、同心構造権限です。</span><span class="sxs-lookup"><span data-stu-id="9de84-108">Another key aspect of this security model is concentric permissions.</span></span> <span data-ttu-id="9de84-109">同心構造権限では、オブジェクト (警告、オペレーター、ジョブ、スケジュール、プロキシなど) に対して、高いレベルの特権を持つロールは、低いレベルの特権を持つロールの権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="9de84-109">Under concentric permissions, more privileged roles inherit the permissions of less privileged roles on objects (including alerts, operators, jobs, schedules, and proxies).</span></span> <span data-ttu-id="9de84-110">詳しくは、「 [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9de84-110">For more information, see [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="9de84-111">ここでは、データ コレクションの全般的なセキュリティと、ユーザーがデータ コレクターを構成および使用したり、管理データ ウェアハウスに関連するタスクを実行したりするために必要なロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9de84-111">The following sections describe data collection security in general, as well as the roles you must grant to users so they can configure and use the data collector, and carry out tasks associated with the management data warehouse.</span></span>  
  
## <a name="general-security"></a><span data-ttu-id="9de84-112">全般的なセキュリティ</span><span class="sxs-lookup"><span data-stu-id="9de84-112">General Security</span></span>  
 <span data-ttu-id="9de84-113">データ コレクターは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の文書化されている標準に従ってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9de84-113">The data collector is installed according to the documented standards specified for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
### <a name="network-security"></a><span data-ttu-id="9de84-114">ネットワークのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="9de84-114">Network Security</span></span>  
 <span data-ttu-id="9de84-115">対象のインスタンス、構成サーバーに関連付けられているリレーショナル インスタンス、実行中のコレクション セット、および管理データ ウェアハウスをホストするサーバーの間で、秘密情報がやり取りされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-115">Sensitive information can be passed between target instances, the relational instance associated with the configuration server, the collection sets that are running, and the server that hosts the management data warehouse.</span></span>  
  
 <span data-ttu-id="9de84-116">ネットワークで送信されるデータを保護するために、標準のセキュリティ メカニズム ( [!INCLUDE[tsql](../../includes/tsql-md.md)]のプロトコル暗号化など) が実装されています。</span><span class="sxs-lookup"><span data-stu-id="9de84-116">To protect any data that is transferred over a network, the standard security mechanisms are implemented, such as protocol encryption for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-data-collector"></a><span data-ttu-id="9de84-117">データ コレクターの構成および使用のための権限</span><span class="sxs-lookup"><span data-stu-id="9de84-117">Permissions for Configuring and Using the Data Collector</span></span>  
 <span data-ttu-id="9de84-118">タスクによっては、ユーザーが、データ コレクターのために用意されている 1 つ以上の固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-118">Depending on the task, users must be members of one or more of the fixed database roles provided for the data collector.</span></span> <span data-ttu-id="9de84-119">特権レベルの高いロールから順に、次に示します。</span><span class="sxs-lookup"><span data-stu-id="9de84-119">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   `dc_admin`  
  
-   <span data-ttu-id="9de84-120">**dc_operator**</span><span class="sxs-lookup"><span data-stu-id="9de84-120">**dc_operator**</span></span>  
  
-   <span data-ttu-id="9de84-121">**dc_proxy**</span><span class="sxs-lookup"><span data-stu-id="9de84-121">**dc_proxy**</span></span>  
  
 <span data-ttu-id="9de84-122">上記のロールは、msdb データベースに格納されています。</span><span class="sxs-lookup"><span data-stu-id="9de84-122">These roles are stored in the msdb database.</span></span> <span data-ttu-id="9de84-123">既定では、これらのデータベース ロールのメンバーであるユーザーはいません。</span><span class="sxs-lookup"><span data-stu-id="9de84-123">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="9de84-124">これらのロールのユーザー メンバーシップは、明示的に許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-124">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="9de84-125">固定サーバーロールのメンバーであるユーザーには、 `sysadmin` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントオブジェクトとデータコレクタービューへのフルアクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-125">Users who are members of the `sysadmin` fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent objects and data collector views.</span></span> <span data-ttu-id="9de84-126">しかし、これらのユーザーも、データ コレクターのロールに明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-126">However, they need to be explicitly added to data collector roles.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9de84-127">db_ssisadmin ロールおよび dc_admin ロールのメンバーは、特権を sysadmin に昇格できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-127">Members of the db_ssisadmin role and the dc_admin role may be able to elevate their privileges to sysadmin.</span></span> <span data-ttu-id="9de84-128">このような特権の昇格が発生するのは、それらのロールが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを変更でき、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エージェントの sysadmin セキュリティ コンテキストを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="9de84-128">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the sysadmin security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="9de84-129">メンテナンス プラン、データ コレクション セット、およびその他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行時にこの特権の昇格を防ぐには、特権が制限されたプロキシ アカウントを使用するようにパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを構成するか、db_ssisadmin ロールおよび dc_admin ロールには sysadmin メンバーのみを追加するようにします。</span><span class="sxs-lookup"><span data-stu-id="9de84-129">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add sysadmin members to the db_ssisadmin and dc_admin roles.</span></span>  
  
### <a name="dc_admin-role"></a><span data-ttu-id="9de84-130">dc_admin ロール</span><span class="sxs-lookup"><span data-stu-id="9de84-130">dc_admin Role</span></span>  
 <span data-ttu-id="9de84-131">ロールに割り当てられたユーザーには、 `dc_admin` サーバーインスタンス上のデータコレクターの構成への完全な管理者アクセス権 (作成、読み取り、更新、および削除) が与えられます。</span><span class="sxs-lookup"><span data-stu-id="9de84-131">Users assigned to the `dc_admin` role have full administrator access (Create, Read, Update, and Delete) to the data collector configuration on a server instance.</span></span> <span data-ttu-id="9de84-132">このロールのメンバーが実行できる操作を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9de84-132">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="9de84-133">コレクター レベルのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="9de84-133">Set collector-level properties.</span></span>  
  
-   <span data-ttu-id="9de84-134">新しいコレクション セットの追加</span><span class="sxs-lookup"><span data-stu-id="9de84-134">Add new collection sets.</span></span>  
  
-   <span data-ttu-id="9de84-135">新しいコレクション型のインストール</span><span class="sxs-lookup"><span data-stu-id="9de84-135">Install new collection types.</span></span>  
  
-   <span data-ttu-id="9de84-136">**dc_operator** ロールに対して許可されているすべての操作の実行</span><span class="sxs-lookup"><span data-stu-id="9de84-136">Perform all the operations permitted to the **dc_operator** role.</span></span>  
  
 <span data-ttu-id="9de84-137">ロールは、 `dc_admin` 次のロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="9de84-137">The `dc_admin` role is a member of the following roles:</span></span>  
  
-   <span data-ttu-id="9de84-138">**SQLAgentUserRole**。</span><span class="sxs-lookup"><span data-stu-id="9de84-138">**SQLAgentUserRole**.</span></span> <span data-ttu-id="9de84-139">スケジュールを作成したりジョブを実行したりするために必要です。</span><span class="sxs-lookup"><span data-stu-id="9de84-139">This role is required to create schedules and run jobs.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9de84-140">データコレクター用に作成されたプロキシは、にアクセスを許可 `dc_admin` して、プロキシを必要とする任意のジョブステップでそれらを作成して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-140">Proxies created for the data collector must grant access to `dc_admin` to create them and use them in any job steps that require a proxy.</span></span>  
  
-   <span data-ttu-id="9de84-141">**dc_operator**。</span><span class="sxs-lookup"><span data-stu-id="9de84-141">**dc_operator**.</span></span> <span data-ttu-id="9de84-142">のメンバーは `dc_admin` 、 **dc_operator**に与えられた権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="9de84-142">Members of `dc_admin` inherit the permissions given to **dc_operator**.</span></span>  
  
### <a name="dc_operator-role"></a><span data-ttu-id="9de84-143">dc_operator ロール</span><span class="sxs-lookup"><span data-stu-id="9de84-143">dc_operator Role</span></span>  
 <span data-ttu-id="9de84-144">**dc_operator** ロールのメンバーには、読み取りと更新のアクセス権が与えられます。</span><span class="sxs-lookup"><span data-stu-id="9de84-144">Members of the **dc_operator** role have Read and Update access.</span></span> <span data-ttu-id="9de84-145">このロールは、コレクション セットの実行と構成に関連する操作タスクをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9de84-145">This role supports operations tasks related to running and configuring collection sets.</span></span> <span data-ttu-id="9de84-146">このロールのメンバーが実行できる操作を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9de84-146">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="9de84-147">コレクション セットの開始または停止</span><span class="sxs-lookup"><span data-stu-id="9de84-147">Start or stop a collection set.</span></span>  
  
-   <span data-ttu-id="9de84-148">既存のコレクション セットの列挙</span><span class="sxs-lookup"><span data-stu-id="9de84-148">Enumerate existing collection sets.</span></span>  
  
-   <span data-ttu-id="9de84-149">コレクション セットに関連付けられている詳細情報 (コレクション アイテムや収集頻度など) の表示</span><span class="sxs-lookup"><span data-stu-id="9de84-149">View the detailed information (for example, collection items, and collection frequency) associated with a collection set.</span></span>  
  
-   <span data-ttu-id="9de84-150">既存のコレクション セットのアップロード頻度の変更</span><span class="sxs-lookup"><span data-stu-id="9de84-150">Change the upload frequency for existing collection sets.</span></span>  
  
-   <span data-ttu-id="9de84-151">既存のコレクション セットに含まれるコレクション アイテムの収集頻度の変更</span><span class="sxs-lookup"><span data-stu-id="9de84-151">Change the collection frequency for collection items that are part of an existing collection set.</span></span>  
  
 <span data-ttu-id="9de84-152">**dc_operator** ロールは、データ コレクター パッケージを列挙して表示するために必要な次のロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="9de84-152">The **dc_operator** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="9de84-153">**db_ssisltduser**</span><span class="sxs-lookup"><span data-stu-id="9de84-153">**db_ssisltduser**</span></span>  
  
-   <span data-ttu-id="9de84-154">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="9de84-154">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="9de84-155">詳細については、「[Integration Services のロール &#40;SSIS サービス&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9de84-155">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
### <a name="dc_proxy-role"></a><span data-ttu-id="9de84-156">dc_proxy ロール</span><span class="sxs-lookup"><span data-stu-id="9de84-156">dc_proxy Role</span></span>  
 <span data-ttu-id="9de84-157">**dc_proxy** ロールのメンバーには、データ コレクターのコレクション セットとコレクター レベルのプロパティへの読み取りアクセス権が与えられます。</span><span class="sxs-lookup"><span data-stu-id="9de84-157">Members of the **dc_proxy** role have Read access to data collector collection sets and collector-level properties.</span></span> <span data-ttu-id="9de84-158">自身が所有するジョブを実行したり、既存のプロキシ アカウントとして実行するジョブ ステップを作成したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9de84-158">Members of this role can also execute jobs that they own and create job steps that run as an existing proxy account.</span></span>  
  
 <span data-ttu-id="9de84-159">このロールのメンバーが実行できる操作を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9de84-159">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="9de84-160">コレクション セットの構成情報 (コレクション アイテムの入力パラメーターや収集頻度など) の表示</span><span class="sxs-lookup"><span data-stu-id="9de84-160">View collection set configuration information (for example, input parameters for collection items, and the collection frequency for these items).</span></span>  
  
-   <span data-ttu-id="9de84-161">署名されたストアド プロシージャしかアクセスできない暗号化された内部情報 (データのアップロードに使用されるデータ ウェアハウスの接続情報など) の取得</span><span class="sxs-lookup"><span data-stu-id="9de84-161">Obtain internal encrypted information that can only be accessed by a signed stored procedure (for example, data warehouse connection information used for data uploads).</span></span>  
  
-   <span data-ttu-id="9de84-162">コレクション セットの実行時イベントのログ記録</span><span class="sxs-lookup"><span data-stu-id="9de84-162">Log collection-set run-time events.</span></span>  
  
 <span data-ttu-id="9de84-163">**dc_proxy** ロールは、データ コレクター パッケージを列挙して表示するために必要な次のロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="9de84-163">The **dc_proxy** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="9de84-164">**db_ssisltduser**。</span><span class="sxs-lookup"><span data-stu-id="9de84-164">**db_ssisltduser**.</span></span>  
  
-   <span data-ttu-id="9de84-165">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="9de84-165">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="9de84-166">詳細については、「[Integration Services のロール &#40;SSIS サービス&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9de84-166">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-management-data-warehouse"></a><span data-ttu-id="9de84-167">管理データ ウェアハウスの構成および使用のための権限</span><span class="sxs-lookup"><span data-stu-id="9de84-167">Permissions for Configuring and Using the Management Data Warehouse</span></span>  
 <span data-ttu-id="9de84-168">タスクによっては、ユーザーが、管理データ ウェアハウスへのアクセスのために用意されている 1 つ以上の固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-168">Depending on the task, users must be members of one or more of the fixed database roles provided for accessing the management data warehouse.</span></span> <span data-ttu-id="9de84-169">特権レベルの高いロールから順に、次に示します。</span><span class="sxs-lookup"><span data-stu-id="9de84-169">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   <span data-ttu-id="9de84-170">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="9de84-170">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="9de84-171">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="9de84-171">**mdw_writer**</span></span>  
  
-   <span data-ttu-id="9de84-172">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="9de84-172">**mdw_reader**</span></span>  
  
 <span data-ttu-id="9de84-173">上記のロールは、msdb データベースに格納されています。</span><span class="sxs-lookup"><span data-stu-id="9de84-173">These roles are stored in the msdb database.</span></span> <span data-ttu-id="9de84-174">既定では、これらのデータベース ロールのメンバーであるユーザーはいません。</span><span class="sxs-lookup"><span data-stu-id="9de84-174">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="9de84-175">これらのロールのユーザー メンバーシップは、明示的に許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-175">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="9de84-176">固定サーバーロールのメンバーであるユーザーには、 `sysadmin` データコレクタービューへのフルアクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-176">Users who are members of the `sysadmin` fixed server role have full access to data collector views.</span></span> <span data-ttu-id="9de84-177">しかし、その他の操作を実行するには、明示的にデータベース ロールに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-177">However, they need to be explicitly added to database roles to perform other operations.</span></span>  
  
### <a name="mdw_admin-role"></a><span data-ttu-id="9de84-178">mdw_admin ロール</span><span class="sxs-lookup"><span data-stu-id="9de84-178">mdw_admin Role</span></span>  
 <span data-ttu-id="9de84-179">**mdw_admin** ロールのメンバーには、管理データ ウェアハウスへの読み取り、書き込み、更新、および削除のアクセス権が与えられます。</span><span class="sxs-lookup"><span data-stu-id="9de84-179">Members of the **mdw_admin** role have Read, Write, Update, and Delete access to the management data warehouse.</span></span>  
  
 <span data-ttu-id="9de84-180">このロールのメンバーが実行できる操作を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9de84-180">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="9de84-181">管理データ ウェアハウスのスキーマを必要に応じて変更する (新しいコレクション型がインストールされたときに新しいテーブルを追加するなど)</span><span class="sxs-lookup"><span data-stu-id="9de84-181">Change the management data warehouse schema when required (for example, adding a new table when a new collection type is installed).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9de84-182">スキーマが変更されている場合、ユーザーは新しいコレクター型をインストールするためにロールのメンバーでもある必要があり `dc_admin` ます。この操作には、msdb のデータコレクターの構成を更新する権限が必要であるためです。</span><span class="sxs-lookup"><span data-stu-id="9de84-182">Where there is a schema change, the user must also be a member of the `dc_admin` role to install a new collector type, since this action requires permission to update the data collector configuration in msdb.</span></span>  
  
-   <span data-ttu-id="9de84-183">管理データ ウェアハウスのメンテナンス ジョブ (アーカイブやクリーンアップなど) を実行する</span><span class="sxs-lookup"><span data-stu-id="9de84-183">Run maintenance jobs on the management data warehouse, such as archive or cleanup.</span></span>  
  
### <a name="mdw_writer-role"></a><span data-ttu-id="9de84-184">mdw_writer ロール</span><span class="sxs-lookup"><span data-stu-id="9de84-184">mdw_writer Role</span></span>  
 <span data-ttu-id="9de84-185">**mdw_writer** ロールのメンバーは、管理データ ウェアハウスへのデータのアップロードや書き込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9de84-185">Members of the **mdw_writer** role can upload and write data to the management data warehouse.</span></span> <span data-ttu-id="9de84-186">管理データ ウェアハウスにデータを格納するデータ コレクターはすべてこのロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9de84-186">Any data collector that stores data in the management data warehouse has to be a member of this role.</span></span>  
  
### <a name="mdw_reader-role"></a><span data-ttu-id="9de84-187">mdw_reader ロール</span><span class="sxs-lookup"><span data-stu-id="9de84-187">mdw_reader Role</span></span>  
 <span data-ttu-id="9de84-188">**mdw_reader** ロールのメンバーには、管理データ ウェアハウスへの読み取りアクセス権が与えられます。</span><span class="sxs-lookup"><span data-stu-id="9de84-188">Members of the **mdw_reader** role have Read access to the management data warehouse.</span></span> <span data-ttu-id="9de84-189">このロールの目的は、履歴データへのアクセスを提供してトラブルシューティングをサポートすることであるため、このロールのメンバーは、管理データ ウェアハウスのスキーマのその他の要素を表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="9de84-189">Because the purpose of this role is to support troubleshooting by providing access to historical data, members of this role cannot view other elements of the management data warehouse schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de84-190">参照</span><span class="sxs-lookup"><span data-stu-id="9de84-190">See Also</span></span>  
 [<span data-ttu-id="9de84-191">SQL Server エージェントのセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="9de84-191">Implement SQL Server Agent Security</span></span>](../../ssms/agent/implement-sql-server-agent-security.md)  
  
  

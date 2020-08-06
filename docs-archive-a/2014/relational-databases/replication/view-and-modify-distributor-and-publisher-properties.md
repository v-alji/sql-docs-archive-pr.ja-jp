---
title: ディストリビューターとパブリッシャーのプロパティの表示および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 571f6f3a0d44f0fc87c67885249fca441776946d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634377"
---
# <a name="view-and-modify-distributor-and-publisher-properties"></a><span data-ttu-id="1edf5-102">ディストリビューターとパブリッシャーのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="1edf5-102">View and Modify Distributor and Publisher Properties</span></span>
  <span data-ttu-id="1edf5-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、ディストリビューターとパブリッシャーのプロパティを表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-103">This topic describes how to view and modify Distributor and Publisher properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="1edf5-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1edf5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1edf5-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1edf5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1edf5-106">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="1edf5-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1edf5-107">Security</span><span class="sxs-lookup"><span data-stu-id="1edf5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1edf5-108">**ディストリビューターとパブリッシャーのプロパティを表示または変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="1edf5-108">**To view and modify Distributor and Publisher properties, using:**</span></span>  
  
     [<span data-ttu-id="1edf5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1edf5-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1edf5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1edf5-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1edf5-111">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="1edf5-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1edf5-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="1edf5-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1edf5-113">推奨事項</span><span class="sxs-lookup"><span data-stu-id="1edf5-113">Recommendations</span></span>  
  
-   <span data-ttu-id="1edf5-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンのパブリッシャーでは、固定サーバー ロール **sysadmin** のユーザーが、 **[サブスクライバー]** ページでサブスクライバーを登録できます。</span><span class="sxs-lookup"><span data-stu-id="1edf5-114">For Publishers running versions prior to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user in the **sysadmin** fixed server role can register Subscribers on the **Subscribers** page.</span></span> <span data-ttu-id="1edf5-115">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降では、サブスクライバーをレプリケーションに明示的に登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1edf5-115">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], it is no longer necessary to explicitly register Subscribers for replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1edf5-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1edf5-116">Security</span></span>  
 <span data-ttu-id="1edf5-117">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-117">When possible, prompt users to enter security credentials at runtime.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1edf5-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1edf5-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="1edf5-119">ディストリビューターのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-119">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="1edf5-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-120">Connect to the Distributor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="1edf5-121">**[レプリケーション]** フォルダーを右クリックし、 **[ディストリビューターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-121">Right-click the **Replication** folder, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="1edf5-122">**[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスで、プロパティを表示および変更します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-122">View and modify properties in the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
    -   <span data-ttu-id="1edf5-123">ディストリビューション データベースのプロパティを表示および変更するには、ダイアログ ボックスの **[全般]** ページにあるデータベースのプロパティ ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-123">To view and modify properties for a distribution database, click the properties button (**...**) for the database on the **General** page of thedialog box.</span></span>  
  
    -   <span data-ttu-id="1edf5-124">ディストリビューターと関連付けられたパブリッシャーのプロパティを表示および変更するには、ダイアログ ボックスの **[パブリッシャー]** ページでパブリッシャーのプロパティ ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-124">To view and modify Publisher properties associated with the Distributor, click the properties button (**...**) for the Publisher on the **Publishers** page of the dialog box.</span></span>  
  
    -   <span data-ttu-id="1edf5-125">レプリケーション エージェントのプロファイルにアクセスするには、ダイアログ ボックスの **[全般]** ページの **[プロファイルの既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-125">To access profiles for replication agents, click the **Profile Defaults** button on the **General** page of the dialog box.</span></span> <span data-ttu-id="1edf5-126">詳しくは、「 [レプリケーション エージェント プロファイル](agents/replication-agent-profiles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1edf5-126">For more information, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  
  
    -   <span data-ttu-id="1edf5-127">パブリッシャーで管理用のストアド プロシージャを実行したり、ディストリビューターで情報を更新したりするときに使用するアカウントのパスワードを変更するには、ダイアログ ボックスの **[パブリッシャー]** ページで **[パスワード]** ボックスおよび **[パスワードの確認入力]** ボックスに新しいパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-127">To change the password for the account used when administrative stored procedures execute at the Publisher and update information at the Distributor, enter a new password in the **Password** and **Confirm password** boxes on the **Publishers** page of the dialog box.</span></span> <span data-ttu-id="1edf5-128">詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1edf5-128">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
4.  <span data-ttu-id="1edf5-129">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-129">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="1edf5-130">パブリッシャーのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-130">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="1edf5-131">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-131">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="1edf5-132">**[レプリケーション]** フォルダーを右クリックし、 **[パブリッシャーのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-132">Right-click the **Replication** folder, and then click **Publisher Properties**.</span></span>  
  
3.  <span data-ttu-id="1edf5-133">[\*\*パブリッシャーのプロパティ- \< Publisher > \*\* ] ダイアログボックスでプロパティを表示および変更します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-133">View and modify properties in the **Publisher Properties - \< Publisher >** dialog box.</span></span>  
  
    -   <span data-ttu-id="1edf5-134">固定サーバー ロール **sysadmin** のユーザーは、 **[パブリケーション データベース]** のページでデータベースのレプリケーションを有効化できます。</span><span class="sxs-lookup"><span data-stu-id="1edf5-134">A user in the **sysadmin** fixed server role can enable databases for replication on the **Publication Databases** page.</span></span> <span data-ttu-id="1edf5-135">データベースを有効化しても、そのデータベースがパブリッシュされるわけではありません。固定データベース ロール **db_owner** の任意のユーザーが、1 つ以上のパブリケーションをデータベースに作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1edf5-135">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications in the database.</span></span>  
  
4.  <span data-ttu-id="1edf5-136">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-136">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1edf5-137">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1edf5-137">Using Transact-SQL</span></span>  
 <span data-ttu-id="1edf5-138">パブリッシャーとディストリビューターのプロパティは、プログラムからレプリケーション ストアド プロシージャを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="1edf5-138">Publisher and Distributor properties can be viewed programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a><span data-ttu-id="1edf5-139">ディストリビューターとディストリビューション データベースのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-139">To view Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="1edf5-140">[sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) を実行すると、ディストリビューター、ディストリビューション データベース、作業ディレクトリに関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="1edf5-140">Execute [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) to return information about the Distributor, distribution database, and working directory.</span></span>  
  
2.  <span data-ttu-id="1edf5-141">[sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) を実行すると、指定されたディストリビューション データベースのプロパティが返されます。</span><span class="sxs-lookup"><span data-stu-id="1edf5-141">Execute [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) to return properties of a specified distribution database.</span></span>  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a><span data-ttu-id="1edf5-142">ディストリビューターとディストリビューション データベースのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-142">To change Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="1edf5-143">ディストリビューターのプロパティを変更するには、ディストリビューターで [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-143">At the Distributor, execute [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) to modify Distributor properties.</span></span>  
  
2.  <span data-ttu-id="1edf5-144">ディストリビューション データベースのプロパティを変更するには、ディストリビューターで [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-144">At the Distributor, execute [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) to modify distribution database properties.</span></span>  
  
3.  <span data-ttu-id="1edf5-145">ディストリビューターのパスワードを変更するには、ディストリビューターで [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-145">At the Distributor, execute [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) to change the Distributor password.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1edf5-146">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-146">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="1edf5-147">資格情報をスクリプト ファイルに含める必要がある場合は、不正なアクセスが行われないようにファイルをセキュリティで保護してください。</span><span class="sxs-lookup"><span data-stu-id="1edf5-147">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
4.  <span data-ttu-id="1edf5-148">ディストリビューターを使用しているパブリッシャーのプロパティを変更するには、ディストリビューターで [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-148">At the Distributor, execute [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) to change the properties of a Publisher using the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1edf5-149">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1edf5-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="1edf5-150">次の例では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトによってディストリビューターおよびディストリビューション データベースに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-150">The following example [!INCLUDE[tsql](../../includes/tsql-md.md)] script returns information about the Distributor and distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_helpdistributor](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributor)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributiondb)]  
  
 <span data-ttu-id="1edf5-151">次の例では、ディストリビューターの保有期間、ディストリビューターへの接続時に使用されるパスワード、およびディストリビューターが各種レプリケーション エージェントの状態を確認する間隔 (ハートビート間隔) を変更します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-151">This example changes retention periods for the Distributor, the password used when connecting to the Distributor, and the interval at which the Distributor checks the status of various replication agents (also known as the heartbeat interval).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1edf5-152">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-152">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="1edf5-153">資格情報をスクリプト ファイルに含める必要がある場合は、不正なアクセスが行われないようにファイルをセキュリティで保護してください。</span><span class="sxs-lookup"><span data-stu-id="1edf5-153">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_property)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributiondb)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_password)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="1edf5-154">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="1edf5-154">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="1edf5-155">ディストリビューターのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-155">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="1edf5-156"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1edf5-157"><xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="1edf5-158">手順 1 の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-158">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="1edf5-159">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> プロパティをチェックして、現在接続されているサーバーがディストリビューターであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-159">(Optional) Check the <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> property to verify that the currently connected server is a Distributor.</span></span>  
  
4.  <span data-ttu-id="1edf5-160"><xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> メソッドを呼び出して、サーバーからプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties from the server.</span></span>  
  
5.  <span data-ttu-id="1edf5-161">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> オブジェクトの設定可能なディストリビューター プロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-161">(Optional) To change properties, set a new value for one or more of the Distributor properties that can be set on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object.</span></span>  
  
6.  <span data-ttu-id="1edf5-162">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationServer> プロパティが `true` に設定されている場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出して変更内容をサーバーにコミットします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-162">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a><span data-ttu-id="1edf5-163">ディストリビューション データベースのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-163">To view and modify distribution database properties</span></span>  
  
1.  <span data-ttu-id="1edf5-164"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-164">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1edf5-165"><xref:Microsoft.SqlServer.Replication.DistributionDatabase> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> class.</span></span> <span data-ttu-id="1edf5-166">name プロパティを指定し、手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-166">Specify the name property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="1edf5-167"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、サーバーからプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-167">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties from the server.</span></span> <span data-ttu-id="1edf5-168">このメソッドから `false` が返された場合、指定した名前のデータベースはサーバー上に存在しません。</span><span class="sxs-lookup"><span data-stu-id="1edf5-168">If this method returns `false`, the database with the specified name does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="1edf5-169">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> の設定可能なプロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-169">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> properties that can be set.</span></span>  
  
5.  <span data-ttu-id="1edf5-170">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.DistributionDatabase> プロパティが `true` に設定されている場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出して変更内容をサーバーにコミットします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-170">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="1edf5-171">パブリッシャーのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-171">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="1edf5-172"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-172">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1edf5-173"><xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="1edf5-174"><xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> プロパティを指定し、手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-174">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="1edf5-175">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> の設定可能なプロパティに新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-175">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> properties that can be set.</span></span>  
  
4.  <span data-ttu-id="1edf5-176">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.DistributionPublisher> プロパティが `true` に設定されている場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出して変更内容をサーバーにコミットします。</span><span class="sxs-lookup"><span data-stu-id="1edf5-176">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="1edf5-177">パブリッシャーからディストリビューターへの管理接続に使用されているパスワードを変更するには</span><span class="sxs-lookup"><span data-stu-id="1edf5-177">To change the password for the administrative connection from the Publisher to the Distributor</span></span>  
  
1.  <span data-ttu-id="1edf5-178"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-178">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1edf5-179"><xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-179">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
3.  <span data-ttu-id="1edf5-180"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに、手順 1. の接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-180">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="1edf5-181"><xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-181">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
5.  <span data-ttu-id="1edf5-182"><xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="1edf5-183">新しいパスワード値を *password* パラメーターに渡します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-183">Pass the new password value for the *password* parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1edf5-184">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-184">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="1edf5-185">資格情報を保存する必要がある場合は、 [Windows .NET&#xA0;Framework に用意されている](https://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-185">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
6.  <span data-ttu-id="1edf5-186">(省略可) このディストリビューターを使用している各リモート パブリッシャーでパスワードを変更するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1edf5-186">(Optional) Perform the following steps to change the password at each remote Publisher that uses this Distributor:</span></span>  
  
    1.  <span data-ttu-id="1edf5-187"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
    2.  <span data-ttu-id="1edf5-188"><xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
    3.  <span data-ttu-id="1edf5-189"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに、手順 6a. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-189">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 6a.</span></span>  
  
    4.  <span data-ttu-id="1edf5-190"><xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
    5.  <span data-ttu-id="1edf5-191"><xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-191">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="1edf5-192">手順 5. の新しいパスワード値を *password* パラメーターに渡します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-192">Pass the new password value from Step 5 for the *password* parameter.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="1edf5-193">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="1edf5-193">Example (RMO)</span></span>  
 <span data-ttu-id="1edf5-194">次の例に、ディストリビューションのプロパティおよびディストリビューション データベースのプロパティを変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1edf5-194">This example shows how to change Distribution and distribution database properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1edf5-195">資格情報をコードに記述するのを避けるため、新しいディストリビューター パスワードは実行時に指定するようにしています。</span><span class="sxs-lookup"><span data-stu-id="1edf5-195">To avoid storing credentials in the code, the new Distributor password is supplied at runtime.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a><span data-ttu-id="1edf5-196">参照</span><span class="sxs-lookup"><span data-stu-id="1edf5-196">See Also</span></span>  
 <span data-ttu-id="1edf5-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1edf5-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="1edf5-198">[パブリッシングおよびディストリビューションの無効化](disable-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="1edf5-198">[Disable Publishing and Distribution](disable-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="1edf5-199">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="1edf5-199">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="1edf5-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1edf5-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="1edf5-201">[ディストリビューターおよびパブリッシャーの情報スクリプト](administration/distributor-and-publisher-information-script.md) </span><span class="sxs-lookup"><span data-stu-id="1edf5-201">[Distributor and Publisher Information Script](administration/distributor-and-publisher-information-script.md) </span></span>  
 <span data-ttu-id="1edf5-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1edf5-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="1edf5-203">レプリケーション モニターを使用して情報を表示し、タスクを実行する</span><span class="sxs-lookup"><span data-stu-id="1edf5-203">View Information and Perform Tasks using Replication Monitor</span></span>](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
  

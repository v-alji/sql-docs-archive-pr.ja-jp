---
title: SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- remote login errors [SQL Server]
- standalone computer names [SQL Server]
- names [SQL Server], standalone instances of SQL Server
- renaming standalone instances of SQL Server
- sysservers system table
- removing remote logins
- deleting remote logins
- dropping remote logins
ms.assetid: bbaf1445-b8a2-4ebf-babe-17d8cf20b037
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 079348921900a7cbf880027433280253df1a9e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740285"
---
# <a name="rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server"></a><span data-ttu-id="4ae10-102">SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更</span><span class="sxs-lookup"><span data-stu-id="4ae10-102">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>
  <span data-ttu-id="4ae10-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行するコンピューターの名前を変更した場合、変更後の名前は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時に認識されます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-103">When you change the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the new name is recognized during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span> <span data-ttu-id="4ae10-104">コンピューター名を再設定するためにセットアップを再度実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4ae10-104">You do not have to run Setup again to reset the computer name.</span></span> <span data-ttu-id="4ae10-105">代わりに次の手順を実行して、sys.servers に格納され、システム関数 @@SERVERNAME でレポートされるシステム メタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-105">Instead, use the following steps to update system metadata that is stored in sys.servers and reported by the system function @@SERVERNAME.</span></span> <span data-ttu-id="4ae10-106">@@SERVERNAME を使用するか、sys.servers からサーバー名のクエリを実行するリモート接続およびリモート アプリケーションのコンピューター名の変更を反映するには、システム メタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-106">Update system metadata to reflect computer name changes for remote connections and applications that use @@SERVERNAME, or that query the server name from sys.servers.</span></span>  
  
 <span data-ttu-id="4ae10-107">ここで示す手順を実行しても、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの名前を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4ae10-107">The following steps cannot be used to rename an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4ae10-108">変更できるのは、インスタンス名のうち、コンピューター名に対応する部分のみです。</span><span class="sxs-lookup"><span data-stu-id="4ae10-108">They can be used only to rename the part of the instance name that corresponds to the computer name.</span></span> <span data-ttu-id="4ae10-109">たとえば、Instance1 という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスをホストする MB1 というコンピューターを、MB2 のような別の名前に変更できます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-109">For example, you can change a computer named MB1 that hosts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named Instance1 to another name, such as MB2.</span></span> <span data-ttu-id="4ae10-110">ただし、名前のインスタンスの部分 (Instance1) は変更されません。</span><span class="sxs-lookup"><span data-stu-id="4ae10-110">However, the instance part of the name, Instance1, will remain unchanged.</span></span> <span data-ttu-id="4ae10-111">この例では、 \\\\*ComputerName*\\*InstanceName* が、 \\\MB1\Instance1 から \\\MB2\Instance1 に変更されます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-111">In this example, the \\\\*ComputerName*\\*InstanceName* would be changed from \\\MB1\Instance1 to \\\MB2\Instance1.</span></span>  
  
 <span data-ttu-id="4ae10-112">**Before you begin**</span><span class="sxs-lookup"><span data-stu-id="4ae10-112">**Before you begin**</span></span>  
  
 <span data-ttu-id="4ae10-113">名前変更のプロセスを開始する前に、次の情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-113">Before you begin the renaming process, review the following information:</span></span>  
  
-   <span data-ttu-id="4ae10-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターに含まれている場合、コンピューターの名前変更のプロセスは、スタンドアロン インスタンスをホストするコンピューターとは異なります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-114">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the computer renaming process differs from a computer that hosts a stand-alone instance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4ae10-115">レプリケーションでログ配布を使用する場合を除き、レプリケーションに関連するコンピューターの名前は変更できません。</span><span class="sxs-lookup"><span data-stu-id="4ae10-115">does not support renaming computers that are involved in replication, except when you use log shipping with replication.</span></span> <span data-ttu-id="4ae10-116">プライマリ コンピューターが完全に存在しなくなった場合は、ログ配布のセカンダリ コンピューターの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-116">The secondary computer in log shipping can be renamed if the primary computer is permanently lost.</span></span> <span data-ttu-id="4ae10-117">詳細については、[ログ配布とレプリケーション &#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae10-117">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4ae10-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を使用するように構成されたコンピューターの名前を変更すると、コンピューター名の変更後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を使用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-118">When you rename a computer that is configured to use [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might not be available after the computer name change.</span></span> <span data-ttu-id="4ae10-119">詳細については、「 [Server Web Service の名前の変更](../../reporting-services/report-server/rename-a-report-server-computer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae10-119">For more information, see [Rename a Report Server Computer](../../reporting-services/report-server/rename-a-report-server-computer.md).</span></span>  
  
-   <span data-ttu-id="4ae10-120">データベース ミラーリングを使用する構成のコンピューターの名前を変更するときは、名前変更操作の前にデータベース ミラーリングを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-120">When you rename a computer that is configured to use database mirroring, you must turn off database mirroring before the renaming operation.</span></span> <span data-ttu-id="4ae10-121">次に、新しいコンピューター名でデータベース ミラーリングを再確立します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-121">Then, re-establish database mirroring with the new computer name.</span></span> <span data-ttu-id="4ae10-122">データベース ミラーリングのメタデータは、新しいコンピューター名に自動的には更新されません。</span><span class="sxs-lookup"><span data-stu-id="4ae10-122">Metadata for database mirroring will not be updated automatically to reflect the new computer name.</span></span> <span data-ttu-id="4ae10-123">次の手順を実行してシステム メタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-123">Use the following steps to update system metadata.</span></span>  
  
-   <span data-ttu-id="4ae10-124">コンピューター名へのハードコード参照を使用する Windows グループをとおして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続できなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-124">Users who connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through a Windows group that uses a hard-coded reference to the computer name might not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4ae10-125">この状況は、名前を変更した場合に、Windows グループで変更前のコンピューター名が指定されていると発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-125">This can occur after the rename if the Windows group specifies the old computer name.</span></span> <span data-ttu-id="4ae10-126">このような Windows グループが名前変更の後でも [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続を確立できるようにするには、新しいコンピューター名を指定するように Windows グループを更新します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-126">To ensure that such Windows groups have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity following the renaming operation, update the Windows group to specify the new computer name.</span></span>  
  
 <span data-ttu-id="4ae10-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動した後、新しいコンピューター名を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続できます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-127">You can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the new computer name after you have restarted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4ae10-128">@@SERVERNAME がローカル サーバー インスタンスの更新後の名前を返すことを確認するには、シナリオに応じて次のプロシージャを手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-128">To ensure that @@SERVERNAME returns the updated name of the local server instance, you should manually run the following procedure that applies to your scenario.</span></span> <span data-ttu-id="4ae10-129">使用するプロシージャは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のインスタンスと名前付きインスタンスのどちらをホストするコンピューターを更新しているかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-129">The procedure you use depends on whether you are updating a computer that hosts a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-rename-a-computer-that-hosts-a-stand-alone-instance-of-ssnoversion"></a><span data-ttu-id="4ae10-130">スタンドアロン インスタンスをホストするコンピューターの名前を変更するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae10-130">To rename a computer that hosts a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="4ae10-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のインスタンスをホストする名前変更されたコンピューターの場合は、次のプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-131">For a renamed computer that hosts a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name>;  
    GO  
    sp_addserver <new_name>, local;  
    GO  
    ```  
  
     <span data-ttu-id="4ae10-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-132">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="4ae10-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の名前付きインスタンスをホストする名前変更されたコンピューターの場合は、次のプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-133">For a renamed computer that hosts a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name\instancename>;  
    GO  
    sp_addserver <new_name\instancename>, local;  
    GO  
    ```  
  
     <span data-ttu-id="4ae10-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-134">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="after-the-renaming-operation"></a><span data-ttu-id="4ae10-135">名前変更操作の後</span><span class="sxs-lookup"><span data-stu-id="4ae10-135">After the Renaming Operation</span></span>  
 <span data-ttu-id="4ae10-136">コンピューターの名前を変更した場合は、変更前のコンピューター名を使用している接続はすべて、変更後の名前で接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-136">After a computer has been renamed, any connections that used the old computer name must connect by using the new name.</span></span>  
  
#### <a name="to-verify-that-the-renaming-operation-has-completed-successfully"></a><span data-ttu-id="4ae10-137">名前変更操作が正常に完了したことを検証するには</span><span class="sxs-lookup"><span data-stu-id="4ae10-137">To verify that the renaming operation has completed successfully</span></span>  
  
-   <span data-ttu-id="4ae10-138">@@SERVERNAME または sys.servers で情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-138">Select information from either @@SERVERNAME or sys.servers.</span></span> <span data-ttu-id="4ae10-139">@@SERVERNAME 関数では新しい名前が返されます。sys.servers テーブルには新しい名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-139">The @@SERVERNAME function will return the new name, and the sys.servers table will show the new name.</span></span> <span data-ttu-id="4ae10-140">次は @@SERVERNAME の使用例です。</span><span class="sxs-lookup"><span data-stu-id="4ae10-140">The following example shows the use of @@SERVERNAME.</span></span>  
  
    ```  
    SELECT @@SERVERNAME AS 'Server Name';  
    ```  
  
## <a name="additional-considerations"></a><span data-ttu-id="4ae10-141">その他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="4ae10-141">Additional Considerations</span></span>  
 <span data-ttu-id="4ae10-142">**リモート ログイン** - コンピューターでリモート ログインを行っている場合に、 **sp_dropserver** を実行すると次のようなエラーが発生することがあります:</span><span class="sxs-lookup"><span data-stu-id="4ae10-142">**Remote Logins** - If the computer has any remote logins, running **sp_dropserver** might generate an error similar to the following:</span></span>  
  
 `Server: Msg 15190, Level 16, State 1, Procedure sp_dropserver, Line 44 There are still remote logins for the server 'SERVER1'.`  
  
 <span data-ttu-id="4ae10-143">このエラーを解決するには、このサーバーに対するリモート ログインを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-143">To resolve the error, you must drop remote logins for this server.</span></span>  
  
#### <a name="to-drop-remote-logins"></a><span data-ttu-id="4ae10-144">リモート ログインを削除するには</span><span class="sxs-lookup"><span data-stu-id="4ae10-144">To drop remote logins</span></span>  
  
-   <span data-ttu-id="4ae10-145">既定のインスタンスの場合は、次のプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-145">For a default instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name;  
    GO  
    ```  
  
-   <span data-ttu-id="4ae10-146">名前付きインスタンスの場合は、次のプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-146">For a named instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name\instancename;  
    GO  
    ```  
  
 <span data-ttu-id="4ae10-147">**リンク サーバー構成** - リンク サーバー構成はコンピューター名の変更操作の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-147">**Linked Server Configurations** - Linked server configurations will be affected by the computer renaming operation.</span></span> <span data-ttu-id="4ae10-148">`sp_addlinkedserver` または `sp_setnetname` を使用してコンピューターの名前参照を更新します。</span><span class="sxs-lookup"><span data-stu-id="4ae10-148">Use `sp_addlinkedserver` or `sp_setnetname` to update computer name references.</span></span> <span data-ttu-id="4ae10-149">詳細については、「[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)」または「[sp_setnetname &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae10-149">For more information, see the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) or [sp_setnetname &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql).</span></span>  
  
 <span data-ttu-id="4ae10-150">**クライアントのエイリアス** - 名前付きパイプを使用するクライアントのエイリアスはコンピューター名の変更操作の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="4ae10-150">**Client Alias Names** - Client aliases that use named pipes will be affected by the computer renaming operation.</span></span> <span data-ttu-id="4ae10-151">たとえば、SRVR1 に対するエイリアス "PROD_SRVR" が作成され、名前付きパイプのプロトコルが使用されている場合、パイプ名は `\\SRVR1\pipe\sql\query`のようになります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-151">For example, if an alias "PROD_SRVR" was created to point to SRVR1 and uses the named pipes protocol, the pipe name will look like `\\SRVR1\pipe\sql\query`.</span></span> <span data-ttu-id="4ae10-152">コンピューター名が変更された後は、名前付きパイプのパスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="4ae10-152">After the computer is renamed, the path of the named pipe will no longer be valid and.</span></span> <span data-ttu-id="4ae10-153">名前付きパイプの詳細については、「 [名前付きパイプを使用した有効な接続文字列の作成](https://go.microsoft.com/fwlink/?LinkId=111063)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae10-153">For more information about named pipes, see the [Creating a Valid Connection String Using Named Pipes](https://go.microsoft.com/fwlink/?LinkId=111063).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae10-154">参照</span><span class="sxs-lookup"><span data-stu-id="4ae10-154">See Also</span></span>  
 [<span data-ttu-id="4ae10-155">SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="4ae10-155">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  

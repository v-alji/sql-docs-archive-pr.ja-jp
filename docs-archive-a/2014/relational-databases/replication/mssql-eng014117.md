---
title: MSSQL_ENG014117 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014117 error
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4694aacc7d1f5ee31f4ff54d8cdd4256b48f713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630936"
---
# <a name="mssql_eng014117"></a><span data-ttu-id="6335c-102">MSSQL_ENG014117</span><span class="sxs-lookup"><span data-stu-id="6335c-102">MSSQL_ENG014117</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6335c-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="6335c-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6335c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6335c-104">Product Name</span></span>|<span data-ttu-id="6335c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6335c-105">SQL Server</span></span>|  
|<span data-ttu-id="6335c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6335c-106">Event ID</span></span>|<span data-ttu-id="6335c-107">14117</span><span class="sxs-lookup"><span data-stu-id="6335c-107">14117</span></span>|  
|<span data-ttu-id="6335c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6335c-108">Event Source</span></span>|<span data-ttu-id="6335c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6335c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6335c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6335c-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6335c-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6335c-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6335c-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6335c-112">Message Text</span></span>|<span data-ttu-id="6335c-113">'%s' はディストリビューション データベースとして構成されていません。</span><span class="sxs-lookup"><span data-stu-id="6335c-113">'%s' is not configured as a distribution database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6335c-114">説明</span><span class="sxs-lookup"><span data-stu-id="6335c-114">Explanation</span></span>  
 <span data-ttu-id="6335c-115">このエラーは、次のいずれかまたは両方に該当する場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6335c-115">This error can occur if one or both of the following are true:</span></span>  
  
-   <span data-ttu-id="6335c-116">指定したディストリビューション データベースのエントリが、 **msdb..MSdistributiondbs**に存在しない場合。</span><span class="sxs-lookup"><span data-stu-id="6335c-116">The entry for the specified distribution database is missing from **msdb..MSdistributiondbs**.</span></span>  
  
-   <span data-ttu-id="6335c-117">**master** データベース内にローカル サーバーのエントリがない場合、またはエントリは存在するが正しくない場合。</span><span class="sxs-lookup"><span data-stu-id="6335c-117">There is not an entry for the local server in the **master** database, or the entry that is there is incorrect.</span></span>  
  
     <span data-ttu-id="6335c-118">レプリケーションでは、コンピューター名とオプションのインスタンス名 (クラスター化されたインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仮想サーバー名とオプションのインスタンス名) を使用して、トポロジのすべてのサーバーを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6335c-118">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="6335c-119">レプリケーションが正しく機能するためには、トポロジの各サーバーに対して `SELECT @@SERVERNAME` によって返された値が、コンピューター名または仮想サーバー名と、オプションのインスタンス名で一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6335c-119">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
     <span data-ttu-id="6335c-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのいずれかを IP アドレスまたは完全修飾ドメイン名 (FQDN) で登録している場合、レプリケーションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6335c-120">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="6335c-121">レプリケーションの構成時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内に IP アドレスまたは FQDN で登録された [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスがあった場合、このエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6335c-121">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6335c-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6335c-122">User Action</span></span>  
 <span data-ttu-id="6335c-123">ディストリビューター インスタンスが正しく登録されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6335c-123">Verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="6335c-124">コンピューターのネットワーク名と SQL Server インスタンスの名前が異なる場合は、次のいずれかを実行してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-124">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="6335c-125">SQL Server インスタンス名を有効なネットワーク名として追加します。</span><span class="sxs-lookup"><span data-stu-id="6335c-125">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="6335c-126">代替ネットワーク名を設定する 1 つの方法は、その名前をローカル ホスト ファイルに追加することです。</span><span class="sxs-lookup"><span data-stu-id="6335c-126">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="6335c-127">ローカル ホスト ファイルは、既定では、WINDOWS\system32\drivers\etc または WINNT\system32\drivers\etc にあります。詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-127">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="6335c-128">たとえば、コンピューター名が comp1、そのコンピューターの IP アドレスが 10.193.17.129、インスタンス名が inst1/instname の場合、ホスト ファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="6335c-128">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="6335c-129">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="6335c-129">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="6335c-130">ディストリビューションを無効化し、インスタンスを登録して、ディストリビューションを再設定してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-130">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="6335c-131">@@SERVERNAME の値が、クラスター化されていないインスタンスに対して適切でない場合は、次の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-131">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="6335c-132">[sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) ストアド プロシージャを実行したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動し、@@SERVERNAME への変更を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6335c-132">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="6335c-133">@@SERVERNAME の値がクラスター化されたインスタンスに対して適切でない場合は、クラスター アドミニストレーターを使用して名前を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6335c-133">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="6335c-134">詳細については、「[Always On フェールオーバー クラスター インスタンス (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-134">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
 <span data-ttu-id="6335c-135">ディストリビューター インスタンスが正しく登録されていることを確認したら、ディストリビューション データベースが **msdb..MSdistributiondbs**の一覧に表示されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6335c-135">After verifying that the Distributor instance is registered properly, verify that the distribution database is listed in **msdb..MSdistributiondbs**.</span></span> <span data-ttu-id="6335c-136">表示されていない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6335c-136">If it is not listed:</span></span>  
  
1.  <span data-ttu-id="6335c-137">ディストリビューション構成のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6335c-137">Script out the distribution configuration.</span></span> <span data-ttu-id="6335c-138">詳細については、「[レプリケーションのスクリプト作成](scripting-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-138">For more information, see [Scripting Replication](scripting-replication.md).</span></span>  
  
2.  <span data-ttu-id="6335c-139">ディストリビューションを無効化してから、再度有効化します。</span><span class="sxs-lookup"><span data-stu-id="6335c-139">Disable distribution and then re-enable it.</span></span> <span data-ttu-id="6335c-140">詳しくは、「 [Configure Distribution](configure-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6335c-140">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6335c-141">参照</span><span class="sxs-lookup"><span data-stu-id="6335c-141">See Also</span></span>  
 [<span data-ttu-id="6335c-142">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="6335c-142">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  

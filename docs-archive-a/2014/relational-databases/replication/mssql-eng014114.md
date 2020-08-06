---
title: MSSQL_ENG014114 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014114 error
ms.assetid: f5f04590-e1c6-40d8-ab2b-98c791a0fc44
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba2a1fde59f55eecbfeeec46555567cde964f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630935"
---
# <a name="mssql_eng014114"></a><span data-ttu-id="5a692-102">MSSQL_ENG014114</span><span class="sxs-lookup"><span data-stu-id="5a692-102">MSSQL_ENG014114</span></span>
    
## <a name="message-details"></a><span data-ttu-id="5a692-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="5a692-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a692-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5a692-104">Product Name</span></span>|<span data-ttu-id="5a692-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5a692-105">SQL Server</span></span>|  
|<span data-ttu-id="5a692-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5a692-106">Event ID</span></span>|<span data-ttu-id="5a692-107">14114</span><span class="sxs-lookup"><span data-stu-id="5a692-107">14114</span></span>|  
|<span data-ttu-id="5a692-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5a692-108">Event Source</span></span>|<span data-ttu-id="5a692-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5a692-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5a692-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5a692-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="5a692-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5a692-111">Symbolic Name</span></span>||  
|<span data-ttu-id="5a692-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5a692-112">Message Text</span></span>|<span data-ttu-id="5a692-113">'%s' はディストリビューターとして構成されていません。</span><span class="sxs-lookup"><span data-stu-id="5a692-113">'%s' is not configured as a Distributor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5a692-114">説明</span><span class="sxs-lookup"><span data-stu-id="5a692-114">Explanation</span></span>  
 <span data-ttu-id="5a692-115">エラー メッセージで 'NULL' ではない特定のインスタンスが指定されている場合、指定されたインスタンスはディストリビューターとして認識されるように正しく構成されていません。</span><span class="sxs-lookup"><span data-stu-id="5a692-115">If the error message specifies a particular instance, rather than 'null', the instance specified has not been properly configured to be recognized as a Distributor.</span></span>  
  
 <span data-ttu-id="5a692-116">メッセージで 'NULL' がディストリビューターとして指定されている場合、 **master** データベースのローカル サーバーにエントリがないか、エントリが正しくありません (おそらくコンピューターの名前が変更されたことが原因です)。</span><span class="sxs-lookup"><span data-stu-id="5a692-116">If the message specifies 'null' as a Distributor, there is no entry for the local server in **master** database, or the entry is incorrect (perhaps because the computer was renamed).</span></span> <span data-ttu-id="5a692-117">レプリケーションでは、コンピューター名とオプションのインスタンス名 (クラスター化されたインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仮想サーバー名とオプションのインスタンス名) を使用して、トポロジのすべてのサーバーを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a692-117">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="5a692-118">レプリケーションが正しく機能するためには、トポロジの各サーバーに対して `SELECT @@SERVERNAME` によって返された値が、コンピューター名または仮想サーバー名と、オプションのインスタンス名で一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a692-118">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
 <span data-ttu-id="5a692-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのいずれかを IP アドレスまたは完全修飾ドメイン名 (FQDN) で登録している場合、レプリケーションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="5a692-119">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="5a692-120">レプリケーションの構成時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内に IP アドレスまたは FQDN で登録された [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスがあった場合、このエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5a692-120">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5a692-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5a692-121">User Action</span></span>  
 <span data-ttu-id="5a692-122">エラー メッセージで特定のインスタンスが指定されている場合、サーバーをディストリビューターとして構成してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-122">If the error message specifies a particular instance, configure the server as a Distributor.</span></span> <span data-ttu-id="5a692-123">詳しくは、「 [Configure Distribution](configure-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-123">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
 <span data-ttu-id="5a692-124">エラー メッセージで特定のインスタンスが指定されていない (つまり 'NULL' である) 場合、ディストリビューター インスタンスが正しく登録されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-124">If the message does not specify a particular instance ('null'), verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="5a692-125">コンピューターのネットワーク名と SQL Server インスタンスの名前が異なる場合は、次のいずれかを実行してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-125">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="5a692-126">SQL Server インスタンス名を有効なネットワーク名として追加します。</span><span class="sxs-lookup"><span data-stu-id="5a692-126">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="5a692-127">代替ネットワーク名を設定する 1 つの方法は、その名前をローカル ホスト ファイルに追加することです。</span><span class="sxs-lookup"><span data-stu-id="5a692-127">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="5a692-128">ローカル ホスト ファイルは、既定では、WINDOWS\system32\drivers\etc または WINNT\system32\drivers\etc にあります。詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-128">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="5a692-129">たとえば、コンピューター名が comp1、そのコンピューターの IP アドレスが 10.193.17.129、インスタンス名が inst1/instname の場合、ホスト ファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a692-129">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="5a692-130">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="5a692-130">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="5a692-131">ディストリビューションを無効化し、インスタンスを登録して、ディストリビューションを再設定してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-131">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="5a692-132">@@SERVERNAME の値が、クラスター化されていないインスタンスに対して適切でない場合は、次の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-132">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="5a692-133">[sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) ストアド プロシージャを実行したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動し、@@SERVERNAME への変更を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a692-133">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="5a692-134">@@SERVERNAME の値がクラスター化されたインスタンスに対して適切でない場合は、クラスター アドミニストレーターを使用して名前を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a692-134">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="5a692-135">詳細については、「[Always On フェールオーバー クラスター インスタンス (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a692-135">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a692-136">参照</span><span class="sxs-lookup"><span data-stu-id="5a692-136">See Also</span></span>  
 [<span data-ttu-id="5a692-137">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="5a692-137">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  

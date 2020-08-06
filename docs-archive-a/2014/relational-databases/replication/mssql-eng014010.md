---
title: MSSQL_ENG014010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014010 error
ms.assetid: 6ea84f2f-e7a2-4028-9ea9-af0d2eba660e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c3d989eb7ae78562fb77d9896545539ba4ca3c7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631819"
---
# <a name="mssql_eng014010"></a><span data-ttu-id="a7075-102">MSSQL_ENG014010</span><span class="sxs-lookup"><span data-stu-id="a7075-102">MSSQL_ENG014010</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a7075-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="a7075-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7075-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a7075-104">Product Name</span></span>|<span data-ttu-id="a7075-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a7075-105">SQL Server</span></span>|  
|<span data-ttu-id="a7075-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a7075-106">Event ID</span></span>|<span data-ttu-id="a7075-107">14010</span><span class="sxs-lookup"><span data-stu-id="a7075-107">14010</span></span>|  
|<span data-ttu-id="a7075-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a7075-108">Event Source</span></span>|<span data-ttu-id="a7075-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a7075-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a7075-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a7075-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a7075-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a7075-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a7075-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a7075-112">Message Text</span></span>|<span data-ttu-id="a7075-113">サーバー '%s' はサブスクリプション サーバーとして定義されていません。</span><span class="sxs-lookup"><span data-stu-id="a7075-113">The server '%s' is not defined as a subscription server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a7075-114">説明</span><span class="sxs-lookup"><span data-stu-id="a7075-114">Explanation</span></span>  
 <span data-ttu-id="a7075-115">レプリケーションでは、コンピューター名とオプションのインスタンス名 (クラスター化されたインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仮想サーバー名とオプションのインスタンス名) を使用して、トポロジのすべてのサーバーを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7075-115">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="a7075-116">レプリケーションが正しく機能するためには、トポロジの各サーバーに対して `SELECT @@SERVERNAME` によって返された値が、コンピューター名または仮想サーバー名と、オプションのインスタンス名で一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7075-116">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
 <span data-ttu-id="a7075-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのいずれかを IP アドレスまたは完全修飾ドメイン名 (FQDN) で登録している場合、レプリケーションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a7075-117">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="a7075-118">レプリケーションを構成するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスのいずれかを IP アドレスまたは FQDN で登録した場合、このエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a7075-118">If you have any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a7075-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a7075-119">User Action</span></span>  
 <span data-ttu-id="a7075-120">トポロジのすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが適切に登録されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a7075-120">Verify that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances in the topology are registered properly.</span></span> <span data-ttu-id="a7075-121">コンピューターのネットワーク名と SQL Server インスタンスの名前が異なる場合は、次のいずれかを実行してください。</span><span class="sxs-lookup"><span data-stu-id="a7075-121">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="a7075-122">SQL Server インスタンス名を有効なネットワーク名として追加します。</span><span class="sxs-lookup"><span data-stu-id="a7075-122">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="a7075-123">代替ネットワーク名を設定する 1 つの方法は、その名前をローカル ホスト ファイルに追加することです。</span><span class="sxs-lookup"><span data-stu-id="a7075-123">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="a7075-124">ローカル ホスト ファイルは、既定では、WINDOWS\system32\drivers\etc または WINNT\system32\drivers\etc にあります。詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7075-124">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="a7075-125">たとえば、コンピューター名が comp1、そのコンピューターの IP アドレスが 10.193.17.129、インスタンス名が inst1/instname の場合、ホスト ファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="a7075-125">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="a7075-126">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="a7075-126">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="a7075-127">レプリケーションを削除し、各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを登録して、レプリケーションを再設定します。</span><span class="sxs-lookup"><span data-stu-id="a7075-127">Remove replication, register each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then reestablish replication.</span></span> <span data-ttu-id="a7075-128">@@SERVERNAME の値が、クラスター化されていないインスタンスに対して適切でない場合は、次の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="a7075-128">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="a7075-129">[sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) ストアド プロシージャを実行したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動し、@@SERVERNAME への変更を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7075-129">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="a7075-130">@@SERVERNAME の値がクラスター化されたインスタンスに対して適切でない場合は、クラスター アドミニストレーターを使用して名前を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7075-130">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="a7075-131">詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7075-131">For more information, see [AlwaysOn Failover Cluster Instances &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7075-132">参照</span><span class="sxs-lookup"><span data-stu-id="a7075-132">See Also</span></span>  
 <span data-ttu-id="a7075-133">[@@SERVERNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/servername-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7075-133">[@@SERVERNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/servername-transact-sql) </span></span>  
 [<span data-ttu-id="a7075-134">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="a7075-134">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  

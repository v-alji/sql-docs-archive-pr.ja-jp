---
title: AlwaysOn 可用性グループを使用した FILESTREAM と FileTable (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7de7b4d66890bb5f1fe49799844f666de81f4db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640239"
---
# <a name="filestream-and-filetable-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="e6438-102">FILESTREAM および FileTable と AlwaysOn 可用性グループ (SQLServer)</span><span class="sxs-lookup"><span data-stu-id="e6438-102">FILESTREAM and FileTable with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="e6438-103">このトピックでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]と FILESTREAM 機能および FileTable 機能を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6438-103">This topic contains information about the using the FILESTREAM and FileTable features with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="e6438-104">すべての FILESTREAM 機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e6438-104">All FILESTREAM functionality is supported.</span></span> <span data-ttu-id="e6438-105">フェールオーバー後、FILESTREAM データは読み取り可能なセカンダリ レプリカと新しいプライマリの両方でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e6438-105">After a failover, FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
 <span data-ttu-id="e6438-106">FileTable 機能は部分的にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e6438-106">FileTable functionality is partially supported.</span></span> <span data-ttu-id="e6438-107">フェールオーバー後、FileTable データはプライマリ レプリカ上でアクセスできますが、読み取り可能なセカンダリ レプリカ上ではアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="e6438-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
 <span data-ttu-id="e6438-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e6438-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="e6438-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="e6438-109">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="e6438-110">FILESTREAM および FileTable アクセスでの仮想ネットワーク名 (VNN) の使用</span><span class="sxs-lookup"><span data-stu-id="e6438-110">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>](#vnn)  
  
-   [<span data-ttu-id="e6438-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="e6438-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="e6438-112">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e6438-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e6438-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="e6438-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="e6438-114">FileTable を使用するかどうかにかかわらず、FILESTREAM を使用するデータベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで FILESTREAM が有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e6438-114">Before adding a database that uses FILESTREAM, with or without FileTable, to an availability group, ensure that FILESTREAM is enabled on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="e6438-115">詳細については、「 [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e6438-115">For more information, see [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md).</span></span>  
  
##  <a name="using-virtual-network-names-vnns-for-filestream-and-filetable-access"></a><a name="vnn"></a><span data-ttu-id="e6438-116">FILESTREAM および FileTable アクセスでの Virtual Network 名 (Vnn) の使用</span><span class="sxs-lookup"><span data-stu-id="e6438-116">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>  
 <span data-ttu-id="e6438-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスで FILESTREAM を有効にすると、インスタンス レベルでの共有が作成され、FILESTREAM データにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e6438-117">When you enable FILESTREAM on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], an instance-level share is created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="e6438-118">この共有にアクセスするには、次の形式でコンピューター名を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6438-118">You access this share by using the computer name in the following format:</span></span>  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 <span data-ttu-id="e6438-119">ただし AlwaysOn 可用性グループでは、コンピューターの名前が仮想ネットワーク名 (VNN) を使用して仮想化されています。</span><span class="sxs-lookup"><span data-stu-id="e6438-119">In an AlwaysOn availability group, however, the name of the computer is virtualized by using a Virtual Network Name, or VNN.</span></span> <span data-ttu-id="e6438-120">コンピューターが可用性グループのプライマリ レプリカであり、可用性グループ内のデータベースに FILESTREAM データが格納されている場合、VNN スコープの共有も作成され、FILESTREAM データにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e6438-120">When the computer is the primary replica in an availability group, and databases in the availability group contain FILESTREAM data, then a VNN-scoped share is also created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="e6438-121">これは、Transact-SQL による FILESTREAM データへのアクセスには影響しません。</span><span class="sxs-lookup"><span data-stu-id="e6438-121">This does not affect Transact-SQL access to FILESTREAM data.</span></span> <span data-ttu-id="e6438-122">ただし、ファイル システム API を使用するアプリケーションは、次の形式のパスを持つ VNN スコープの共有を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6438-122">However applications that use file system APIs have to use the VNN-scoped share, which has a path in the following format:</span></span>  
  
 `\\<VNN>\<filestream_share_name>`  
  
 <span data-ttu-id="e6438-123">この VNN スコープの共有は、次のいずれかのイベントが発生するときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6438-123">This VNN-scoped share is created when one of the following events occurs.</span></span>  
  
-   <span data-ttu-id="e6438-124">プライマリ レプリカ上にある AlwaysOn 可用性グループに FILESTREAM データを格納するデータベースを追加します。</span><span class="sxs-lookup"><span data-stu-id="e6438-124">You add a database that contains FILESTREAM data to an AlwaysOn availability group on the primary replica.</span></span> <span data-ttu-id="e6438-125">この場合、共有 `\\<computer_name>\<filestream_share_name>` は既に存在します。</span><span class="sxs-lookup"><span data-stu-id="e6438-125">In this case, the share `\\<computer_name>\<filestream_share_name>` already exists.</span></span> <span data-ttu-id="e6438-126">共有 `\\<VNN>\<filestream_share_name>` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6438-126">The share `\\<VNN>\<filestream_share_name>` is created.</span></span>  
  
-   <span data-ttu-id="e6438-127">可用性グループが含まれるプライマリ レプリカ上で、ファイル I/O ストリーム アクセスに対して FILESTREAM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e6438-127">You enable FILESTREAM for file i/o streaming access on a primary replica that has availability groups.</span></span> <span data-ttu-id="e6438-128">次の共有が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6438-128">The following shares are created:</span></span>  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  <span data-ttu-id="e6438-129">`\\<VNN1>\<filestream_share_name>` (可用性グループ 1 向け)。</span><span class="sxs-lookup"><span data-stu-id="e6438-129">`\\<VNN1>\<filestream_share_name>` for availability group 1.</span></span>  
  
    3.  <span data-ttu-id="e6438-130">`\\<VNN2>\<filestream_share_name>` (可用性グループ 2 向け)。</span><span class="sxs-lookup"><span data-stu-id="e6438-130">`\\<VNN2>\<filestream_share_name>` for availability group 2.</span></span>  
  
 <span data-ttu-id="e6438-131">これらの VNN スコープの共有は、すべてのセカンダリ レプリカにも反映されます。</span><span class="sxs-lookup"><span data-stu-id="e6438-131">These VNN-scoped shares are also propagated to all secondary replicas.</span></span>  
  
 <span data-ttu-id="e6438-132">FILESTREAM データまたは FileTable データを格納するデータベースが AlwaysOn 可用性グループに属する場合、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="e6438-132">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="e6438-133">FILESTREAM および FileTable 関数は、コンピューター名ではなく仮想ネットワーク名 (VNN) のやり取りを行います。</span><span class="sxs-lookup"><span data-stu-id="e6438-133">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="e6438-134">関数の詳細については、「[Filestream および FileTable 関数 &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6438-134">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="e6438-135">ファイル システム API を介した FILESTREAM または FileTable データへのすべてのアクセスでは、コンピューター名ではなく VNN を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6438-135">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span>  
  
 <span data-ttu-id="e6438-136">データベースが可用性グループの一部である場合、アプリケーションで `\\<computer_name>\<filestream_share_name>` の形式のコンピューター名を使用して共有にアクセスしようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e6438-136">If your application tries to access the share by using the computer name in the format `\\<computer_name>\<filestream_share_name>` when the database is part of an availability group, then an error is raised.</span></span>  
  
 <span data-ttu-id="e6438-137">データベースが可用性グループの一部ではない場合、アプリケーションで VNN スコープのパスを使用して共有にアクセスしようとすると、要求が正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="e6438-137">If your application tries to access the share by using a VNN-scoped path when the database is not part of an availability group, then the request may succeed.</span></span> <span data-ttu-id="e6438-138">この場合、仮想ネットワーク名は、コンピューター名に解決されます。</span><span class="sxs-lookup"><span data-stu-id="e6438-138">In this case, the virtual network name is resolved to the computer name.</span></span> <span data-ttu-id="e6438-139">ただし、可用性グループが削除されると VNN スコープのパスの動作が停止するため、この使用法はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="e6438-139">However this usage is strongly discouraged, since the VNN-scoped path will stop working if the availability group is dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e6438-140">関連タスク</span><span class="sxs-lookup"><span data-stu-id="e6438-140">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e6438-141">FILESTREAM の有効化と構成</span><span class="sxs-lookup"><span data-stu-id="e6438-141">Enable and Configure FILESTREAM</span></span>](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [<span data-ttu-id="e6438-142">FileTable の前提条件の有効化</span><span class="sxs-lookup"><span data-stu-id="e6438-142">Enable the Prerequisites for FileTable</span></span>](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="e6438-143">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e6438-143">Related Content</span></span>  
 <span data-ttu-id="e6438-144">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e6438-144">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6438-145">参照</span><span class="sxs-lookup"><span data-stu-id="e6438-145">See Also</span></span>  
 [<span data-ttu-id="e6438-146">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="e6438-146">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  

---
title: Oracle パブリッシングの用語 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], glossary
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d135fb8ea3c1678f5ef31f0d7da6a717ab628999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721309"
---
# <a name="glossary-of-terms-for-oracle-publishing"></a><span data-ttu-id="db356-102">Oracle パブリッシングの用語</span><span class="sxs-lookup"><span data-stu-id="db356-102">Glossary of Terms for Oracle Publishing</span></span>
  <span data-ttu-id="db356-103">Oracle パブリッシングの構成および管理を行う場合には、以下に示す Oracle の用語を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="db356-103">You should be familiar with the following Oracle terms when configuring and administering Oracle publishing.</span></span> <span data-ttu-id="db356-104">Oracle の用語の完全な一覧については、Oracle のオンライン マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="db356-104">For a complete list of Oracle terms, see the Oracle online documentation.</span></span>  
  
 <span data-ttu-id="db356-105">索引構成表 (IOT)</span><span class="sxs-lookup"><span data-stu-id="db356-105">Index Organized Tables (IOT)</span></span>  
 <span data-ttu-id="db356-106">データがディスク上でインデックス順に物理的に並べ替えられたテーブルです。[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のクラスター化インデックス付きテーブルに似ています。</span><span class="sxs-lookup"><span data-stu-id="db356-106">A table whose data is physically sorted on disk in index order; it is similar to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table with a clustered index.</span></span> <span data-ttu-id="db356-107">IOT はクラスター化インデックス付きテーブルとしてサブスクライバーにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="db356-107">An IOT is replicated to a Subscriber as a table with a clustered index.</span></span>  
  
 <span data-ttu-id="db356-108">インスタンス</span><span class="sxs-lookup"><span data-stu-id="db356-108">Instance</span></span>  
 <span data-ttu-id="db356-109">Oracle データベースはインスタンスに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="db356-109">An Oracle database is associated with an instance.</span></span> <span data-ttu-id="db356-110">このインスタンスは、メモリ、およびデータベースをサポートするバックグラウンド プロセスから構成されます。</span><span class="sxs-lookup"><span data-stu-id="db356-110">The instance comprises the memory and background processes supporting the database.</span></span> <span data-ttu-id="db356-111">Oracle のインスタンスは常に単一のデータベースにマッピングされます。一方、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスには複数のデータベースを格納できます。</span><span class="sxs-lookup"><span data-stu-id="db356-111">An Oracle instance always maps to a single database, whereas an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can contain many databases.</span></span> <span data-ttu-id="db356-112">状況によっては、1 つの Oracle データベースに複数のインスタンスを持たせることもできます。</span><span class="sxs-lookup"><span data-stu-id="db356-112">There are circumstances in which an Oracle database can have multiple instances.</span></span>  
  
 <span data-ttu-id="db356-113">Oracle リスナー</span><span class="sxs-lookup"><span data-stu-id="db356-113">Oracle Listener</span></span>  
 <span data-ttu-id="db356-114">Oracle データベース インスタンスの受信ネットワーク トラフィックを処理します。</span><span class="sxs-lookup"><span data-stu-id="db356-114">Handles incoming network traffic for an Oracle database instance.</span></span> <span data-ttu-id="db356-115">Oracle データベースへのネットワーク接続を構成する場合、トラフィックの送信に使用するプロトコルと、リスナーがトラフィックを受信待ちするポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="db356-115">When you configure network connectivity to an Oracle database, you specify the protocol through which traffic is sent and the port on which the Listener listens for traffic.</span></span> <span data-ttu-id="db356-116">通常の構成ではリスナーは Oracle データベースのインスタンスと同一のコンピューター上で実行されます。リスナーは 1 つ以上のインスタンスに対し機能するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="db356-116">The Listener is typically configured to run on the same computer as the Oracle database instance and can be configured to serve one or more instances.</span></span>  
  
 <span data-ttu-id="db356-117">ROWID</span><span class="sxs-lookup"><span data-stu-id="db356-117">ROWID</span></span>  
 <span data-ttu-id="db356-118">データベースの特定の行の位置を示すポインターです。</span><span class="sxs-lookup"><span data-stu-id="db356-118">A pointer to the location of a specific row in a database.</span></span> <span data-ttu-id="db356-119">テーブル スキャンやインデックスよりも ROWID を使用する方が行を高速に取得できるため、レプリケーションではパブリッシュされたテーブルの変更を処理する際、一時的に ROWID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="db356-119">Because retrieving rows using the ROWID is faster than using a table scan or index, replication uses the ROWID temporarily during processing of published table changes.</span></span>  
  
 <span data-ttu-id="db356-120">Sequence</span><span class="sxs-lookup"><span data-stu-id="db356-120">Sequence</span></span>  
 <span data-ttu-id="db356-121">一意の数値を生成するためのデータベース オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="db356-121">A database object that is used to generate unique numbers.</span></span> <span data-ttu-id="db356-122">レプリケーションではシーケンスを使用して、パブリッシュされたテーブルへの変更を順序付けします。</span><span class="sxs-lookup"><span data-stu-id="db356-122">Replication uses sequences to order changes made to published tables.</span></span>  
  
 <span data-ttu-id="db356-123">SQL\*Plus</span><span class="sxs-lookup"><span data-stu-id="db356-123">SQL\*Plus</span></span>  
 <span data-ttu-id="db356-124">Oracle データベースへのアクセスおよび照会に使用されるアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="db356-124">An application used to access and query Oracle databases.</span></span> <span data-ttu-id="db356-125">これは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd** に似ています。</span><span class="sxs-lookup"><span data-stu-id="db356-125">It is similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.</span></span>  
  
 <span data-ttu-id="db356-126">シノニム</span><span class="sxs-lookup"><span data-stu-id="db356-126">Synonym</span></span>  
 <span data-ttu-id="db356-127">オブジェクトの別名です。</span><span class="sxs-lookup"><span data-stu-id="db356-127">An alias for an object.</span></span> <span data-ttu-id="db356-128">Oracle パブリッシャーを構成すると、特別なパブリック シノニム **MSSQLSERVERDISTRIBUTOR** が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="db356-128">The special public synonym **MSSQLSERVERDISTRIBUTOR** is automatically created when an Oracle Publisher is configured.</span></span> <span data-ttu-id="db356-129">このシノニムは **HREPL_Distributor** テーブルを参照して、パブリッシャーにサービスを提供する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターへの論理ポインターを示します。</span><span class="sxs-lookup"><span data-stu-id="db356-129">The synonym references the **HREPL_Distributor** table and provides a logical pointer to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor that services the Publisher.</span></span>  
  
 <span data-ttu-id="db356-130">Oracle データベースがパブリッシュされた後で、別の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターを使用するようにパブリッシャーを構成することはできません。これは、パブリッシャーにサービスを提供するように既に構成されている特定のディストリビューターが、このパブリック シノニムによって識別されるためです。</span><span class="sxs-lookup"><span data-stu-id="db356-130">After an Oracle database has been published, subsequent attempts to configure this Publisher to use a different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor will fail, because this public synonym identifies the particular Distributor already configured to service the Publisher.</span></span>  
  
 <span data-ttu-id="db356-131">テーブルスペース</span><span class="sxs-lookup"><span data-stu-id="db356-131">Tablespace</span></span>  
 <span data-ttu-id="db356-132">データベース領域の単位で、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のファイル グループにほぼ等しい意味です。</span><span class="sxs-lookup"><span data-stu-id="db356-132">A unit of database storage that is roughly equivalent to a filegroup in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="db356-133">TNS サービス名</span><span class="sxs-lookup"><span data-stu-id="db356-133">TNS Service Name</span></span>  
 <span data-ttu-id="db356-134">TNS (Transparent Network Substrate) とは、Oracle データベースが使用する通信層です。</span><span class="sxs-lookup"><span data-stu-id="db356-134">TNS (Transparent Network Substrate) is a communication layer used by Oracle databases.</span></span> <span data-ttu-id="db356-135">TNS サービス名は、ネットワーク上での Oracle データベース インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="db356-135">The TNS Service Name is the name by which an Oracle database instance is known on a network.</span></span> <span data-ttu-id="db356-136">TNS サービス名は、Oracle データベースへの接続を構成するときに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="db356-136">You assign a TNS Service Name when you configure connectivity to the Oracle database.</span></span> <span data-ttu-id="db356-137">レプリケーションでは TNS サービス名を使用してパブリッシャーを識別し、接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="db356-137">Replication uses the TNS Service name to identify the Publisher and to establish connections.</span></span>  
  
 <span data-ttu-id="db356-138">ユーザー スキーマ</span><span class="sxs-lookup"><span data-stu-id="db356-138">User schema</span></span>  
 <span data-ttu-id="db356-139">ユーザー スキーマは、特定のデータベース オブジェクトのセットを所有するデータベース ユーザーとして考えることができます。</span><span class="sxs-lookup"><span data-stu-id="db356-139">A user schema can be thought of as a database user who owns a particular set of database objects.</span></span> <span data-ttu-id="db356-140">レプリケーションの管理ユーザー スキーマは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーション処理により Oracle データベース内で作成されたすべてのオブジェクトを所有します。ただし、パブリック シノニム **MSSQLSERVERDISTRIBUTOR** は除きます。</span><span class="sxs-lookup"><span data-stu-id="db356-140">The replication administrative user schema owns all objects created by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication process in the Oracle database, with the exception of the **MSSQLSERVERDISTRIBUTOR** public synonym.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db356-141">参照</span><span class="sxs-lookup"><span data-stu-id="db356-141">See Also</span></span>  
 <span data-ttu-id="db356-142">[Configure an Oracle Publisher (Oracle パブリッシャーの構成)](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="db356-142">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="db356-143">[Oracle パブリッシャー上で作成されたオブジェクト](objects-created-on-the-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="db356-143">[Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md) </span></span>  
 <span data-ttu-id="db356-144">[SQL Server 以外のパブリッシャー](non-sql-server-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="db356-144">[Non-SQL Server Publishers](non-sql-server-publishers.md) </span></span>  
 [<span data-ttu-id="db356-145">Oracle パブリッシングの概要</span><span class="sxs-lookup"><span data-stu-id="db356-145">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  

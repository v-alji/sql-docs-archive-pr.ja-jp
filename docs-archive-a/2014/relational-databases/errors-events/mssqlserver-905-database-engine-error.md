---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7dd3c8c5a287e2d123e2a9d1430ecd49b27f29f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640004"
---
# <a name="mssqlserver_905"></a><span data-ttu-id="10c8b-102">MSSQLSERVER_905</span><span class="sxs-lookup"><span data-stu-id="10c8b-102">MSSQLSERVER_905</span></span>
    
## <a name="details"></a><span data-ttu-id="10c8b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="10c8b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10c8b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="10c8b-104">Product Name</span></span>|<span data-ttu-id="10c8b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="10c8b-105">SQL Server</span></span>|  
|<span data-ttu-id="10c8b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="10c8b-106">Event ID</span></span>|<span data-ttu-id="10c8b-107">905</span><span class="sxs-lookup"><span data-stu-id="10c8b-107">905</span></span>|  
|<span data-ttu-id="10c8b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="10c8b-108">Event Source</span></span>|<span data-ttu-id="10c8b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="10c8b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="10c8b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="10c8b-110">Component</span></span>|<span data-ttu-id="10c8b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="10c8b-111">SQLEngine</span></span>|  
|<span data-ttu-id="10c8b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="10c8b-112">Symbolic Name</span></span>|<span data-ttu-id="10c8b-113">DBSTARTUP_EE_PARTITIONING</span><span class="sxs-lookup"><span data-stu-id="10c8b-113">DBSTARTUP_EE_PARTITIONING</span></span>|  
|<span data-ttu-id="10c8b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="10c8b-114">Message Text</span></span>|<span data-ttu-id="10c8b-115">データベース '%.\*ls' は、このエディションの SQL Server では起動できません。このデータベースには、パーティション関数 '%.\*ls' が含まれています。</span><span class="sxs-lookup"><span data-stu-id="10c8b-115">Database '%.\*ls' cannot be started in this edition of SQL Server because it contains a partition function '%.\*ls'.</span></span> <span data-ttu-id="10c8b-116">パーティション分割は SQL Server Enterprise Edition でしかサポートされません。</span><span class="sxs-lookup"><span data-stu-id="10c8b-116">Only Enterprise edition of SQL Server supports partitioning.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10c8b-117">説明</span><span class="sxs-lookup"><span data-stu-id="10c8b-117">Explanation</span></span>  
 <span data-ttu-id="10c8b-118">データベースに 1 つ以上のパーティション テーブルまたはパーティション インデックスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="10c8b-118">The database contains one or more partitioned tables or indexes.</span></span> <span data-ttu-id="10c8b-119">このエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではパーティション分割を使用できません。</span><span class="sxs-lookup"><span data-stu-id="10c8b-119">This edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot use partitioning.</span></span> <span data-ttu-id="10c8b-120">したがって、データベースを正常に起動できません。</span><span class="sxs-lookup"><span data-stu-id="10c8b-120">Therefore, the database cannot be started correctly.</span></span> <span data-ttu-id="10c8b-121">パーティション テーブルとパーティション インデックスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="10c8b-121">Partitioned tables and indexes are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="10c8b-122">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10c8b-122">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10c8b-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="10c8b-123">User Action</span></span>  
 <span data-ttu-id="10c8b-124">sp_detach_db ストアド プロシージャを使用してデータベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="10c8b-124">Detach the database by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="10c8b-125">必要であればファイルを移動してから、CREATE DATABASE で FOR ATTACH オプションまたは FOR ATTACH_REBUILD_LOG オプションを使用し、サポートされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エディションのインスタンスにデータベースをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="10c8b-125">Move the files if it is needed, and then attach the database to an instance of a supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition by using the CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="10c8b-126">すべてのテーブルのパーティションを無効にし、パーティション関数を削除します。</span><span class="sxs-lookup"><span data-stu-id="10c8b-126">Disable partitioning on all tables and remove the partitioning functions.</span></span> <span data-ttu-id="10c8b-127">もう一度、データベースをデタッチしてから、現在のサーバーにデータベースを再アタッチします。</span><span class="sxs-lookup"><span data-stu-id="10c8b-127">Detach the database again, and reattach the database to the current server.</span></span>  
  
  

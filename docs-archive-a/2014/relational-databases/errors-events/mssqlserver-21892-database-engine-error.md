---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd3bfa1213f0569293991d6bd759619c6e7b596
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740021"
---
# <a name="mssqlserver_21892"></a><span data-ttu-id="a67dd-102">MSSQLSERVER_21892</span><span class="sxs-lookup"><span data-stu-id="a67dd-102">MSSQLSERVER_21892</span></span>
    
## <a name="details"></a><span data-ttu-id="a67dd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a67dd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a67dd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a67dd-104">Product Name</span></span>|<span data-ttu-id="a67dd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a67dd-105">SQL Server</span></span>|  
|<span data-ttu-id="a67dd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a67dd-106">Event ID</span></span>|<span data-ttu-id="a67dd-107">21892</span><span class="sxs-lookup"><span data-stu-id="a67dd-107">21892</span></span>|  
|<span data-ttu-id="a67dd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a67dd-108">Event Source</span></span>|<span data-ttu-id="a67dd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a67dd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a67dd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a67dd-110">Component</span></span>|<span data-ttu-id="a67dd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a67dd-111">SQLEngine</span></span>|  
|<span data-ttu-id="a67dd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a67dd-112">Symbolic Name</span></span>|<span data-ttu-id="a67dd-113">SQLErrorNum21892</span><span class="sxs-lookup"><span data-stu-id="a67dd-113">SQLErrorNum21892</span></span>|  
|<span data-ttu-id="a67dd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a67dd-114">Message Text</span></span>|<span data-ttu-id="a67dd-115">仮想ネットワーク名 '%s' にプライマリとして関連付けられた可用性グループにある sys.availability_replicas で、メンバー レプリカのサーバー名をクエリすることができません。エラー = %d、エラー メッセージ = '%s'。</span><span class="sxs-lookup"><span data-stu-id="a67dd-115">Unable to query sys.availability_replicas at the availability group primary associated with virtual network name '%s' for the server names of the member replicas: error = %d, error message = %s.',</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a67dd-116">説明</span><span class="sxs-lookup"><span data-stu-id="a67dd-116">Explanation</span></span>  
 <span data-ttu-id="a67dd-117">`sp_validate_replica_hosts_as_publishers` は、リダイレクトされたパブリッシャーに関連付けられている可用性グループの現在のプライマリにクエリを実行し、メンバー レプリカをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを特定します。</span><span class="sxs-lookup"><span data-stu-id="a67dd-117">`sp_validate_replica_hosts_as_publishers` queries the current primary of the availability group associated with the redirected publisher, to determine the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that host the member replicas.</span></span>  <span data-ttu-id="a67dd-118">このクエリが失敗すると、エラー 21892 が返されます。</span><span class="sxs-lookup"><span data-stu-id="a67dd-118">When this query fails, error 21892 is returned.</span></span>  
  
 <span data-ttu-id="a67dd-119">`sp_validate_replica_hosts_as_publishers` は通常、一時リンク サーバーを最初に使用するため、接続の問題がある場合は `sp_validate_replica_hosts_as_publishers` で初めて問題が現れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a67dd-119">`sp_validate_replica_hosts_as_publishers` is typically on of the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with `sp_validate_replica_hosts_as_publishers`.</span></span> <span data-ttu-id="a67dd-120">`sp_validate_redirected_publisher` と異なり、`sp_validate_replica_hosts_as_publishers` が使用するリンク サーバーは、いずれかの可用性グループ レプリカ ホストに接続するときに常に呼び出し元の資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="a67dd-120">Unlike `sp_validate_redirected_publisher`, the linked server used by `sp_validate_replica_hosts_as_publishers` always uses the credentials of the caller when connecting to any of the availability group replica hosts.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a67dd-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a67dd-121">User Action</span></span>  
 <span data-ttu-id="a67dd-122">このストアド プロシージャを実行する場合は、レプリカのすべてに対して有効なログインから実行してください。</span><span class="sxs-lookup"><span data-stu-id="a67dd-122">When running this stored procedure, made certain that you run from a login that is valid on all of the replicas.</span></span> <span data-ttu-id="a67dd-123">ログインには、可用性グループのメタデータ テーブルにクエリを実行し、パブリッシャー データベース レプリカのサブスクリプション メタデータ データベースにクエリを実行するための十分な権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a67dd-123">The login will require sufficient authorization to query availability group metadata tables as well as to query the subscription metadata tables in the publisher database replica.</span></span>  
  
 <span data-ttu-id="a67dd-124">参照される元のエラーを確認し、エラーの原因と適切な修正措置を特定します。</span><span class="sxs-lookup"><span data-stu-id="a67dd-124">Examine the original referenced error to determine the cause of the failure and appropriate corrective action.</span></span>  
  
  

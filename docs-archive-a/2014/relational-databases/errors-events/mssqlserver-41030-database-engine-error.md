---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b137b739d4c1641b88983708df62d2e52fd0eab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736372"
---
# <a name="mssqlserver_41030"></a><span data-ttu-id="74358-102">MSSQLSERVER_41030</span><span class="sxs-lookup"><span data-stu-id="74358-102">MSSQLSERVER_41030</span></span>
    
## <a name="details"></a><span data-ttu-id="74358-103">詳細</span><span class="sxs-lookup"><span data-stu-id="74358-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74358-104">製品名</span><span class="sxs-lookup"><span data-stu-id="74358-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="74358-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="74358-105">Event ID</span></span>|<span data-ttu-id="74358-106">41030</span><span class="sxs-lookup"><span data-stu-id="74358-106">41030</span></span>|  
|<span data-ttu-id="74358-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="74358-107">Event Source</span></span>|<span data-ttu-id="74358-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="74358-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="74358-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="74358-109">Component</span></span>|<span data-ttu-id="74358-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="74358-110">SQLEngine</span></span>|  
|<span data-ttu-id="74358-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="74358-111">Symbolic Name</span></span>|<span data-ttu-id="74358-112">OPEN_CLUSTER_SUB_KEY</span><span class="sxs-lookup"><span data-stu-id="74358-112">OPEN_CLUSTER_SUB_KEY</span></span>|  
|<span data-ttu-id="74358-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="74358-113">Message Text</span></span>|<span data-ttu-id="74358-114">Windows Server フェールオーバー クラスタリング レジストリ サブキー '%.\*ls' を開くことができませんでした (エラー コード %d)。</span><span class="sxs-lookup"><span data-stu-id="74358-114">Failed to open the Windows Server Failover Clustering registry subkey '%.\*ls' (Error code %d).</span></span>  <span data-ttu-id="74358-115">親キーはクラスター ルート キーです。</span><span class="sxs-lookup"><span data-stu-id="74358-115">The parent key is the cluster root key.</span></span>  <span data-ttu-id="74358-116">WSFC サービスは実行されていないか、現在の状態でアクセスできない可能性があります。または、指定された引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="74358-116">The WSFC service may not be running or may not be accessible in its current state, or the specified arguments are invalid.</span></span> <span data-ttu-id="74358-117">対応する可用性グループが削除されている場合、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="74358-117">If the corresponding availability group has been dropped, this error is expected.</span></span> <span data-ttu-id="74358-118">このエラー コードの詳細については、Windows 開発ドキュメントの「システム エラー コード」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74358-118">For information about this error code, see "System Error Codes" in the Windows Development documentation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74358-119">説明</span><span class="sxs-lookup"><span data-stu-id="74358-119">Explanation</span></span>  
 <span data-ttu-id="74358-120">WSFC クラスターが破棄されると、[!INCLUDE[ssHADR](../../includes/sshadr-md.md)] に関連するすべてのレジストリ キーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="74358-120">If a WSFC cluster is destroyed, it removes all registry keys related to [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74358-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="74358-121">User Action</span></span>  
 <span data-ttu-id="74358-122">WSFC クラスターを再作成した後、AlwaysOn が有効になっている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの各クラスター ノードで AlwaysOn を無効にし、再度有効にします。</span><span class="sxs-lookup"><span data-stu-id="74358-122">After re-creating a WSFC cluster, disable and then re-enable AlwaysOn on every cluster node on which an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is enabled for AlwaysOn.</span></span> <span data-ttu-id="74358-123">この作業には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="74358-123">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for this task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74358-124">参照</span><span class="sxs-lookup"><span data-stu-id="74358-124">See Also</span></span>  
 <span data-ttu-id="74358-125">[AlwaysOn 可用性グループ &#40;SQL Server を有効または無効にする&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="74358-125">[Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="74358-126">Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server</span><span class="sxs-lookup"><span data-stu-id="74358-126">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  

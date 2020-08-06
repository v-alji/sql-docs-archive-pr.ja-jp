---
title: MSSQLSERVER_9955 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56b9f9b4b7923f8973bd7167c3c1bf77e92300c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639986"
---
# <a name="mssqlserver_9955"></a><span data-ttu-id="0f0e8-102">MSSQLSERVER_9955</span><span class="sxs-lookup"><span data-stu-id="0f0e8-102">MSSQLSERVER_9955</span></span>
    
## <a name="details"></a><span data-ttu-id="0f0e8-103">詳細</span><span class="sxs-lookup"><span data-stu-id="0f0e8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f0e8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="0f0e8-104">Product Name</span></span>|<span data-ttu-id="0f0e8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f0e8-105">SQL Server</span></span>|  
|<span data-ttu-id="0f0e8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0f0e8-106">Event ID</span></span>|<span data-ttu-id="0f0e8-107">9955</span><span class="sxs-lookup"><span data-stu-id="0f0e8-107">9955</span></span>|  
|<span data-ttu-id="0f0e8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="0f0e8-108">Event Source</span></span>|<span data-ttu-id="0f0e8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0f0e8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0f0e8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0f0e8-110">Component</span></span>|<span data-ttu-id="0f0e8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0f0e8-111">SQLEngine</span></span>|  
|<span data-ttu-id="0f0e8-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="0f0e8-112">Symbolic Name</span></span>|<span data-ttu-id="0f0e8-113">FTXT2_MSSEARCHACCESSDENY</span><span class="sxs-lookup"><span data-stu-id="0f0e8-113">FTXT2_MSSEARCHACCESSDENY</span></span>|  
|<span data-ttu-id="0f0e8-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="0f0e8-114">Message Text</span></span>|<span data-ttu-id="0f0e8-115">SQL Server は、名前付きパイプ '%ls' を作成して、フルテキスト フィルター デーモンと通信することができませんでした (Windows エラー: %d)。</span><span class="sxs-lookup"><span data-stu-id="0f0e8-115">SQL Server failed to create named pipe '%ls' to communicate with the full-text filter daemon (Windows error: %d).</span></span> <span data-ttu-id="0f0e8-116">フィルター デーモン ホスト プロセス用の名前付きパイプが既に存在するか、システムのリソースが不足しているか、またはフィルター デーモン アカウント グループのセキュリティ ID 番号 (SID) の検索に失敗したかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0f0e8-116">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span> <span data-ttu-id="0f0e8-117">このエラーを解決するには、実行中のフルテキスト フィルター デーモン プロセスをすべて終了し、必要に応じて、フルテキスト デーモン ランチャー サービス アカウントを再構成してください。</span><span class="sxs-lookup"><span data-stu-id="0f0e8-117">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon launcher service account.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0f0e8-118">説明</span><span class="sxs-lookup"><span data-stu-id="0f0e8-118">Explanation</span></span>  
 <span data-ttu-id="0f0e8-119">このメッセージは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がフルテキスト フィルター デーモンと通信するための名前付きパイプを作成できなかったことが原因で表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f0e8-119">This message occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failed to create a named pipe to communicate with the full-text filter daemon.</span></span> <span data-ttu-id="0f0e8-120">フィルター デーモン ホスト プロセス用の名前付きパイプが既に存在するか、システムのリソースが不足しているか、またはフィルター デーモン アカウント グループのセキュリティ ID 番号 (SID) の検索に失敗したかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0f0e8-120">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0f0e8-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="0f0e8-121">User Action</span></span>  
 <span data-ttu-id="0f0e8-122">このエラーを解決するには、実行中のフルテキスト フィルター デーモン プロセスをすべて終了し、必要に応じて SQL Server 構成マネージャーを使用してフルテキスト デーモン ホスト アカウントを再構成します。</span><span class="sxs-lookup"><span data-stu-id="0f0e8-122">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon host account by using the SQL Server Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0e8-123">参照</span><span class="sxs-lookup"><span data-stu-id="0f0e8-123">See Also</span></span>  
 <span data-ttu-id="0f0e8-124">[SQL Server 構成マネージャー](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0f0e8-124">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="0f0e8-125">[フルテキストフィルターデーモンランチャーのサービスアカウントの設定](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="0f0e8-125">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 [<span data-ttu-id="0f0e8-126">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="0f0e8-126">Full-Text Search</span></span>](../search/full-text-search.md)  
  
  

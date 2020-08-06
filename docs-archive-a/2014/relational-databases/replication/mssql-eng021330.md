---
title: MSSQL_ENG021330 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4338756a641b23bfc6f52da6b3de296bb6415756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714182"
---
# <a name="mssql_eng021330"></a><span data-ttu-id="6a43c-102">MSSQL_ENG021330</span><span class="sxs-lookup"><span data-stu-id="6a43c-102">MSSQL_ENG021330</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6a43c-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="6a43c-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a43c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6a43c-104">Product Name</span></span>|<span data-ttu-id="6a43c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a43c-105">SQL Server</span></span>|  
|<span data-ttu-id="6a43c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6a43c-106">Event ID</span></span>|<span data-ttu-id="6a43c-107">21330</span><span class="sxs-lookup"><span data-stu-id="6a43c-107">21330</span></span>|  
|<span data-ttu-id="6a43c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6a43c-108">Event Source</span></span>|<span data-ttu-id="6a43c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a43c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a43c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6a43c-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6a43c-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6a43c-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6a43c-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6a43c-112">Message Text</span></span>|<span data-ttu-id="6a43c-113">レプリケーション作業ディレクトリにサブディレクトリを作成できませんでした。(%ls)</span><span class="sxs-lookup"><span data-stu-id="6a43c-113">Failed to create a sub-directory under the replication working directory.(%ls)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a43c-114">説明</span><span class="sxs-lookup"><span data-stu-id="6a43c-114">Explanation</span></span>  
 <span data-ttu-id="6a43c-115">このエラーは、サブスクリプションが手動で初期化され、レプリケーション スクリプトを保存するディレクトリの作成で問題があった場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6a43c-115">This error can occur when a subscription is initialized manually, and there is a problem creating the directory in which replication scripts are stored.</span></span> <span data-ttu-id="6a43c-116">このエラーは、権限に関する問題によって発生する可能性があります。サブスクリプションがスナップショットを使用しないで初期化される場合、パブリッシャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの実行に使用されるアカウントは、ディストリビューターのスナップショット フォルダーに対する書き込み権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a43c-116">The error can be caused by a permissions issue: when a subscription is initialized without using a snapshot, the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher must have write permissions on the snapshot folder at the Distributor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a43c-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6a43c-117">User Action</span></span>  
 <span data-ttu-id="6a43c-118">スナップショット フォルダーに対して正しいパスが指定されていること、およびパブリッシャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの実行に使用されるアカウントが十分な権限を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a43c-118">Ensure that the correct path has been specified for the snapshot folder and that the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher has sufficient permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a43c-119">参照</span><span class="sxs-lookup"><span data-stu-id="6a43c-119">See Also</span></span>  
 <span data-ttu-id="6a43c-120">[既定のスナップショットの場所の指定](snapshot-options.md#snapshot-folder-locations) </span><span class="sxs-lookup"><span data-stu-id="6a43c-120">[Specify the Default Snapshot Location](snapshot-options.md#snapshot-folder-locations) </span></span>  
 <span data-ttu-id="6a43c-121">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6a43c-121">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="6a43c-122">スナップショットを使用しないトランザクション サブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="6a43c-122">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  

---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b73d3216f07cb44d750a37149634258648f1bd48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714177"
---
# <a name="mssql_eng021385"></a><span data-ttu-id="6ee99-102">MSSQL_ENG021385</span><span class="sxs-lookup"><span data-stu-id="6ee99-102">MSSQL_ENG021385</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6ee99-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="6ee99-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ee99-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6ee99-104">Product Name</span></span>|<span data-ttu-id="6ee99-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6ee99-105">SQL Server</span></span>|  
|<span data-ttu-id="6ee99-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6ee99-106">Event ID</span></span>|<span data-ttu-id="6ee99-107">21385</span><span class="sxs-lookup"><span data-stu-id="6ee99-107">21385</span></span>|  
|<span data-ttu-id="6ee99-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6ee99-108">Event Source</span></span>|<span data-ttu-id="6ee99-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6ee99-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6ee99-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6ee99-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6ee99-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6ee99-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6ee99-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6ee99-112">Message Text</span></span>|<span data-ttu-id="6ee99-113">スナップショットはパブリケーション '%s' の処理に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6ee99-113">Snapshot failed to process publication '%s'.</span></span> <span data-ttu-id="6ee99-114">アクティブなスキーマ変更または新しいアーティクルが追加されたことが原因の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6ee99-114">Possibly due to active schema change activity or new articles being added.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ee99-115">説明</span><span class="sxs-lookup"><span data-stu-id="6ee99-115">Explanation</span></span>  
 <span data-ttu-id="6ee99-116">このエラーは、アーティクルの追加や削除、パブリッシュされたオブジェクトへのスキーマ変更の実行など、パブリケーション データベースに対する変更が実行中のときに、スナップショット エージェントが起動されると発生します。</span><span class="sxs-lookup"><span data-stu-id="6ee99-116">This error is raised if the Snapshot Agent starts running when there are ongoing changes to the publication database, including adding or dropping articles and performing schema changes on published objects.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ee99-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6ee99-117">User Action</span></span>  
 <span data-ttu-id="6ee99-118">パブリケーション データベースに対する変更が完了した後に、スナップショット エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="6ee99-118">Restart the Snapshot Agent after changes to the publication database are complete.</span></span> <span data-ttu-id="6ee99-119">詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ee99-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee99-120">参照</span><span class="sxs-lookup"><span data-stu-id="6ee99-120">See Also</span></span>  
 [<span data-ttu-id="6ee99-121">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="6ee99-121">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  

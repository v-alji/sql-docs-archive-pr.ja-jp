---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 704b847bde2d7b4da9da91b4b24bfe2b9e2afa07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643911"
---
# <a name="mssqlserver_1462"></a><span data-ttu-id="242e6-102">MSSQLSERVER_1462</span><span class="sxs-lookup"><span data-stu-id="242e6-102">MSSQLSERVER_1462</span></span>
    
## <a name="details"></a><span data-ttu-id="242e6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="242e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="242e6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="242e6-104">Product Name</span></span>|<span data-ttu-id="242e6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="242e6-105">SQL Server</span></span>|  
|<span data-ttu-id="242e6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="242e6-106">Event ID</span></span>|<span data-ttu-id="242e6-107">1462</span><span class="sxs-lookup"><span data-stu-id="242e6-107">1462</span></span>|  
|<span data-ttu-id="242e6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="242e6-108">Event Source</span></span>|<span data-ttu-id="242e6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="242e6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="242e6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="242e6-110">Component</span></span>|<span data-ttu-id="242e6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="242e6-111">SQLEngine</span></span>|  
|<span data-ttu-id="242e6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="242e6-112">Symbolic Name</span></span>|<span data-ttu-id="242e6-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span><span class="sxs-lookup"><span data-stu-id="242e6-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span></span>|  
|<span data-ttu-id="242e6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="242e6-114">Message Text</span></span>|<span data-ttu-id="242e6-115">やり直し操作の失敗により、データベース ミラーリングが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="242e6-115">Database mirroring is disabled due to a failed redo operation.</span></span> <span data-ttu-id="242e6-116">再開できません。</span><span class="sxs-lookup"><span data-stu-id="242e6-116">Unable to resume.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="242e6-117">説明</span><span class="sxs-lookup"><span data-stu-id="242e6-117">Explanation</span></span>  
 <span data-ttu-id="242e6-118">データベース ミラーリングで、ミラーでのログ レコードの再実行に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="242e6-118">Database mirroring failed to redo a log record on the mirror.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="242e6-119">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="242e6-119">Possible Causes</span></span>  
 <span data-ttu-id="242e6-120">最も可能性が高い原因は、プリンシパル データベースでファイルの追加操作が完了しても、ファイル名またはディレクトリ構造がプリンシパル サーバーとミラー サーバーで異なるために、ミラー データベースで失敗したことです。</span><span class="sxs-lookup"><span data-stu-id="242e6-120">The most likely cause is that an add-file operation completed on the principal database but then failed on the mirror database because file names or directory structures differ on the principal server and mirror server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="242e6-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="242e6-121">User Action</span></span>  
 <span data-ttu-id="242e6-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログで、このエラーの原因を調べます。</span><span class="sxs-lookup"><span data-stu-id="242e6-122">Look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the cause of this error.</span></span> <span data-ttu-id="242e6-123">原因を解決してデータベースでミラーリングを再開します。</span><span class="sxs-lookup"><span data-stu-id="242e6-123">Try to resolve the cause and resume mirroring on the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="242e6-124">参照</span><span class="sxs-lookup"><span data-stu-id="242e6-124">See Also</span></span>  
 [<span data-ttu-id="242e6-125">データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="242e6-125">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  

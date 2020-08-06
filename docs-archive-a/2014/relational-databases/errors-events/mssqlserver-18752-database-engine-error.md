---
title: MSSQLSERVER_18752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a463e4019875f4a233ae2920f32bc2252376a41c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640040"
---
# <a name="mssqlserver_18752"></a><span data-ttu-id="12bf4-102">MSSQLSERVER_18752</span><span class="sxs-lookup"><span data-stu-id="12bf4-102">MSSQLSERVER_18752</span></span>
    
## <a name="details"></a><span data-ttu-id="12bf4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="12bf4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12bf4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="12bf4-104">Product Name</span></span>|<span data-ttu-id="12bf4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="12bf4-105">SQL Server</span></span>|  
|<span data-ttu-id="12bf4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="12bf4-106">Event ID</span></span>|<span data-ttu-id="12bf4-107">18752</span><span class="sxs-lookup"><span data-stu-id="12bf4-107">18752</span></span>|  
|<span data-ttu-id="12bf4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="12bf4-108">Event Source</span></span>|<span data-ttu-id="12bf4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="12bf4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="12bf4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="12bf4-110">Component</span></span>|<span data-ttu-id="12bf4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="12bf4-111">SQLEngine</span></span>|  
|<span data-ttu-id="12bf4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="12bf4-112">Symbolic Name</span></span>|<span data-ttu-id="12bf4-113">REPL_INUSE</span><span class="sxs-lookup"><span data-stu-id="12bf4-113">REPL_INUSE</span></span>|  
|<span data-ttu-id="12bf4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="12bf4-114">Message Text</span></span>|<span data-ttu-id="12bf4-115">同時にデータベースに接続できるログ リーダー エージェントまたはログ関連のプロシージャ (sp_repldone、sp_replcmds、および sp_replshowcmds) は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="12bf4-115">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="12bf4-116">ログ関連のプロシージャを実行した場合、そのプロシージャが実行された接続を削除するか、その接続に対して sp_replflush を実行してから、ログ リーダー エージェントを開始するか、別のログ関連のプロシージャを実行してください。</span><span class="sxs-lookup"><span data-stu-id="12bf4-116">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12bf4-117">説明</span><span class="sxs-lookup"><span data-stu-id="12bf4-117">Explanation</span></span>  
 <span data-ttu-id="12bf4-118">同時にデータベースに接続できるログ リーダー エージェントまたはログ関連のプロシージャは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="12bf4-118">Only one Log Reader agent or log-related procedure can connect to a database at a time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12bf4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="12bf4-119">User Action</span></span>  
 <span data-ttu-id="12bf4-120">同じパブリッシング データベースに対して他のログ リーダーが実行されていないこと、および sp_replcmds/sp_repltrans/sp_repldone を実行した後に、running sp_replflush を実行していない、または切断していないアクティブな接続が他にないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="12bf4-120">Make sure no other logreader is running for the same publishing database, and no other active connection had previously run sp_replcmds/sp_repltrans/sp_repldone without running sp_replflush afterwards or disconnecting.</span></span>  
  
  

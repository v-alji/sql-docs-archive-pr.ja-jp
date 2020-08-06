---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34414754ea9d25ad89f6aba767197eb1dfc10d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640991"
---
# <a name="mssqlserver_3151"></a><span data-ttu-id="a60a8-102">MSSQLSERVER_3151</span><span class="sxs-lookup"><span data-stu-id="a60a8-102">MSSQLSERVER_3151</span></span>
    
## <a name="details"></a><span data-ttu-id="a60a8-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a60a8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a60a8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a60a8-104">Product Name</span></span>|<span data-ttu-id="a60a8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a60a8-105">SQL Server</span></span>|  
|<span data-ttu-id="a60a8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a60a8-106">Event ID</span></span>|<span data-ttu-id="a60a8-107">3151</span><span class="sxs-lookup"><span data-stu-id="a60a8-107">3151</span></span>|  
|<span data-ttu-id="a60a8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a60a8-108">Event Source</span></span>|<span data-ttu-id="a60a8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a60a8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a60a8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a60a8-110">Component</span></span>|<span data-ttu-id="a60a8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a60a8-111">SQLEngine</span></span>|  
|<span data-ttu-id="a60a8-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a60a8-112">Symbolic Name</span></span>|<span data-ttu-id="a60a8-113">LDDB_MASTER_LOAD_FAILED</span><span class="sxs-lookup"><span data-stu-id="a60a8-113">LDDB_MASTER_LOAD_FAILED</span></span>|  
|<span data-ttu-id="a60a8-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a60a8-114">Message Text</span></span>|<span data-ttu-id="a60a8-115">master データベースを復元できませんでした。</span><span class="sxs-lookup"><span data-stu-id="a60a8-115">Failed to restore master database.</span></span> <span data-ttu-id="a60a8-116">SQL Server をシャットダウンしています。</span><span class="sxs-lookup"><span data-stu-id="a60a8-116">Shutting down SQL Server.</span></span> <span data-ttu-id="a60a8-117">エラー ログを確認し、master データベースを再構築してください。</span><span class="sxs-lookup"><span data-stu-id="a60a8-117">Check the error logs, and rebuild the master database.</span></span> <span data-ttu-id="a60a8-118">master データベースを再構築する方法の詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a60a8-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a60a8-119">説明</span><span class="sxs-lookup"><span data-stu-id="a60a8-119">Explanation</span></span>  
 <span data-ttu-id="a60a8-120">これは一般エラー メッセージであり、**master** データベースに関するさまざまな問題を示しています。</span><span class="sxs-lookup"><span data-stu-id="a60a8-120">This is a general error message indicating various problems with the **master** database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a60a8-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a60a8-121">User Action</span></span>  
 <span data-ttu-id="a60a8-122">詳細については、エラー ログを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a60a8-122">Check the error logs for more information.</span></span> <span data-ttu-id="a60a8-123">使用可能な **master** データベースを作成するには、REBUILDDATABASE オプションを使用して Setup.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="a60a8-123">To create a usable **master** database, run Setup.exe with the REBUILDDATABASE option.</span></span> <span data-ttu-id="a60a8-124">詳細については、SQL Server オンライン ブックの「方法:コマンド プロンプトからの SQL Server のインストール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a60a8-124">For more information see "How to: Install SQL Server from the Command Prompt" in SQL Server Books Online.</span></span>  
  
  

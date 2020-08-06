---
title: MSSQLSERVER_17132 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 609b9cea138db15cefd002f494620b5a1da7b208
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715353"
---
# <a name="mssqlserver_17132"></a><span data-ttu-id="dbbac-102">MSSQLSERVER_17132</span><span class="sxs-lookup"><span data-stu-id="dbbac-102">MSSQLSERVER_17132</span></span>
    
## <a name="details"></a><span data-ttu-id="dbbac-103">詳細</span><span class="sxs-lookup"><span data-stu-id="dbbac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dbbac-104">製品名</span><span class="sxs-lookup"><span data-stu-id="dbbac-104">Product Name</span></span>|<span data-ttu-id="dbbac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dbbac-105">SQL Server</span></span>|  
|<span data-ttu-id="dbbac-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="dbbac-106">Event ID</span></span>|<span data-ttu-id="dbbac-107">17132</span><span class="sxs-lookup"><span data-stu-id="dbbac-107">17132</span></span>|  
|<span data-ttu-id="dbbac-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="dbbac-108">Event Source</span></span>|<span data-ttu-id="dbbac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dbbac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dbbac-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="dbbac-110">Component</span></span>|<span data-ttu-id="dbbac-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dbbac-111">SQLEngine</span></span>|  
|<span data-ttu-id="dbbac-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="dbbac-112">Symbolic Name</span></span>|<span data-ttu-id="dbbac-113">INIT_NODESSPACE</span><span class="sxs-lookup"><span data-stu-id="dbbac-113">INIT_NODESSPACE</span></span>|  
|<span data-ttu-id="dbbac-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="dbbac-114">Message Text</span></span>|<span data-ttu-id="dbbac-115">記述子用のメモリが不足しているので、サーバーのスタートアップに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="dbbac-115">Server startup failed due to insufficient memory for descriptor.</span></span> <span data-ttu-id="dbbac-116">不要なメモリ負荷を減らすか、システム メモリを増やしてください。</span><span class="sxs-lookup"><span data-stu-id="dbbac-116">Reduce non-essential memory load or increase system memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dbbac-117">説明</span><span class="sxs-lookup"><span data-stu-id="dbbac-117">Explanation</span></span>  
 <span data-ttu-id="dbbac-118">サーバー内部の記述子を格納するための十分なメモリの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="dbbac-118">Failed to allocate enough memory to store server internal descriptor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dbbac-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="dbbac-119">User Action</span></span>  
 <span data-ttu-id="dbbac-120">コンピューターにメモリを追加してください。</span><span class="sxs-lookup"><span data-stu-id="dbbac-120">Add more memory to the machine.</span></span> <span data-ttu-id="dbbac-121">一般的なメモリのトラブルシューティング手順を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dbbac-121">Generic memory troubleshooting steps may be useful.</span></span>  
  
  

---
title: MSSQLSERVER_8642 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e30296fa569599b91ca74edc7535d330119e1680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642819"
---
# <a name="mssqlserver_8642"></a><span data-ttu-id="d53c5-102">MSSQLSERVER_8642</span><span class="sxs-lookup"><span data-stu-id="d53c5-102">MSSQLSERVER_8642</span></span>
    
## <a name="details"></a><span data-ttu-id="d53c5-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d53c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d53c5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d53c5-104">Product Name</span></span>|<span data-ttu-id="d53c5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d53c5-105">SQL Server</span></span>|  
|<span data-ttu-id="d53c5-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d53c5-106">Event ID</span></span>|<span data-ttu-id="d53c5-107">8642</span><span class="sxs-lookup"><span data-stu-id="d53c5-107">8642</span></span>|  
|<span data-ttu-id="d53c5-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d53c5-108">Event Source</span></span>|<span data-ttu-id="d53c5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d53c5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d53c5-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d53c5-110">Component</span></span>|<span data-ttu-id="d53c5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d53c5-111">SQLEngine</span></span>|  
|<span data-ttu-id="d53c5-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d53c5-112">Symbolic Name</span></span>|<span data-ttu-id="d53c5-113">EXCHNGSTART_ERR</span><span class="sxs-lookup"><span data-stu-id="d53c5-113">EXCHNGSTART_ERR</span></span>|  
|<span data-ttu-id="d53c5-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d53c5-114">Message Text</span></span>|<span data-ttu-id="d53c5-115">クエリ プロセッサは、クエリの並列実行に必要なスレッド リソースを開始できませんでした。</span><span class="sxs-lookup"><span data-stu-id="d53c5-115">The query processor could not start the necessary thread resources for parallel query execution.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d53c5-116">説明</span><span class="sxs-lookup"><span data-stu-id="d53c5-116">Explanation</span></span>  
 <span data-ttu-id="d53c5-117">サーバー上のスレッド リソースが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d53c5-117">Thread resources are low in the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d53c5-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d53c5-118">User Action</span></span>  
 <span data-ttu-id="d53c5-119">サーバーの負荷を軽減してからクエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="d53c5-119">Reduce load on the server, and run the query again.</span></span>  
  
  

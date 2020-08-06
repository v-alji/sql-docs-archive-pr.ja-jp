---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 261d352084e490fb7f9216e1a7e352542e85a6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640042"
---
# <a name="mssqlserver_1807"></a><span data-ttu-id="d98e9-102">MSSQLSERVER_1807</span><span class="sxs-lookup"><span data-stu-id="d98e9-102">MSSQLSERVER_1807</span></span>
    
## <a name="details"></a><span data-ttu-id="d98e9-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d98e9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d98e9-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d98e9-104">Product Name</span></span>|<span data-ttu-id="d98e9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d98e9-105">SQL Server</span></span>|  
|<span data-ttu-id="d98e9-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d98e9-106">Event ID</span></span>|<span data-ttu-id="d98e9-107">1807</span><span class="sxs-lookup"><span data-stu-id="d98e9-107">1807</span></span>|  
|<span data-ttu-id="d98e9-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d98e9-108">Event Source</span></span>|<span data-ttu-id="d98e9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d98e9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d98e9-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d98e9-110">Component</span></span>|<span data-ttu-id="d98e9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d98e9-111">SQLEngine</span></span>|  
|<span data-ttu-id="d98e9-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d98e9-112">Symbolic Name</span></span>|<span data-ttu-id="d98e9-113">CANNOT_EX_LOCK</span><span class="sxs-lookup"><span data-stu-id="d98e9-113">CANNOT_EX_LOCK</span></span>|  
|<span data-ttu-id="d98e9-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d98e9-114">Message Text</span></span>|<span data-ttu-id="d98e9-115">データベース '%.\*ls' を排他的にロックできませんでした。</span><span class="sxs-lookup"><span data-stu-id="d98e9-115">Could not obtain exclusive lock on database '%.\*ls'.</span></span> <span data-ttu-id="d98e9-116">後でこの操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="d98e9-116">Retry the operation later.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d98e9-117">説明</span><span class="sxs-lookup"><span data-stu-id="d98e9-117">Explanation</span></span>  
 <span data-ttu-id="d98e9-118">データベースに対して排他的なアクセスを必要とする操作で、排他ロックを獲得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="d98e9-118">An operation that required exclusive access to the database was unable to obtain it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d98e9-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d98e9-119">User Action</span></span>  
 <span data-ttu-id="d98e9-120">このデータベースに対する接続をすべて切断するか、クエリを後で再試行します。</span><span class="sxs-lookup"><span data-stu-id="d98e9-120">Disconnect all the connections to that database or try the query again later.</span></span>  
  
  

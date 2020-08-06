---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f98c831642580587552bf60c604d84c38fffca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643846"
---
# <a name="mssqlserver_5245"></a><span data-ttu-id="346b2-102">MSSQLSERVER_5245</span><span class="sxs-lookup"><span data-stu-id="346b2-102">MSSQLSERVER_5245</span></span>
    
## <a name="details"></a><span data-ttu-id="346b2-103">詳細</span><span class="sxs-lookup"><span data-stu-id="346b2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="346b2-104">製品名</span><span class="sxs-lookup"><span data-stu-id="346b2-104">Product Name</span></span>|<span data-ttu-id="346b2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="346b2-105">SQL Server</span></span>|  
|<span data-ttu-id="346b2-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="346b2-106">Event ID</span></span>|<span data-ttu-id="346b2-107">5245</span><span class="sxs-lookup"><span data-stu-id="346b2-107">5245</span></span>|  
|<span data-ttu-id="346b2-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="346b2-108">Event Source</span></span>|<span data-ttu-id="346b2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="346b2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="346b2-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="346b2-110">Component</span></span>|<span data-ttu-id="346b2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="346b2-111">SQLEngine</span></span>|  
|<span data-ttu-id="346b2-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="346b2-112">Symbolic Name</span></span>|<span data-ttu-id="346b2-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="346b2-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span></span>|  
|<span data-ttu-id="346b2-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="346b2-114">Message Text</span></span>|<span data-ttu-id="346b2-115">オブジェクト ID O_ID (オブジェクト 'NAME'):DBCC ではこのオブジェクトをロックできませんでした。ロック要求がタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="346b2-115">Object ID O_ID (object 'NAME'): DBCC could not obtain a lock on this object because the lock request time-out period was exceeded.</span></span> <span data-ttu-id="346b2-116">このオブジェクトはスキップされたので、処理されません。</span><span class="sxs-lookup"><span data-stu-id="346b2-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="346b2-117">説明</span><span class="sxs-lookup"><span data-stu-id="346b2-117">Explanation</span></span>  
 <span data-ttu-id="346b2-118">DBCC が、指定されたオブジェクト用にテーブルのロック獲得を待機している間に、ロック要求のタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="346b2-118">A lock time-out occurred while DBCC was waiting on a table lock for the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="346b2-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="346b2-119">User Action</span></span>  
 <span data-ttu-id="346b2-120">DBCC コマンドを再実行します。</span><span class="sxs-lookup"><span data-stu-id="346b2-120">Rerun the DBCC command.</span></span>  
  
  

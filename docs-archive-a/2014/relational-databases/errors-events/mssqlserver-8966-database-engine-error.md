---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d3a12d5d0732ba8694db3d4c7dcae1eac59d28b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646165"
---
# <a name="mssqlserver_8966"></a><span data-ttu-id="94ff7-102">MSSQLSERVER_8966</span><span class="sxs-lookup"><span data-stu-id="94ff7-102">MSSQLSERVER_8966</span></span>
    
## <a name="details"></a><span data-ttu-id="94ff7-103">詳細</span><span class="sxs-lookup"><span data-stu-id="94ff7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94ff7-104">製品名</span><span class="sxs-lookup"><span data-stu-id="94ff7-104">Product Name</span></span>|<span data-ttu-id="94ff7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="94ff7-105">SQL Server</span></span>|  
|<span data-ttu-id="94ff7-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="94ff7-106">Event ID</span></span>|<span data-ttu-id="94ff7-107">8966</span><span class="sxs-lookup"><span data-stu-id="94ff7-107">8966</span></span>|  
|<span data-ttu-id="94ff7-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="94ff7-108">Event Source</span></span>|<span data-ttu-id="94ff7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="94ff7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="94ff7-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="94ff7-110">Component</span></span>|<span data-ttu-id="94ff7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="94ff7-111">SQLEngine</span></span>|  
|<span data-ttu-id="94ff7-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="94ff7-112">Symbolic Name</span></span>|<span data-ttu-id="94ff7-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span><span class="sxs-lookup"><span data-stu-id="94ff7-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span></span>|  
|<span data-ttu-id="94ff7-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="94ff7-114">Message Text</span></span>|<span data-ttu-id="94ff7-115">ラッチ型 TYPE のページ P_ID を読み取ってラッチすることができません。</span><span class="sxs-lookup"><span data-stu-id="94ff7-115">Unable to read and latch page P_ID with latch type TYPE.</span></span> <span data-ttu-id="94ff7-116">OPERATION が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="94ff7-116">OPERATION failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="94ff7-117">説明</span><span class="sxs-lookup"><span data-stu-id="94ff7-117">Explanation</span></span>  
 <span data-ttu-id="94ff7-118">ページの読み取りに失敗したか、PFS ページまたは GAM ページでラッチを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="94ff7-118">The page read failed or a latch could not be taken on a PFS or GAM page.</span></span> <span data-ttu-id="94ff7-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに、ラッチ タイムアウトまたは他の添付メッセージが記録される場合があります。</span><span class="sxs-lookup"><span data-stu-id="94ff7-119">There may be latch time-out or other accompanying messages in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94ff7-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="94ff7-120">User Action</span></span>  
 <span data-ttu-id="94ff7-121">SQL エラー ログの添付メッセージを確認し、これらのエラーを解決します。</span><span class="sxs-lookup"><span data-stu-id="94ff7-121">Review the SQL error log for accompanying messages and resolve these errors.</span></span>  
  
  

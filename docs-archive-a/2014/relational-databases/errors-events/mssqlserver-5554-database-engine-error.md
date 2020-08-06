---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5095a50f257abafb6ebde97bb32c57bc71fc4e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641682"
---
# <a name="mssqlserver_5554"></a><span data-ttu-id="500aa-102">MSSQLSERVER_5554</span><span class="sxs-lookup"><span data-stu-id="500aa-102">MSSQLSERVER_5554</span></span>
    
## <a name="details"></a><span data-ttu-id="500aa-103">詳細</span><span class="sxs-lookup"><span data-stu-id="500aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="500aa-104">製品名</span><span class="sxs-lookup"><span data-stu-id="500aa-104">Product Name</span></span>|<span data-ttu-id="500aa-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="500aa-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="500aa-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="500aa-106">Event ID</span></span>|<span data-ttu-id="500aa-107">5554</span><span class="sxs-lookup"><span data-stu-id="500aa-107">5554</span></span>|  
|<span data-ttu-id="500aa-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="500aa-108">Event Source</span></span>|<span data-ttu-id="500aa-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="500aa-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="500aa-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="500aa-110">Component</span></span>|<span data-ttu-id="500aa-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="500aa-111">SQLEngine</span></span>|  
|<span data-ttu-id="500aa-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="500aa-112">Symbolic Name</span></span>|<span data-ttu-id="500aa-113">FS_MINIVER_OVERFLOW</span><span class="sxs-lookup"><span data-stu-id="500aa-113">FS_MINIVER_OVERFLOW</span></span>|  
|<span data-ttu-id="500aa-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="500aa-114">Message Text</span></span>|<span data-ttu-id="500aa-115">1 つのファイルのバージョンの総数が、ファイル システムで設定されている上限に達しました。</span><span class="sxs-lookup"><span data-stu-id="500aa-115">The total number of versions for a single file has reached the maximum limit set by the file system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="500aa-116">説明</span><span class="sxs-lookup"><span data-stu-id="500aa-116">Explanation</span></span>  
 <span data-ttu-id="500aa-117">複数のアクティブな結果セット (MARS) またはトリガーのシナリオでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はオペレーティング システムによって指定されたミニバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="500aa-117">In multiple active result sets (MARS) or trigger scenarios, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the miniversion specified by the operating system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="500aa-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="500aa-118">User Action</span></span>  
 <span data-ttu-id="500aa-119">同じトランザクション内のデータを繰り返し更新しないようにします。</span><span class="sxs-lookup"><span data-stu-id="500aa-119">Try to avoid repeated updates to the data in the same transaction.</span></span>  
  
  

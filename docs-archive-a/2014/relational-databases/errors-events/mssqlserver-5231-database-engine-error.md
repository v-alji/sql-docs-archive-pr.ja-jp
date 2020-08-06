---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 68f40ac3a566280526757bd8b83c784954ba3dde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713182"
---
# <a name="mssqlserver_5231"></a><span data-ttu-id="049ea-102">MSSQLSERVER_5231</span><span class="sxs-lookup"><span data-stu-id="049ea-102">MSSQLSERVER_5231</span></span>
    
## <a name="details"></a><span data-ttu-id="049ea-103">詳細</span><span class="sxs-lookup"><span data-stu-id="049ea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="049ea-104">製品名</span><span class="sxs-lookup"><span data-stu-id="049ea-104">Product Name</span></span>|<span data-ttu-id="049ea-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="049ea-105">SQL Server</span></span>|  
|<span data-ttu-id="049ea-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="049ea-106">Event ID</span></span>|<span data-ttu-id="049ea-107">5231</span><span class="sxs-lookup"><span data-stu-id="049ea-107">5231</span></span>|  
|<span data-ttu-id="049ea-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="049ea-108">Event Source</span></span>|<span data-ttu-id="049ea-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="049ea-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="049ea-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="049ea-110">Component</span></span>|<span data-ttu-id="049ea-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="049ea-111">SQLEngine</span></span>|  
|<span data-ttu-id="049ea-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="049ea-112">Symbolic Name</span></span>|<span data-ttu-id="049ea-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span><span class="sxs-lookup"><span data-stu-id="049ea-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span></span>|  
|<span data-ttu-id="049ea-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="049ea-114">Message Text</span></span>|<span data-ttu-id="049ea-115">オブジェクト ID O_ID (オブジェクト 'NAME'):このオブジェクトを確認のためにロックしようとして、デッドロックが発生しました。</span><span class="sxs-lookup"><span data-stu-id="049ea-115">Object ID O_ID (object 'NAME'): A deadlock occurred while trying to lock this object for checking.</span></span> <span data-ttu-id="049ea-116">このオブジェクトはスキップされたので、処理されません。</span><span class="sxs-lookup"><span data-stu-id="049ea-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="049ea-117">説明</span><span class="sxs-lookup"><span data-stu-id="049ea-117">Explanation</span></span>  
 <span data-ttu-id="049ea-118">DBCC がオブジェクトをロックしようとしてデッドロックが発生し、DBCC がデッドロック対象として選択されました。</span><span class="sxs-lookup"><span data-stu-id="049ea-118">A deadlock occurred when DBCC was trying to lock the object, and DBCC was chosen as the deadlock victim.</span></span> <span data-ttu-id="049ea-119">このオブジェクトは処理されません。</span><span class="sxs-lookup"><span data-stu-id="049ea-119">The object will not be processed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="049ea-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="049ea-120">User Action</span></span>  
 <span data-ttu-id="049ea-121">なし</span><span class="sxs-lookup"><span data-stu-id="049ea-121">None</span></span>  
  
  

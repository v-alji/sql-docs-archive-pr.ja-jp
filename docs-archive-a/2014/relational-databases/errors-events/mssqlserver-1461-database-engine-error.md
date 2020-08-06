---
title: MSSQLSERVER_1461 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6667728b2cc134632ddc538b662d73533ee4d6ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643913"
---
# <a name="mssqlserver_1461"></a><span data-ttu-id="e1ad4-102">MSSQLSERVER_1461</span><span class="sxs-lookup"><span data-stu-id="e1ad4-102">MSSQLSERVER_1461</span></span>
    
## <a name="details"></a><span data-ttu-id="e1ad4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e1ad4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1ad4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e1ad4-104">Product Name</span></span>|<span data-ttu-id="e1ad4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e1ad4-105">SQL Server</span></span>|  
|<span data-ttu-id="e1ad4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e1ad4-106">Event ID</span></span>|<span data-ttu-id="e1ad4-107">1461</span><span class="sxs-lookup"><span data-stu-id="e1ad4-107">1461</span></span>|  
|<span data-ttu-id="e1ad4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e1ad4-108">Event Source</span></span>|<span data-ttu-id="e1ad4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e1ad4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e1ad4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e1ad4-110">Component</span></span>|<span data-ttu-id="e1ad4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e1ad4-111">SQLEngine</span></span>|  
|<span data-ttu-id="e1ad4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e1ad4-112">Symbolic Name</span></span>|<span data-ttu-id="e1ad4-113">DBM_SAFETY_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="e1ad4-113">DBM_SAFETY_MISMATCH</span></span>|  
|<span data-ttu-id="e1ad4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e1ad4-114">Message Text</span></span>|<span data-ttu-id="e1ad4-115">データベース "%.\*ls" で、データベース ミラーリングの安全性レベルがサーバー間で異なることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="e1ad4-115">Different database mirroring safety levels among servers were detected for database "%.\*ls".</span></span> <span data-ttu-id="e1ad4-116">FULL 安全性レベルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1ad4-116">The FULL safety level will be used.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1ad4-117">説明</span><span class="sxs-lookup"><span data-stu-id="e1ad4-117">Explanation</span></span>  
 <span data-ttu-id="e1ad4-118">トランザクションの安全性設定がプリンシパル データベースとミラー データベースで一致しなかったため、トランザクションの安全性レベルの変更時にミラーリング接続が切断されました。</span><span class="sxs-lookup"><span data-stu-id="e1ad4-118">Mirroring connections were broken when the transaction safety level was modified because the transaction safety settings were inconsistent on the principal and mirror databases.</span></span> <span data-ttu-id="e1ad4-119">既定では、トランザクションの安全性が FULL の安全性設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1ad4-119">The default safety setting of full-transaction safety will be used.</span></span> <span data-ttu-id="e1ad4-120">セッションは高い安全モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e1ad4-120">The session will run in high-safety mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1ad4-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e1ad4-121">User Action</span></span>  
 <span data-ttu-id="e1ad4-122">トランザクションの安全性を OFF に設定するには、プリンシパル データベースで ALTER DATABASE *database_name* SET PARTNER SAFETY OFF ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="e1ad4-122">To set transaction safety off, rerun the ALTER DATABASE *database_name* SET PARTNER SAFETY OFF statement on the principal database.</span></span>  
  
  

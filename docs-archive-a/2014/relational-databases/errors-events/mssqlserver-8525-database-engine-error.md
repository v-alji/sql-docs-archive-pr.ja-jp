---
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 36db48ca2a9afd08dadcd12abc13b9978e227b00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642824"
---
# <a name="mssqlserver_8525"></a><span data-ttu-id="2590e-102">MSSQLSERVER_8525</span><span class="sxs-lookup"><span data-stu-id="2590e-102">MSSQLSERVER_8525</span></span>
    
## <a name="details"></a><span data-ttu-id="2590e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2590e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2590e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2590e-104">Product Name</span></span>|<span data-ttu-id="2590e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2590e-105">SQL Server</span></span>|  
|<span data-ttu-id="2590e-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2590e-106">Event ID</span></span>|<span data-ttu-id="2590e-107">8525</span><span class="sxs-lookup"><span data-stu-id="2590e-107">8525</span></span>|  
|<span data-ttu-id="2590e-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2590e-108">Event Source</span></span>|<span data-ttu-id="2590e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2590e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2590e-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2590e-110">Component</span></span>|<span data-ttu-id="2590e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2590e-111">SQLEngine</span></span>|  
|<span data-ttu-id="2590e-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2590e-112">Symbolic Name</span></span>||  
|<span data-ttu-id="2590e-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2590e-113">Message Text</span></span>|<span data-ttu-id="2590e-114">分散トランザクションが完了しました。</span><span class="sxs-lookup"><span data-stu-id="2590e-114">Distributed transaction completed.</span></span> <span data-ttu-id="2590e-115">このセッションを新規トランザクションまたは NULL トランザクションのいずれかに参加させます。</span><span class="sxs-lookup"><span data-stu-id="2590e-115">Either enlist this session in a new transaction or the NULL transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2590e-116">説明</span><span class="sxs-lookup"><span data-stu-id="2590e-116">Explanation</span></span>  
 <span data-ttu-id="2590e-117">分散トランザクション コーディネーターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用するプログラミング モデルでは、分散トランザクションに対してアプリケーションを明示的に参加させたり参加を解除したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2590e-117">The programming model for using the Distributed Transaction Coordinator with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires applications to explicitly enlist to and defect from a distributed transaction.</span></span>  
  
 <span data-ttu-id="2590e-118">このエラーは、次の 4 つの条件が揃った場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2590e-118">This error occurs when the following four conditions are met:</span></span>  
  
-   <span data-ttu-id="2590e-119">アプリケーションが分散トランザクションに参加している。</span><span class="sxs-lookup"><span data-stu-id="2590e-119">The application has enlisted into a distributed transaction.</span></span>  
  
-   <span data-ttu-id="2590e-120">トランザクションが、何かの理由でコミットまたはロールバックされた状態で終了した。</span><span class="sxs-lookup"><span data-stu-id="2590e-120">The transaction has ended, either committed or rolled back, for any reason.</span></span>  
  
-   <span data-ttu-id="2590e-121">ユーザー アプリケーションが、分散トランザクションへの参加を明示的に解除されていないか、新しい分散トランザクションに明示的に参加していない。</span><span class="sxs-lookup"><span data-stu-id="2590e-121">The user application has not explicitly defected from a distributed transaction or explicitly enlisted into a new distributed transaction.</span></span>  
  
-   <span data-ttu-id="2590e-122">既存の分散トランザクションへの参加の解除でも新しい分散トランザクションへの参加でもないトランザクション操作、たとえば、クエリの実行やローカル トランザクションの開始を、アプリケーションで試行している。</span><span class="sxs-lookup"><span data-stu-id="2590e-122">The application tries to do any transactional operation other than defecting from existing distributed transaction or enlisting to a new distributed transaction, such as issuing a query or starting a local transaction.</span></span>  
  
 <span data-ttu-id="2590e-123">ローカル トランザクションを作成する操作をアプリケーションで実行している場合はエラー状態 1 が使用され、バインドされたセッションへの参加をアプリケーションで試みている場合はエラー状態 2 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2590e-123">Error state 1 is used when the application performs an operation that creates local transactions, and state 2 is used when application tries to enlist to a bound session.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2590e-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2590e-124">User Action</span></span>  
 <span data-ttu-id="2590e-125">アプリケーションは、分散トランザクションに参加した後、その分散トランザクションへの参加を明示的に解除するか、別の分散トランザクションに参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2590e-125">After an application has enlisted into a distributed transaction, the application must explicitly defect from the distributed transaction or enlist to another distributed transaction.</span></span> <span data-ttu-id="2590e-126">これにより、前のトランザクションへの参加が暗黙的に解除されます。</span><span class="sxs-lookup"><span data-stu-id="2590e-126">This will implicitly defect from a previous enlisted transaction.</span></span> <span data-ttu-id="2590e-127">分散トランザクションへの参加やその解除を行うための正確な構文については、アプリケーションのプログラミング インターフェイス マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2590e-127">For the exact syntax to defect from or enlist to a distributed transaction, see the programming interface manual for the application.</span></span>  
  
  

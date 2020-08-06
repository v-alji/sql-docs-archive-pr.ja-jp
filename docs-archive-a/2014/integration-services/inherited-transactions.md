---
title: 継承されたトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ecb480420fe9f2492c29fad37ee3cc6e6501e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641155"
---
# <a name="inherited-transactions"></a><span data-ttu-id="87e27-102">トランザクションの継承</span><span class="sxs-lookup"><span data-stu-id="87e27-102">Inherited Transactions</span></span>
  <span data-ttu-id="87e27-103">パッケージでパッケージ実行タスクを使用して、別のパッケージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="87e27-103">A package can run another package by using the Execute Package task.</span></span> <span data-ttu-id="87e27-104">パッケージ実行タスクで実行される子パッケージでは、独自のパッケージ トランザクションを作成する場合もあれば、親パッケージのトランザクションを継承する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="87e27-104">The child package, which is the package run by the Execute Package task, may create its own package transaction, or it may inherit the parent package transaction.</span></span>  
  
 <span data-ttu-id="87e27-105">次の 2 つの条件に該当する場合、パッケージは親パッケージのトランザクションを継承します。</span><span class="sxs-lookup"><span data-stu-id="87e27-105">A child package inherits the parent package transaction if both of the following are true:</span></span>  
  
-   <span data-ttu-id="87e27-106">パッケージがパッケージ実行タスクによって呼び出される。</span><span class="sxs-lookup"><span data-stu-id="87e27-106">The package is invoked by an Execute Package task.</span></span>  
  
-   <span data-ttu-id="87e27-107">パッケージを呼び出すパッケージ実行タスクも、親パッケージのトランザクションに参加している。</span><span class="sxs-lookup"><span data-stu-id="87e27-107">The Execute Package task that invoked the package also joined the parent package transaction.</span></span>  
  
 <span data-ttu-id="87e27-108">子パッケージ自身がトランザクションに参加していなければ、子パッケージのコンテナーやタスクは親パッケージのトランザクションに参加できません。</span><span class="sxs-lookup"><span data-stu-id="87e27-108">Containers and tasks in the child package cannot join the parent package transaction unless the child package itself joins the transaction.</span></span>  
  
## <a name="illustration-of-package-transactions"></a><span data-ttu-id="87e27-109">パッケージ トランザクションの図</span><span class="sxs-lookup"><span data-stu-id="87e27-109">Illustration of Package Transactions</span></span>  
 <span data-ttu-id="87e27-110">次の図には、3 個のパッケージがあり、すべてトランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="87e27-110">In the following diagram, there are three packages that all use transactions.</span></span> <span data-ttu-id="87e27-111">各パッケージには、複数のタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87e27-111">Each package contains multiple tasks.</span></span> <span data-ttu-id="87e27-112">トランザクションの動作がわかりやすいように、パッケージ実行タスクは 1 つだけ示されています。</span><span class="sxs-lookup"><span data-stu-id="87e27-112">To emphasize the behavior of the transactions, only the Execute Package tasks are shown.</span></span> <span data-ttu-id="87e27-113">パッケージ A がパッケージ B および C を実行します。次に、パッケージ B がパッケージ D および E を実行し、パッケージ C がパッケージ F を実行します。</span><span class="sxs-lookup"><span data-stu-id="87e27-113">Package A runs packages B and C. In turn, package B runs packages D and E, and package C runs package F.</span></span>  
  
 <span data-ttu-id="87e27-114">パッケージとタスクのトランザクション属性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87e27-114">Packages and tasks have the following transaction attributes:</span></span>  
  
-   <span data-ttu-id="87e27-115">パッケージ A および C の**TransactionOption** は **Required** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="87e27-115">**TransactionOption** is set to **Required** on packages A and C</span></span>  
  
-   <span data-ttu-id="87e27-116">パッケージ B と D、およびパッケージ実行タスク B、パッケージ実行タスク D、パッケージ実行タスク F の**TransactionOption** は **Supported** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="87e27-116">**TransactionOption** is set to **Supported** on packages B and D, and on the tasks Execute Package B, Execute Package D, and Execute Package F.</span></span>  
  
-   <span data-ttu-id="87e27-117">パッケージ E、およびパッケージ実行タスク C、パッケージ実行タスク E の**TransactionOption** は **NotSupported** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="87e27-117">**TransactionOption** is set to **NotSupported** on package E, and on the tasks Execute Package C and Execute Package E.</span></span>  
  
 <span data-ttu-id="87e27-118">![トランザクションの継承フロー](media/mw-dts-executepack.gif "トランザクションの継承フロー")</span><span class="sxs-lookup"><span data-stu-id="87e27-118">![Flow of inherited transactions](media/mw-dts-executepack.gif "Flow of inherited transactions")</span></span>  
  
 <span data-ttu-id="87e27-119">パッケージ B、D、および F のみが親パッケージのトランザクションを継承できます。</span><span class="sxs-lookup"><span data-stu-id="87e27-119">Only packages B, D, and F can inherit transactions from their parent packages.</span></span>  
  
 <span data-ttu-id="87e27-120">パッケージ B および D は、パッケージ A が開始したトランザクションを継承します。</span><span class="sxs-lookup"><span data-stu-id="87e27-120">Packages B and D inherit the transaction that was started by package A.</span></span>  
  
 <span data-ttu-id="87e27-121">パッケージ F はパッケージ C が開始したトランザクションを継承します。</span><span class="sxs-lookup"><span data-stu-id="87e27-121">Package F inherits the transaction that was started by package C.</span></span>  
  
 <span data-ttu-id="87e27-122">パッケージ A および C は独自のトランザクションを制御します。</span><span class="sxs-lookup"><span data-stu-id="87e27-122">Packages A and C control their own transactions.</span></span>  
  
 <span data-ttu-id="87e27-123">パッケージ E はトランザクションを使用しません。</span><span class="sxs-lookup"><span data-stu-id="87e27-123">Package E does not use transactions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="87e27-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="87e27-124">Related Tasks</span></span>  
 [<span data-ttu-id="87e27-125">トランザクションを使用するようにパッケージを構成する</span><span class="sxs-lookup"><span data-stu-id="87e27-125">Configure a Package to Use Transactions</span></span>](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  

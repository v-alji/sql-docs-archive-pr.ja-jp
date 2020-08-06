---
title: 'チュートリアル: ポリシーベースの管理を使用したベストプラクティスの評価 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- best practices analyzer
- Policy-Based Management, best practices policies
- Best Practices [Database Engine]
- Policy-Based Management, evaluating policies
- BPA
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: c7867f9b-7acc-4fae-bde1-63808c403ebc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 42e6b505c71abecce7b56b5cb2544b4e9f4e8f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717043"
---
# <a name="tutorial-evaluating-best-practices-by-using-policy-based-management"></a><span data-ttu-id="362a8-102">チュートリアル:ポリシー ベースの管理を使用したベスト プラクティスの評価</span><span class="sxs-lookup"><span data-stu-id="362a8-102">Tutorial: Evaluating Best Practices by Using Policy-Based Management</span></span>
  <span data-ttu-id="362a8-103">「ポリシー ベースの管理を使用したベスト プラクティスの評価」チュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="362a8-103">Welcome to the Evaluating Best Practices by Using Policy-Based Management tutorial.</span></span> <span data-ttu-id="362a8-104">このチュートリアルは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] について理解しており、ポリシー ベースの管理を初めて使用するユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="362a8-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but new to Policy-Based Management.</span></span> <span data-ttu-id="362a8-105">ポリシー ベースの管理は、サイト管理の基準を適用するために使用できるポリシーを定義するためのシステムです。</span><span class="sxs-lookup"><span data-stu-id="362a8-105">Policy-Based Management is a system for defining policies that can be used enforce site administration standards.</span></span> <span data-ttu-id="362a8-106">ポリシー ベースの管理には一連のベスト プラクティス ポリシーが含まれており、これらを使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを分析し、インスタンスがベスト プラクティスのガイドラインと推奨事項に適合しているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="362a8-106">Policy-Based Management includes a set of best practices policies that you can use to analyze an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to determine whether the instance meets best practices guidelines and recommendations.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="362a8-107">学習する内容</span><span class="sxs-lookup"><span data-stu-id="362a8-107">What You Will Learn</span></span>  
 <span data-ttu-id="362a8-108">このチュートリアルでは、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]のベスト プラクティス ポリシーを要求時 (アドホック) またはスケジュールに基づいて評価する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="362a8-108">In this tutorial, you will learn how to evaluate best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on an on-demand (or "ad hoc") basis, or on a scheduled basis.</span></span>  
  
 <span data-ttu-id="362a8-109">このチュートリアルは、次の 2 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="362a8-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="362a8-110">レッスン 1:要求に基づくベスト プラクティスの評価</span><span class="sxs-lookup"><span data-stu-id="362a8-110">Lesson 1: Evaluate Best Practices on an On-Demand Basis</span></span>](../../2014/tutorials/lesson-1-evaluate-best-practices-on-an-on-demand-basis.md)  
 <span data-ttu-id="362a8-111">このレッスンでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスに対して、ポリシーの要求時評価を実行します。</span><span class="sxs-lookup"><span data-stu-id="362a8-111">In this lesson, you perform an on-demand evaluation of the policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="362a8-112">レッスン 2: スケジュールに基づくベスト プラクティス ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="362a8-112">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
 <span data-ttu-id="362a8-113">このレッスンでは、スケジュールに基づいてベスト プラクティス ポリシーを実行するよう構成します。</span><span class="sxs-lookup"><span data-stu-id="362a8-113">In this lesson, you configure best practices policies to run on a scheduled basis.</span></span> <span data-ttu-id="362a8-114">このレッスンで、スケジュールされたポリシーを単一インスタンス上で構成する方法と、スケジュールされたポリシーを集中管理された場所から [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の複数インスタンスに配置する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="362a8-114">The lesson shows how to configure scheduled policies on a single instance, and how to deploy scheduled policies from a central location to multiple instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="362a8-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="362a8-115">Requirements</span></span>  
 <span data-ttu-id="362a8-116">このレッスンを学習するには、データベースに関する基礎知識と、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]について基本的に理解していることが必要です。</span><span class="sxs-lookup"><span data-stu-id="362a8-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="362a8-117">このチュートリアルを使用するには、サーバーに [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="362a8-117">To use this tutorial, the server must have [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="362a8-118">チュートリアルを開始する</span><span class="sxs-lookup"><span data-stu-id="362a8-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="362a8-119">レッスン 1:要求に基づくベスト プラクティスの評価</span><span class="sxs-lookup"><span data-stu-id="362a8-119">Lesson 1: Evaluate Best Practices on an On-Demand Basis</span></span>](../../2014/tutorials/lesson-1-evaluate-best-practices-on-an-on-demand-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="362a8-120">参照</span><span class="sxs-lookup"><span data-stu-id="362a8-120">See Also</span></span>  
 [<span data-ttu-id="362a8-121">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="362a8-121">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  

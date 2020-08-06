---
title: 'チュートリアル : ポリシー ベースの管理を使用したサーバーの管理 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: 7de96e7b-9fb8-4cc8-8d85-61345d68a1e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b707a5ecd362c6b3b54e853f89d79e25a9e1428
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634452"
---
# <a name="tutorial-administering-servers-by-using-policy-based-management"></a><span data-ttu-id="ded72-102">チュートリアル:ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="ded72-102">Tutorial: Administering Servers by Using Policy-Based Management</span></span>
  <span data-ttu-id="ded72-103">「ポリシー ベースの管理を使用したサーバーの管理」チュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="ded72-103">Welcome to the Administering Servers by Using Policy-Based Management Policies tutorial.</span></span> <span data-ttu-id="ded72-104">このチュートリアルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] については理解しているが、ポリシー ベースの管理を初めて使用するユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="ded72-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but new to the Policy-Based Management.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="ded72-105">学習する内容</span><span class="sxs-lookup"><span data-stu-id="ded72-105">What You Will Learn</span></span>  
 <span data-ttu-id="ded72-106">このチュートリアルでは、サーバーを管理するポリシー、および単一のデータベースに適用されるポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ded72-106">This tutorial creates a policy to administer your server and a policy that applies to a single database.</span></span> <span data-ttu-id="ded72-107">ポリシーには、準拠していることをテストするために要求に応じて実行されるものと、</span><span class="sxs-lookup"><span data-stu-id="ded72-107">One policy is run on demand to test for compliance.</span></span> <span data-ttu-id="ded72-108">今後の準拠を適用するものがあります。</span><span class="sxs-lookup"><span data-stu-id="ded72-108">The other policy enforces future compliance.</span></span>  
  
 <span data-ttu-id="ded72-109">このチュートリアルは、次の 2 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="ded72-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="ded72-110">レッスン 1:"既定でオフ" ポリシーの作成と適用</span><span class="sxs-lookup"><span data-stu-id="ded72-110">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
 <span data-ttu-id="ded72-111">このレッスンでは、データベース メールをサーバーで有効化しないように指定するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ded72-111">This lesson creates a policy that specifies that Database Mail is not enabled on the server.</span></span> <span data-ttu-id="ded72-112">さらに、サーバーがポリシーに準拠しているかどうかを確認し、データベース メールを無効にしてサーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="ded72-112">Then, it checks to see whether your server complies with the policy, and configures the server by disabling Database Mail.</span></span>  
  
 [<span data-ttu-id="ded72-113">レッスン 2: 名前付け基準ポリシーの作成と適用</span><span class="sxs-lookup"><span data-stu-id="ded72-113">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
 <span data-ttu-id="ded72-114">このレッスンでは、テーブルの名前付け基準を定義して適用するポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ded72-114">This lesson creates a policy that defines and enforces a naming standard for tables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded72-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="ded72-115">Requirements</span></span>  
 <span data-ttu-id="ded72-116">このレッスンを学習するには、データベースに関する基礎知識と、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]について基本的に理解していることが必要です。</span><span class="sxs-lookup"><span data-stu-id="ded72-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ded72-117">このチュートリアルを使用するには、システムに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ded72-117">To use this tutorial, your system must have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="ded72-118">チュートリアルを開始する</span><span class="sxs-lookup"><span data-stu-id="ded72-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="ded72-119">レッスン 1:"既定でオフ" ポリシーの作成と適用</span><span class="sxs-lookup"><span data-stu-id="ded72-119">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="ded72-120">参照</span><span class="sxs-lookup"><span data-stu-id="ded72-120">See Also</span></span>  
 [<span data-ttu-id="ded72-121">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="ded72-121">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  

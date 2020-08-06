---
title: 'レッスン 1 : "既定でオフ" ポリシーの作成と適用 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: d31367db-b7db-44c4-8df2-f1240474cf78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a76df1a72b93d09c5c1c199cb0246dbb51c9cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632424"
---
# <a name="lesson-1-create-and-apply-an-off-by-default-policy"></a><span data-ttu-id="39200-102">レッスン 1:"既定でオフ" ポリシーの作成と適用</span><span class="sxs-lookup"><span data-stu-id="39200-102">Lesson 1: Create and Apply an Off By Default Policy</span></span>
  <span data-ttu-id="39200-103">ポリシー ベースの管理ポリシーを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の複数のインスタンス、複数のインスタンス オブジェクト、1 つのサーバー インスタンス、複数のデータベース、または複数のデータベース オブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="39200-103">Using Policy-Based Management policies, you can administer one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], one or more instance objects, server instances, one or more databases, or one or more database objects.</span></span> <span data-ttu-id="39200-104">データベース管理者は、特定のサーバーでデータベース メールが有効化されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="39200-104">As the database administrator, you want to ensure that certain servers do not have Database Mail enabled.</span></span> <span data-ttu-id="39200-105">このレッスンでは、このようなサーバー オプションを設定する条件およびポリシーを作成し、</span><span class="sxs-lookup"><span data-stu-id="39200-105">In this lesson, you will create a condition and a policy that sets that server option.</span></span> <span data-ttu-id="39200-106">サーバーがこのポリシーに準拠しているかどうかを確認するためにサーバーをテストします。</span><span class="sxs-lookup"><span data-stu-id="39200-106">You will test the server to see whether it complies with the policy.</span></span> <span data-ttu-id="39200-107">次に、このポリシーを使用してサーバーを再構成し、サーバーがポリシーに準拠するようにします。</span><span class="sxs-lookup"><span data-stu-id="39200-107">Then, you will use the policy to reconfigure the server to bring the server into compliance.</span></span>  
  
 <span data-ttu-id="39200-108">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="39200-108">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="39200-109">"既定でオフ" ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="39200-109">Create the Off By Default Policy</span></span>](lesson-1-1-create-the-off-by-default-policy.md)  
  
-   [<span data-ttu-id="39200-110">"既定でオフ" ポリシーを実行するためのサーバーの構成</span><span class="sxs-lookup"><span data-stu-id="39200-110">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="39200-111">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="39200-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="39200-112">"既定でオフ" ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="39200-112">Create the Off By Default Policy</span></span>](lesson-1-1-create-the-off-by-default-policy.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="39200-113">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="39200-113">Next Lesson</span></span>  
 [<span data-ttu-id="39200-114">レッスン 2: 名前付け基準ポリシーの作成と適用</span><span class="sxs-lookup"><span data-stu-id="39200-114">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  

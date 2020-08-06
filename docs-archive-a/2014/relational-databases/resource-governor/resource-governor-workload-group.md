---
title: リソース ガバナー ワークロード グループ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group
- workload groups [SQL Server]
- workload groups [SQL Server], overview
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c6fa8f6fe960571f10d6a8505329fbe8f400e6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715138"
---
# <a name="resource-governor-workload-group"></a><span data-ttu-id="8c567-102">リソース ガバナー ワークロード グループ</span><span class="sxs-lookup"><span data-stu-id="8c567-102">Resource Governor Workload Group</span></span>
  <span data-ttu-id="8c567-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース ガバナーでは、ワークロード グループは分類基準が類似しているセッション要求のコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="8c567-103">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resource Governor, a workload group serves as a container for session requests that have similar classification criteria.</span></span> <span data-ttu-id="8c567-104">ワークロードは、セッションの全体的な監視を可能にし、セッションのポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="8c567-104">A workload allows for aggregate monitoring of the sessions, and defines policies for the sessions.</span></span> <span data-ttu-id="8c567-105">各ワークロード グループはリソース プール内に存在します。リソース プールは [!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンスの物理リソースのサブセットを表します。</span><span class="sxs-lookup"><span data-stu-id="8c567-105">Each workload group is in a resource pool, which represents a subset of the physical resources of an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="8c567-106">セッションの起動時に、リソース ガバナーの分類子によって、セッションは指定されたワークロード グループに割り当てられます。セッションの実行にはワークロード グループに割り当てられたポリシーおよびリソース プールに対して定義されたリソースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c567-106">When a session is started, the Resource Governor classifier assigns the session to a specific workload group, and the session must run using the policies assigned to the workload group and the resources defined for the resource pool.</span></span>  
  
## <a name="workload-group-concepts"></a><span data-ttu-id="8c567-107">ワークロード グループの概念</span><span class="sxs-lookup"><span data-stu-id="8c567-107">Workload Group Concepts</span></span>  
 <span data-ttu-id="8c567-108">ワークロード グループは、分類基準を適用して類似すると判断されたセッション要求のコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="8c567-108">A workload group serves as a container for session requests that are similar according to the classification criteria that are applied to each request.</span></span> <span data-ttu-id="8c567-109">ワークロード グループによって、リソース消費の全体的な監視、およびグループ内のすべての要求に対する一貫したポリシーの適用が可能となります。</span><span class="sxs-lookup"><span data-stu-id="8c567-109">A workload group allows the aggregate monitoring of resource consumption and the application of a uniform policy to all the requests in the group.</span></span> <span data-ttu-id="8c567-110">グループは、そのメンバーに対するポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="8c567-110">A group defines the policies for its members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c567-111">ユーザー定義のワークロード グループは、リソース プール間で移動できます。</span><span class="sxs-lookup"><span data-stu-id="8c567-111">User-defined workload groups can be moved from one resource pool to another.</span></span>  
  
 <span data-ttu-id="8c567-112">リソース ガバナーでは、内部グループと既定のグループの 2 つのワークロード グループが事前に定義されます。</span><span class="sxs-lookup"><span data-stu-id="8c567-112">Resource Governor predefines two workload groups: the internal group and the default group.</span></span> <span data-ttu-id="8c567-113">内部グループとして分類されたグループは変更できませんが、監視することはできます。</span><span class="sxs-lookup"><span data-stu-id="8c567-113">A user cannot change anything classified as an internal group, but can monitor it.</span></span> <span data-ttu-id="8c567-114">次の条件に当てはまる場合は、要求が既定のグループへと分類されます。</span><span class="sxs-lookup"><span data-stu-id="8c567-114">Requests are classified into the default group when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="8c567-115">要求を分類する基準がない。</span><span class="sxs-lookup"><span data-stu-id="8c567-115">There are no criteria to classify a request.</span></span>  
  
-   <span data-ttu-id="8c567-116">要求を存在しないグループに分類しようとした。</span><span class="sxs-lookup"><span data-stu-id="8c567-116">There is an attempt to classify the request into a non-existent group.</span></span>  
  
-   <span data-ttu-id="8c567-117">一般的な分類エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="8c567-117">There is a general classification failure.</span></span>  
  
 <span data-ttu-id="8c567-118">リソース ガバナーには、ワークロード グループを作成、変更、および削除するための DDL ステートメントも用意されています。</span><span class="sxs-lookup"><span data-stu-id="8c567-118">Resource Governor also provides DDL statements for creating, changing, and dropping workload groups.</span></span>  
  
## <a name="workload-group-tasks"></a><span data-ttu-id="8c567-119">ワークロード グループのタスク</span><span class="sxs-lookup"><span data-stu-id="8c567-119">Workload Group Tasks</span></span>  
  
|<span data-ttu-id="8c567-120">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="8c567-120">Task Description</span></span>|<span data-ttu-id="8c567-121">トピック</span><span class="sxs-lookup"><span data-stu-id="8c567-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="8c567-122">ワークロード グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c567-122">Describes how to create a workload group.</span></span>|[<span data-ttu-id="8c567-123">ワークロード グループの作成</span><span class="sxs-lookup"><span data-stu-id="8c567-123">Create a Workload Group</span></span>](create-a-workload-group.md)|  
|<span data-ttu-id="8c567-124">ワークロード グループの設定を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c567-124">Describes how to change workload group settings.</span></span>|[<span data-ttu-id="8c567-125">ワークロード グループの設定の変更</span><span class="sxs-lookup"><span data-stu-id="8c567-125">Change Workload Group Settings</span></span>](change-workload-group-settings.md)|  
|<span data-ttu-id="8c567-126">ワークロード グループを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c567-126">Describes how to delete a workload group.</span></span>|[<span data-ttu-id="8c567-127">ワークロード グループの削除</span><span class="sxs-lookup"><span data-stu-id="8c567-127">Delete a Workload Group</span></span>](delete-a-workload-group.md)|  
  
## <a name="see-also"></a><span data-ttu-id="8c567-128">参照</span><span class="sxs-lookup"><span data-stu-id="8c567-128">See Also</span></span>  
 <span data-ttu-id="8c567-129">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8c567-129">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="8c567-130">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8c567-130">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="8c567-131">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="8c567-131">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="8c567-132">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="8c567-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="8c567-133">[テンプレートを使用してリソース ガバナーを構成する](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="8c567-133">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="8c567-134">リソース ガバナー プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="8c567-134">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  

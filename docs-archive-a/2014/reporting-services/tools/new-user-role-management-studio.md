---
title: '[新しいユーザー ロール] (Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 78201c5ebedd0cdb7f8108b9e6effcaa7fbe87b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716014"
---
# <a name="new-user-role-management-studio"></a><span data-ttu-id="1bbc5-102">[新しいユーザー ロール]\(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1bbc5-102">New User Role (Management Studio)</span></span>
  <span data-ttu-id="1bbc5-103">このページを使用すると、アイテムレベルのロールの定義を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-103">Use this page to create an item-level role definition.</span></span> <span data-ttu-id="1bbc5-104">アイテムレベルのロールの定義とは、レポート サーバーによって管理されるフォルダー、レポート、モデル、リソース、および共有データ ソースに関連してユーザーが実行できるタスクを列挙する、名前付きの一連のタスクです。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-104">An item-level role definition is a named collection of tasks that enumerate the tasks a user can perform in relation to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="1bbc5-105">アイテムレベルのロールの定義の一例として、事前定義された閲覧者ロールがあります。閲覧者ロールは、レポートのエンド ユーザーがフォルダー間の移動やレポートの表示に必要とする操作の種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-105">An example of an item-level role definition is the predefined Browser role that identifies the kinds of actions a report end user might require for navigating folders and viewing reports.</span></span>  
  
 <span data-ttu-id="1bbc5-106">ロールの定義の数は、それほど多くありません。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-106">Role definitions are intended to be few in number.</span></span> <span data-ttu-id="1bbc5-107">ほとんどの組織では、少数のロールの定義しか必要としません。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-107">Most organizations only require a few role definitions.</span></span> <span data-ttu-id="1bbc5-108">ただし、事前定義されたロールの定義が不十分な場合は、既存のロールの定義を変更したり、新しいロールの定義を作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-108">However, if the predefined role definitions are insufficient, you can vary them or create new ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bbc5-109">ロールの定義は、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-109">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="1bbc5-110">レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-110">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1bbc5-111">オプション</span><span class="sxs-lookup"><span data-stu-id="1bbc5-111">Options</span></span>  
 <span data-ttu-id="1bbc5-112">**Name**</span><span class="sxs-lookup"><span data-stu-id="1bbc5-112">**Name**</span></span>  
 <span data-ttu-id="1bbc5-113">ロールの定義名を入力します。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-113">Type the name of the role definition.</span></span> <span data-ttu-id="1bbc5-114">ロールの定義名は、レポート サーバーの名前空間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-114">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="1bbc5-115">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="1bbc5-116">また、スペースおよびいくつかの記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="1bbc5-117">名前を指定するときに使用できない記号は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="1bbc5-118">; ?</span><span class="sxs-lookup"><span data-stu-id="1bbc5-118">; ?</span></span> <span data-ttu-id="1bbc5-119">: \@ & = +、$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="1bbc5-119">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="1bbc5-120">" /</span><span class="sxs-lookup"><span data-stu-id="1bbc5-120">" /</span></span>  
  
 <span data-ttu-id="1bbc5-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="1bbc5-121">**Description**</span></span>  
 <span data-ttu-id="1bbc5-122">ロールの使用方法やロールがサポートする内容を列挙する説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-122">Type a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="1bbc5-123">**タスク**</span><span class="sxs-lookup"><span data-stu-id="1bbc5-123">**Task**</span></span>  
 <span data-ttu-id="1bbc5-124">このロールで実行できるタスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-124">Select the tasks that can be performed through this role.</span></span> <span data-ttu-id="1bbc5-125">新しいタスクを作成したり、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]によってサポートされている既存のタスクを変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-125">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="1bbc5-126">アイテムレベルのロールの定義には、アイテムレベルのタスクのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-126">Only item-level tasks can be used in an item-level role definition.</span></span>  
  
 <span data-ttu-id="1bbc5-127">**タスクの説明**</span><span class="sxs-lookup"><span data-stu-id="1bbc5-127">**Task Description**</span></span>  
 <span data-ttu-id="1bbc5-128">タスクでサポートされる操作または権限を列挙する、タスクの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="1bbc5-128">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbc5-129">参照</span><span class="sxs-lookup"><span data-stu-id="1bbc5-129">See Also</span></span>  
 <span data-ttu-id="1bbc5-130">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="1bbc5-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="1bbc5-131">ロールの定義</span><span class="sxs-lookup"><span data-stu-id="1bbc5-131">Role Definitions</span></span>](../security/role-definitions.md)  
  
  

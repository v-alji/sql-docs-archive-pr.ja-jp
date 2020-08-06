---
title: 新しいシステム ロール (Management Studio) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a744fc78bdd5ae6ef3a37f96ff5ae8cd10f71a80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716017"
---
# <a name="new-system-role-management-studio"></a><span data-ttu-id="ecaef-102">[新しいシステム ロール]\(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ecaef-102">New System Role (Management Studio)</span></span>
  <span data-ttu-id="ecaef-103">このページを使用すると、システムレベルのロールの定義を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ecaef-103">Use this page to create a system-level role definition.</span></span> <span data-ttu-id="ecaef-104">システム ロールの定義には、レポート サーバー全体に適用する、システムレベルのタスクのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecaef-104">A system role definition specifies a set of system-level tasks that apply to a report server as whole.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecaef-105">ロールの定義は、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecaef-105">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="ecaef-106">レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ecaef-106">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ecaef-107">オプション</span><span class="sxs-lookup"><span data-stu-id="ecaef-107">Options</span></span>  
 <span data-ttu-id="ecaef-108">**Name**</span><span class="sxs-lookup"><span data-stu-id="ecaef-108">**Name**</span></span>  
 <span data-ttu-id="ecaef-109">ロールの定義名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ecaef-109">Type the name of the role definition.</span></span> <span data-ttu-id="ecaef-110">ロールの定義名は、レポート サーバーの名前空間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecaef-110">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="ecaef-111">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecaef-111">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="ecaef-112">また、スペースおよびいくつかの記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ecaef-112">It can also include spaces and some symbols.</span></span> <span data-ttu-id="ecaef-113">名前を指定するときに使用できない記号は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ecaef-113">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="ecaef-114">; ?</span><span class="sxs-lookup"><span data-stu-id="ecaef-114">; ?</span></span> <span data-ttu-id="ecaef-115">: \@ & = +、$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="ecaef-115">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="ecaef-116">" /</span><span class="sxs-lookup"><span data-stu-id="ecaef-116">" /</span></span>  
  
 <span data-ttu-id="ecaef-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="ecaef-117">**Description**</span></span>  
 <span data-ttu-id="ecaef-118">ロールの使用方法を説明する場合やロールがサポートする内容を列挙する場合に説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="ecaef-118">Provide a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="ecaef-119">**タスク**</span><span class="sxs-lookup"><span data-stu-id="ecaef-119">**Task**</span></span>  
 <span data-ttu-id="ecaef-120">このロールで実行できるシステムレベル タスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="ecaef-120">Select the system-level tasks that can be performed through this role.</span></span> <span data-ttu-id="ecaef-121">新しいタスクを作成したり、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]によってサポートされている既存のタスクを変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ecaef-121">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ecaef-122">システム ロール定義にはアイテムレベル タスクを選択できません。</span><span class="sxs-lookup"><span data-stu-id="ecaef-122">You cannot choose item-level tasks for a system role definition.</span></span>  
  
 <span data-ttu-id="ecaef-123">**タスクの説明**</span><span class="sxs-lookup"><span data-stu-id="ecaef-123">**Task Description**</span></span>  
 <span data-ttu-id="ecaef-124">タスクでサポートされる操作または権限を列挙する、タスクの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="ecaef-124">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecaef-125">参照</span><span class="sxs-lookup"><span data-stu-id="ecaef-125">See Also</span></span>  
 <span data-ttu-id="ecaef-126">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ecaef-126">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="ecaef-127">ロールの定義</span><span class="sxs-lookup"><span data-stu-id="ecaef-127">Role Definitions</span></span>](../security/role-definitions.md)  
  
  

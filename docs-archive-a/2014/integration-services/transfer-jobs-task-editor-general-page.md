---
title: '[ジョブ転送タスクエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.general.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: 96531920-92d4-4a3b-a38a-6f0c8bc78ada
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d824c1904b8a3ffd0078f778a78dea898ab53577
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710957"
---
# <a name="transfer-jobs-task-editor-general-page"></a><span data-ttu-id="732d2-102">[ジョブ転送タスク エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="732d2-102">Transfer Jobs Task Editor (General Page)</span></span>
  <span data-ttu-id="732d2-103">**[ジョブ転送タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、ジョブ転送タスクの名前と説明を入力できます。</span><span class="sxs-lookup"><span data-stu-id="732d2-103">Use the **General** page of the **Transfer Jobs Task Editor** dialog box to name and describe the Transfer Jobs task.</span></span> <span data-ttu-id="732d2-104">ジョブ転送タスクの詳細については、「 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="732d2-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="732d2-105">転送先サーバー上の **sysadmin** 固定サーバー ロールのメンバー、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント固定データベース ロールのうち 1 つのロールのメンバーだけが、転送先にジョブを正常に作成できます。</span><span class="sxs-lookup"><span data-stu-id="732d2-105">Only members of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles on the destination server can successfully create jobs there.</span></span> <span data-ttu-id="732d2-106">転送元サーバー上のジョブにアクセスするには、ユーザーは少なくとも転送元サーバー上で **SQLAgentUserRole** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="732d2-106">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role there.</span></span> <span data-ttu-id="732d2-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント固定データベース ロールおよびその権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../ssms/agent/sql-server-agent-fixed-database-roles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="732d2-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="732d2-108">オプション</span><span class="sxs-lookup"><span data-stu-id="732d2-108">Options</span></span>  
 <span data-ttu-id="732d2-109">**Name**</span><span class="sxs-lookup"><span data-stu-id="732d2-109">**Name**</span></span>  
 <span data-ttu-id="732d2-110">ジョブ転送タスクの一意な名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="732d2-110">Type a unique name for the Transfer Jobs task.</span></span> <span data-ttu-id="732d2-111">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="732d2-111">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="732d2-112">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="732d2-112">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="732d2-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="732d2-113">**Description**</span></span>  
 <span data-ttu-id="732d2-114">ジョブ転送タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="732d2-114">Type a description of the Transfer Jobs task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="732d2-115">参照</span><span class="sxs-lookup"><span data-stu-id="732d2-115">See Also</span></span>  
 <span data-ttu-id="732d2-116">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="732d2-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="732d2-117">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="732d2-117">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="732d2-118">[ジョブ転送タスクエディター &#40;ジョブページ&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span><span class="sxs-lookup"><span data-stu-id="732d2-118">[Transfer Jobs Task Editor &#40;Jobs Page&#41;](../../2014/integration-services/transfer-jobs-task-editor-jobs-page.md) </span></span>  
 <span data-ttu-id="732d2-119">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="732d2-119">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  

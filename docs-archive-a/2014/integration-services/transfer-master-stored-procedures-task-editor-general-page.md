---
title: '[Master ストアドプロシージャ転送タスクエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a25a5c9c6ed3802e21ac522e94163ce5fb9e8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718464"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a><span data-ttu-id="2cee2-102">[Master ストアド プロシージャ転送タスク エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="2cee2-102">Transfer Master Stored Procedures Task Editor (General Page)</span></span>
  <span data-ttu-id="2cee2-103">**[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、Master ストアド プロシージャ転送タスクの名前と説明を入力できます。</span><span class="sxs-lookup"><span data-stu-id="2cee2-103">Use the **General** page of the **Transfer Master Stored Procedures Task Editor** dialog box to name and describe the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="2cee2-104">このタスクの詳細については、「 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cee2-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cee2-105">このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、 **dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。</span><span class="sxs-lookup"><span data-stu-id="2cee2-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="2cee2-106">コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cee2-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2cee2-107">オプション</span><span class="sxs-lookup"><span data-stu-id="2cee2-107">Options</span></span>  
 <span data-ttu-id="2cee2-108">**Name**</span><span class="sxs-lookup"><span data-stu-id="2cee2-108">**Name**</span></span>  
 <span data-ttu-id="2cee2-109">Master ストアド プロシージャ転送タスクの一意な名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cee2-109">Type a unique name for the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="2cee2-110">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2cee2-110">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cee2-111">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cee2-111">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="2cee2-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="2cee2-112">**Description**</span></span>  
 <span data-ttu-id="2cee2-113">Master ストアド プロシージャ転送タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cee2-113">Type a description of the Transfer Master Stored Procedures task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cee2-114">参照</span><span class="sxs-lookup"><span data-stu-id="2cee2-114">See Also</span></span>  
 <span data-ttu-id="2cee2-115">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2cee2-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="2cee2-116">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="2cee2-116">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="2cee2-117">[Master ストアドプロシージャ転送タスクエディター &#40;ストアドプロシージャページ&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span><span class="sxs-lookup"><span data-stu-id="2cee2-117">[Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span></span>  
 <span data-ttu-id="2cee2-118">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="2cee2-118">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  

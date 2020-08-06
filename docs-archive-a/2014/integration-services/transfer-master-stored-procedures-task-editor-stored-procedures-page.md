---
title: '[Master ストアドプロシージャ転送タスクエディター] ([ストアドプロシージャ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f9fad408b54d4ef27d4c5d06b0d352f366ad9c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718458"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a><span data-ttu-id="73d8b-102">[Master ストアド プロシージャ転送タスク エディター] ([ストアド プロシージャ] ページ)</span><span class="sxs-lookup"><span data-stu-id="73d8b-102">Transfer Master Stored Procedures Task Editor (Stored Procedures Page)</span></span>
  <span data-ttu-id="73d8b-103">**[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[ストアド プロシージャ]** ページを使用すると、 **の 1 つのインスタンスの** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースから **の別のインスタンスの** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベースに、1 つ以上のユーザー定義ストアド プロシージャをコピーする場合のプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="73d8b-103">Use the **Stored Procedures** page of the **Transfer Master Stored Procedures Task Editor** dialog box to specify properties for copying one or more user-defined stored procedures from the **master** database in one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to a **master** database in another instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="73d8b-104">このタスクの詳細については、「 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73d8b-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73d8b-105">このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、 **dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="73d8b-106">コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="73d8b-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="73d8b-107">オプション</span><span class="sxs-lookup"><span data-stu-id="73d8b-107">Options</span></span>  
 <span data-ttu-id="73d8b-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="73d8b-108">**SourceConnection**</span></span>  
 <span data-ttu-id="73d8b-109">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="73d8b-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="73d8b-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="73d8b-111">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="73d8b-112">**[IfObjectExists]**</span><span class="sxs-lookup"><span data-stu-id="73d8b-112">**IfObjectExists**</span></span>  
 <span data-ttu-id="73d8b-113">コピー先のサーバーの **master** データベースに存在する名前と同じ名前を持つ、ユーザー定義ストアド プロシージャの処理方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-113">Select how the task should handle user-defined stored procedures of the same name that already exist in the **master** database on the destination server.</span></span>  
  
 <span data-ttu-id="73d8b-114">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="73d8b-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="73d8b-115">値</span><span class="sxs-lookup"><span data-stu-id="73d8b-115">Value</span></span>|<span data-ttu-id="73d8b-116">説明</span><span class="sxs-lookup"><span data-stu-id="73d8b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="73d8b-117">**[FailTask]**</span><span class="sxs-lookup"><span data-stu-id="73d8b-117">**FailTask**</span></span>|<span data-ttu-id="73d8b-118">ストアド プロシージャがコピー先のサーバーの **master** データベースに既に存在する名前と同じ名前を持つ場合、タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-118">Task fails if stored procedures of the same name already exist in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="73d8b-119">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="73d8b-119">**Overwrite**</span></span>|<span data-ttu-id="73d8b-120">コピー先のサーバーの **master** データベースにある同じ名前のストアド プロシージャを上書きします。</span><span class="sxs-lookup"><span data-stu-id="73d8b-120">Task overwrites stored procedures of the same name in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="73d8b-121">**Skip**</span><span class="sxs-lookup"><span data-stu-id="73d8b-121">**Skip**</span></span>|<span data-ttu-id="73d8b-122">コピー先のサーバーの **master** データベースにある同じ名前のストアド プロシージャをスキップします。</span><span class="sxs-lookup"><span data-stu-id="73d8b-122">Task skips stored procedures of the same name that exist in the **master** database on the destination server.</span></span>|  
  
 <span data-ttu-id="73d8b-123">**[TransferAllStoredProcedures]**</span><span class="sxs-lookup"><span data-stu-id="73d8b-123">**TransferAllStoredProcedures**</span></span>  
 <span data-ttu-id="73d8b-124">コピー元のサーバーの **master** データベースのすべてのユーザー定義ストアド プロシージャをコピー先のサーバーにコピーするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-124">Select whether all user-defined stored procedures in the **master** database on the source server should be copied to the destination server.</span></span>  
  
|<span data-ttu-id="73d8b-125">値</span><span class="sxs-lookup"><span data-stu-id="73d8b-125">Value</span></span>|<span data-ttu-id="73d8b-126">説明</span><span class="sxs-lookup"><span data-stu-id="73d8b-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="73d8b-127">**True** にします</span><span class="sxs-lookup"><span data-stu-id="73d8b-127">**True**</span></span>|<span data-ttu-id="73d8b-128">**master** データベースのユーザー定義ストアド プロシージャをすべてコピーします。</span><span class="sxs-lookup"><span data-stu-id="73d8b-128">Copy all user-defined stored procedures in the **master** database.</span></span>|  
|<span data-ttu-id="73d8b-129">**False**</span><span class="sxs-lookup"><span data-stu-id="73d8b-129">**False**</span></span>|<span data-ttu-id="73d8b-130">指定したストアド プロシージャのみをコピーします。</span><span class="sxs-lookup"><span data-stu-id="73d8b-130">Copy only the specified stored procedures.</span></span>|  
  
 <span data-ttu-id="73d8b-131">**[StoredProceduresList]**</span><span class="sxs-lookup"><span data-stu-id="73d8b-131">**StoredProceduresList**</span></span>  
 <span data-ttu-id="73d8b-132">コピー先の **master** データベースにコピーする、コピー元サーバーの **master** データベースのユーザー定義ストアド プロシージャを選択します。</span><span class="sxs-lookup"><span data-stu-id="73d8b-132">Select which user-defined stored procedures in the **master** database on the source server should be copied to the destination **master** database.</span></span> <span data-ttu-id="73d8b-133">このオプションは、 **[TransferAllStoredProcedures]** を **[False]** に設定した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="73d8b-133">This option is only available when **TransferAllStoredProcedures** is set to **False**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d8b-134">参照</span><span class="sxs-lookup"><span data-stu-id="73d8b-134">See Also</span></span>  
 <span data-ttu-id="73d8b-135">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="73d8b-135">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="73d8b-136">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="73d8b-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="73d8b-137">[Master ストアドプロシージャ転送タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="73d8b-137">[Transfer Master Stored Procedures Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="73d8b-138">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="73d8b-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="73d8b-139">SMO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="73d8b-139">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  

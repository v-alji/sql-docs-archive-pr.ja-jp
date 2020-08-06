---
title: Oracle CDC Service の管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5fbe769980297a06b7958ecad04bfed85b9b714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712273"
---
# <a name="manage-an-oracle-cdc-service"></a><span data-ttu-id="b2c72-102">Manage an Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="b2c72-102">Manage an Oracle CDC Service</span></span>
  <span data-ttu-id="b2c72-103">CDC Service 構成コンソールを使用すると、特定の CDC Service を管理できます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-103">You can use the CDC Service Configuration Console to manage a specific CDC Service.</span></span>  
  
 <span data-ttu-id="b2c72-104">**操作する CDC サービスを選択するには**</span><span class="sxs-lookup"><span data-stu-id="b2c72-104">**To select the CDC service you want to work with**</span></span>  
  
1.  <span data-ttu-id="b2c72-105">CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b2c72-105">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
2.  <span data-ttu-id="b2c72-106">操作する CDC サービスを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c72-106">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="b2c72-107">操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-107">You can also right-click the CDC service you want to work with and select the desired action.</span></span> <span data-ttu-id="b2c72-108">「 [CDC Service で可能な操作](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2c72-108">See [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).</span></span>  
  
 <span data-ttu-id="b2c72-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="b2c72-109">**OR**</span></span>  
  
1.  <span data-ttu-id="b2c72-110">CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c72-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console.</span></span>  
  
2.  <span data-ttu-id="b2c72-111">CDC Service 構成コンソールの中央のセクションで、操作するサービスを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c72-111">From the middle section of the CDC Service Configuration Console, select the service you want to work with.</span></span>  
  
     <span data-ttu-id="b2c72-112">操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-112">You can also right-click the CDC service you want to work with and select the desired action.</span></span> <span data-ttu-id="b2c72-113">「 [CDC Service で可能な操作](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2c72-113">See [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).</span></span>  
  
##  <a name="what-can-you-do-with-a-cdc-service"></a><a name="BKMK_WhatcandowithCDCService"></a> <span data-ttu-id="b2c72-114">CDC Service で可能な操作</span><span class="sxs-lookup"><span data-stu-id="b2c72-114">What can you do with a CDC Service</span></span>  
 <span data-ttu-id="b2c72-115">CDC サービスの操作時には、以下のアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-115">You can carry out the following actions when working with a CDC service.</span></span>  
  
### <a name="delete-the-service"></a><span data-ttu-id="b2c72-116">サービスの削除</span><span class="sxs-lookup"><span data-stu-id="b2c72-116">Delete the service</span></span>  
 <span data-ttu-id="b2c72-117">サービスを削除するには、CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c72-117">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
 <span data-ttu-id="b2c72-118">または、削除する CDC サービスを右クリックして **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c72-118">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
 <span data-ttu-id="b2c72-119">**注**: 実行中のサービスを削除した場合、サービスは停止されてから削除されます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-119">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
 <span data-ttu-id="b2c72-120">Oracle CDC Windows Service の定義を削除するには、プログラムに、関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の MSXDBCDC データベースに対する更新アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="b2c72-120">To delete the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="b2c72-121">[OK] をクリックしてサービスを削除すると、MSXDBCDC データベース内にある Oracle CDC Service 登録の削除が試みられます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-121">When you click OK to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="b2c72-122">プログラムが適切な権限を持っていないため Oracle CDC Service 登録を削除できない場合、ユーザーは、MSXDBCDC データベースに対する更新権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="b2c72-122">If the program cannot delete the Oracle CDC Service registration because it does not have the proper permissions, it prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with update permissions to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="b2c72-123">[SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2c72-123">For information about the data you must enter in the Connect to SQL Server dialog box, see [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
### <a name="edit-the-cdc-service-properties"></a><span data-ttu-id="b2c72-124">CDC Service のプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="b2c72-124">Edit the CDC Service Properties</span></span>  
 <span data-ttu-id="b2c72-125">CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c72-125">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
 <span data-ttu-id="b2c72-126">または、プロパティを編集する CDC サービスを右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c72-126">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c72-127">参照</span><span class="sxs-lookup"><span data-stu-id="b2c72-127">See Also</span></span>  
 [<span data-ttu-id="b2c72-128">ローカルの CDC Service を管理する方法</span><span class="sxs-lookup"><span data-stu-id="b2c72-128">How to Manage a Local CDC Service</span></span>](how-to-manage-a-local-cdc-service.md)  

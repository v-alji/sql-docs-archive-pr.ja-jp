---
title: CDC サービスの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manSer
ms.assetid: 645ae53f-f352-4d6a-9eb0-264e53a93a18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d630392216e51efd9ea64116d57b388202061ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712277"
---
# <a name="manage-a-cdc-service"></a><span data-ttu-id="e0f71-102">CDC サービスの管理</span><span class="sxs-lookup"><span data-stu-id="e0f71-102">Manage a CDC Service</span></span>
  <span data-ttu-id="e0f71-103">CDC デザイナー コンソールを使用して、CDC Service 構成コンソールで作成したサービスを表示し、Oracle CDC Service 内のすべてのインスタンスを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="e0f71-103">You can use the CDC Designer Console to view the services you created with the CDC Service Configuration Console and manage all of the instances in the Oracle CDC Service.</span></span>  
  
 <span data-ttu-id="e0f71-104">サービスに関する情報の表示およびサービスの管理を行うには、左ペインでサービスの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0f71-104">Click the name of the service in the left pane to display information about the service and to manage it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0f71-105">この一覧にサービスを追加するには、まず CDC Service 構成コンソールを使用してサービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0f71-105">You must first create a service using the CDC Service Configuration Console to add services to this list.</span></span> <span data-ttu-id="e0f71-106">サービスを作成する方法については、CDC Service 構成コンソールのオンライン ヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0f71-106">For information on how to create a service, see the online help provided with the CDC Service Configuration Console.</span></span>  
  
## <a name="what-you-can-do-when-you-display-the-cdc-service-information"></a><span data-ttu-id="e0f71-107">CDC サービスの情報を表示しているときに実行できるタスク</span><span class="sxs-lookup"><span data-stu-id="e0f71-107">What you can do when you display the CDC service information</span></span>  
 <span data-ttu-id="e0f71-108">サービスに関する情報を表示しているときは、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e0f71-108">You can do the following when you display information about a service:</span></span>  
  
 <span data-ttu-id="e0f71-109">**選択したサービスに新しい CDC インスタンスを作成する**</span><span class="sxs-lookup"><span data-stu-id="e0f71-109">**Create a new CDC instance for the selected service**</span></span>  
  
 <span data-ttu-id="e0f71-110">サービスの新しいインスタンスを作成するには、右ペインで **[新しい Oracle CDC インスタンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0f71-110">Click **New Oracle CDC Instance** in the right pane to create a new instance for that service.</span></span> <span data-ttu-id="e0f71-111">インスタンスを作成するための新しいインスタンス ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="e0f71-111">The New Instance wizard opens to create the instance.</span></span> <span data-ttu-id="e0f71-112">新しいインスタンス ウィザードの詳細については、「 [Use the New Instance Wizard](use-the-new-instance-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0f71-112">For more information about the New Instance wizard, see [Use the New Instance Wizard](use-the-new-instance-wizard.md).</span></span>  
  
 <span data-ttu-id="e0f71-113">**サービスのすべての CDC インスタンスを開始する**</span><span class="sxs-lookup"><span data-stu-id="e0f71-113">**Start all CDC instances in the service**</span></span>  
  
 <span data-ttu-id="e0f71-114">サービスのすべての定義済みインスタンスからのデータのキャプチャを開始するには、右ペインで **[すべてのインスタンスの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0f71-114">Click **Start All Instances** in the right pane to begin capturing data from all the defined instances in the service.</span></span>  
  
 <span data-ttu-id="e0f71-115">**サービスのすべての CDC インスタンスを停止する**</span><span class="sxs-lookup"><span data-stu-id="e0f71-115">**Stop all CDC instances in the service**</span></span>  
  
 <span data-ttu-id="e0f71-116">**[すべてのインスタンスの停止]** をクリックして、サービスのすべてのインスタンスの変更データ キャプチャを停止します。</span><span class="sxs-lookup"><span data-stu-id="e0f71-116">Click **Stop All Instances** to stop the change data capture for all instances in the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f71-117">参照</span><span class="sxs-lookup"><span data-stu-id="e0f71-117">See Also</span></span>  
 <span data-ttu-id="e0f71-118">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e0f71-118">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="e0f71-119">[CDC デザイナー コンソールから CDC サービスを管理する方法](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="e0f71-119">[How to Manage a CDC Service from the CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="e0f71-120">新しいインスタンス ウィザードを使用する</span><span class="sxs-lookup"><span data-stu-id="e0f71-120">Use the New Instance Wizard</span></span>](use-the-new-instance-wizard.md)  
  
  

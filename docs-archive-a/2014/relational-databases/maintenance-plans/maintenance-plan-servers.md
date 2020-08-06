---
title: '[メンテナンス プラン] ([サーバー]) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c971edc9b641846068313f47ca410715ec552014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639488"
---
# <a name="maintenance-plan-servers"></a><span data-ttu-id="11cce-102">[メンテナンス プラン] ([サーバー])</span><span class="sxs-lookup"><span data-stu-id="11cce-102">Maintenance Plan (Servers)</span></span>
  <span data-ttu-id="11cce-103">**[サーバー]** ダイアログ ボックスでは、メンテナンス プランを実行するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="11cce-103">Use the **Servers** dialog box to select the servers where you want to run the maintenance plan.</span></span>  
  
 <span data-ttu-id="11cce-104">1 台のマスター サーバーと 1 台以上のターゲット サーバーで構成されたマルチサーバー環境は、マルチサーバー メンテナンス プランを作成するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11cce-104">A multiserver environment containing one master server and one or more target servers must be configured to create a multiserver maintenance plan.</span></span> <span data-ttu-id="11cce-105">マルチサーバー メンテナンス プランでは、ローカル サーバーをマスター サーバーとして構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11cce-105">For multiserver maintenance plans, the local server should be configured as a master server.</span></span> <span data-ttu-id="11cce-106">マルチサーバー環境では、" **(local)** " マスター サーバーと対応するすべてのターゲット サーバーがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="11cce-106">In multiserver environments, this dialog box displays the **(local)** master server and all corresponding target servers.</span></span> <span data-ttu-id="11cce-107">ローカル サーバーに対して 1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブが作成されます。</span><span class="sxs-lookup"><span data-stu-id="11cce-107">One [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created for the local server.</span></span> <span data-ttu-id="11cce-108">このジョブが有効かどうかは、" **(local)** " サーバーを選択するかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="11cce-108">It is enabled or disabled depending on whether you select the **(local)** server.</span></span> <span data-ttu-id="11cce-109">ターゲット サーバーを選択すると、マルチサーバー ジョブが作成され、選択した各ターゲット サーバーにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="11cce-109">If target servers are selected, a multiserver job is created and downloaded to each of the selected target servers.</span></span> <span data-ttu-id="11cce-110">ターゲット サーバーを選択しない場合、マルチサーバー ジョブは削除されます。</span><span class="sxs-lookup"><span data-stu-id="11cce-110">If no target servers are selected, the multiserver job is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11cce-111">参照</span><span class="sxs-lookup"><span data-stu-id="11cce-111">See Also</span></span>  
 <span data-ttu-id="11cce-112">[メンテナンス プラン](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="11cce-112">[Maintenance Plans](maintenance-plans.md) </span></span>  
 <span data-ttu-id="11cce-113">[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="11cce-113">[Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="11cce-114">[マスター サーバーの作成](../../ssms/agent/make-a-master-server.md) </span><span class="sxs-lookup"><span data-stu-id="11cce-114">[Make a Master Server](../../ssms/agent/make-a-master-server.md) </span></span>  
 [<span data-ttu-id="11cce-115">ターゲット サーバーの作成</span><span class="sxs-lookup"><span data-stu-id="11cce-115">Make a Target Server</span></span>](../../ssms/agent/make-a-target-server.md)  
  
  

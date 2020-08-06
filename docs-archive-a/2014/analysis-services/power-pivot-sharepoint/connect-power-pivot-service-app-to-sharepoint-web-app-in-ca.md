---
title: サーバーの全体管理で PowerPivot サービスアプリケーションを SharePoint Web アプリケーションに接続する |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5fc6dcde4cc2d18c3650adbab0ec71ef5c6265cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643549"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a><span data-ttu-id="edb5b-102">サーバーの全体管理で PowerPivot サービスアプリケーションを SharePoint Web アプリケーションに接続する</span><span class="sxs-lookup"><span data-stu-id="edb5b-102">Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration</span></span>
  <span data-ttu-id="edb5b-103">PowerPivot サービス アプリケーションは、ファーム内の任意の数の SharePoint Web アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="edb5b-103">A PowerPivot service application can be used by any number of SharePoint Web applications in the farm.</span></span> <span data-ttu-id="edb5b-104">PowerPivot サービス アプリケーションを使用できるようにするには、サービス関連付けリストに PowerPivot サービス アプリケーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="edb5b-104">To make a PowerPivot service application available, you add it to a service association list.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="edb5b-105">PowerPivot 管理ダッシュボードが正しく機能するには、既定のグループに PowerPivot サービス アプリケーションが 1 つ存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="edb5b-105">You must have one PowerPivot service application in the default group to ensure that PowerPivot Management Dashboard works properly.</span></span> <span data-ttu-id="edb5b-106">既定のグループに複数の PowerPivot サービス アプリケーションを追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="edb5b-106">Do not add more than one PowerPivot service application to the default group.</span></span> <span data-ttu-id="edb5b-107">同じ型のサービス アプリケーションのエントリを複数追加する構成はサポートされていないため、エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="edb5b-107">Adding multiple entries of the same service application type is not a supported configuration and might cause errors.</span></span> <span data-ttu-id="edb5b-108">追加のサービス アプリケーションを作成する場合は、それらをカスタム リストに追加してください。</span><span class="sxs-lookup"><span data-stu-id="edb5b-108">If you are creating additional service applications, add them to custom lists.</span></span>  
  
 <span data-ttu-id="edb5b-109">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="edb5b-109">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="edb5b-110">既定のグループへの PowerPivot サービス アプリケーションの追加</span><span class="sxs-lookup"><span data-stu-id="edb5b-110">Add PowerPivot Services Application to the Default Group</span></span>](#default)  
  
 [<span data-ttu-id="edb5b-111">カスタム サービス関連付けリストへの PowerPivot サービス アプリケーションの追加</span><span class="sxs-lookup"><span data-stu-id="edb5b-111">Add PowerPivot Services Application a Custom Service Association List</span></span>](#custom)  
  
##  <a name="add-powerpivot-services-application-to-the-default-group"></a><a name="default"></a><span data-ttu-id="edb5b-112">既定のグループへの PowerPivot サービスアプリケーションの追加</span><span class="sxs-lookup"><span data-stu-id="edb5b-112">Add PowerPivot Services Application to the Default Group</span></span>  
 <span data-ttu-id="edb5b-113">サービス関連付けリストは、ファーム内の他の SharePoint Web アプリケーションにリソースを提供する共有サービスのリストです。</span><span class="sxs-lookup"><span data-stu-id="edb5b-113">A service association list is a list of shared services that provide resources to other SharePoint Web applications in the farm.</span></span> <span data-ttu-id="edb5b-114">ファームには、サービス関連付けの既定のグループが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="edb5b-114">There is one default group of service associations for the farm.</span></span>  
  
 <span data-ttu-id="edb5b-115">リストに含めるには、PowerPivot サービス アプリケーションをアプリケーションの作成時に追加するか、アプリケーションの作成後に次の手順を使用して追加します。</span><span class="sxs-lookup"><span data-stu-id="edb5b-115">To be on the list, a PowerPivot service application can either be added when you create the application or afterwards by using the following steps.</span></span>  
  
1.  <span data-ttu-id="edb5b-116">サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの関連付けの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-116">In Central Administration, in **Application Management**, click **Configure service application associations**.</span></span>  
  
2.  <span data-ttu-id="edb5b-117">アプリケーション プロキシ グループで、 **[既定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-117">In Application Proxy Group, click **default**.</span></span>  
  
3.  <span data-ttu-id="edb5b-118">PowerPivot サービス アプリケーション (型名 `PowerPivot Service Application Proxy` で示されます) の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-118">Select the checkbox next to the PowerPivot service application (indicated by type name `PowerPivot Service Application Proxy`).</span></span> <span data-ttu-id="edb5b-119">PowerPivot サービス アプリケーションが複数ある場合は、そのうちの 1 つだけを選択します。</span><span class="sxs-lookup"><span data-stu-id="edb5b-119">If you have more than one PowerPivot service application, choose just one.</span></span>  
  
4.  <span data-ttu-id="edb5b-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-120">Click **OK**.</span></span>  
  
##  <a name="add-powerpivot-services-application-a-custom-service-association-list"></a><a name="custom"></a><span data-ttu-id="edb5b-121">カスタムサービス関連付けリストへの PowerPivot サービスアプリケーションの追加</span><span class="sxs-lookup"><span data-stu-id="edb5b-121">Add PowerPivot Services Application a Custom Service Association List</span></span>  
 <span data-ttu-id="edb5b-122">既定のグループは、カスタム リストで置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="edb5b-122">The default group can be replaced by a custom list.</span></span> <span data-ttu-id="edb5b-123">カスタム リストは、SharePoint Web アプリケーションごとに作成します。</span><span class="sxs-lookup"><span data-stu-id="edb5b-123">A custom list is created specifically for a single SharePoint Web application.</span></span> <span data-ttu-id="edb5b-124">カスタム リストは既定のグループをオーバーライドし、既定のグループは、ファームまたはサービスの管理者が指定したサービス関連付けとのみ置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="edb5b-124">It overrides the default group and replaces it with only those service associations that a farm or service administrator specifies.</span></span> <span data-ttu-id="edb5b-125">複数の PowerPivot サービス アプリケーションを作成した場合は、使用するサービス アプリケーションをカスタム リストで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="edb5b-125">If you created multiple PowerPivot service applications, you must use a custom list to specify which one to use.</span></span> <span data-ttu-id="edb5b-126">カスタム リストを他の Web アプリケーションで再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="edb5b-126">A custom list cannot be reused by other Web applications.</span></span> <span data-ttu-id="edb5b-127">カスタム リストは、作成対象の Web アプリケーションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="edb5b-127">It applies only to the Web application for which it was created.</span></span>  
  
1.  <span data-ttu-id="edb5b-128">サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[Web アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-128">In Central Administration, in **Application Management**, click **Manage web applications**.</span></span>  
  
2.  <span data-ttu-id="edb5b-129">アプリケーションを選択します ("SharePoint -80" など)。</span><span class="sxs-lookup"><span data-stu-id="edb5b-129">Select the application (for example, SharePoint -80).</span></span>  
  
3.  <span data-ttu-id="edb5b-130">Web アプリケーションの [管理] で、 **[サービス接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-130">In Web Applications, in Manage, click **Service Connections**.</span></span>  
  
4.  <span data-ttu-id="edb5b-131">**[次の接続グループを編集する]** で、 **[カスタム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-131">In **Edit the following group of connections**, select **[custom]**.</span></span>  
  
5.  <span data-ttu-id="edb5b-132">使用する各サービス アプリケーション接続の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-132">Select the checkbox next to each service application connection you want to use.</span></span> <span data-ttu-id="edb5b-133">PowerPivot サービス アプリケーション ([型] が `PowerPivot Service Application Proxy` に設定されているアプリケーション) が複数ある場合は、そのうちの 1 つだけを選択してください。</span><span class="sxs-lookup"><span data-stu-id="edb5b-133">If you have multiple PowerPivot service applications (indicated by Type set to `PowerPivot Service Application Proxy`), be sure to choose only one.</span></span>  
  
6.  <span data-ttu-id="edb5b-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="edb5b-134">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb5b-135">参照</span><span class="sxs-lookup"><span data-stu-id="edb5b-135">See Also</span></span>  
 <span data-ttu-id="edb5b-136">[サーバーの全体管理での PowerPivot サービスアプリケーションの作成と構成](create-and-configure-power-pivot-service-application-in-ca.md) </span><span class="sxs-lookup"><span data-stu-id="edb5b-136">[Create and Configure a PowerPivot Service Application in Central Administration](create-and-configure-power-pivot-service-application-in-ca.md) </span></span>  
 [<span data-ttu-id="edb5b-137">初期構成 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="edb5b-137">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  

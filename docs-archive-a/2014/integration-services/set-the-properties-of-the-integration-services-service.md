---
title: Integration Services Service | のプロパティを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 055eadd9a1d59c59dd40675b142eae480763f6f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742365"
---
# <a name="set-the-properties-of-the-integration-services-service"></a><span data-ttu-id="3c06c-102">Integration Services サービスのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="3c06c-102">Set the Properties of the Integration Services Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="3c06c-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="3c06c-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3c06c-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="3c06c-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="3c06c-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]でパッケージを管理および監視します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages and monitors packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3c06c-107">を最初にインストールすると [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが開始され、サービスのスタートアップの種類が [自動] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-107">When you first install [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span>  
  
 <span data-ttu-id="3c06c-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスをインストールしたら、SQL Server 構成マネージャーまたはサービス MMC スナップインを使用してサービスのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-108">After the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has been installed, you can set the properties of the service by using either SQL Server Configuration Manager or the Services MMC snap-in.</span></span>  
  
 <span data-ttu-id="3c06c-109">パッケージを格納および管理する場所など、サービスのその他の重要な機能を構成するには、サービスの構成ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c06c-109">To configure other important features of the service, including the locations where it stores and manages packages, you must modify the configuration file of the service.</span></span> <span data-ttu-id="3c06c-110">詳細については、「 [Integration Services サービスの構成 (SSIS サービス)](service/integration-services-service-ssis-service.md)との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3c06c-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a><span data-ttu-id="3c06c-111">SQL Server 構成マネージャーを使用して Integration Services サービスのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="3c06c-111">To set properties of the Integration Services service by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="3c06c-112">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-112">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="3c06c-113">**[SQL Server 構成マネージャー]** スナップインで、サービスの一覧から **[SQL Server Integration Services]** を探します。次に、 **[SQL Server Integration Services]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-113">In the **SQL Server Configuration Manager** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3c06c-114">[ **SQL Server Integration Services のプロパティ**] ダイアログボックスでは、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-114">In the **SQL Server Integration Services Properties** dialog box you can do the following:</span></span>  
  
    -   <span data-ttu-id="3c06c-115">**[ログオン]** タブをクリックして、アカウント名などのログオン情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-115">Click the **Log On** tab to view the logon information such as the account name.</span></span>  
  
    -   <span data-ttu-id="3c06c-116">**[サービス]** タブをクリックして、ホスト コンピューター名などのサービスに関する情報を表示し、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの開始モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-116">Click the **Service** tab to view information about the service such as the name of the host computer and to specify the start mode of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3c06c-117">**[詳細設定]** タブに、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスに関する情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="3c06c-117">The **Advanced** tab contains no information for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="3c06c-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="3c06c-119">**[ファイル]** メニューの **[終了]** をクリックして **[SQL Server 構成マネージャー]** スナップインを終了します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-119">On the **File** menu, click **Exit** to close the **SQL Server Configuration Manager** snap-in.</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a><span data-ttu-id="3c06c-120">[サービス] を使用して Integration Services サービスのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="3c06c-120">To set properties of the Integration Services service by using Services</span></span>  
  
1.  <span data-ttu-id="3c06c-121">**[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]**、カテゴリの表示を使用している場合は **[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-121">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="3c06c-122">[**サービス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-122">Click **Services**.</span></span>  
  
3.  <span data-ttu-id="3c06c-123">**[サービス]** スナップインで、サービスの一覧から **[SQL Server Integration Services]** を探します。 **[SQL Server Integration Services]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-123">In the **Services** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3c06c-124">**[SQL Server Integration Services のプロパティ]** ダイアログ ボックスでは、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-124">In the **SQL Server Integration Services Properties** dialog box, you can do the following:</span></span>  
  
    -   <span data-ttu-id="3c06c-125">[**全般**] タブをクリックします。サービスを有効にするには、手動または自動のスタートアップの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-125">Click the **General** tab. To enable the service, select either the manual or automatic startup type.</span></span> <span data-ttu-id="3c06c-126">サービスを無効にするには、 **[スタートアップの種類]** ボックスで [無効] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-126">To disable the service, select Disable in the **Startup type** box.</span></span> <span data-ttu-id="3c06c-127">[無効] を選択しても、実行中のサービスは停止されません。</span><span class="sxs-lookup"><span data-stu-id="3c06c-127">Selecting Disable does not stop the service if it is currently running.</span></span>  
  
         <span data-ttu-id="3c06c-128">サービスが既に有効になっている場合は、 **[停止]** をクリックしてサービスを停止したり、 **[開始]** をクリックしてサービスを開始したりできます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-128">If the service is already enabled, you can click **Stop** to stop the service, or click **Start** to start the service.</span></span>  
  
    -   <span data-ttu-id="3c06c-129">**[ログオン]** タブをクリックして、ログオン情報を表示または編集します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-129">Click the **Log On** tab to view or edit the logon information.</span></span>  
  
    -   <span data-ttu-id="3c06c-130">**[復旧]** タブをクリックして、サービスが失敗した場合のコンピューターの既定の応答を表示します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-130">Click the **Recovery** tab to view the default computer responses to service failure.</span></span> <span data-ttu-id="3c06c-131">これらのオプションは、環境に合わせて変更できます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-131">You can modify these options to suit your environment.</span></span>  
  
    -   <span data-ttu-id="3c06c-132">**[依存関係]** タブをクリックして、依存サービスの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-132">Click the **Dependencies** tab to view a list of dependent services.</span></span> <span data-ttu-id="3c06c-133">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、依存関係を持ちません。</span><span class="sxs-lookup"><span data-stu-id="3c06c-133">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has no dependencies.</span></span>  
  
5.  <span data-ttu-id="3c06c-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c06c-134">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="3c06c-135">[スタートアップの種類] で [手動] または [自動] を選択している場合は、必要に応じて、 **[SQL Server Integration Services]** を右クリックし、 **[開始]、[停止]、または [再起動]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="3c06c-135">Optionally, if the startup type is Manual or Automatic, you can right-click **SQL Server Integration Services** and click **Start, Stop, or Restart**.</span></span>  
  
7.  <span data-ttu-id="3c06c-136">**[ファイル]** メニューの **[終了]** をクリックして **[サービス]** スナップインを終了します。</span><span class="sxs-lookup"><span data-stu-id="3c06c-136">On the **File** menu, click **Exit** to close the **Services** snap-in.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c06c-137">参照</span><span class="sxs-lookup"><span data-stu-id="3c06c-137">See Also</span></span>  
 [<span data-ttu-id="3c06c-138">Integration Services サービスを管理する</span><span class="sxs-lookup"><span data-stu-id="3c06c-138">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  

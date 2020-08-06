---
title: アップグレードアドバイザー分析ウィザードを実行する方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7c3e5e8a52c3b166b076aedb122e68f860037edf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644805"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="ddde9-102">アップグレード アドバイザー分析ウィザードを実行する方法</span><span class="sxs-lookup"><span data-stu-id="ddde9-102">How to: Run the Upgrade Advisor Analysis Wizard</span></span>
  <span data-ttu-id="ddde9-103">アップグレード アドバイザー分析ウィザードは、アップグレード アドバイザー開始ページから起動します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-103">You start the Upgrade Advisor Analysis Wizard from the Upgrade Advisor start page.</span></span> <span data-ttu-id="ddde9-104">ここでは、アップグレード アドバイザー分析ウィザードの実行方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-104">This topic describes how to run the Upgrade Advisor Analysis Wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ddde9-105">アップグレード アドバイザー分析ウィザードを実行すると、アップグレード アドバイザーによって既定のレポート フォルダーにレポートが保存されます。</span><span class="sxs-lookup"><span data-stu-id="ddde9-105">When you run the Upgrade Advisor Analysis Wizard, Upgrade Advisor saves the reports in the default report folder.</span></span> <span data-ttu-id="ddde9-106">ただし、レポート ビューアーで表示されるのは、保存されている最近 5 件のレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="ddde9-106">However, the report viewer displays only the five latest saved reports.</span></span> <span data-ttu-id="ddde9-107">レポートの既定の場所は、My Documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports. です。</span><span class="sxs-lookup"><span data-stu-id="ddde9-107">The default location for the reports is My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.</span></span>  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="ddde9-108">アップグレードアドバイザー分析ウィザードを実行するには</span><span class="sxs-lookup"><span data-stu-id="ddde9-108">To run the Upgrade Advisor Analysis Wizard</span></span>  
  
1.  <span data-ttu-id="ddde9-109">アップグレードアドバイザーの開始ページで、[**アップグレードアドバイザー分析ウィザードの起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddde9-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Analysis Wizard**.</span></span>  
  
2.  <span data-ttu-id="ddde9-110">[ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント**] ページで、スキャンするサーバーの名前を [**サーバー名**] ボックスに入力し、[**検出\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddde9-110">On the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components** page, enter the name of the server to scan in the **Server name** box, and then click **Detect**.</span></span> <span data-ttu-id="ddde9-111">サーバー名については次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="ddde9-111">Use the following guidelines for the server name:</span></span>  
  
    -   <span data-ttu-id="ddde9-112">クラスター化されていないインスタンスをスキャンするには、コンピューター名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-112">To scan nonclustered instances, enter the computer name.</span></span>  
  
    -   <span data-ttu-id="ddde9-113">クラスター化されたインスタンスをスキャンするには、仮想 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-113">To scan clustered instances, enter the virtual [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name.</span></span>  
  
    -   <span data-ttu-id="ddde9-114">クラスターのノードにインストールされている非クラスター化コンポーネントをスキャンするには、ノード名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-114">To scan nonclustered components that are installed on a node of a cluster, enter the node name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="ddde9-115">アップグレード アドバイザーは、クライアント接続に標準ポート (1433) を使用するように設定されていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスには接続できません。</span><span class="sxs-lookup"><span data-stu-id="ddde9-115">Upgrade Advisor does not support connecting to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is not set to use the standard port (1433) for client connections.</span></span> <span data-ttu-id="ddde9-116">標準ポート (1433) を使用していない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するには、IP アドレスとポートを使用して別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-116">If you want to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that does not use the standard port (1433), create an alias using the IP address and the port.</span></span> <span data-ttu-id="ddde9-117">クライアントプロトコルの構成とインスタンスの別名の作成の詳細について [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、「[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddde9-117">For more information about configuring client protocols and creating an alias for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
    >   
    >  <span data-ttu-id="ddde9-118">アップグレードアドバイザーを実行しているコンピューターにがインストールされていない場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、[**開始**] をクリックし、を実行し `cliconfg` ます。</span><span class="sxs-lookup"><span data-stu-id="ddde9-118">If you do not have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer on which you are running Upgrade Advisor, click **Start**, and then run  `cliconfg`.</span></span> <span data-ttu-id="ddde9-119">[ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントネットワークユーティリティ\*\*] ダイアログボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="ddde9-119">This opens the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility** dialog box.</span></span> <span data-ttu-id="ddde9-120">エイリアスを作成するには、[**別名**] タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-120">Use the **Alias** tab to create the alias.</span></span>  
  
3.  <span data-ttu-id="ddde9-121">検出されたコンポーネントの一覧を確認し、必要に応じて選択内容を変更して、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddde9-121">Review the list of components detected, modify the selections as necessary, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ddde9-122">[**接続パラメーター** ] ページで、スキャンするインスタンスを選択し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、認証方法を選択します。必要に応じて、ユーザー名とパスワードの情報を入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddde9-122">On the **Connection Parameters** page, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you want to scan, select the authentication method and, if necessary, enter user name and password information, and then click **Next**.</span></span>  
  
     <span data-ttu-id="ddde9-123">既定のインスタンス名は MSSQLSERVER です。</span><span class="sxs-lookup"><span data-stu-id="ddde9-123">The default instance name is MSSQLSERVER.</span></span>  
  
5.  <span data-ttu-id="ddde9-124">選択したコンポーネントに対し、必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-124">For selected components, enter the requested information.</span></span> <span data-ttu-id="ddde9-125">個々のダイアログボックスの詳細については、「 [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddde9-125">For more information about individual dialog boxes, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
6.  <span data-ttu-id="ddde9-126">[**アップグレードアドバイザーの設定の確認**] ページで、入力した情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-126">On the **Confirm Upgrade Advisor Setting** page, review the information that you entered.</span></span> <span data-ttu-id="ddde9-127">アップグレードレポートを送信する場合は、[**レポートをに [!INCLUDE[msCoName](../../includes/msconame-md.md)] 送信**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-127">You can select **Send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)]** if you want to submit your upgrade report.</span></span> <span data-ttu-id="ddde9-128">プライバシー ポリシーを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddde9-128">You can also review the privacy policy.</span></span>  
  
7.  <span data-ttu-id="ddde9-129">[**実行**] をクリックして、のインスタンスを分析し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ddde9-129">Click **Run** to analyze the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
8.  <span data-ttu-id="ddde9-130">分析が完了したら、[**レポートの起動**] をクリックして、検出されたアップグレードの問題を確認します。</span><span class="sxs-lookup"><span data-stu-id="ddde9-130">When the analysis is finished, click **Launch Report** to view the detected upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddde9-131">参照</span><span class="sxs-lookup"><span data-stu-id="ddde9-131">See Also</span></span>  
 <span data-ttu-id="ddde9-132">[方法: アップグレードアドバイザーを起動する](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="ddde9-132">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="ddde9-133">[アップグレードアドバイザー &#40;ユーザーインターフェイス&#41;を実行しています](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="ddde9-133">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 [<span data-ttu-id="ddde9-134">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="ddde9-134">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

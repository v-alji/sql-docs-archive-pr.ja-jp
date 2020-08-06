---
title: SSIS サービスにアクセスできるように Windows ファイアウォールを構成する |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], firewalls
- Windows Firewall [Integration Services]
- unauthorized access [Integration Services]
- Integration Services service, firewalls
- firewall systems [Integration Services]
- SQL Server Integration Services, firewalls
- SSIS, firewalls
ms.assetid: 39975cf2-c351-4205-8c39-27a0fadfb010
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d18b061ce16c88c50bbc08874efec455c28e15a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645754"
---
# <a name="configure-a-windows-firewall-for-access-to-the-ssis-service"></a><span data-ttu-id="9dfc2-102">SSIS サービスにアクセスするように Windows ファイアウォールを構成する</span><span class="sxs-lookup"><span data-stu-id="9dfc2-102">Configure a Windows Firewall for Access to the SSIS Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="9dfc2-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="9dfc2-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="9dfc2-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="9dfc2-106">Windows ファイアウォール システムは、ネットワーク接続経由でコンピューター リソースに不正なアクセスが行われるのを防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-106">The windowsfirewall system helps prevent unauthorized access to computer resources over a network connection.</span></span> <span data-ttu-id="9dfc2-107">このファイアウォールを経由して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] にアクセスするには、アクセスを有効にするようにファイアウォールを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-107">To access [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] through this firewall, you have to configure the firewall to enable access.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9dfc2-108">リモート サーバーに格納されるパッケージを管理するために、そのリモート サーバー上の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスのインスタンスに接続する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-108">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="9dfc2-109">代わりに、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの構成ファイルを編集し、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でリモート サーバーに格納されているパッケージが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-109">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="9dfc2-110">詳細については、「 [Integration Services サービスの構成 (SSIS サービス)](configuring-the-integration-services-service-ssis-service.md)との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](configuring-the-integration-services-service-ssis-service.md).</span></span>  
  
 <span data-ttu-id="9dfc2-111">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、DCOM プロトコルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-111">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses the DCOM protocol.</span></span> <span data-ttu-id="9dfc2-112">ファイアウォール経由で DCOM プロトコルがどのように動作するかの詳細については、「[ファイアウォールでの分散 COM の使用](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-112">For more information about how the DCOM protocol works through firewalls, see the article, "[Using Distributed COM with Firewalls](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)".</span></span>  
  
 <span data-ttu-id="9dfc2-113">多くのファイアウォール システムが市販されています。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-113">There are many firewall systems available.</span></span> <span data-ttu-id="9dfc2-114">Windows ファイアウォール以外のファイアウォールを実行している場合、使用しているシステム固有の情報については、そのファイアウォールのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-114">If you are running a firewall other than windowsfirewall, see your firewall documentation for information that is specific to the system you are using.</span></span>  
  
 <span data-ttu-id="9dfc2-115">ファイアウォールでアプリケーション レベルのフィルター処理がサポートされている場合は、Windows によって提供されるユーザー インターフェイスを使用して、プログラムやサービスなどの例外を指定し、ファイアウォールを通過することを許可できます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-115">If the firewall supports application-level filtering, you can use the user interface that Windows provides to specify the exceptions that are allowed through the firewall, such as programs and services.</span></span> <span data-ttu-id="9dfc2-116">それ以外の場合は、限定された TCP ポートのセットを使用するように DCOM を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-116">Otherwise, you have to configure DCOM to use a limited set of TCP ports.</span></span> <span data-ttu-id="9dfc2-117">上記の Microsoft Web サイト リンクには、使用する TCP ポートを指定する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-117">The Microsoft website link previously provided includes information about how to specify the TCP ports to use.</span></span>  
  
 <span data-ttu-id="9dfc2-118">Integration Services サービスでは、ポート 135 を使用します。このポートは変更できません。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-118">The Integration Services service uses port 135, and the port cannot be changed.</span></span> <span data-ttu-id="9dfc2-119">サービス コントロール マネージャー (SCM) のアクセスのためには、TCP ポート 135 を開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-119">You have to open TCP port 135 for access to the service control manager (SCM).</span></span> <span data-ttu-id="9dfc2-120">SCM は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの起動と停止、実行中のサービスに対する制御要求の転送などのタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-120">SCM performs tasks such as starting and stopping [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] services and transmitting control requests to the running service.</span></span>  
  
 <span data-ttu-id="9dfc2-121">以下のセクションに記載されている情報は、Windows ファイアウォールに固有の情報です。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-121">The information in the following section is specific to windowsfirewall.</span></span> <span data-ttu-id="9dfc2-122">Windows ファイアウォール システムを構成する方法には、コマンド プロンプトでコマンドを実行する方法と、[Windows ファイアウォール] ダイアログ ボックスでプロパティを設定する方法があります。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-122">You can configure the windowsfirewall system by running a command at the command prompt, or by setting properties in the windowsfirewall dialog box.</span></span>  
  
 <span data-ttu-id="9dfc2-123">Windows ファイアウォールの既定の設定の詳細と、データベース エンジン、Analysis Services、Reporting Services、および Integration Services に影響する TCP ポートの説明については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-123">For more information about the default windowsfirewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="configuring-a-windowsfirewall"></a><span data-ttu-id="9dfc2-124">Windows ファイアウォールの構成</span><span class="sxs-lookup"><span data-stu-id="9dfc2-124">Configuring a windowsfirewall</span></span>  
 <span data-ttu-id="9dfc2-125">次のコマンドを使用すると、TCP ポート 135 を開き、MsDtsSrvr.exe を例外リストに追加し、ファイアウォールのブロックを解除するスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-125">You can use the following commands to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-windowsfirewall-using-the-command-prompt-window"></a><span data-ttu-id="9dfc2-126">コマンド プロンプト ウィンドウを使用して Windows ファイアウォールを構成するには</span><span class="sxs-lookup"><span data-stu-id="9dfc2-126">To configure a windowsfirewall using the Command Prompt window</span></span>  
  
1.  <span data-ttu-id="9dfc2-127">`netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET` コマンドを実行します</span><span class="sxs-lookup"><span data-stu-id="9dfc2-127">Run the command: `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`</span></span>  
  
2.  <span data-ttu-id="9dfc2-128">`netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET` コマンドを実行します</span><span class="sxs-lookup"><span data-stu-id="9dfc2-128">Run the command: `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9dfc2-129">すべてのコンピューターおよびインターネット上のコンピューターに対してファイアウォールを開くには、scope=SUBNET を scope=ALL に変更します。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-129">To open the firewall for all computers, and also for computers on the Internet, replace scope=SUBNET with scope=ALL.</span></span>  
  
 <span data-ttu-id="9dfc2-130">次の手順では、Windows のユーザー インターフェイスを使用して、TCP ポート 135 を開き、MsDtsSrvr.exe を例外リストに追加して、ファイアウォールのブロックを解除するスコープを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-130">The following procedure describes how to use the Windows user interface to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-firewall-using-the-windowsfirewall-dialog-box"></a><span data-ttu-id="9dfc2-131">[Windows ファイアウォール] ダイアログ ボックスを使用してファイアウォールを構成するには</span><span class="sxs-lookup"><span data-stu-id="9dfc2-131">To configure a firewall using the windowsfirewall dialog box</span></span>  
  
1.  <span data-ttu-id="9dfc2-132">コントロール パネルの **[Windows ファイアウォール]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-132">In the Control Panel, double-click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="9dfc2-133">**[Windows ファイアウォール]** ダイアログ ボックスで、 **[例外]** タブをクリックし、 **[プログラムの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-133">In the **Windows Firewall** dialog box, click the **Exceptions** tab and then click **Add Program.**</span></span>  
  
3.  <span data-ttu-id="9dfc2-134">**[プログラムの追加]** ダイアログ ボックスで、 **[参照]** をクリックし、Program Files\Microsoft SQL Server\100\DTS\Binn フォルダーに移動します。次に MsDtsSrvr.exe をクリックし、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-134">In the **Add a Program** dialog box, **click Browse**, navigate to the Program Files\Microsoft SQL Server\100\DTS\Binn folder, click MsDtsSrvr.exe, and then click **Open**.</span></span> <span data-ttu-id="9dfc2-135">**[OK]** をクリックして、 **[プログラムの追加]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-135">Click **OK** to close the **Add a Program** dialog box.</span></span>  
  
4.  <span data-ttu-id="9dfc2-136">**[例外]** タブで、 **[ポートの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-136">On the **Exceptions** tab, click **Add Port.**</span></span>  
  
5.  <span data-ttu-id="9dfc2-137">**[ポートの追加]** ダイアログ ボックスの **[名前]** ボックスに、「 **RPC(TCP/135)**」またはその他のわかりやすい名前を入力します。次に、 **[ポート番号]** ボックスに「 **135** 」と入力し、 **[TCP]** をクリックにします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-137">In the **Add a Port** dialog box, type **RPC(TCP/135)** or another descriptive name in the **Nam**e box, type **135** in the **Port Number** box, and then select **TCP**.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="9dfc2-138">サービスは常にポート 135 を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-138">service always uses port 135.</span></span> <span data-ttu-id="9dfc2-139">別のポートを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-139">You cannot specify a different port.</span></span>  
  
6.  <span data-ttu-id="9dfc2-140">**[ポートの追加]** ダイアログ ボックスで、必要に応じて **[スコープの変更]** をクリックし、既定のスコープを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-140">In the **Add a Port** dialog box, you can optionally click **Change Scope** to modify the default scope.</span></span>  
  
7.  <span data-ttu-id="9dfc2-141">**[スコープの変更]** ダイアログ ボックスで、 **[ユーザーのネットワーク (サブネット) のみ]** を選択するか、カスタムの一覧を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-141">In the **Change Scope** dialog box, select **My network (subnet only)** or type a custom list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="9dfc2-142">**[OK]** をクリックして **[ポートの追加]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-142">To close the **Add a Port** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="9dfc2-143">**[OK]** をクリックして **[Windows ファイアウォール]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-143">To close the **Windows Firewall** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9dfc2-144">Windows ファイアウォールを構成するために、この手順では、コントロール パネルの **[Windows ファイアウォール]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-144">To configure the windowsfirewall, this procedure uses the **Windows Firewall** item in Control Panel.</span></span> <span data-ttu-id="9dfc2-145">**[Windows ファイアウォール]** では、現在のネットワークの場所のプロファイルに対してのみファイアウォールを構成できます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-145">The **Windows Firewall** item only configures the firewall for the current network location profile.</span></span> <span data-ttu-id="9dfc2-146">ただし、Windows ファイアウォールは、 **netsh** コマンド ライン ツール、またはセキュリティが強化された Windows ファイアウォールの [!INCLUDE[msCoName](../includes/msconame-md.md)] 管理コンソール (MMC) スナップインを使用して構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-146">However, you can also configure the windowsfirewall by using the **netsh** command line tool or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC) snap-in named windowsfirewall with Advanced Security.</span></span> <span data-ttu-id="9dfc2-147">これらのツールの詳細については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfc2-147">For more information about these tools, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dfc2-148">参照</span><span class="sxs-lookup"><span data-stu-id="9dfc2-148">See Also</span></span>  
 <span data-ttu-id="9dfc2-149">[SSIS サービス &#40;Integration Services サービスの構成&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="9dfc2-149">[Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="9dfc2-150">Integration Services サービス (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="9dfc2-150">Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  

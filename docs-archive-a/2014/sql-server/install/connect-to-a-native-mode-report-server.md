---
title: ネイティブモードのレポートサーバーへの接続 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634242"
---
# <a name="connect-to-a-native-mode-report-server"></a><span data-ttu-id="97890-102">ネイティブ モードのレポート サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="97890-102">Connect to a Native Mode Report Server</span></span>
  <span data-ttu-id="97890-103">このダイアログ ボックスを使用すると、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のローカルまたはリモートの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー インスタンスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="97890-103">Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server instance.</span></span> <span data-ttu-id="97890-104">このツールを使用して、以前のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーに接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="97890-104">You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span> <span data-ttu-id="97890-105">一度に接続できるインスタンスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="97890-105">You can only connect to one instance at a time.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="97890-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="97890-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97890-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードを構成および管理するために、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは使用しません。</span><span class="sxs-lookup"><span data-stu-id="97890-107">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="97890-108">SharePoint モードでレポート サーバーを構成するには、SharePoint サーバーの全体管理と PowerShell スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="97890-108">You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="97890-109">詳細については、「 [SharePoint 2010 用 Reporting Services の SharePoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97890-109">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="97890-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager (RSConfigTool.exe) は、"highestAvailable" の特権レベルでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="97890-110">The[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) is installed with a privilege level of "highestAvailable".</span></span> <span data-ttu-id="97890-111">この動作は仕様です。</span><span class="sxs-lookup"><span data-stu-id="97890-111">This behavior is by design.</span></span> <span data-ttu-id="97890-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API と通信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97890-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI APIs.</span></span> <span data-ttu-id="97890-113">一部の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通信には、高いレベルまたは管理者の特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="97890-113">Some of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI communication requires a higher level or administrative of privileges.</span></span>  
  
-   <span data-ttu-id="97890-114">ローカル レポート サーバー インスタンスに接続するには、既定値を使用して **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97890-114">To connect to a local report server instance, use the default values and click **Connect**.</span></span> <span data-ttu-id="97890-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーにより、ローカル サーバー名が提供され、既定のインスタンスが検出されます。</span><span class="sxs-lookup"><span data-stu-id="97890-115">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the local server name and detects the default instance.</span></span> <span data-ttu-id="97890-116">ほとんどの場合、値を変更せずに **[接続]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="97890-116">In most cases, you can click **Connect** without having to change the values.</span></span> <span data-ttu-id="97890-117">複数のインスタンスがインストールされている場合は、使用するインスタンスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97890-117">If you installed more than one instance, you must select the one that you want to use.</span></span>  
  
-   <span data-ttu-id="97890-118">リモート レポート サーバー インスタンスに接続するには、サーバー名を入力して **[検索]** をクリックします。次に、インスタンスを選択して **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97890-118">To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="97890-119">このダイアログ ボックスを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="97890-119">To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="97890-120">このダイアログ ボックスは、ツールを起動すると直ちに表示されます。</span><span class="sxs-lookup"><span data-stu-id="97890-120">This dialog box appears immediately when you start the tool.</span></span> <span data-ttu-id="97890-121">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97890-121">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="97890-122">Options</span><span class="sxs-lookup"><span data-stu-id="97890-122">Options</span></span>  
 <span data-ttu-id="97890-123">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="97890-123">**Server Name**</span></span>  
 <span data-ttu-id="97890-124">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされているコンピューターのネットワーク名を入力します。</span><span class="sxs-lookup"><span data-stu-id="97890-124">Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is installed.</span></span> <span data-ttu-id="97890-125">プレフィックスやスラッシュを含めずに、コンピューター名だけを入力してください。</span><span class="sxs-lookup"><span data-stu-id="97890-125">Type just the computer name; do not include a prefix or slashes.</span></span>  
  
 <span data-ttu-id="97890-126">**探す**</span><span class="sxs-lookup"><span data-stu-id="97890-126">**Find**</span></span>  
 <span data-ttu-id="97890-127">**[サーバー名]** で指定したコンピューターを検索します。</span><span class="sxs-lookup"><span data-stu-id="97890-127">Find the computer specified in **Server Name**.</span></span>  
  
 <span data-ttu-id="97890-128">**[レポート サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="97890-128">**Report Server Instance**</span></span>  
 <span data-ttu-id="97890-129">複数のレポート サーバー インスタンスをインストールしている場合は、接続先のインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="97890-129">Select which instance to connect to if multiple report server instances are installed.</span></span> <span data-ttu-id="97890-130">選択できるのは有効なインスタンスだけです。</span><span class="sxs-lookup"><span data-stu-id="97890-130">Only valid instances are available for selection.</span></span> <span data-ttu-id="97890-131">以前のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをサイド バイ サイドで実行している場合は、一覧にインスタンスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="97890-131">If you are running older versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, those instances will not appear in the list.</span></span>  
  
 <span data-ttu-id="97890-132">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="97890-132">**Connect**</span></span>  
 <span data-ttu-id="97890-133">指定したサーバーおよびインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="97890-133">Connect to the server and instance you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97890-134">参照</span><span class="sxs-lookup"><span data-stu-id="97890-134">See Also</span></span>  
 [<span data-ttu-id="97890-135">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="97890-135">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  

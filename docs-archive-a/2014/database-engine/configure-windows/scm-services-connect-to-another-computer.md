---
title: 別のコンピューターへの接続 (SQL Server 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3d478cebc1ca36ccb8f87b0355b7c8fe0a928cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645850"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a><span data-ttu-id="9404d-102">別のコンピューターへの接続 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="9404d-102">Connect to Another Computer (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="9404d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で別のコンピューターに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9404d-103">This topic describes how to connect to another computer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9404d-104">Windows の [コンピューターの管理] の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) を開くための最初の手順に従って、コンピューターに接続し、[サービスとアプリケーション] ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9404d-104">Follow the first procedure to open the Windows Computer Management [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (mmc), connect to the computer, and expand the Services and Applications tree.</span></span> <span data-ttu-id="9404d-105">2 番目の手順に従って、リモート コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーへのリンクを含むファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9404d-105">Follow the second procedure to create a file with a link to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9404d-106">リモートで接続している場合、一部の操作は構成マネージャーで実行することができません。</span><span class="sxs-lookup"><span data-stu-id="9404d-106">Some actions cannot be performed by Configuration Manager when connecting remotely.</span></span>  
  
 <span data-ttu-id="9404d-107">別のコンピューターのサービスを開始、停止、一時停止、または再開するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサーバーに接続し、サーバーまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを右クリックし、次に目的の操作をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-107">To start, stop, pause, or resume services on another computer, you can also connect to the server with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the server or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and then click the desired action.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a><span data-ttu-id="9404d-108">Windows のコンピューターの管理を使用して別のコンピューターに接続するには</span><span class="sxs-lookup"><span data-stu-id="9404d-108">To connect to another computer with Windows Computer Management</span></span>  
  
1.  <span data-ttu-id="9404d-109">**[スタート]** メニューで **[マイ コンピューター]** を右クリックし、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-109">On the **Start** menu, right-click **My Computer**, and then click **Manage.**</span></span>  
  
2.  <span data-ttu-id="9404d-110">**[コンピューターの管理]** で **[コンピューターの管理 (ローカル)]** を右クリックし、 **[別のコンピューターへ接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-110">In **Computer Management**, right-click **Computer Management (Local)**, and then click **Connect to another computer**.</span></span>  
  
3.  <span data-ttu-id="9404d-111">**[コンピューターの選択]** ダイアログ ボックスの **[別のコンピューター]** ボックスに管理するコンピューターの名前を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-111">In the **Select Computer** dialog box, in the **Another computer** text box, type the name of the computer you want to manage, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9404d-112">リモート コンピューターで実行されているサービスが、[コンピューターの管理] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9404d-112">Computer Management displays the services running on the remote computer.</span></span> <span data-ttu-id="9404d-113">最上位ノードが **[コンピューターの管理** ]\<*remotecomputer*> に変更されます。</span><span class="sxs-lookup"><span data-stu-id="9404d-113">The top-level node changes to **Computer Management** \<*remotecomputer*>.</span></span>  
  
4.  <span data-ttu-id="9404d-114">コンソール ツリーの **[サービスとアプリケーション]** を展開し、 **[SQL Server 構成マネージャー]** を展開して、リモート コンピューターのサービスを管理します。</span><span class="sxs-lookup"><span data-stu-id="9404d-114">In the console tree, expand **Services and Applications**, and then expand **SQL Server Configuration Manager** to manage the remote computer's services.</span></span>  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a><span data-ttu-id="9404d-115">別のコンピューターの SQL Server 構成マネージャーへのリンクを保存するには</span><span class="sxs-lookup"><span data-stu-id="9404d-115">To save a link to SQL Server Configuration Manager for another computer</span></span>  
  
1.  <span data-ttu-id="9404d-116">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-116">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="9404d-117">[**名前**] ボックスに「」と入力して、 `mmc -a` [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールを作成者モードで開きます。</span><span class="sxs-lookup"><span data-stu-id="9404d-117">In the **Open** box, type `mmc -a` to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console in author mode.</span></span>  
  
3.  <span data-ttu-id="9404d-118">**[ファイル]** メニューの **[スナップインの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-118">On the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
4.  <span data-ttu-id="9404d-119">**[スナップインの追加と削除]** ウィンドウで **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-119">In the **Add/Remove Snap-in** window, click **Add**.</span></span>  
  
5.  <span data-ttu-id="9404d-120">**[スタンドアロン スナップインの追加]** ウィンドウで **[コンピューターの管理]** をクリックし、次に **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-120">In the **Add Standalone Snap-in** window, click **Computer Management** and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="9404d-121">**[コンピューターの管理]** ウィンドウの **[別のコンピューター]** をクリックし、管理するリモート コンピューターの名前を入力して **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-121">In the **Computer Management** window, click **Another computer**, type the name of the remote computer you wish to manage, and then click **Finish**.</span></span>  
  
7.  <span data-ttu-id="9404d-122">**[スタンドアロン スナップインの追加]** ウィンドウで **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-122">In the **Add Standalone Snap-in** window, click **Close**.</span></span>  
  
8.  <span data-ttu-id="9404d-123">**[スナップインの追加と削除]** ウィンドウで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-123">In the **Add/Remove Snap-in** window, click **OK**.</span></span>  
  
9. <span data-ttu-id="9404d-124">[**コンピューターの管理] ( ***\<computer name>*** )**、[**サービスとアプリケーション**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="9404d-124">Expand **Computer Management (***\<computer name>***)**, and **Services and Applications**.</span></span>  
  
10. <span data-ttu-id="9404d-125">**[SQL Server 構成マネージャー]** を右クリックして、 **[ここから新しいウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-125">Right-click **SQL Server Configuration Manager**, and then click **New Window from here**.</span></span>  
  
11. <span data-ttu-id="9404d-126">**[ウィンドウ]** メニューの **[コンソール ルート]** をクリックし、最初のウィンドウに切り替えてからそのウィンドウを削除します。</span><span class="sxs-lookup"><span data-stu-id="9404d-126">On the **Window** menu, click **Console Root**, to switch back to the first window, and delete the window.</span></span>  
  
12. <span data-ttu-id="9404d-127">[**ファイル**] メニューの [名前を付け**て保存**] をクリックし、ファイル拡張子の付いた適切な名前を使用して、目的のフォルダーにファイルを保存し `.msc` ます。</span><span class="sxs-lookup"><span data-stu-id="9404d-127">On the **File** menu, click **Save As**, and save the file in the desired folder, with an appropriate name with the `.msc` file extension.</span></span> <span data-ttu-id="9404d-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9404d-128">Close the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span>  
  
13. <span data-ttu-id="9404d-129">ターゲット コンピューターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、そのファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404d-129">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on the target computer, double-click the file.</span></span> <span data-ttu-id="9404d-130">必要な場合は、デスクトップまたは **[スタート]** メニューにファイルへのリンクを保存します。</span><span class="sxs-lookup"><span data-stu-id="9404d-130">If desired, save a link to the file on the desktop or in the **Start** menu.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9404d-131">リモート コンピューターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用する場合、コンピューター名が明らかではないため、誤って別のコンピューターを停止または構成してしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9404d-131">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer, the computer name is not obvious and it is possible to mistakenly stop or configure the wrong computer.</span></span> <span data-ttu-id="9404d-132">サービスを変更する前に、 **[サービス]** タブの **[ホスト名]** ボックスを調べてコンピューター名を確認してください。</span><span class="sxs-lookup"><span data-stu-id="9404d-132">On the **Service** tab, check the **Host Name** box to confirm the computer name before modifying a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9404d-133">参照</span><span class="sxs-lookup"><span data-stu-id="9404d-133">See Also</span></span>  
 [<span data-ttu-id="9404d-134">SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成</span><span class="sxs-lookup"><span data-stu-id="9404d-134">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  

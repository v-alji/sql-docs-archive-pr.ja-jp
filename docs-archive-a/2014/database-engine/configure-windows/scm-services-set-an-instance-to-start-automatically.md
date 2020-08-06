---
title: SQL Server のインスタンスを自動的に開始するように設定する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2fc21bd881c1588da47710c6d8437e31d3df2ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738754"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a><span data-ttu-id="70f6a-102">SQL Server のインスタンスが自動的に開始されるようにする設定 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="70f6a-102">Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="70f6a-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスを自動的に開始するように設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70f6a-103">This topic describes how to set an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to start automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="70f6a-104">セットアップのとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常、自動的に開始するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="70f6a-104">During setup, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is normally configured to start automatically.</span></span> <span data-ttu-id="70f6a-105">手動で開始するように構成した場合、この設定をいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="70f6a-105">If this was not done, you can change that setting at any time.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="70f6a-106">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="70f6a-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a><span data-ttu-id="70f6a-107">SQL Server のインスタンスを自動的に起動するように設定するには</span><span class="sxs-lookup"><span data-stu-id="70f6a-107">To set an instance of SQL Server to start automatically</span></span>  
  
1.  <span data-ttu-id="70f6a-108">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70f6a-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70f6a-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="70f6a-109">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="70f6a-110">**Windows 10**:</span><span class="sxs-lookup"><span data-stu-id="70f6a-110">**Windows 10**:</span></span>  
    >          <span data-ttu-id="70f6a-111">Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="70f6a-111">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="70f6a-112">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="70f6a-112">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="70f6a-113">SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。</span><span class="sxs-lookup"><span data-stu-id="70f6a-113">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="70f6a-114">Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70f6a-114">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="70f6a-115">Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70f6a-115">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="70f6a-116">**Windows 8**:</span><span class="sxs-lookup"><span data-stu-id="70f6a-116">**Windows 8**:</span></span>  
    >          <span data-ttu-id="70f6a-117">Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 \*\*SQLServerManager \<version> \*\* 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="70f6a-117">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="70f6a-118">**[SQL Server 構成マネージャー]** で **[サービス]** を展開し、 **[SQL Server]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70f6a-118">In **SQL Server Configuration Manager**, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="70f6a-119">詳細ペインで、自動的に開始するインスタンスの名前を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70f6a-119">In the details pane, right-click the name of the instance you want to start automatically, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="70f6a-120">**[SQL Server \<***instancename***> のプロパティ]** ダイアログ ボックスで、 **[開始モード]** を **[自動]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="70f6a-120">In the **SQL Server \<***instancename***> Properties** dialog box, set **Start Mode** to **Automatic**.</span></span>  
  
5.  <span data-ttu-id="70f6a-121">**[OK]** をクリックして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="70f6a-121">Click **OK**, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f6a-122">参照</span><span class="sxs-lookup"><span data-stu-id="70f6a-122">See Also</span></span>  
 <span data-ttu-id="70f6a-123">[SQL Server のインスタンスの自動開始の回避 &#40;SQL Server 構成マネージャー&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span><span class="sxs-lookup"><span data-stu-id="70f6a-123">[Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span></span>  
 <span data-ttu-id="70f6a-124">[別のコンピューターへの接続 &#40;SQL Server 構成マネージャー&#41;](scm-services-connect-to-another-computer.md) </span><span class="sxs-lookup"><span data-stu-id="70f6a-124">[Connect to Another Computer &#40;SQL Server Configuration Manager&#41;](scm-services-connect-to-another-computer.md) </span></span>  
 [<span data-ttu-id="70f6a-125">SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成</span><span class="sxs-lookup"><span data-stu-id="70f6a-125">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  

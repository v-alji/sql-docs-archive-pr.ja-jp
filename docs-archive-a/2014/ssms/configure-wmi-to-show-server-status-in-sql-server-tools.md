---
title: SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 138abbe2b7b819d6afd6da62135f7cd7ce86496f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737422"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a><span data-ttu-id="15ebe-102">SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成</span><span class="sxs-lookup"><span data-stu-id="15ebe-102">Configure WMI to Show Server Status in SQL Server Tools</span></span>
  <span data-ttu-id="15ebe-103">このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]で、SQL Server ツールにサーバーの状態を表示するように WMI を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15ebe-103">This topic describes how to configure WMI to show the server status in SQL Server tools in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="15ebe-104">サーバーに接続する際には、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]構成マネージャーだけでなく [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のコンポーネントである登録済みサーバーおよびオブジェクト エクスプローラーの両方で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) サービスおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント (MSSQLSERVER) サービスの状態を取得するために、WMI (Windows Management Instrumentation) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="15ebe-104">When connecting to servers, both the Registered Servers and Object Explorer components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], as well as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager, use Windows Management Instrumentation (WMI) to obtain the status of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER) services.</span></span> <span data-ttu-id="15ebe-105">サービスの状態を表示するには、WMI オブジェクトに対するリモート アクセスの権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="15ebe-105">To display the status of the service, the user must have rights to remotely access the WMI object.</span></span> <span data-ttu-id="15ebe-106">このアクセス許可を構成するには、サーバーに WMI をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ebe-106">The server must have WMI installed to configure this permission.</span></span>  
  
##  <a name="to-configure-wmi-permission"></a><a name="SSMSProcedure"></a><span data-ttu-id="15ebe-107">WMI アクセス許可を構成するには</span><span class="sxs-lookup"><span data-stu-id="15ebe-107">To configure WMI permission</span></span>  
  
1.  <span data-ttu-id="15ebe-108">リモート サーバーの **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ebe-108">On the **Start** menu on the remote server, click **Run**.</span></span>  
  
2.  <span data-ttu-id="15ebe-109">[**名前**] ボックスに「」と入力し、 `wmimgmt.msc` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ebe-109">In the **Open** box type `wmimgmt.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="15ebe-110">**[Windows Management Infrastructure (WMI)]** の **[WMI コントロール (ローカル)]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ebe-110">In the **Windows Management Infrastructure** program, right-click **WMI Control (Local)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="15ebe-111">**[WMI コントロール (ローカル) のプロパティ]** ダイアログ ボックスの **[セキュリティ]** タブで、 **[Root]** を展開し、 **[CIMV2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ebe-111">In the **WMI Control (Local) Properties** dialog box, on the **Security** tab, expand **Root**, and then click **CIMV2**.</span></span>  
  
5.  <span data-ttu-id="15ebe-112">**[セキュリティ]** をクリックして **[セキュリティ ROOT\CIMV2]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="15ebe-112">Click **Security** to open the **Security for ROOT\CIMV2** dialog box.</span></span>  
  
6.  <span data-ttu-id="15ebe-113">**[グループ名またはユーザー名]** ボックスにグループまたはユーザーを追加して選択します。</span><span class="sxs-lookup"><span data-stu-id="15ebe-113">Add a group or user to the **Group or user names** box and select it.</span></span>  
  
7.  <span data-ttu-id="15ebe-114">**[**_\<group or user> のアクセス許可]_ ボックスで、サービスの状態をリモートから確認できるようにするユーザーの **[リモートの有効化]** の **[許可]** 列にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="15ebe-114">In the **Permissions for**_\<group or user>_ box, select the **Allow** column, for the **Remote Enable** permission, for users whom you wish to remotely detect the service status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ebe-115">参照</span><span class="sxs-lookup"><span data-stu-id="15ebe-115">See Also</span></span>  
 [<span data-ttu-id="15ebe-116">SQL Server エージェント サービスの開始、停止、または一時停止</span><span class="sxs-lookup"><span data-stu-id="15ebe-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  

---
title: SQL Server のインスタンスの自動起動を禁止する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f93f5abc749f589ab4208b3a4c9434ca63b8769
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641862"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="0b88a-102">SQL Server のインスタンスの自動開始の回避 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="0b88a-102">Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="0b88a-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスが自動的に開始されないようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b88a-103">This topic describes how prevent an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from starting automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0b88a-104">は通常、自動的に開始するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="0b88a-104">is normally configured to start automatically.</span></span> <span data-ttu-id="0b88a-105">インスタンスの開始モードを手動に設定することによって、その構成を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0b88a-105">You can change that by setting the start mode for the instance to manual.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0b88a-106">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="0b88a-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a><span data-ttu-id="0b88a-107">SQL Server のインスタンスの自動開始を回避するには</span><span class="sxs-lookup"><span data-stu-id="0b88a-107">To prevent automatic startup of an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="0b88a-108">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b88a-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="0b88a-109">[SQL Server 構成マネージャー] で **[サービス]** を展開し、 **[SQL Server]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b88a-109">In SQL Server Configuration Manager, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="0b88a-110">詳細ペインで、 **[MSSQLServer]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b88a-110">In the details pane, right-click **MSSQLServer**, and then click **Properties.**</span></span>  
  
4.  <span data-ttu-id="0b88a-111">[ **SQL Server の \<**_instancename_**> プロパティ**] ダイアログボックスの [**プロパティ**] ボックスで、[**開始モード**] の値を [**手動**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="0b88a-111">In the **SQL Server \<**_instancename_**> Properties** dialog box, in the **Properties** box, set the value of **Start Mode** to **Manual**.</span></span>  
  
5.  <span data-ttu-id="0b88a-112">**[OK]** をクリックして **[SQL Server \<**_instancename_**> のプロパティ]** ダイアログ ボックスを閉じ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0b88a-112">Click **OK** to close the **SQL Server \<**_instancename_**> Properties** dialog box, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b88a-113">参照</span><span class="sxs-lookup"><span data-stu-id="0b88a-113">See Also</span></span>  
 [<span data-ttu-id="0b88a-114">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="0b88a-114">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  

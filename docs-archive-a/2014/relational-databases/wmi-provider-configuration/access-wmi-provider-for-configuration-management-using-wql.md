---
title: WQL を使用して構成管理の WMI プロバイダーにアクセスする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b58297c5e292ceb18a6e2e50e2b25b9aa352e2fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630823"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a><span data-ttu-id="f3695-102">WQL を使用して構成管理の WMI プロバイダーにアクセスする</span><span class="sxs-lookup"><span data-stu-id="f3695-102">Access WMI Provider for Configuration Management using WQL</span></span>
  <span data-ttu-id="f3695-103">このセクションでは、WMI Provider for Computer Management に対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL (Windows Management Instrumentation Query Language) ステートメントを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3695-103">This section describes how to execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language (WQL) statements against the WMI Provider for Computer Management.</span></span>  
  
 <span data-ttu-id="f3695-104">この例では、WQL エディター、WBEMtest.exe を使用して、WMI プロバイダーに対して WQL クエリを実行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク プロトコル、および別名を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f3695-104">The example uses a WQL editor, WBEMtest.exe, to run WQL queries against the WMI Provider to enumerate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network protocols, and aliases.</span></span>  
  
### <a name="querying-services-using-wbemtest"></a><span data-ttu-id="f3695-105">WBEMtest を使用したサービスの照会</span><span class="sxs-lookup"><span data-stu-id="f3695-105">Querying services using WBEMtest</span></span>  
  
1.  <span data-ttu-id="f3695-106">[**スタート**] メニューの [**実行**] をクリックし、「」と入力し `WBEMtest` ます。</span><span class="sxs-lookup"><span data-stu-id="f3695-106">From the **Start** menu, click **Run**, and then enter `WBEMtest`.</span></span>  
  
2.  <span data-ttu-id="f3695-107">WBEMtest.exe のダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3695-107">The WBEMtest.exe dialog appears.</span></span> <span data-ttu-id="f3695-108">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3695-108">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="f3695-109">最初のテキスト フィールドに、WMI Provider for Computer Management の名前空間 (「root\Microsoft\SqlServer\ComputerManagement11」) を入力します。</span><span class="sxs-lookup"><span data-stu-id="f3695-109">In the first text field, type the WMI Provider for Computer Management namespace: root\Microsoft\SqlServer\ComputerManagement11.</span></span> <span data-ttu-id="f3695-110">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3695-110">Click **Connect**.</span></span>  
  
4.  <span data-ttu-id="f3695-111">**[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3695-111">Click **Query**.</span></span> <span data-ttu-id="f3695-112">ローカルコンピューターで現在実行されているサービスを返すクエリを入力します: **SELECT \* FROM sqlservice。**</span><span class="sxs-lookup"><span data-stu-id="f3695-112">Type a query that returns the current services running on the local computer: **SELECT \* FROM SqlService.**</span></span> <span data-ttu-id="f3695-113">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3695-113">Click **Apply**.</span></span>  
  
5.  <span data-ttu-id="f3695-114">「`WHERE ServiceName = "MSSQLSERVER"`」を追加することで、クエリを絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="f3695-114">Further refine the query by adding `WHERE ServiceName = "MSSQLSERVER"`.</span></span>  
  
  

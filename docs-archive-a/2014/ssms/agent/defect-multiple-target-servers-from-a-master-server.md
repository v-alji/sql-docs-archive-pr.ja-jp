---
title: マスター サーバーからの複数のターゲット サーバーの参加の解除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
ms.openlocfilehash: b31a8bc38968733de0a23f67a71772721c8baedd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715037"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="d7c40-102">マスター サーバーからの複数のターゲット サーバーの参加の解除</span><span class="sxs-lookup"><span data-stu-id="d7c40-102">Defect Multiple Target Servers from a Master Server</span></span>
  <span data-ttu-id="d7c40-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、マルチサーバー管理構成から複数のターゲット サーバーの参加を解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c40-103">This topic describes how to defect multiple target servers from a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d7c40-104">この手順はマスター サーバーから実行します。</span><span class="sxs-lookup"><span data-stu-id="d7c40-104">Run this procedure from the master server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d7c40-105">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d7c40-105">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="d7c40-106">マスター サーバーから複数のターゲット サーバーの参加を解除するには</span><span class="sxs-lookup"><span data-stu-id="d7c40-106">To defect multiple target servers from a master server</span></span>  
  
1.  <span data-ttu-id="d7c40-107">**オブジェクト エクスプローラー**で、マスター サーバーとして構成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d7c40-107">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="d7c40-108">**[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7c40-108">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="d7c40-109">**[命令を通知]** をクリックし、 **[命令の種類]** ボックスの一覧の **[参加解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7c40-109">Click **Post Instructions**, and then in the **Instruction type** list, select **Defect**.</span></span>  
  
4.  <span data-ttu-id="d7c40-110">**[受信者]** で、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d7c40-110">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="d7c40-111">このマスター サーバーのすべてのターゲット サーバーの参加を解除するには、**[すべてのターゲット サーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7c40-111">Click **All target servers** to defect all target servers of this master server.</span></span> <span data-ttu-id="d7c40-112">このオプションは、現在のマルチサーバー管理構成を完全にアンインストールする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="d7c40-112">Use this option if you want to completely uninstall the current multiserver administration configuration.</span></span>  
  
    -   <span data-ttu-id="d7c40-113">このマスター サーバーから一部のターゲット サーバーだけを参加解除するには、 **[特定のターゲット サーバー]** をクリックし、参加を解除するサーバーの **[選択]** ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7c40-113">Click **These target servers**, and then click the corresponding **Select** box, to defect some, but not all, target servers of this master server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c40-114">参照</span><span class="sxs-lookup"><span data-stu-id="d7c40-114">See Also</span></span>  
 <span data-ttu-id="d7c40-115">[マルチサーバー環境の作成](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="d7c40-115">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="d7c40-116">[エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="d7c40-116">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="d7c40-117">マスター サーバーからのターゲット サーバーの参加の解除</span><span class="sxs-lookup"><span data-stu-id="d7c40-117">Defect a Target Server from a Master Server</span></span>](defect-a-target-server-from-a-master-server.md)  
  
  

---
title: SQL Server の Managed Instance (SQL Server ユーティリティ) でユーティリティコレクションセットのプロキシアカウントを変更します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19f60c607ed661ef42c1c1c0e48854cdfd69a912
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633151"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a><span data-ttu-id="94461-102">SQL Server のマネージド インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントの変更 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="94461-102">Change the Proxy Account for the Utility Collection Set on a Managed Instance of SQL Server (SQL Server Utility)</span></span>
  <span data-ttu-id="94461-103">このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のマネージド インスタンスでユーティリティ コレクション セットのプロキシ アカウントを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94461-103">This topic describes how to change the proxy account for the Utility Collection Set on a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="94461-104">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="94461-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a><span data-ttu-id="94461-105">SQL Server のマネージド インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントを変更するには</span><span class="sxs-lookup"><span data-stu-id="94461-105">To change the proxy account for the utility collection set on a managed instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="94461-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。</span><span class="sxs-lookup"><span data-stu-id="94461-106">Remove the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
    -   <span data-ttu-id="94461-107">SSMS の **ユーティリティ エクスプローラー** で **[マネージド インスタンス]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="94461-107">In **Utility Explorer** in SSMS, click on the **Managed Instances** node.</span></span>  
  
    -   <span data-ttu-id="94461-108">**ユーティリティ エクスプローラー** のリスト ビューで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前を右クリックし、 **[マネージド インスタンスの削除]** をクリックします。詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94461-108">In the **Utility Explorer** list view, right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name, and select **Remove Managed Instance...**. For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="94461-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに再度登録します。</span><span class="sxs-lookup"><span data-stu-id="94461-109">Enroll the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility again.</span></span>  
  
    -   <span data-ttu-id="94461-110">SSMS の**ユーティリティ エクスプローラー**で、 **[マネージド インスタンス]** ノードを右クリックし、 **[マネージド インスタンスの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94461-110">In **Utility Explorer** in SSMS, right-click on the **Managed Instances** node, and select **Add Managed Instance...**.</span></span>  
  
    -   <span data-ttu-id="94461-111">新しいプロキシ アカウントを指定して、画面の指示に従ってウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="94461-111">Follow prompts to complete the wizard, specifying the new proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94461-112">参照</span><span class="sxs-lookup"><span data-stu-id="94461-112">See Also</span></span>  
 <span data-ttu-id="94461-113">[SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="94461-113">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="94461-114">SQL Server ユーティリティのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="94461-114">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  

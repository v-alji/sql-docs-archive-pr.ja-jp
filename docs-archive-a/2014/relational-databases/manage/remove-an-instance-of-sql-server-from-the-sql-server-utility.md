---
title: SQL Server ユーティリティからの SQL Server のインスタンスの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c09897fcd3ac6d82308288391cf54176eef49d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645598"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a><span data-ttu-id="ceec6-102">SQL Server ユーティリティからの SQL Server のインスタンスの削除</span><span class="sxs-lookup"><span data-stu-id="ceec6-102">Remove an Instance of SQL Server from the SQL Server Utility</span></span>
  <span data-ttu-id="ceec6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスを削除するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-103">Use the following steps to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ceec6-104">この手順では、UCP リスト ビューから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが削除されるため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのデータ収集が停止します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-104">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection stops.</span></span> <span data-ttu-id="ceec6-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはアンインストールされません。</span><span class="sxs-lookup"><span data-stu-id="ceec6-105">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ceec6-106">この手順を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを削除する前に、削除するインスタンス上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および SQL Server エージェントのサービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-106">Before you use this procedure to remove an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and SQL Server Agent services are running on the instance to remove.</span></span>  
  
1.  <span data-ttu-id="ceec6-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のユーティリティ エクスプローラーで、 **[マネージド インスタンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceec6-107">From the Utility Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click on **Managed Instances**.</span></span> <span data-ttu-id="ceec6-108">ユーティリティ エクスプローラーのコンテンツ ウィンドウで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスのリスト ビューを確認します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-108">Observe the list view of managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the Utility Explorer content pane.</span></span>  
  
2.  <span data-ttu-id="ceec6-109">リスト ビューの **[SQL Server インスタンス名]** 列で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-109">In the **SQL Server Instance Name** column of the list view, select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to remove from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ceec6-110">削除するインスタンスを右クリックし、 **[マネージ インスタンスの削除...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceec6-110">Right-click on the instance to remove, and select **Remove Managed Instance...**.</span></span>  
  
3.  <span data-ttu-id="ceec6-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの管理者特権を持つ資格情報を指定します。 **[Connect...]\(接続...\)** をクリックし、 **[サーバーに接続]** ダイアログ ボックスの情報を確認してから、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceec6-111">Specify credentials with administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Click **Connect...**, verify the information in the **Connect to Server** dialog box, then click **Connect**.</span></span> <span data-ttu-id="ceec6-112">**[マネージド インスタンスの削除]** ダイアログ ボックスにログイン情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceec6-112">You will see the login information on the **Remove Managed Instance** dialog.</span></span>  
  
4.  <span data-ttu-id="ceec6-113">操作を実行する場合は **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceec6-113">To confirm the operation, click **OK**.</span></span> <span data-ttu-id="ceec6-114">操作を終了する場合は **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceec6-114">To quit the operation, click **Cancel**.</span></span>  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a><span data-ttu-id="ceec6-115">SQL Server ユーティリティから SQL Server のマネージド インスタンスを手動で削除する</span><span class="sxs-lookup"><span data-stu-id="ceec6-115">Manually Remove a Managed Instance of SQL Server from a SQL Server Utility</span></span>  
 <span data-ttu-id="ceec6-116">この手順では、UCP リスト ビューから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが削除され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのデータ収集が停止されます。</span><span class="sxs-lookup"><span data-stu-id="ceec6-116">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and stops [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection.</span></span> <span data-ttu-id="ceec6-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはアンインストールされません。</span><span class="sxs-lookup"><span data-stu-id="ceec6-117">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
 <span data-ttu-id="ceec6-118">PowerShell を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスを削除するには、</span><span class="sxs-lookup"><span data-stu-id="ceec6-118">To use PowerShell to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ceec6-119">このスクリプトで、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-119">This script performs the following operations:</span></span>  
  
-   <span data-ttu-id="ceec6-120">サーバー インスタンス名で UCP を取得します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-120">Gets the UCP by server instance name.</span></span>  
  
-   <span data-ttu-id="ceec6-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-121">Removes the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
```powershell
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
<span data-ttu-id="ceec6-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス名は、に格納されているとおりに正確に参照することが重要です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ceec6-122">It's important to refer to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name exactly as it is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ceec6-123">大文字と小文字を区別する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの場合、@@SERVERNAME によって返された文字種を正確に使用して、インスタンス名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceec6-123">On a case-sensitive instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must specify the instance name using the exact casing as returned by @@SERVERNAME.</span></span> 

<span data-ttu-id="ceec6-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンスのインスタンス名を取得するには、マネージド インスタンスで次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ceec6-124">To get the instance name for the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run this query on the managed instance:</span></span>  
  
```sql
select @@SERVERNAME AS instance_name  
```  
  
 <span data-ttu-id="ceec6-125">この時点で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスは UCP から完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="ceec6-125">At this point, the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is fully removed from the UCP.</span></span> <span data-ttu-id="ceec6-126">このインスタンスは、次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのデータを更新すると、リスト ビューに表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ceec6-126">It disappears from the list view the next time you refresh data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ceec6-127">この状態は、ユーザーが SSMS ユーザー インターフェイスで、マネージド インスタンスの削除操作を正常に完了した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="ceec6-127">This state is identical to a user successfully going through the remove managed instance operation in the SSMS user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceec6-128">参照</span><span class="sxs-lookup"><span data-stu-id="ceec6-128">See Also</span></span>  
 <span data-ttu-id="ceec6-129">[ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ceec6-129">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="ceec6-130">SQL Server ユーティリティのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ceec6-130">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  

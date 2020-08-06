---
title: SQL Server のインスタンス間での UCP の移動 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2cf17a79c9a1bb1bd7e86e1ecb36ef671414fb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640926"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a><span data-ttu-id="215ee-102">SQL Server のインスタンス間での UCP の移動 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="215ee-102">Move a UCP from One Instance of SQL Server to Another (SQL Server Utility)</span></span>
  <span data-ttu-id="215ee-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の 1 つのインスタンスから別のインスタンスにユーティリティ コントロール ポイント (UCP) を移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="215ee-103">This topic describes how to move a utility control point (UCP) from one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="215ee-104">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="215ee-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a><span data-ttu-id="215ee-105">SQL Server のインスタンス間での UCP の移動</span><span class="sxs-lookup"><span data-stu-id="215ee-105">Move a UCP from one instance of SQL Server to another.</span></span>  
  
1.  <span data-ttu-id="215ee-106">UCP の新しいホスト インスタンスとなる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに新しい UCP を作成します。</span><span class="sxs-lookup"><span data-stu-id="215ee-106">Create a new UCP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that will be the new host instance of the UCP.</span></span> <span data-ttu-id="215ee-107">詳細については、「[SQL Server ユーティリティ コントロール ポイントの作成 &#40;SQL Server ユーティリティ&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215ee-107">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="215ee-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、既定以外のポリシー設定が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに設定されている場合、ポリシーのしきい値を新しい UCP で再設定できるようにメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="215ee-108">If non-default policy settings have been set for any instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make note of the policy thresholds so that you can re-establish them on the new UCP.</span></span> <span data-ttu-id="215ee-109">既定のポリシーは、インスタンスが新しい UCP に追加されるときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="215ee-109">Default policies are applied when instances are added to the new UCP.</span></span> <span data-ttu-id="215ee-110">既定のポリシーが有効な場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのリスト ビューの **[ポリシーの種類]** 列に **[グローバル]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="215ee-110">If default policies are in effect, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility list view displays **Global** in the **Policy Type** column.</span></span>  
  
3.  <span data-ttu-id="215ee-111">古い UCP からすべてのマネージド インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="215ee-111">Remove all managed instances from the old UCP.</span></span> <span data-ttu-id="215ee-112">詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215ee-112">For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
4.  <span data-ttu-id="215ee-113">古い UCP のユーティリティ管理データ ウェアハウス (UMDW) をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="215ee-113">Back up the utility management data warehouse (UMDW) from the old UCP.</span></span> <span data-ttu-id="215ee-114">ファイル名は Sysutility_mdw_\<GUID>_DATA で、データベースの既定の場所は \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\ です (通常、\<System drive> は C: ドライブ)。</span><span class="sxs-lookup"><span data-stu-id="215ee-114">The filename is Sysutility_mdw_\<GUID>_DATA, and the database default location is \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="215ee-115">詳細については、「 [バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215ee-115">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
5.  <span data-ttu-id="215ee-116">UMDW のバックアップを新しい UCP に復元します。</span><span class="sxs-lookup"><span data-stu-id="215ee-116">Restore the backup of the UMDW to the new UCP.</span></span> <span data-ttu-id="215ee-117">詳細については、「 [バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215ee-117">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
6.  <span data-ttu-id="215ee-118">インスタンスを新しい UCP に登録し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで管理されるようにします。</span><span class="sxs-lookup"><span data-stu-id="215ee-118">Enroll instances into the new UCP to make them managed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="215ee-119">詳細については、「[SQL Server のインスタンスの登録 &#40;SQL Server ユーティリティ&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215ee-119">For more information, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
7.  <span data-ttu-id="215ee-120">必要に応じて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンスにカスタムのポリシー定義を実装します。</span><span class="sxs-lookup"><span data-stu-id="215ee-120">Implement custom policy definitions for the managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as necessary.</span></span>  
  
8.  <span data-ttu-id="215ee-121">データの収集と集計の操作が完了するまで約 1 時間待機します。</span><span class="sxs-lookup"><span data-stu-id="215ee-121">Wait approximately 1 hour for data collection and aggregation operations to complete.</span></span>  
  
9. <span data-ttu-id="215ee-122">データを更新するには、 **ユーティリティ エクスプローラー** で **[マネージド インスタンス]** ノードを右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="215ee-122">To refresh data, right-click the **Managed Instances** node in **Utility Explorer**, then select **Refresh**.</span></span> <span data-ttu-id="215ee-123">リスト ビューのデータは、 **ユーティリティ エクスプローラー** のコンテンツ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="215ee-123">List view data are displayed in the **Utility Explorer** content pane.</span></span> <span data-ttu-id="215ee-124">詳細については、「[リソース正常性ポリシーの結果の表示 &#40;SQL Server ユーティリティ&#41;](view-resource-health-policy-results-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215ee-124">For more information, see [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215ee-125">参照</span><span class="sxs-lookup"><span data-stu-id="215ee-125">See Also</span></span>  
 <span data-ttu-id="215ee-126">[SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="215ee-126">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="215ee-127">SQL Server のインスタンスの登録 &#40;SQL Server ユーティリティ&#41;</span><span class="sxs-lookup"><span data-stu-id="215ee-127">Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;</span></span>](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  

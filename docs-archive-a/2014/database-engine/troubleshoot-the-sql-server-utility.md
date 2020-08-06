---
title: SQL Server ユーティリティのトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3c139f9f084374aeb711e905ac0c315acc25c6ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720337"
---
# <a name="troubleshoot-the-sql-server-utility"></a><span data-ttu-id="c5a47-102">SQL Server ユーティリティのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c5a47-102">Troubleshoot the SQL Server Utility</span></span>
  <span data-ttu-id="c5a47-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのトラブルシューティングの項目としては、UCP を使用した SQL Server インスタンスの登録処理の失敗の解決、データ収集の失敗 (UCP のマネージド インスタンスのリスト ビューで灰色のアイコンが表示される) に対するトラブルシューティング、パフォーマンス ボトルネックの緩和、リソースの正常性に関する問題の解決などがあります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-103">Troubleshooting [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility issues might include resolving a failed operation to enroll an instance of SQL Server with a UCP, troubleshooting failed data collection resulting in gray icons in the managed instance list view on a UCP, mitigating performance bottlenecks, or resolving resource health issues.</span></span> <span data-ttu-id="c5a47-104">UCP によって識別されるリソース正常性の問題を軽減する方法の詳細につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「[トラブルシューティング SQL Server Resource Health &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5a47-104">For more information about mitigating resource health issues identified by a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, see [Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).</span></span>  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a><span data-ttu-id="c5a47-105">SQL Server インスタンスを SQL Server ユーティリティに登録する処理の失敗</span><span class="sxs-lookup"><span data-stu-id="c5a47-105">Failed Operation to Enroll an Instance of SQL Server into a SQL Server Utility</span></span>  
 <span data-ttu-id="c5a47-106">登録する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用して接続し、UCP があるドメインとは異なる Active Directory ドメインに属するプロキシ アカウントを指定した場合、インスタンスの検証には成功しますが、次のエラー メッセージが表示されて登録処理に失敗します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-106">If you connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, and you specify a proxy account that belongs to a different Active Directory domain than the domain where the UCP is located, instance validation succeeds, but the enrollment operation fails with the following error message:</span></span>  
  
 <span data-ttu-id="c5a47-107">Transact-SQL ステートメントまたはバッチの実行中に例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="c5a47-107">An exception occurred while executing a Transact-SQL statement or batch.</span></span> <span data-ttu-id="c5a47-108">(Microsoft.SqlServer.ConnectionInfo)</span><span class="sxs-lookup"><span data-stu-id="c5a47-108">(Microsoft.SqlServer.ConnectionInfo)</span></span>  
  
 <span data-ttu-id="c5a47-109">追加情報:Windows NT グループまたはユーザー '\<DomainName\AccountName>' に関する情報を取得できませんでした。エラー コード 0x5。</span><span class="sxs-lookup"><span data-stu-id="c5a47-109">Additional information:  Could not obtain information about Windows NT group/user '\<DomainName\AccountName>', error code 0x5.</span></span> <span data-ttu-id="c5a47-110">(Microsoft SQL Server、エラー:15404)</span><span class="sxs-lookup"><span data-stu-id="c5a47-110">(Microsoft SQL Server, Error: 15404)</span></span>  
  
 <span data-ttu-id="c5a47-111">この問題は、次のようなシナリオで発生します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-111">This issue occurs in the following example scenario:</span></span>  
  
1.  <span data-ttu-id="c5a47-112">UCP は "Domain_1" のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="c5a47-112">The UCP is a member of "Domain_1."</span></span>  
  
2.  <span data-ttu-id="c5a47-113">一方向のドメイン信頼関係が存在します。つまり、"Domain_1" は "Domain_2" から信頼されていませんが、"Domain_2" は "Domain_1" から信頼されています。</span><span class="sxs-lookup"><span data-stu-id="c5a47-113">A one-way domain trust relationship is in place: that is, "Domain_1" is not trusted by "Domain_2" but "Domain_2" is trusted by "Domain_1."</span></span>  
  
3.  <span data-ttu-id="c5a47-114">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティに登録する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスは、"Domain_1" のメンバーでもあります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-114">The instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility is also a member of "Domain_1."</span></span>  
  
4.  <span data-ttu-id="c5a47-115">登録操作中に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "sa" を使用して登録するのインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-115">During the enroll operation, connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using "sa".</span></span> <span data-ttu-id="c5a47-116">"Domain_2" からのプロキシ アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-116">Specify a proxy account from "Domain_2."</span></span>  
  
5.  <span data-ttu-id="c5a47-117">検証に成功しますが、登録に失敗します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-117">Validation succeeds but enrollment fails.</span></span>  
  
 <span data-ttu-id="c5a47-118">上記の例を使用して、この問題の回避策として、のインスタンスに接続して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "sa" を使用してユーティリティに登録し、"Domain_1" からプロキシアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-118">The workaround for this issue, using the example above, is to connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility using "sa" and provide a proxy account from "Domain_1."</span></span>  
  
## <a name="failed-wmi-validation"></a><span data-ttu-id="c5a47-119">WMI 検証の失敗</span><span class="sxs-lookup"><span data-stu-id="c5a47-119">Failed WMI Validation</span></span>  
 <span data-ttu-id="c5a47-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスで WMI が正しく構成されていない場合は、UCP の作成操作とマネージド インスタンスの登録操作で警告が表示されますが、操作はブロックされません。</span><span class="sxs-lookup"><span data-stu-id="c5a47-120">If WMI is not properly configured on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the Create UCP and Enroll Managed Instance operations display a warning, but the operation is not blocked.</span></span> <span data-ttu-id="c5a47-121">また、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントが目的の WMI クラスに対する権限を持たないように [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント アカウントの構成を変更した場合、影響を受ける [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスでデータ収集を行うと UCP へのアップロードに失敗します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-121">Additionally, if you change the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent account configuration so that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent does not have permission to required WMI classes, data collection on the affected managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fails to upload to the UCP.</span></span> <span data-ttu-id="c5a47-122">この結果、UCP に灰色のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5a47-122">This results in gray icons in the UCP.</span></span>  
  
 <span data-ttu-id="c5a47-123">データ収集が失敗した結果、影響を受ける [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスの UCP リスト ビューに灰色の状態アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5a47-123">Failed data collection results in gray status icons in the UCP list view for affected managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5a47-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスのジョブ履歴には、sysutility_mi_collect_and_upload がステップ 2 (PowerShell スクリプトから収集されたデータのステージング) で失敗したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="c5a47-124">The job history on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shows that sysutility_mi_collect_and_upload fails on step 2 (Stage Data Collected from PowerShell Script).</span></span>  
  
 <span data-ttu-id="c5a47-125">エラー メッセージの要約は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5a47-125">The simplified error messages are:</span></span>  
  
 <span data-ttu-id="c5a47-126">シェル変数 "ErrorActionPreference" が Stop に設定されているため、コマンドの実行が停止しました: アクセスが拒否されました。</span><span class="sxs-lookup"><span data-stu-id="c5a47-126">Command execution stopped because the shell variable "ErrorActionPreference" is set to Stop: Access denied.</span></span>  
  
 <span data-ttu-id="c5a47-127">エラー: \<Date-time (MM/DD/YYYY HH:MM:SS)> : cpu プロパティの収集中に例外がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="c5a47-127">ERROR: \<Date-time (MM/DD/YYYY HH:MM:SS)>: Caught exception while collecting cpu properties.</span></span>  <span data-ttu-id="c5a47-128">WMI クエリに失敗した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-128">A WMI query might have failed.</span></span>  <span data-ttu-id="c5a47-129">警告。</span><span class="sxs-lookup"><span data-stu-id="c5a47-129">WARNING.</span></span>  
  
 <span data-ttu-id="c5a47-130">この問題を解決するには、次の構成設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-130">To resolve this issue, verify the following configuration settings:</span></span>  
  
-   <span data-ttu-id="c5a47-131">Windows Server 2003 上で、SQL Server エージェント サービスは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスの Windows Performance Monitoring グループに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-131">On Windows Server 2003, the SQL Server Agent service must be part of the Windows Performance Monitoring group on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c5a47-132">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンス上で、WMI サービスが有効になっており、構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-132">The WMI service must be enabled and configured on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c5a47-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンス上で、WMI リポジトリが破損している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-133">The WMI repository might be corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c5a47-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンス上で、パフォーマンス ライブラリが欠落または破損している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-134">The performance library might be missing or corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c5a47-135">指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが UCP にデータを報告するように正しく構成されていることを検証するには、指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスで次のクラスが使用可能であり、SQL Server エージェント サービス アカウントからこれらのクラスにアクセスできるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-135">To verify that the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is configured properly to report data to the UCP, verify that the following classes are available on the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and that they are accessible to SQL Server Agent service account:</span></span>  
  
-   <span data-ttu-id="c5a47-136">Win32_MountPoint</span><span class="sxs-lookup"><span data-stu-id="c5a47-136">Win32_MountPoint</span></span>  
  
-   <span data-ttu-id="c5a47-137">Win32_PerfRawData_PerfProc_Process</span><span class="sxs-lookup"><span data-stu-id="c5a47-137">Win32_PerfRawData_PerfProc_Process</span></span>  
  
-   <span data-ttu-id="c5a47-138">Win32_PerfRawData_PerfOS_Processor</span><span class="sxs-lookup"><span data-stu-id="c5a47-138">Win32_PerfRawData_PerfOS_Processor</span></span>  
  
-   <span data-ttu-id="c5a47-139">Win32_Processor</span><span class="sxs-lookup"><span data-stu-id="c5a47-139">Win32_Processor</span></span>  
  
-   <span data-ttu-id="c5a47-140">Win32_Volume</span><span class="sxs-lookup"><span data-stu-id="c5a47-140">Win32_Volume</span></span>  
  
-   <span data-ttu-id="c5a47-141">Win32_LogicalDisk</span><span class="sxs-lookup"><span data-stu-id="c5a47-141">Win32_LogicalDisk</span></span>  
  
 <span data-ttu-id="c5a47-142">各クラスで Get-WmiObject PowerShell コマンドレットを使用して、各クラスにアクセスできるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-142">You can use the Get-WmiObject PowerShell cmdlet on each of the classes to verify that each class is accessible.</span></span> <span data-ttu-id="c5a47-143">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスで、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-143">Run the following cmdlets on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 <span data-ttu-id="c5a47-144">WMI のトラブルシューティングの詳細については、「 [wmi のトラブルシューティング](https://go.microsoft.com/fwlink/?LinkId=178250)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5a47-144">For more information about troubleshooting WMI, see [Troubleshooting WMI](https://go.microsoft.com/fwlink/?LinkId=178250).</span></span> <span data-ttu-id="c5a47-145">SQL Server ユーティリティのこれらの操作におけるクエリはローカルで実行されるので、DCOM およびリモート トラブルシューティングの内容は適用されません。</span><span class="sxs-lookup"><span data-stu-id="c5a47-145">Note that queries in these SQL Server Utility operations are running locally, so the DCOM and remote troubleshooting content does not apply.</span></span>  
  
## <a name="failed-data-collection"></a><span data-ttu-id="c5a47-146">データ収集の失敗</span><span class="sxs-lookup"><span data-stu-id="c5a47-146">Failed Data Collection</span></span>  
 <span data-ttu-id="c5a47-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのデータ収集イベントが失敗した場合は、次の可能性を検討してください。</span><span class="sxs-lookup"><span data-stu-id="c5a47-147">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility data collection events fail, consider the following possibilities:</span></span>  
  
-   <span data-ttu-id="c5a47-148">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンス上の "ユーティリティ情報" コレクション セットのプロパティは一切変更しないでください。また、データ コレクションはユーティリティ エージェント ジョブによって制御されるため、データ コレクションのオン/オフを手動で切り替えることも避けてください。</span><span class="sxs-lookup"><span data-stu-id="c5a47-148">Do not change any properties of the "Utility Information" collection set on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and do not turn data collection on/off manually, as data collection is controlled by a Utility agent job.</span></span>  
  
-   <span data-ttu-id="c5a47-149">WMI 検証に失敗したか、この機能がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c5a47-149">Failed or unsupported WMI validation.</span></span> <span data-ttu-id="c5a47-150">詳細については、このトピックの前半の「WMI 検証の失敗」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5a47-150">For more information, see the Failed WMI Validation section earlier in this topic.</span></span>  
  
-   <span data-ttu-id="c5a47-151">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのビューポイントのデータは自動的に更新されないため、マネージド インスタンスのリスト ビューのデータを手動で更新してください。</span><span class="sxs-lookup"><span data-stu-id="c5a47-151">Refresh data in the managed instance list view, as data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility viewpoints does not refresh automatically.</span></span> <span data-ttu-id="c5a47-152">データを更新するには、 **ユーティリティ エクスプローラー** のナビゲーション ウィンドウで **[マネージド インスタンス]** ノードを右クリックして **[更新]** をクリックするか、リスト ビューで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス名を右クリックして **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-152">To refresh data, right-click the **Managed Instances** node in the **Utility Explorer Navigation** pane, then select **Refresh**, or right-click on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name in the list view, then select **Refresh**.</span></span> <span data-ttu-id="c5a47-153">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが UCP に登録された後、ユーティリティ エクスプローラーのコンテンツ ウィンドウ内のダッシュボードとビューポイントに最初に表示されるまでに最大 30 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-153">Note that after an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has been enrolled with a UCP, it can take up to 30 minutes for data to first appear in the dashboard and viewpoints in the Utility Explorer content pane.</span></span>  
  
-   <span data-ttu-id="c5a47-154">SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-154">Use SQL Server Configuration Manager to verify that the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   <span data-ttu-id="c5a47-155">データ コレクションまたはデータ アップロードがタイムアウトの問題で失敗する場合は、MSDB データベースの dbo.fn_sysutility_mi_get_collect_script() 関数を更新します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-155">If data collection or data upload fail due to timeout issues, update the function dbo.fn_sysutility_mi_get_collect_script() in the MSDB database.</span></span> <span data-ttu-id="c5a47-156">具体的には、"Invoke-BulkCopyCommand()" 関数に次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-156">Specifically, in the function "Invoke-BulkCopyCommand()" add line:</span></span>  
  
    ```
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     <span data-ttu-id="c5a47-157">タイムアウトの既定値は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="c5a47-157">The default timeout value is 30 seconds.</span></span>  
  
-   <span data-ttu-id="c5a47-158">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスがクラスター化されていない場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスが実行されていることと、このサービスが UCP、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスで自動的に開始するように設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-158">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not clustered, verify that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running and that the service is set to start automatically on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c5a47-159">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスでデータ収集を実行するために有効なアカウントが使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-159">Verify that a valid account is being used to run data collection on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5a47-160">たとえば、パスワードの有効期限が切れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-160">For example, the password may have expired.</span></span> <span data-ttu-id="c5a47-161">プロキシ パスワードの有効期限が切れている場合は、次のように、SSMS でパスワード資格情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-161">If the proxy password has expired, update password credentials in SSMS, as follows:</span></span>  
  
    1.  <span data-ttu-id="c5a47-162">SSMS の **オブジェクト エクスプローラー**で、 **[セキュリティ]** ノードを展開し、 **[資格情報]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-162">In SSMS **Object Explorer**, expand the **Security** node, then expand the **Credentials** node.</span></span>  
  
    2.  <span data-ttu-id="c5a47-163">**UtilityAgentProxyCredential_ \<GUID> **を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-163">Right-click on **UtilityAgentProxyCredential_\<GUID>** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="c5a47-164">[資格情報のプロパティ] ダイアログボックスで、 \*\*UtilityAgentProxyCredential_ \<GUID> \*\*資格情報に必要な資格情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-164">On the Credential Properties dialog, update credentials as necessary for the **UtilityAgentProxyCredential_\<GUID>** credential.</span></span>  
  
    4.  <span data-ttu-id="c5a47-165">**[OK]** をクリックして変更を確定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-165">Click **OK** to confirm the change.</span></span>  
  
-   <span data-ttu-id="c5a47-166">TCP/IP は、UCP と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスで有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-166">TCP/IP should be enabled on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5a47-167">TCP/IP は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用して有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-167">Enable TCP/IP through [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="c5a47-168">UCP の SQL Server Browser サービスを開始して、自動的に開始するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-168">The SQL Server Browser service on the UCP should be started and configured to start automatically.</span></span> <span data-ttu-id="c5a47-169">組織の方針で SQL Server Browser サービスを使用できない場合は、次の手順を実行して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスから UCP に接続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-169">If your organization prevents use of the SQL Server Browser service, use the following steps to allow a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to the UCP:</span></span>  
  
    1.  <span data-ttu-id="c5a47-170">のマネージインスタンス上の Windows タスクバーで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、[**スタート**] をクリックし、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-170">On the Windows taskbar on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], click **Start**, then click **Run...**.</span></span>  
  
    2.  <span data-ttu-id="c5a47-171">該当するボックスに「cliconfg.exe」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-171">Type "cliconfg.exe" in the space provided, then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="c5a47-172">"SQL クライアント設定ユーティリティ EXE" の起動を許可するように求めるメッセージが表示されたら、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-172">If prompted to allow "SQL Client Configuration Utility EXE" to start, click "**Continue**."</span></span>  
  
    4.  <span data-ttu-id="c5a47-173">[**クライアントネットワークユーティリティの SQL Server** ] ダイアログボックスで、[**別名**] タブを選択し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-173">On the **SQL Server Client Network Utility** dialog box, select the **Alias** tab, then click **Add...**.</span></span>  
  
    5.  <span data-ttu-id="c5a47-174">**[ネットワーク ライブラリ設定の追加]** ダイアログ ボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="c5a47-174">On the **Add Network Library Configuration** dialog box:</span></span>  
  
    6.  <span data-ttu-id="c5a47-175">ネットワーク ライブラリの一覧で、[TCP/IP] を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-175">Specify TCP/IP from the list of network libraries.</span></span>  
  
    7.  <span data-ttu-id="c5a47-176">**[サーバー別名]** ボックスに、UCP の ComputerName\InstanceName を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-176">Specify the ComputerName\InstanceName of the UCP in the **Server Alias** text box.</span></span>  
  
    8.  <span data-ttu-id="c5a47-177">**[サーバー名]** ボックスに、UCP の ComputerName を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-177">Specify the ComputerName of the UCP in the **Server Name** text box.</span></span>  
  
    9. <span data-ttu-id="c5a47-178">**[ポートを動的に決定する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-178">Uncheck the **Dynamically determine port** checkbox.</span></span>  
  
    10. <span data-ttu-id="c5a47-179">**[ポート番号]** ボックスに、UCP がリッスンしているポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-179">Specify the port number that the UCP is listening on in the **Port number** text box.</span></span>  
  
    11. <span data-ttu-id="c5a47-180">**[OK]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-180">Click **OK** to save your changes.</span></span>  
  
    12. <span data-ttu-id="c5a47-181">SQL Server Browser サービスが無効になっている UCP に接続する、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスごとに、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-181">Repeat these steps for each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that connects to a UCP where the SQL Server Browser service is not enabled.</span></span>  
  
-   <span data-ttu-id="c5a47-182">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスがネットワークに接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-182">Ensure that managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are connected to the network.</span></span>  
  
-   <span data-ttu-id="c5a47-183">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンス上に、名前が同じでも大文字と小文字の区別に関する設定が異なるデータベースがある場合は、データベースとそのビューポイントが正しく識別されず、データ収集に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-183">If there are databases with the same name but different case-sensitivity settings on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the identification between the database and its viewpoints can be incorrect, resulting in failed data collection.</span></span> <span data-ttu-id="c5a47-184">たとえば、"MYDATABASE" という名前のデータベースで、実際には "MyDatabase" という名前のデータベースの正常性状態が示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-184">For example, a database named "MYDATABASE" might show health states for a database named "MyDatabase".</span></span> <span data-ttu-id="c5a47-185">この場合、エラーにはなりません。</span><span class="sxs-lookup"><span data-stu-id="c5a47-185">No error is generated in this scenario.</span></span> <span data-ttu-id="c5a47-186">データ収集の失敗は、データベース ファイルやファイル グループの名前など、UCP に表示される他のオブジェクトの大文字と小文字の不一致から発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-186">Failed data collection can also result from case-sensitivity mismatches in other objects displayed in the UCP, like database file and file group names.</span></span>  
  
-   <span data-ttu-id="c5a47-187">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスが Windows Server 2003 コンピューター上でホストされている場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービス アカウントは、Performance Monitor Users セキュリティ グループまたはローカルの Administrators グループに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a47-187">If a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is hosted on a Windows Server 2003 computer, then the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account must belong to the Performance Monitor Users security group or the local Administrators group.</span></span> <span data-ttu-id="c5a47-188">属していない場合は、アクセス拒否エラーが発生してデータ収集が失敗します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-188">Otherwise, data collection will fail with an access denied error.</span></span> <span data-ttu-id="c5a47-189">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービス アカウントを Performance Monitor Users セキュリティ グループに追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-189">To add a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account to the Performance Monitor Users security group, use the following steps:</span></span>  
  
    1.  <span data-ttu-id="c5a47-190">**[コンピューターの管理]** を開き、 **[ローカル ユーザーとグループ]**、 **[グループ]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-190">Open **Computer Management**, then **Local Users and Groups**, then **Groups**.</span></span>  
  
    2.  <span data-ttu-id="c5a47-191">**[Performance Monitor Users]** を右クリックし、 **[グループに追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-191">Right-click **Performance Monitor Users** and select **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="c5a47-192">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-192">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="c5a47-193">SQL Server エージェント サービスを実行しているアカウントを入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5a47-193">Enter the account that the SQL Server Agent service is running under, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="c5a47-194">ユーザーをこのグループに追加する前に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが既に UCP に登録されている場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="c5a47-194">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] was already enrolled with the UCP before adding the user to this group, restart the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a47-195">参照</span><span class="sxs-lookup"><span data-stu-id="c5a47-195">See Also</span></span>  
 <span data-ttu-id="c5a47-196">[SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="c5a47-196">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="c5a47-197">SQL Server のリソース正常性のトラブルシューティング &#40;SQL Server ユーティリティ&#41;</span><span class="sxs-lookup"><span data-stu-id="c5a47-197">Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)

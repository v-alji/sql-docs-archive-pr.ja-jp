---
title: ユーティリティの管理 (SQL Server ユーティリティ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 3e5a00c3-8905-40f0-9ddc-d924df9c2f0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fca4ea655ffdcf8471d1340016d16f2c5b9c352a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715670"
---
# <a name="utility-administration-sql-server-utility"></a><span data-ttu-id="6bc64-102">ユーティリティの管理 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="6bc64-102">Utility Administration (SQL Server Utility)</span></span>
  <span data-ttu-id="6bc64-103">ユーティリティの管理の各タブでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのポリシー設定、セキュリティ設定、およびデータ ウェアハウス設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-103">Use the Utility Administration tabs to manage policy, security, and data warehouse settings for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="6bc64-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティの概念の詳細については、「 [SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc64-104">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility concepts, see [SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6bc64-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="6bc64-105">UI element list</span></span>  
 <span data-ttu-id="6bc64-106">[ポリシー] タブ - このタブでは、グローバル監視ポリシーを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-106">Policy tab - Use the policy tab to view or specify global monitoring policies.</span></span>  
  
 <span data-ttu-id="6bc64-107">[グローバル データ層アプリケーション監視ポリシーを設定する] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-107">Set global data-tier application monitoring policies.</span></span> <span data-ttu-id="6bc64-108">このオプションの値一覧を表示するには、ポリシー名の横にある矢印をクリックするか、ポリシーのタイトルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-108">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="6bc64-109">[アプリケーションがプロセッサの能力を使い果たすタイミング] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-109">When is an application running out of processor capacity?</span></span> <span data-ttu-id="6bc64-110">このポリシー説明の右側にあるコントロールを使用してポリシーを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-110">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="6bc64-111">また、画面の下部にあるボタンを使用して、既定値を復元したり変更を破棄したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-111">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="6bc64-112">プロセッサ使用率の既定の最大値は 70% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-112">The default maximum value for processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="6bc64-113">プロセッサ使用率の既定の最小値は 0% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-113">The default minimum value for processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="6bc64-114">[アプリケーションがファイル領域を使い果たすタイミング] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-114">When is an application running out of file space?</span></span> <span data-ttu-id="6bc64-115">このポリシー説明の右側にあるコントロールを使用して、データ ファイルまたはログ ファイルの領域使用率ポリシーを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-115">To change the policy for data file or log file space utilization, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="6bc64-116">また、画面の下部にあるボタンを使用して、既定値を復元したり変更を破棄したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-116">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="6bc64-117">ファイル領域使用率の既定の最大値は 70% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-117">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="6bc64-118">ファイル領域使用率の既定の最小値は 0% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-118">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="6bc64-119">[グローバル SQL Server マネージド インスタンス アプリケーション監視ポリシーを設定する] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-119">Set global SQL Server managed instance application monitoring policies.</span></span> <span data-ttu-id="6bc64-120">このオプションの値一覧を表示するには、ポリシー名の横にある矢印をクリックするか、ポリシーのタイトルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-120">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="6bc64-121">[ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスがプロセッサの能力を使い果たすタイミング] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-121">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of processor capacity?</span></span> <span data-ttu-id="6bc64-122">このポリシー説明の右側にあるコントロールを使用してポリシーを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-122">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="6bc64-123">また、画面の下部にあるボタンを使用して、既定値を復元したり変更を破棄したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-123">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="6bc64-124">インスタンスのプロセッサ使用率の既定の最大値は 70% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-124">The default maximum value for instance processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="6bc64-125">インスタンスのプロセッサ使用率の既定の最小値は 0% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-125">The default minimum value for instance processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="6bc64-126">[ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンピューターのマネージド インスタンスがプロセッサの能力を使い果たすタイミング] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-126">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of processor capacity?</span></span> <span data-ttu-id="6bc64-127">このポリシー説明の右側にあるコントロールを使用してポリシーを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-127">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="6bc64-128">また、画面の下部にあるボタンを使用して、既定値を復元したり変更を破棄したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-128">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="6bc64-129">コンピューターのプロセッサ使用率の既定の最大値は 70% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-129">The default maximum value for computer processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="6bc64-130">コンピューターのプロセッサ使用率の既定の最小値は 0% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-130">The default minimum value for computer processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="6bc64-131">[ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスがファイル領域を使い果たすタイミング] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-131">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of file space?</span></span> <span data-ttu-id="6bc64-132">このポリシー説明の右側にあるコントロールを使用して、データ ファイルまたはログ ファイルの領域使用率ポリシーを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-132">To change the policy for data file or log file space utilization , use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="6bc64-133">また、画面の下部にあるボタンを使用して、既定値を復元したり変更を破棄したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-133">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="6bc64-134">ファイル領域使用率の既定の最大値は 70% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-134">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="6bc64-135">ファイル領域使用率の既定の最小値は 0% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-135">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="6bc64-136">[ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンピューターのマネージド インスタンスが記憶域ボリュームの領域を使い果たすタイミング] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-136">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of storage volume space?</span></span> <span data-ttu-id="6bc64-137">このポリシー説明の右側にあるコントロールを使用してポリシーを変更し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-137">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="6bc64-138">また、画面の下部にあるボタンを使用して、既定値を復元したり変更を破棄したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-138">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="6bc64-139">コンピューターのボリューム領域使用率の既定の最大値は 70% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-139">The default maximum value for computer volume space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="6bc64-140">コンピューターのボリューム領域使用率の既定の最小値は 0% です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-140">The default minimum value for computer volume space utilization is 0%.</span></span>  
  
 <span data-ttu-id="6bc64-141">[変動の激しいリソースによって生じるポリシー違反ノイズの軽減] :</span><span class="sxs-lookup"><span data-stu-id="6bc64-141">Reducing policy violation noise from highly volatile resources.</span></span> <span data-ttu-id="6bc64-142">この機能のコントロールを表示するには、画面の右側にある下向き矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-142">To expand the controls for this feature, click on the down-arrow on the right side of the display.</span></span>  
 <span data-ttu-id="6bc64-143">詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc64-143">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6bc64-144">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="6bc64-144">UI element list</span></span>  
 <span data-ttu-id="6bc64-145">[セキュリティ] タブ - UCP の管理または読み取りの権限とログイン名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-145">Security tab - Displays login names with permissions to administer or read from the UCP.</span></span>  
  
 <span data-ttu-id="6bc64-146">[Utility Reader ロールに追加される UCP のログインを選択する]</span><span class="sxs-lookup"><span data-stu-id="6bc64-146">Select the logins from the UCP that will be added to the Utility Reader role.</span></span>  
 <span data-ttu-id="6bc64-147">Utility Reader 特権があるユーザー アカウントでは、以下のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-147">The Utility Reader privilege allows the user account to:</span></span>  
  
-   <span data-ttu-id="6bc64-148">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティに接続する</span><span class="sxs-lookup"><span data-stu-id="6bc64-148">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="6bc64-149">SSMS のユーティリティ エクスプローラーで、すべてのビューポイントを表示する</span><span class="sxs-lookup"><span data-stu-id="6bc64-149">See all viewpoints in the Utility Explorer in SSMS.</span></span>  
  
-   <span data-ttu-id="6bc64-150">SSMS のユーティリティ エクスプローラーで、[ユーティリティの管理] ノードの設定を表示する</span><span class="sxs-lookup"><span data-stu-id="6bc64-150">See settings on the Utility Administration node in Utility Explorer in SSMS.</span></span>  
  
 <span data-ttu-id="6bc64-151">ユーティリティ管理者は、SQL Server のインスタンスを SQL Server ユーティリティに登録したり、SQL Server のインスタンスを SQL Server ユーティリティから削除したりできるほか、マネージド インスタンスのポリシーの変更や UCP の管理設定の変更が可能です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-151">Utility administrators can enroll instances of SQL Server into and remove instances of SQL Server from a SQL Server Utility, as well as modify policies on managed instances and modify administration settings on the UCP.</span></span>  
  
 <span data-ttu-id="6bc64-152">ユーティリティ管理者になるには、SQL Server のインスタンスに対する sysadmin 特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-152">To be a Utility administrator, you must have sysadmin privileges on the instance of SQL Server.</span></span> <span data-ttu-id="6bc64-153">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP のユーザー アカウントを追加または変更するには、SSMS のオブジェクト エクスプローラーを使用して、SQL Server の UCP インスタンスのサーバー ログインにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bc64-153">To add or change user accounts for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, use Object Explorer in SSMS to add the user to the server logins of the UCP instance of SQL Server.</span></span> <span data-ttu-id="6bc64-154">詳細については、「[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc64-154">For more information, see [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6bc64-155">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="6bc64-155">UI element list</span></span>  
 <span data-ttu-id="6bc64-156">[データ ウェアハウス] タブ - ユーティリティ管理データ ウェアハウスの構成の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bc64-156">Data Warehouse tab - Displays configuration details for the utility management data warehouse.</span></span>  
  
 <span data-ttu-id="6bc64-157">データ保有期間</span><span class="sxs-lookup"><span data-stu-id="6bc64-157">Data Retention</span></span>  
 <span data-ttu-id="6bc64-158">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンス用に収集された使用率情報のデータ保有期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="6bc64-158">Specify the data retention period for utilization information collected for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6bc64-159">既定の期間は 1 年です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-159">The default time period is 1 year.</span></span> <span data-ttu-id="6bc64-160">最小値は 1 か月です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-160">The minimum value is 1 month.</span></span> <span data-ttu-id="6bc64-161">指定可能な最長期間は 2 年です。</span><span class="sxs-lookup"><span data-stu-id="6bc64-161">The longest supported value is 2 years.</span></span>  
  
 <span data-ttu-id="6bc64-162">[ユーティリティ データ ウェアハウスの構成情報]</span><span class="sxs-lookup"><span data-stu-id="6bc64-162">Utility Data Warehouse Configuration Information</span></span>  
 <span data-ttu-id="6bc64-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のこのリリースで構成できない構成設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6bc64-163">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="6bc64-164">UMDW 名: Sysutility_mdw_\<GUID>_DATA。</span><span class="sxs-lookup"><span data-stu-id="6bc64-164">UMDW name: Sysutility_mdw_\<GUID>_DATA.</span></span>  
  
-   <span data-ttu-id="6bc64-165">コレクション セットのアップロードの頻度: 15 分ごと。</span><span class="sxs-lookup"><span data-stu-id="6bc64-165">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="6bc64-166">UMDW ディレクトリは構成可能です: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\ (通常、\<System drive> は C:\ ドライブ)。</span><span class="sxs-lookup"><span data-stu-id="6bc64-166">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="6bc64-167">ログ ファイル UMDW_\<GUID>_LOG は、同じディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="6bc64-167">The log file, UMDW_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bc64-168">UMDW (sysutility_mdw) ファイルの場所を変更するには、デタッチとアタッチを使用する方法と ALTER DATABASE を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="6bc64-168">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="6bc64-169">ALTER DATABASE の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-169">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="6bc64-170">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc64-170">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="6bc64-171">[追加設定なしの既定値に戻す]</span><span class="sxs-lookup"><span data-stu-id="6bc64-171">Go back to out-of-the-box defaults</span></span>  
 <span data-ttu-id="6bc64-172">このタブの設定を既定値にリセットするには、 **[既定値に戻す]** ボタンをクリックし、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bc64-172">To reset settings on this tab to default values, click the **Restore Defaults** button, then click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc64-173">参照</span><span class="sxs-lookup"><span data-stu-id="6bc64-173">See Also</span></span>  
 <span data-ttu-id="6bc64-174">[ユーティリティダッシュボード &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="6bc64-174">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="6bc64-175">[配置されたデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="6bc64-175">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="6bc64-176">[Managed Instance の詳細 &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="6bc64-176">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="6bc64-177">SQL Server ユーティリティでの SQL Server のインスタンスの監視</span><span class="sxs-lookup"><span data-stu-id="6bc64-177">Monitor Instances of SQL Server in the SQL Server Utility</span></span>](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)  
  
  

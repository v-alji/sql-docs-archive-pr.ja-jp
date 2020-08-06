---
title: データ層アプリケーションのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.upgradedacwizard.reviewpolicy.f1
- sql12.swb.upgradedacwizard.selectoptions.f1
- sql12.swb.upgradedacwizard.selectpackage.f1
- sql12.swb.upgradedacwizard.reviewplan.f1
- sql12.swb.upgradedacwizard.checkdrift.f1
- sql12.swb.upgradedacwizard.summary.f1
- sql12.swb.upgradedacwizard.upgradedac.f1
- sql12.swb.upgradedacwizard.introduction.f1
helpviewer_keywords:
- upgrade DAC
- data-tier application [SQL Server], upgrade
- wizard [DAC], upgrade
- How to [DAC], upgrade
ms.assetid: c117df94-f02b-403f-9383-ec5b3ac3763c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e597d02af28a16539b50ff76503059278ef7a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645129"
---
# <a name="upgrade-a-data-tier-application"></a><span data-ttu-id="21a0d-102">データ層アプリケーションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="21a0d-102">Upgrade a Data-tier Application</span></span>
  <span data-ttu-id="21a0d-103">データ層アプリケーションのアップグレード ウィザードまたは Windows PowerShell スクリプトを使用すると、現在配置されているデータ層アプリケーション (DAC) のスキーマとプロパティを、新しいバージョンの DAC で定義されているスキーマとプロパティに一致するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-103">Use either the Upgrade Data-tier Application Wizard or a Windows PowerShell script to change the schema and properties of a currently deployed data-tier application (DAC) to match the schema and properties defined in a new version of the DAC.</span></span>  
  
-   <span data-ttu-id="21a0d-104">**作業を開始する準備:** [DAC アップグレード オプションの選択](#ChoseDACUpgOptions)、[制限事項と制約事項](#LimitationsRestrictions)、[前提条件](#Prerequisites)、[セキュリティ](#Security)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="21a0d-104">**Before you begin:**  [Choosing DAC Upgrade Options](#ChoseDACUpgOptions), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="21a0d-105">**DAC のアップグレード:** [データ層アプリケーションのアップグレード ウィザードの使用](#UsingDACUpgradeWizard)、[PowerShell の使用](#UpgradeDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="21a0d-105">**To upgrade a DAC, using:**  [The Upgrade Data-tier Application Wizard](#UsingDACUpgradeWizard), [PowerShell](#UpgradeDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21a0d-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="21a0d-106">Before You Begin</span></span>  
 <span data-ttu-id="21a0d-107">DAC アップグレードは、既存のデータベースのスキーマを新しい DAC バージョンで定義されているスキーマに一致するように変更するインプレース アップグレードです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-107">A DAC upgrade is an in-place process that alters the schema of the existing database to match the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="21a0d-108">新しい DAC バージョンは、DAC パッケージ ファイルで提供されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-108">The new version of the DAC is supplied in a DAC package file.</span></span> <span data-ttu-id="21a0d-109">DAC パッケージの作成の詳細については、「 [データ層アプリケーション](data-tier-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-109">For more information about creating a DAC package, see [Data-tier Applications](data-tier-applications.md).</span></span>  
  
###  <a name="choosing-dac-upgrade-options"></a><a name="ChoseDACUpgOptions"></a> <span data-ttu-id="21a0d-110">DAC アップグレード オプションの選択</span><span class="sxs-lookup"><span data-stu-id="21a0d-110">Choosing DAC Upgrade Options</span></span>  
 <span data-ttu-id="21a0d-111">インプレース アップグレードには 4 つのアップグレード オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-111">There are four upgrade options for an in-place upgrade:</span></span>  
  
-   <span data-ttu-id="21a0d-112">[**データ損失を無視**する]-の場合、 `True` 一部の操作によってデータが失われてもアップグレードが続行されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-112">**Ignore Data Loss** - If `True`, the upgrade will proceed even if some of the operations result in the loss of data.</span></span> <span data-ttu-id="21a0d-113">`False` の場合、これらの操作によってアップグレードは終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-113">If `False`, these operations will terminate the upgrade.</span></span> <span data-ttu-id="21a0d-114">たとえば、現在のデータベースにあるテーブルが新しい DAC のスキーマにない場合は、`True` が指定されていると、テーブルは削除されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-114">For example, if a table in the current database is not present in the schema of the new DAC, the table will be dropped if `True` is specified.</span></span> <span data-ttu-id="21a0d-115">既定の設定は `True` です。</span><span class="sxs-lookup"><span data-stu-id="21a0d-115">The default setting is `True`.</span></span>  
  
-   <span data-ttu-id="21a0d-116">**[変更時にブロック**する]-の場合 `True` 、データベーススキーマが前の DAC で定義されているスキーマと異なる場合は、アップグレードが終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-116">**Block on Changes** - If `True`, the upgrade is terminated if the database schema is different than that defined in the previous DAC.</span></span> <span data-ttu-id="21a0d-117">`False` の場合、変更が検出されても、アップグレードは続行されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-117">If `False`, the upgrade continues even if changes are detected.</span></span> <span data-ttu-id="21a0d-118">既定の設定は `False` です。</span><span class="sxs-lookup"><span data-stu-id="21a0d-118">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="21a0d-119">**失敗時にロールバック**する-の場合、 `True` アップグレードはトランザクションに含まれ、エラーが発生すると、ロールバックが試行されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-119">**Rollback on Failure** - If `True`, the upgrade is enclosed in a transaction, and if errors are encountered a rollback will be attempted.</span></span> <span data-ttu-id="21a0d-120">`False` の場合、すべての変更が実行時にコミットされます。エラーが発生する場合は、データベースの前のバックアップの復元が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-120">If `False`, all changes are committed as they are made and if errors occur you may have to restore a previous backup of the database.</span></span> <span data-ttu-id="21a0d-121">既定の設定は `False` です。</span><span class="sxs-lookup"><span data-stu-id="21a0d-121">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="21a0d-122">[**ポリシーの検証をスキップ**]: の場合 `True` 、DAC サーバーの選択ポリシーは評価されません。</span><span class="sxs-lookup"><span data-stu-id="21a0d-122">**Skip Policy Validation** - If `True`, the DAC server selection policy is not evaluated.</span></span> <span data-ttu-id="21a0d-123">`False` の場合は、ポリシーが評価され、検証エラーがあるとアップグレードは終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-123">If `False`, the policy is evaluated and the upgrade terminates if there is a validation error.</span></span> <span data-ttu-id="21a0d-124">既定の設定は `False` です。</span><span class="sxs-lookup"><span data-stu-id="21a0d-124">The default setting is `False`.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="21a0d-125">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="21a0d-125">Limitations and Restrictions</span></span>  
 <span data-ttu-id="21a0d-126">DAC アップグレードは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 以降でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-126">DAC uprades can only be performed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="21a0d-127">前提条件</span><span class="sxs-lookup"><span data-stu-id="21a0d-127">Prerequisites</span></span>  
 <span data-ttu-id="21a0d-128">アップグレードを開始する前に、データベースの完全バックアップを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-128">It is prudent to take a full database backup before starting the upgrade.</span></span> <span data-ttu-id="21a0d-129">アップグレード時にエラーが発生し、すべての変更をロールバックできない場合は、バックアップの復元が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-129">If an upgrade encounters an error and cannot roll back all of its changes, you may need to restore the backup.</span></span>  
  
 <span data-ttu-id="21a0d-130">アップグレードを開始する前に、DAC パッケージとアップグレード処理を検証するには、いくつかの操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-130">Before starting the upgrade, there are several actions that you should take to validate the DAC package and the upgrade actions.</span></span> <span data-ttu-id="21a0d-131">これらのチェックの実行方法の詳細については、「 [Validate a DAC Package](validate-a-dac-package.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="21a0d-132">アップグレード時には、ソースが不明または信頼されていない DAC パッケージは使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-132">We recommend that you do not upgrade by using a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="21a0d-133">こうしたパッケージには、意図しない Transact-SQL コードを実行したり、スキーマを変更してエラーを発生したりする、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-133">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="21a0d-134">パッケージのソースが不明または信頼されていない場合は、使用する前に、DAC をアンパックして、ストアド プロシージャやその他のユーザー定義コードなどのコードもご確認ください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-134">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
-   <span data-ttu-id="21a0d-135">最新バージョンの DAC が配置された後に現在のデータベースに変更が加えられている場合は、一部の変更によってアップグレードが正常に完了しなかったり、アップグレードによって一部の変更が削除されたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-135">If changes have been made to the current database after the last version of the DAC was deployed, some of the changes may prevent the successful completion of the upgrade, or be removed by the upgrade.</span></span> <span data-ttu-id="21a0d-136">まず、データベースで行った変更内容のレポートを生成して、確認してください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-136">You should first generate and review a report of any such changes made in the database.</span></span>  
  
-   <span data-ttu-id="21a0d-137">アップグレードによって実行されるスキーマの変更内容のリストを生成し、問題がないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-137">It is prudent to generate a list of the schema changes the upgrade will perform, and review the list for any problems.</span></span>  
  
 <span data-ttu-id="21a0d-138">DAC パッケージ内のアプリケーション名は、現在配置されている DAC のアプリケーション名と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-138">The application name in the DAC package must match the application name of the currently deployed DAC.</span></span> <span data-ttu-id="21a0d-139">たとえば、現在の DAC のアプリケーション名が **GeneralLedger**の場合、アップグレードできるのは、アプリケーション名が **GeneralLedger**の DAC パッケージを使用する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-139">For example, if the current DAC has an application name of **GeneralLedger**, you can only upgrade by using a DAC package that also has an application name of **GeneralLedger**.</span></span>  
  
 <span data-ttu-id="21a0d-140">すべての変更をログ記録するための十分なトランザクション ログ領域があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-140">Ensure there is enough transaction log space available to log all of the modifications.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="21a0d-141">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="21a0d-141">Security</span></span>  
 <span data-ttu-id="21a0d-142">セキュリティを強化するために、SQL Server 認証のログインは、パスワードなしで DAC パッケージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-142">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="21a0d-143">パッケージが配置またはアップグレードされると、ログインは、生成されたパスワードを伴う無効なログインとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-143">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="21a0d-144">ログインを有効にするには、ALTER ANY LOGIN 権限を持つユーザーとしてログインし、ALTER LOGIN を使用してログインを有効にします。さらに、新しいパスワードを割り当て、そのパスワードを該当ユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-144">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="21a0d-145">Windows 認証ログインの場合、ログインのパスワードは SQL Server で管理されていないため、この操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="21a0d-145">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="21a0d-146">Permissions</span><span class="sxs-lookup"><span data-stu-id="21a0d-146">Permissions</span></span>  
 <span data-ttu-id="21a0d-147">DAC をアップグレードできるのは、 **sysadmin** または **serveradmin** 固定サーバー ロールのメンバーか、 **dbcreator** 固定サーバー ロールに存在する ALTER ANY LOGIN 権限を持つログインのみです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-147">A DAC can only be upgraded by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="21a0d-148">ログインは既存のデータベースの所有者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-148">The login must be the owner of the existing database.</span></span> <span data-ttu-id="21a0d-149">あらかじめ登録された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウント ( **sa** ) も DAC をアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-149">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also upgrade a DAC.</span></span>  
  
##  <a name="using-the-upgrade-data-tier-application-wizard"></a><a name="UsingDACUpgradeWizard"></a> <span data-ttu-id="21a0d-150">データ層アプリケーションのアップグレード ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="21a0d-150">Using the Upgrade Data-tier Application Wizard</span></span>  
 <span data-ttu-id="21a0d-151">**ウィザードを使用して、DAC をアップグレードするには**</span><span class="sxs-lookup"><span data-stu-id="21a0d-151">**To Upgrade a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="21a0d-152">**オブジェクト エクスプローラー**で、アップグレードする DAC を含んだインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-152">In **Object Explorer**, expand the node for the instance containing the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="21a0d-153">**[管理]** ノードを展開し、 **[データ層のアプリケーション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-153">Expand the **Management** node, and then expand the **Data-tier Applications** node.</span></span>  
  
3.  <span data-ttu-id="21a0d-154">アップグレードする DAC のノードを右クリックしてから、 **[データ層アプリケーションのアップグレード]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-154">Right-click the node for the DAC to be upgraded, and then select **Upgrade Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="21a0d-155">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-155">Complete the wizard dialogs:</span></span>  
  
    1.  <span data-ttu-id="21a0d-156">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="21a0d-156">[Introduction Page](#Introduction)</span></span>  
  
    2.  <span data-ttu-id="21a0d-157">[[パッケージの選択] ページ](#Select_dac_package)</span><span class="sxs-lookup"><span data-stu-id="21a0d-157">[Select Package Page](#Select_dac_package)</span></span>  
  
    3.  <span data-ttu-id="21a0d-158">[[ポリシーの確認] ページ](#Review_policy)</span><span class="sxs-lookup"><span data-stu-id="21a0d-158">[Review Policy Page](#Review_policy)</span></span>  
  
    4.  <span data-ttu-id="21a0d-159">[[変更の検出] ページ](#Detect_change)</span><span class="sxs-lookup"><span data-stu-id="21a0d-159">[Detect Change Page](#Detect_change)</span></span>  
  
    5.  <span data-ttu-id="21a0d-160">[[アップグレード計画の確認]](#ReviewUpgPlan)</span><span class="sxs-lookup"><span data-stu-id="21a0d-160">[Review the Upgrade Plan](#ReviewUpgPlan)</span></span>  
  
    6.  <span data-ttu-id="21a0d-161">[[概要] ページ](#Summary)</span><span class="sxs-lookup"><span data-stu-id="21a0d-161">[Summary Page](#Summary)</span></span>  
  
    7.  <span data-ttu-id="21a0d-162">[[DAC のアップグレード] ページ](#Upgrade)</span><span class="sxs-lookup"><span data-stu-id="21a0d-162">[Upgrade DAC Page](#Upgrade)</span></span>  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="21a0d-163">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-163">Introduction Page</span></span>  
 <span data-ttu-id="21a0d-164">このページでは、データ層アプリケーションをアップグレードする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-164">This page describes the steps for upgrading a data-tier application.</span></span>  
  
 <span data-ttu-id="21a0d-165">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="21a0d-165">**Do not show this page again.**</span></span> <span data-ttu-id="21a0d-166">: 今後このページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-166">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="21a0d-167">**[次へ]** : **[パッケージの選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-167">**Next >** - Proceeds to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="21a0d-168">**[キャンセル]** : DAC をアップグレードせずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-168">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="select-package-page"></a><a name="Select_dac_package"></a> <span data-ttu-id="21a0d-169">[パッケージの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-169">Select Package Page</span></span>  
 <span data-ttu-id="21a0d-170">このページでは、新しいバージョンのデータ層アプリケーションを含む DAC パッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-170">Use this page to specify the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="21a0d-171">このページは、2 つの状態を遷移します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-171">The page transitions through two states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="21a0d-172">DAC パッケージの選択</span><span class="sxs-lookup"><span data-stu-id="21a0d-172">Select the DAC Package</span></span>  
 <span data-ttu-id="21a0d-173">ページの初期状態では、配置する DAC パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-173">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="21a0d-174">DAC パッケージは有効な DAC パッケージ ファイルで、拡張子は .dacpac である必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-174">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span> <span data-ttu-id="21a0d-175">DAC パッケージ内の DAC アプリケーション名は、現在の DAC のアプリケーション名と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-175">The DAC application name in the DAC package must be the same as the application name of the current DAC.</span></span>  
  
 <span data-ttu-id="21a0d-176">**[DAC パッケージ]** : 新しいバージョンのデータ層アプリケーションを含む DAC パッケージのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-176">**DAC Package** - Specify the path and file name of the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="21a0d-177">ボックスの右にある **[参照]** をクリックして、DAC パッケージの場所に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-177">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="21a0d-178">**[アプリケーション名]** : DAC が作成されたとき、またはデータベースから抽出されたときに割り当てられた DAC アプリケーション名が表示される読み取り専用のボックスです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-178">**Application Name** - A read-only box that displays the DAC application name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="21a0d-179">**[バージョン]** : DAC が作成されたとき、またはデータベースから抽出されたときに割り当てられたバージョンが表示される読み取り専用のボックスです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-179">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="21a0d-180">**[説明]** : DAC が作成されたとき、またはデータベースから抽出されたときに記述された説明が表示される読み取り専用のボックスです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-180">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="21a0d-181">\*\* \< Previous\*\* -[**概要**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-181">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="21a0d-182">**[次へ]** : 選択したファイルが有効な DAC パッケージかどうかが確認され、進捗状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-182">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="21a0d-183">**[キャンセル]** : DAC をアップグレードせずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-183">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="21a0d-184">DAC パッケージの検証</span><span class="sxs-lookup"><span data-stu-id="21a0d-184">Validating the DAC Package</span></span>  
 <span data-ttu-id="21a0d-185">選択したファイルが有効な DAC パッケージかどうかが確認され、進捗状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-185">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="21a0d-186">DAC パッケージが検証されると、ウィザードは **[ポリシーの確認]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-186">If the DAC package is validated, the wizard proceeds to the **Review Policy** page.</span></span> <span data-ttu-id="21a0d-187">ファイルが有効な DAC パッケージでない場合は、 **[DAC パッケージの選択]** ページが表示されたままになります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-187">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package** page.</span></span> <span data-ttu-id="21a0d-188">別の有効な DAC パッケージを選択するか、ウィザードを取り消して新しい DAC パッケージを生成してください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-188">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="21a0d-189">**[DAC パッケージの内容を検証しています]** : 検証プロセスの現在の状態を示す進捗状況バーです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-189">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="21a0d-190">[ \*\* \< 戻る\*\* **]: [パッケージの選択**] ページの初期状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-190">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="21a0d-191">**[次へ >]** : **[パッケージの選択]** ページの最終状態に進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-191">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="21a0d-192">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-192">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a> <span data-ttu-id="21a0d-193">[ポリシーの確認] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-193">Review Policy Page</span></span>  
 <span data-ttu-id="21a0d-194">このページでは、DAC にポリシーが含まれている場合に DAC サーバーの選択ポリシーを評価した結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-194">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="21a0d-195">DAC サーバーの選択ポリシーは、省略可能で、Microsoft Visual Studio で作成された DAC に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-195">The DAC server selection policy is optional, and is assigned to a DAC authored in Microsoft Visual Studio.</span></span> <span data-ttu-id="21a0d-196">このポリシーでは、サーバーの選択ポリシーのファセットを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスで DAC をホストするために満たす必要がある条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-196">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="21a0d-197">**[ポリシー条件の評価結果]** : DAC サーバーの選択ポリシーの条件の評価に成功したかどうかを示す読み取り専用のレポートです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-197">**Evaluation results of policy conditions** - A read-only report showing whether the evaluations of the conditions in the DAC server selection policy succeeded.</span></span> <span data-ttu-id="21a0d-198">各条件の評価結果が、レポートの各行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-198">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="21a0d-199">**[ポリシー違反を無視します]** : ポリシー条件が満たされていない場合にアップグレードを続行するには、このチェック ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-199">**Ignore policy violations** - Use this check box to proceed with the upgrade if one or more of the policy conditions failed.</span></span> <span data-ttu-id="21a0d-200">すべての条件が満たされていなくても DAC を正常に操作できるようにする場合のみ、このチェック ボックスをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-200">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="21a0d-201">[ \*\* \< 戻る\*\* **]: [パッケージの選択**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-201">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="21a0d-202">**[次へ]** : **[変更の検出]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-202">**Next >** - Proceeds to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="21a0d-203">**[キャンセル]** : DAC をアップグレードせずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-203">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="detect-change-page"></a><a name="Detect_change"></a> <span data-ttu-id="21a0d-204">[変更の検出] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-204">Detect Change Page</span></span>  
 <span data-ttu-id="21a0d-205">このページでは、 **msdb**内の DAC メタデータに格納されているスキーマ定義とは異なるスキーマを作成する、データベースへの変更についてウィザードで確認した結果がレポートされます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-205">Use this page reports the results of the wizards check for changes made to the database that make it's schema different than the schema definition stored in the DAC metadata in **msdb**.</span></span> <span data-ttu-id="21a0d-206">たとえば、最初に DAC が配置された後に、CREATE、ALTER または DROP ステートメントを使用してデータベースでオブジェクトを追加、変更、または削除した場合です。</span><span class="sxs-lookup"><span data-stu-id="21a0d-206">For example, if CREATE, ALTER, or DROP statements have been used to add, change, or remove objects from the database after the DAC was originally deployed.</span></span> <span data-ttu-id="21a0d-207">このページでは、まず進捗状況バーが表示されてから、分析結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-207">The page first displays a progress bar, and then reports the results of the analysis.</span></span>  
  
 <span data-ttu-id="21a0d-208">**[変更を検出しています。これには、数分間かかることがあります]** : ウィザードでデータベースの現在のスキーマと DAC 定義のオブジェクトの間で相違点がチェックされるときに、進捗状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-208">**Detecting change, this may take a few minutes** - Displays a progress bar as the wizard checks for differences between the current schema of the database and the objects in the DAC definition.</span></span>  
  
 <span data-ttu-id="21a0d-209">**[変更の検出結果]** : 分析が完了したことを示し、結果が下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-209">**Change detection results:** - Indicates that the analysis has completed and the results are reported below.</span></span>  
  
 <span data-ttu-id="21a0d-210">**[データベース &lt;DatabaseName&gt; は変更されていません]** : ウィザードで、データベースで定義されているオブジェクトと DAC 定義の対応するオブジェクトの間で相違点が検出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="21a0d-210">**The database DatabaseName has not changed** - The wizard detected no differences in the objects defined in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="21a0d-211">**[データベース &lt;DatabaseName&gt; が変更されました]** : ウィザードで、データベースのオブジェクトと DAC 定義の対応するオブジェクトの間で変更点が検出されました。</span><span class="sxs-lookup"><span data-stu-id="21a0d-211">**The database DatabaseName has changed** - The wizard detected changes between the objects in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="21a0d-212">**[変更が失われる可能性がありますが続行します]** : 現在のデータベース内のオブジェクトやデータの一部が新しいデータベースに存在しない場合があることがわかっていて、アップグレードを続行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-212">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="21a0d-213">このボタンは、変更レポートの分析が完了し、新しいデータベースで必要なオブジェクトやデータを手動で転送するための手順がわかっている場合にのみクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-213">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="21a0d-214">わからない場合は、 **[レポートの保存]** をクリックして変更レポートを保存し、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-214">If you are not sure, click the **Save Report** button to save the change report, then click **Cancel**.</span></span> <span data-ttu-id="21a0d-215">レポートを分析して、アップグレードの完了後に必要なオブジェクトやデータを転送する方法を計画し、ウィザードを再起動します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-215">Analyze the report, plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="21a0d-216">**[レポートの保存]** : ウィザードで検出された、データベースのオブジェクトと DAC 定義の対応するオブジェクトの間の変更点のレポートを保存する場合に、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-216">**Save Report** - Click the button to save a report of the changes the wizard detected between the objects in the database and their counterparts in the DAC definition.</span></span> <span data-ttu-id="21a0d-217">その後、レポートを確認し、アップグレードの完了後に、レポートに表示されたオブジェクトの一部またはすべてを新しいデータベースに組み込む操作を行う必要があるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-217">You can then review the report to determine if you need to take actions after the upgrade completes to incorporate some or all of the objects listed in the report into the new database.</span></span>  
  
 <span data-ttu-id="21a0d-218">[ \*\* \< 戻る\*\* **]: [DAC パッケージの選択**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-218">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="21a0d-219">**[次へ]** : **[オプション]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-219">**Next >** - Proceeds to the **Options** page.</span></span>  
  
 <span data-ttu-id="21a0d-220">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-220">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
## <a name="options-page"></a><span data-ttu-id="21a0d-221">[オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="21a0d-221">Options Page</span></span>  
 <span data-ttu-id="21a0d-222">このページを使用すると、アップグレードの失敗時のロールバック オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-222">Use this page to select the rollback on failure option for the upgrade.</span></span>  
  
 <span data-ttu-id="21a0d-223">**[失敗時にロールバック]** : このオプションを選択すると、アップグレードはトランザクションに含まれ、エラーが発生した場合はウィザードからロールバックを試行できます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-223">**Rollback on failure** - Select this option to enclose the upgrade in a transaction which the wizard can attempt to roll back if errors occur.</span></span> <span data-ttu-id="21a0d-224">オプションの詳細については、「 [DAC アップグレード オプションの選択](#ChoseDACUpgOptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-224">For more information about the option, see [Choosing DAC Upgrade Options](#ChoseDACUpgOptions).</span></span>  
  
 <span data-ttu-id="21a0d-225">**[既定値に戻す]** : オプションを既定値の false に戻します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-225">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="21a0d-226">\*\* \< Previous\*\* -[変更の**検出**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-226">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="21a0d-227">**[次へ]** : **[アップグレード計画の確認]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-227">**Next >** - Proceeds to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="21a0d-228">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-228">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-the-upgrade-plan-page"></a><a name="ReviewUpgPlan"></a> <span data-ttu-id="21a0d-229">[アップグレード計画の確認] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-229">Review the Upgrade Plan Page</span></span>  
 <span data-ttu-id="21a0d-230">このページでは、アップグレード プロセスで実行されるアクションを確認します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-230">Use this page to do review the actions that will be taken by the upgrade process.</span></span> <span data-ttu-id="21a0d-231">アップグレードによって問題が発生しないことが確実である場合にのみ、アップグレードを続行してください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-231">Only proceed when you are confident the upgrade will not create problems.</span></span>  
  
 <span data-ttu-id="21a0d-232">**[次のアクションを使用して DAC をアップグレードします。]**</span><span class="sxs-lookup"><span data-stu-id="21a0d-232">**The following actions will be used to upgrade the DAC.**</span></span> <span data-ttu-id="21a0d-233">: 表示された情報を確認し、実行されるアクションが正しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-233">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="21a0d-234">**[アクション]** 列には、アップグレードを行うために実行される Transact-SQL ステートメントなどのアクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-234">The **Action** column displays the actions, such as Transact-SQL statements, that will be run to perform the upgrade.</span></span> <span data-ttu-id="21a0d-235">**[データ損失]** 列には、関連付けられたアクションによってデータが削除される可能性がある場合に、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-235">The **Data Loss** column will contain a warning if the associated action could delete data.</span></span>  
  
 <span data-ttu-id="21a0d-236">**[更新]** : アクション リストを更新します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-236">**Refresh** - refreshes the action list.</span></span>  
  
 <span data-ttu-id="21a0d-237">**[アクション レポートの保存]** : アクション ウィンドウの内容を HTML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-237">**Save Action Report** - saves the contents of the action window to an HTML file.</span></span>  
  
 <span data-ttu-id="21a0d-238">**[変更が失われる可能性がありますが続行します]** : 現在のデータベース内のオブジェクトやデータの一部が新しいデータベースに存在しない場合があることがわかっていて、アップグレードを続行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-238">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="21a0d-239">このボタンは、変更レポートの分析が完了し、新しいデータベースで必要なオブジェクトやデータを手動で転送するための手順がわかっている場合にのみクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="21a0d-239">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="21a0d-240">わからない場合は、 **[アクション レポートの保存]** をクリックして変更レポートを保存し、 **[スクリプトの保存]** をクリックして Transact-SQL スクリプトを保存してから、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-240">If you are not sure, click the **Save Action Report** button to save the change report and the **Save Scripts** button to save the Transact-SQL script, then click **Cancel**.</span></span> <span data-ttu-id="21a0d-241">レポートとスクリプトを分析して、アップグレードの完了後に必要なオブジェクトやデータを転送する方法を計画し、ウィザードを再起動します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-241">Analyze the report and script, and then plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="21a0d-242">**[スクリプトの保存]** : アップグレードを実行するために使用される Transact-SQL ステートメントをテキスト ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-242">**Save Scripts** - saves the Transact-SQL statements that will be used to perform the upgrade to a text file.</span></span>  
  
 <span data-ttu-id="21a0d-243">**[既定値に戻す]** : オプションを既定値の false に戻します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-243">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="21a0d-244">\*\* \< Previous\*\* -[変更の**検出**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-244">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="21a0d-245">**[次へ]** : **[概要]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-245">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="21a0d-246">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-246">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="21a0d-247">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-247">Summary Page</span></span>  
 <span data-ttu-id="21a0d-248">このページでは、DAC のアップグレード時にウィザードが行うアクションを最終的に確認します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-248">Use this page to do a final review of the actions the wizard will take when upgrading the DAC.</span></span>  
  
 <span data-ttu-id="21a0d-249">**[次の設定を使用して DAC をアップグレードします。]**</span><span class="sxs-lookup"><span data-stu-id="21a0d-249">**The following settings will be used to upgrade your DAC.**</span></span> <span data-ttu-id="21a0d-250">: 表示された情報を確認し、実行されるアクションが正しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-250">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="21a0d-251">このウィンドウには、アップグレード対象として選択した DAC と、新しいバージョンの DAC が含まれている DAC パッケージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-251">The window displays the DAC you selected to be upgraded, and the DAC package containing the new version of the DAC.</span></span> <span data-ttu-id="21a0d-252">また、現在のバージョンのデータベースが現在の DAC 定義と同じかどうか、またはデータベースが変更されているかどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-252">The window also displays whether the current version of the database is the same as the current DAC definition, or if the database has changed.</span></span>  
  
 <span data-ttu-id="21a0d-253">[ \*\* \< 戻る**]: [**アップグレード計画の確認\*\*] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="21a0d-253">**\< Previous** - Returns you to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="21a0d-254">**[次へ]** : DAC を配置し、 **[DAC のアップグレード]** ページに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-254">**Next >** - Deploys the DAC and displays the results in the **Upgrade DAC** page.</span></span>  
  
 <span data-ttu-id="21a0d-255">**[キャンセル]** : DAC を配置せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-255">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="upgrade-dac-page"></a><a name="Upgrade"></a> <span data-ttu-id="21a0d-256">[DAC のアップグレード] ページ</span><span class="sxs-lookup"><span data-stu-id="21a0d-256">Upgrade DAC Page</span></span>  
 <span data-ttu-id="21a0d-257">このページには、アップグレード操作の成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-257">This page reports the success or failure of the upgrade operation.</span></span>  
  
 <span data-ttu-id="21a0d-258">**[DAC をアップグレードしています]** : DAC をアップグレードするために行った各アクションの成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-258">**Upgrading the DAC** - Reports the success or failure of each action taken to upgrade the DAC.</span></span> <span data-ttu-id="21a0d-259">内容を確認して、各アクションの成功または失敗を判断します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-259">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="21a0d-260">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-260">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="21a0d-261">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-261">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="21a0d-262">**[レポートの保存]** : アップグレード レポートを HTML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-262">**Save Report** - Select this button to save the upgrade report to an HTML file.</span></span> <span data-ttu-id="21a0d-263">ファイルには、アクションで発生したすべてのエラーを含む、各アクションのステータスが報告されます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-263">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="21a0d-264">既定のフォルダーは、Windows アカウントの Documents フォルダーにある SQL Server Management Studio\DAC Packages フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="21a0d-264">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="21a0d-265">**[完了]** : ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-265">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="UpgradeDACPowerShell"></a> <span data-ttu-id="21a0d-266">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="21a0d-266">Using PowerShell</span></span>  
 <span data-ttu-id="21a0d-267">**PowerShell スクリプトから IncrementalUpgrade() メソッドを使用して DAC をアップグレードするには**</span><span class="sxs-lookup"><span data-stu-id="21a0d-267">**To upgrade a DAC using the IncrementalUpgrade() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="21a0d-268">SMO サーバー オブジェクトを作成し、アップグレードする DAC が含まれたインスタンスにそれを設定します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-268">Create a SMO Server object and set it to the instance that contains the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="21a0d-269">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-269">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="21a0d-270">`System.IO.File` を使用して、DAC パッケージ ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-270">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="21a0d-271">`add_DacActionStarted` および `add_DacActionFinished` を使用して、DAC アップグレード イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-271">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
5.  <span data-ttu-id="21a0d-272">を設定 `DacUpgradeOptions` します。</span><span class="sxs-lookup"><span data-stu-id="21a0d-272">Set the `DacUpgradeOptions`.</span></span>  
  
6.  <span data-ttu-id="21a0d-273">`IncrementalUpgrade` メソッドを使用して DAC をアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-273">Use the `IncrementalUpgrade` method to upgrade the DAC.</span></span>  
  
7.  <span data-ttu-id="21a0d-274">DAC パッケージ ファイルの読み取りに使用するファイル ストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="21a0d-274">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="21a0d-275">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="21a0d-275">Example (PowerShell)</span></span>  
 <span data-ttu-id="21a0d-276">次の例では、MyApplicationVNext.dacpac パッケージで新しい DAC バージョンを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスの MyApplication という名前の DAC をアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="21a0d-276">The following example upgrades a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a new DAC version in a MyApplicationVNext.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC upgrade events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Upgrade the DAC and close the package.  
$dacName  = "MyApplication"  
  
## Set the upgrade options.  
$upgradeProperties = New-Object Microsoft.SqlServer.Management.Dac.DacUpgradeOptions  
$upgradeProperties.blockonchanges = $true  
$upgradeProperties.ignoredataloss = $false  
$upgradeProperties.rollbackonfailure = $true  
$ upgradeProperties.skippolicyvalidation = $false  
  
## Upgrade the DAC  
$dacstore.IncrementalUpgrade($dacName, $dacType, $upgradeProperties)  
## Close the package file.  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="21a0d-277">参照</span><span class="sxs-lookup"><span data-stu-id="21a0d-277">See Also</span></span>  
 <span data-ttu-id="21a0d-278">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="21a0d-278">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="21a0d-279">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="21a0d-279">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)  

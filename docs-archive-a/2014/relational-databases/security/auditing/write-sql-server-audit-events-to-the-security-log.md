---
title: セキュリティ ログへの SQL サーバー監査イベントの書き込み | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], Security Log
- server audit [SQL Server]
- audits [SQL Server], writing to Security Log
- security logs [SQL Server]
ms.assetid: 6fabeea3-7a42-4769-a0f3-7e04daada314
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d59134b278f29c9b604208d8cab7e982144b9c9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633028"
---
# <a name="write-sql-server-audit-events-to-the-security-log"></a><span data-ttu-id="ac2e3-102">セキュリティ ログへの SQL サーバー監査イベントの書き込み</span><span class="sxs-lookup"><span data-stu-id="ac2e3-102">Write SQL Server Audit Events to the Security Log</span></span>
  <span data-ttu-id="ac2e3-103">高度なセキュリティ環境では、オブジェクト アクセスを記録するイベントを書き込むのに適切な場所は Windows セキュリティ ログです。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-103">In a high security environment, the Windows Security log is the appropriate location to write events that record object access.</span></span> <span data-ttu-id="ac2e3-104">他の監査場所は、サポートされていますが、改ざんされる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-104">Other audit locations are supported but are more subject to tampering.</span></span>  
  
 <span data-ttu-id="ac2e3-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サーバー監査を Windows セキュリティ ログに書き込むための主要な要件は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-105">There are two key requirements for writing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server audits to the Windows Security log:</span></span>  
  
-   <span data-ttu-id="ac2e3-106">オブジェクト アクセスの監査の設定は、イベントをキャプチャするように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-106">The audit object access setting must be configured to capture the events.</span></span> <span data-ttu-id="ac2e3-107">監査ポリシー ツール (`auditpol.exe`) は、" **オブジェクト アクセスの監査** " カテゴリでさまざまなサブポリシー設定を公開しています。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-107">The audit policy tool (`auditpol.exe`) exposes a variety of sub-policies settings in the **audit object access** category.</span></span> <span data-ttu-id="ac2e3-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がオブジェクト アクセスを監査できるようにするには、 **application generated** 設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-108">To allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to audit object access, configure the **application generated** setting.</span></span>  
  
-   <span data-ttu-id="ac2e3-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを実行しているアカウントは、Windows セキュリティ ログに書き込むための " **セキュリティ監査の生成** " 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-109">The account that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running under must have the **generate security audits** permission to write to the Windows Security log.</span></span> <span data-ttu-id="ac2e3-110">既定では、LOCAL SERVICE アカウントおよび NETWORK SERVICE アカウントにこの権限があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-110">By default, the LOCAL SERVICE and the NETWORK SERVICE accounts have this permission.</span></span> <span data-ttu-id="ac2e3-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がこれらのアカウントのいずれかで実行されている場合、この手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-111">This step is not required if [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running under one of those accounts.</span></span>  
  
 <span data-ttu-id="ac2e3-112">Windows の監査ポリシーは、Windows セキュリティ ログに書き込むように構成されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の監査に影響を与えることがあります。監査ポリシーが不適切に構成された場合は、イベントが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-112">The Windows audit policy can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auditing if it is configured to write to the Windows Security log, with the potential of losing events if the audit policy is incorrectly configured.</span></span> <span data-ttu-id="ac2e3-113">通常、Windows セキュリティ ログは、古いイベントを上書きするよう設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-113">Typically, the Windows Security log is set to overwrite the older events.</span></span> <span data-ttu-id="ac2e3-114">これにより、最新のイベントが保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-114">This preserves the most recent events.</span></span> <span data-ttu-id="ac2e3-115">ただし、Windows セキュリティ ログが古いイベントを上書きするよう設定されていない場合、セキュリティ ログがいっぱいになると、システムは Windows イベント 1104 (ログがいっぱいです) を発行します。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-115">However, if the Windows Security log is not set to overwrite older events, then if the Security log is full, the system will issue Windows event 1104 (Log is full).</span></span> <span data-ttu-id="ac2e3-116">このとき、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-116">At that point:</span></span>  
  
-   <span data-ttu-id="ac2e3-117">それ以降のセキュリティ イベントは記録されません。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-117">No further security events will be recorded</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ac2e3-118">はシステムがイベントをセキュリティ ログに記録できないことを検出できないため、監査イベントが失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-118">will not be able to detect that the system is not able to record the events in the Security log, resulting in the potential loss of audit events</span></span>  
  
-   <span data-ttu-id="ac2e3-119">ボックス管理者によってセキュリティ ログが修復されると、ログ動作は正常に戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-119">After the box administrator fixes the Security log, the logging behavior will return to normal.</span></span>  
  
 <span data-ttu-id="ac2e3-120">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-120">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ac2e3-121">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-121">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ac2e3-122">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ac2e3-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ac2e3-123">Security</span><span class="sxs-lookup"><span data-stu-id="ac2e3-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ac2e3-124">**セキュリティ ログに SQL サーバー監査イベントを書き込むには:**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-124">**To write SQL Server audit events to the Security Log:**</span></span>  
  
     [<span data-ttu-id="ac2e3-125">auditpol を使用した Windows のオブジェクト アクセスの監査の設定</span><span class="sxs-lookup"><span data-stu-id="ac2e3-125">Configure the audit object access setting in Windows using auditpol</span></span>](#auditpolAccess)  
  
     [<span data-ttu-id="ac2e3-126">secpol を使用した Windows のオブジェクト アクセスの監査の設定</span><span class="sxs-lookup"><span data-stu-id="ac2e3-126">Configure the audit object access setting in Windows using secpol</span></span>](#secpolAccess)  
  
     [<span data-ttu-id="ac2e3-127">secpol を使用した "セキュリティ監査の生成" 権限のアカウントへの許可</span><span class="sxs-lookup"><span data-stu-id="ac2e3-127">Grant the generate security audits permission to an account using secpol</span></span>](#secpolPermission)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ac2e3-128">はじめに</span><span class="sxs-lookup"><span data-stu-id="ac2e3-128">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ac2e3-129">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ac2e3-129">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ac2e3-130">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンピューターの管理者は、セキュリティ ログのローカル設定がドメイン ポリシーによって上書きされることを理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-130">Administrators of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer should understand that local settings for the Security log can be overwritten by a domain policy.</span></span> <span data-ttu-id="ac2e3-131">この場合、ドメイン ポリシーによってサブカテゴリ設定 (**auditpol /get /subcategory:"application generated"** ) が上書きされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-131">In this case, the domain policy might overwrite the subcategory setting (**auditpol /get /subcategory:"application generated"**).</span></span> <span data-ttu-id="ac2e3-132">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の監査対象であるイベントが記録されないことを検出する方法がない場合、これがイベントをログに記録する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の機能に影響します。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-132">This can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ability to log events without having any way to detect that the events that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is trying to audit are not going to be recorded.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ac2e3-133">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ac2e3-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ac2e3-134">Permissions</span><span class="sxs-lookup"><span data-stu-id="ac2e3-134">Permissions</span></span>  
 <span data-ttu-id="ac2e3-135">これらの設定を行うには、Windows 管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-135">You must be a Windows administrator to configure these settings.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-auditpol"></a><a name="auditpolAccess"></a> <span data-ttu-id="ac2e3-136">auditpol を使用して Windows のオブジェクト アクセスの監査の設定を行うには</span><span class="sxs-lookup"><span data-stu-id="ac2e3-136">To configure the audit object access setting in Windows using auditpol</span></span>  
  
1.  <span data-ttu-id="ac2e3-137">管理権限を使用してコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-137">Open a command prompt with administrative permissions.</span></span>  
  
    1.  <span data-ttu-id="ac2e3-138">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[アクセサリ]** の順にポイントします。次に、 **[コマンド プロンプト]** を右クリックし、 **[管理者として実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-138">On the **Start** menu, point to **All Programs**, point to **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.</span></span>  
  
    2.  <span data-ttu-id="ac2e3-139">**[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-139">If the **User Account Control** dialog box opens, click **Continue**.</span></span>  
  
2.  <span data-ttu-id="ac2e3-140">次のステートメントを実行して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]からの監査を有効にします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-140">Execute the following statement to enable auditing from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
    ```  
    auditpol /set /subcategory:"application generated" /success:enable /failure:enable  
    ```  
  
3.  <span data-ttu-id="ac2e3-141">コマンド プロンプト ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-141">Close the command prompt window.</span></span>  
  
##  <a name="to-grant-the-generate-security-audits-permission-to-an-account-using-secpol"></a><a name="secpolAccess"></a> <span data-ttu-id="ac2e3-142">secpol を使用して "セキュリティ監査の生成" 権限をアカウントに許可するには</span><span class="sxs-lookup"><span data-stu-id="ac2e3-142">To grant the generate security audits permission to an account using secpol</span></span>  
  
1.  <span data-ttu-id="ac2e3-143">任意の Windows オペレーティング システムで、 **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-143">For any Windows operating system, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ac2e3-144">「 **secpol.msc** 」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-144">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="ac2e3-145">**[ユーザー アクセス制御]** ダイアログ ボックスが表示されたら、 **[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-145">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="ac2e3-146">ローカル セキュリティ ポリシー ツールで、 **[セキュリティの設定]** 、 **[ローカル ポリシー]** の順に展開し、 **[ユーザー権利の割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-146">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
4.  <span data-ttu-id="ac2e3-147">結果ペインで **[セキュリティ監査の生成]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-147">In the results pane, double-click **Generate security audits**.</span></span>  
  
5.  <span data-ttu-id="ac2e3-148">**[ローカル セキュリティの設定]** タブの **[ユーザーまたはグループの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-148">On the **Local Security Setting** tab, click **Add User or Group**.</span></span>  
  
6.  <span data-ttu-id="ac2e3-149">**[ユーザー、コンピューター、またはグループの選択]** ダイアログ ボックスで、ユーザー アカウントの名前 ( **domain1\user1** など) を入力して **[OK]** をクリックするか、 **[詳細設定]** をクリックしてアカウントを検索します。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-149">In the **Select Users, Computers, or Groups** dialog box, either type the name of the user account, such as **domain1\user1** and then click **OK**, or click **Advanced** and search for the account.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="ac2e3-150">セキュリティ ポリシー ツールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-150">Close the Security Policy tool.</span></span>  
  
9. <span data-ttu-id="ac2e3-151">この設定を有効にするために [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を再起動します。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-151">Restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to enable this setting.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-secpol"></a><a name="secpolPermission"></a> <span data-ttu-id="ac2e3-152">secpol を使用して Windows のオブジェクト アクセスの監査の設定を行うには</span><span class="sxs-lookup"><span data-stu-id="ac2e3-152">To configure the audit object access setting in Windows using secpol</span></span>  
  
1.  <span data-ttu-id="ac2e3-153">[!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] または Windows Server 2008 より前のオペレーティング システムでは、 **[スタート]** ボタンをクリックして、 **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-153">If the operating system is earlier than [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] or Windows Server 2008, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ac2e3-154">「 **secpol.msc** 」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-154">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="ac2e3-155">**[ユーザー アクセス制御]** ダイアログ ボックスが表示されたら、 **[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-155">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="ac2e3-156">ローカル セキュリティ ポリシー ツールで、 **[セキュリティの設定]** 、 **[ローカル ポリシー]** の順に展開し、 **[監査ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-156">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **Audit Policy**.</span></span>  
  
4.  <span data-ttu-id="ac2e3-157">結果ペインで、 **[オブジェクト アクセスの監査]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-157">In the results pane, double-click **Audit object access**.</span></span>  
  
5.  <span data-ttu-id="ac2e3-158">**[ローカル セキュリティの設定]** タブの **[次の場合に監査する]** で、 **[成功]** チェック ボックスと **[失敗]** チェック ボックスの両方をオンにします。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-158">On the **Local Security Setting** tab, in the **Audit these attempts** area, select both **Success** and **Failure**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="ac2e3-159">セキュリティ ポリシー ツールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-159">Close the Security Policy tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2e3-160">参照</span><span class="sxs-lookup"><span data-stu-id="ac2e3-160">See Also</span></span>  
 [<span data-ttu-id="ac2e3-161">SQL Server Audit &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="ac2e3-161">SQL Server Audit &#40;Database Engine&#41;</span></span>](sql-server-audit-database-engine.md)  
  
  

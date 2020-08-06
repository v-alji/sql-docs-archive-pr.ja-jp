---
title: ユーザーに DQS ロールを付与する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 62ff5eb03fa46279ee1b8a1329c58bd69361ef82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736792"
---
# <a name="grant-dqs-roles-to-users"></a><span data-ttu-id="b7dde-102">ユーザーに DQS ロールを付与する</span><span class="sxs-lookup"><span data-stu-id="b7dde-102">Grant DQS Roles to Users</span></span>
  <span data-ttu-id="b7dde-103">このトピックでは、Windows プリンシパルに基づいて SQL ログインを作成し、DQS_MAIN データベースで [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) ロールを付与する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b7dde-103">This topic describes how to create SQL logins based on a Windows principal, and grant [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7dde-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="b7dde-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="b7dde-105">DQSInstaller.exe ファイルを実行して [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のインストールを完了しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7dde-105">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="b7dde-106">詳細については、「 [Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b7dde-106">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="b7dde-107">SQL ログインを作成し、DQS ロールを付与するには、Windows ユーザー アカウントが適切な固定サーバー ロール (securityadmin、serveradmin、sysadmin など) のメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7dde-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant them DQS roles.</span></span>  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a><span data-ttu-id="b7dde-108">SQL ログインを作成し、DQS ロールを付与するには</span><span class="sxs-lookup"><span data-stu-id="b7dde-108">To create SQL login and grant DQS roles</span></span>  
  
1.  <span data-ttu-id="b7dde-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動します。</span><span class="sxs-lookup"><span data-stu-id="b7dde-109">Start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b7dde-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、SQL Server インスタンスを展開し、 **[セキュリティ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b7dde-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="b7dde-111">**[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[ログイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7dde-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="b7dde-112">**[ログイン - 新規作成]** ダイアログ ボックスの **[ログイン名]** ボックスで Windows ユーザーの名前を指定し、認証の種類として **[Windows 認証]** を指定し、**[検索]** をクリックしてユーザーを検証します。</span><span class="sxs-lookup"><span data-stu-id="b7dde-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
5.  <span data-ttu-id="b7dde-113">ユーザーの検証後、左ペインの **[ユーザー マッピング]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7dde-113">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="b7dde-114">右ペインで、 **[DQS_MAIN]** データベースの **[マップ]** 列のチェック ボックスをオンにし、ユーザーに必要なアクセス レベルに応じて、 **[DQS_MAIN のデータベース ロール メンバーシップ]** ペインで **[dqs_administrator]**、 **[dqs_kb_editor]** 、または **[dqs_kb_operator]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b7dde-114">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span> <span data-ttu-id="b7dde-115">3 つの DQS ロールの詳細については、「 [DQS のセキュリティ](../dqs-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7dde-115">For information about the three DQS roles, see [DQS Security](../dqs-security.md).</span></span>  
  
7.  <span data-ttu-id="b7dde-116">**[ログイン - 新規作成]** ダイアログ ボックスで、**[OK]** をクリックして変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="b7dde-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b7dde-117">**dqs_administrator** ロールをユーザーに付与し、変更を適用してから、ユーザー権限を再びオンにすると、その他の 2 つの DQS ロールのチェック ボックス (**[dq_kb_editor]** および **[dqs_kb_operator]**) もオンになります。</span><span class="sxs-lookup"><span data-stu-id="b7dde-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b7dde-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="b7dde-118">Next Steps</span></span>  
 <span data-ttu-id="b7dde-119">先ほど SQL ログインを作成し、DQS ロールを付与した Windows ユーザー アカウントを使用して [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] へのログオンを試みます。</span><span class="sxs-lookup"><span data-stu-id="b7dde-119">Try logging on to [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] by using the Windows user account for which you just created a SQL login, and granted a DQS role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7dde-120">参照</span><span class="sxs-lookup"><span data-stu-id="b7dde-120">See Also</span></span>  
 <span data-ttu-id="b7dde-121">[Data Quality Services のインストール](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="b7dde-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="b7dde-122">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="b7dde-122">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  

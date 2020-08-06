---
title: データベース メール構成オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlimail.manageexistingaccount.f1
- sql12.swb.sqlimail.addaccounttoprofile.f1
- sql12.swb.sqlmailconfiguration.f1
- sql12.swb.sqlimail.profileandaccountmanagement.f1
- sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- sql12.swb.sqlimail.newsqlimailaccount.f1
- sql12.swb.sqlimail.configuresystem.f1
- sql12.swb.sqlimail.selectconfiguration.f1
- sql12.swb.sqlimail.newprofile.f1
- sql12.swb.sqlimail.manageexistingprofile.f1
- sql12.swb.sqlimail.welcome.f1
- sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- sql12.swb.sqlimail.completewizard.f1
- sql12.swb.sqlimail.newaccount.f1
helpviewer_keywords:
- Database Mail [SQL Server], configuration objects
- Database Mail [SQL Server], accounts
- configuration objects [Database Mail]
- Database Mail [SQL Server], profiles
- profiles [SQL Server], Database Mail
- accounts [Database Mail]
ms.assetid: 03f6e4c0-04ff-490a-bd91-637806215bd1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45dd4bfc8cdb382f9ad093e92c5939986a9db8e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742266"
---
# <a name="database-mail-configuration-objects"></a><span data-ttu-id="7b5a8-102">データベース メール構成オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7b5a8-102">Database Mail Configuration Objects</span></span>
  <span data-ttu-id="7b5a8-103">データベース メールには、2 つの構成オブジェクトがあります。データベース アプリケーションまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent から電子メールを送信する際、データベース メールによって使用される設定は、データベース構成オブジェクトを通じて構成することができます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-103">Database Mail has two configuration objects: The database configuration objects provide a way for you to configure the settings that Database mail should use when sending an email from your database application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="7b5a8-104">データベース メール アカウント</span><span class="sxs-lookup"><span data-stu-id="7b5a8-104">Database Mail accounts</span></span>  
  
-   <span data-ttu-id="7b5a8-105">データベース メール プロファイル</span><span class="sxs-lookup"><span data-stu-id="7b5a8-105">Database Mail profiles</span></span>  
  
  
##  <a name="database-mail-configuration-object-relationship"></a><a name="VisualElement"></a> <span data-ttu-id="7b5a8-106">データベース メール構成オブジェクトの関係</span><span class="sxs-lookup"><span data-stu-id="7b5a8-106">Database Mail Configuration Object Relationship</span></span>  
 <span data-ttu-id="7b5a8-107">この図には、2 つのプロファイル、3 つのアカウント、および 3 人のユーザーが示されています。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-107">The illustration shows two profiles, three accounts, and three users.</span></span> <span data-ttu-id="7b5a8-108">ユーザー 1 には、アカウント 1 とアカウント 2 を使用しているプロファイル 1 へのアクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-108">User 1 has access to Profile 1, which uses Account 1 and Account 2.</span></span> <span data-ttu-id="7b5a8-109">ユーザー 3 には、アカウント 2 とアカウント 3 を使用しているプロファイル 2 へのアクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-109">User 3 has access to Profile 2, which uses Account 2 and Account 3.</span></span> <span data-ttu-id="7b5a8-110">ユーザー 2 には、プロファイル 1 とプロファイル 2 の両方へのアクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-110">User 2 has access to both Profile 1 and Profile 2.</span></span>  
  
 <span data-ttu-id="7b5a8-111">![ユーザー、プロファイル、アカウントの関係](../../database-engine/media/databasemailprofileaccount.gif "ユーザー、プロファイル、アカウントの関係")</span><span class="sxs-lookup"><span data-stu-id="7b5a8-111">![Relationship of users, profiles, and accounts](../../database-engine/media/databasemailprofileaccount.gif "Relationship of users, profiles, and accounts")</span></span>  
  
  
##  <a name="database-mail-account"></a><a name="DBAccount"></a> <span data-ttu-id="7b5a8-112">データベース メール アカウント</span><span class="sxs-lookup"><span data-stu-id="7b5a8-112">Database Mail Account</span></span>  
 <span data-ttu-id="7b5a8-113">データベース メール アカウントには、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SMTP サーバーへの電子メール メッセージの送信に使用される情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-113">A Database Mail account contains the information that Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="7b5a8-114">各アカウントに、1 つの電子メール サーバーの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-114">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="7b5a8-115">データベース メールでは、SMTP サーバーとの通信に関して、次に示す 3 つの認証方法をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-115">A Database Mail supports three methods of authentication to communicate with an SMTP server:</span></span>  
  
-   <span data-ttu-id="7b5a8-116">Windows 認証:SMTP サーバーの認証に [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] の Windows サービス アカウントの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-116">Windows Authentication: Database Mail uses the credentials of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows service account for authentication on the SMTP server.</span></span>  
  
-   <span data-ttu-id="7b5a8-117">基本認証: SMTP サーバーの認証用に指定されたユーザー名とパスワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-117">Basic Authentication:  Database Mail uses the username and password specified to authenticate on the SMTP server.</span></span>  
  
-   <span data-ttu-id="7b5a8-118">匿名認証:SMTP サーバーでは認証が必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-118">Anonymous Authentication:  The SMTP server does not require any authentication.</span></span>  <span data-ttu-id="7b5a8-119">SMTP サーバーの認証には資格情報をまったく使用しません。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-119">Database Mail will not use any credentials to authenticate on the SMTP server.</span></span>  
  
 <span data-ttu-id="7b5a8-120">アカウント情報は、 **msdb** データベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-120">Account information is stored in the **msdb** database.</span></span> <span data-ttu-id="7b5a8-121">各アカウントを構成する情報は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-121">Each account consists of the following information:</span></span>  
  
-   <span data-ttu-id="7b5a8-122">アカウントの名前。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-122">The name of the account.</span></span>  
  
-   <span data-ttu-id="7b5a8-123">アカウントの説明。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-123">A description of the account.</span></span>  
  
-   <span data-ttu-id="7b5a8-124">アカウントの電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-124">The e-mail address of the account.</span></span>  
  
-   <span data-ttu-id="7b5a8-125">アカウントの表示名。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-125">The display name for the account.</span></span>  
  
-   <span data-ttu-id="7b5a8-126">アカウントの返信先情報として使用する電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-126">The e-mail address to use as the reply-to information for the account.</span></span>  
  
-   <span data-ttu-id="7b5a8-127">電子メール サーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-127">The name of the e-mail server.</span></span>  
  
-   <span data-ttu-id="7b5a8-128">電子メール サーバーの種類。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-128">The type of the e-mail server.</span></span> <span data-ttu-id="7b5a8-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、常に SMTP (簡易メール転送プロトコル) です。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-129">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this is always Simple Mail Transfer Protocol(SMTP).</span></span>  
  
-   <span data-ttu-id="7b5a8-130">電子メール サーバーのポート番号。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-130">The port number of the e-mail server.</span></span>  
  
-   <span data-ttu-id="7b5a8-131">SSL (Secure Sockets Layer) を使用して SMTP メール サーバーに接続しているかどうかを示すビット列。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-131">A bit column indicating whether the connection to the SMTP mail server is made using Secure Sockets Layer (SSL).</span></span>  
  
-   <span data-ttu-id="7b5a8-132">[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]用に構成された資格情報を使用して SMTP サーバーに接続しているかどうかを示すビット列。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-132">A bit column indicating whether the connection to the SMTP server is made using the credentials configured for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7b5a8-133">(電子メール サーバーで認証が必要な場合) 電子メール サーバーへの認証に使用するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-133">The user name to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
-   <span data-ttu-id="7b5a8-134">(電子メール サーバーで認証が必要な場合) 電子メール サーバーへの認証に使用するパスワード。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-134">The password to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
 <span data-ttu-id="7b5a8-135">データベース メール構成ウィザードでは、アカウントを作成および管理するための便利な方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-135">The Database Mail Configuration Wizard provides a convenient way to create and manage accounts.</span></span> <span data-ttu-id="7b5a8-136">また、 **msdb** の構成ストアド プロシージャを使用して、アカウントを作成および管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-136">You can also use the configuration stored procedures in **msdb** to create and manage accounts.</span></span>  
  
  
##  <a name="database-mail-profile"></a><a name="DBProfile"></a> <span data-ttu-id="7b5a8-137">[データベース メール プロファイル]</span><span class="sxs-lookup"><span data-stu-id="7b5a8-137">Database Mail Profile</span></span>  
 <span data-ttu-id="7b5a8-138">データベース メール プロファイルとは、関連のあるデータベース メール アカウントに順序を付けたコレクションです。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-138">A Database Mail profile is an ordered collection of related Database Mail accounts.</span></span> <span data-ttu-id="7b5a8-139">データベース メールを使用して電子メールを送信するアプリケーションでは、アカウントを直接使用するのではなく、プロファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-139">Applications that send e-mail using Database Mail specify profiles, instead of using accounts directly.</span></span> <span data-ttu-id="7b5a8-140">アプリケーションが使用するオブジェクトから個別の電子メール サーバーに関する情報を分離することで、柔軟性や信頼性が向上します。つまり、プロファイルにより自動フェールオーバーが提供されるので、ある電子メール サーバーが応答していない場合に、データベース メールによって別の電子メール サーバーに自動的にメールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-140">Separating information about the individual e-mail servers from the objects that the application uses improves flexibility and reliability: profiles provide automatic failover, so that if one e-mail server is unresponsive, Database Mail can automatically send mail to another e-mail server.</span></span> <span data-ttu-id="7b5a8-141">データベース管理者は、アプリケーション コードまたはジョブ ステップを変更する必要なく、アカウントの追加、削除、または再構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-141">Database administrators can add, remove, or reconfigure accounts without requiring changes to application code or job steps.</span></span>  
  
 <span data-ttu-id="7b5a8-142">プロファイルはデータベース管理者が電子メールへのアクセスを制御するうえでも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-142">Profiles also help database administrators control access to e-mail.</span></span> <span data-ttu-id="7b5a8-143">データベース メールを送信するには **DatabaseMailUserRole** のメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-143">Membership in the **DatabaseMailUserRole** is required to send Database Mail.</span></span> <span data-ttu-id="7b5a8-144">プロファイルを使用すると、メールを送信するユーザーおよび使用するアカウントを管理者が柔軟にコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-144">Profiles provide additional flexibility for administrators to control who sends mail and which accounts are used.</span></span>  
  
 <span data-ttu-id="7b5a8-145">プロファイルはパブリックまたはプライベートにできます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-145">A profile may be public or private.</span></span>  
  
 <span data-ttu-id="7b5a8-146">**msdb** データベースの **DatabaseMailUserRole** データベース ロールのすべてのメンバーが、 **パブリック プロファイル** を利用できます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-146">**Public profiles** are available for all members of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span> <span data-ttu-id="7b5a8-147">**DatabaseMailUserRole** ロールのすべてのメンバーは、このプロファイルを使用して電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-147">They allow all members of the **DatabaseMailUserRole** role to send e-mail using the profile.</span></span>  
  
 <span data-ttu-id="7b5a8-148">**プライベート プロファイル** は、 **msdb** データベースのセキュリティ プリンシパル用に定義されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-148">**Private profiles** are defined for security principals in the **msdb** database.</span></span> <span data-ttu-id="7b5a8-149">指定したデータベース ユーザー、ロール、および **sysadmin** 固定サーバー ロールのメンバーのみ、このプロファイルを使用して電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-149">They allow only specified database users, roles, and members of the **sysadmin** fixed server role to send e-mail using the profile.</span></span> <span data-ttu-id="7b5a8-150">既定では、プロファイルはプライベートで、 **sysadmin** 固定サーバー ロールのメンバーのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-150">By default, a profile is private, and allows access only to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="7b5a8-151">プライベート プロファイルを使用するには、 **sysadmin** が、プライベート プロファイルを使用するための権限をユーザーに与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-151">To use a private profile, **sysadmin** must grant users permission to use the profile.</span></span> <span data-ttu-id="7b5a8-152">また、 **sp_send_dbmail** ストアド プロシージャの EXECUTE 権限は、 **DatabaseMailUserRole**のメンバーにのみ与えられます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-152">Additionally, EXECUTE permission on the **sp_send_dbmail** stored procedure is only granted to members of the **DatabaseMailUserRole**.</span></span> <span data-ttu-id="7b5a8-153">ユーザーが電子メール メッセージを送信できるようにするには、システム管理者がユーザーを **DatabaseMailUserRole** データベース ロールに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-153">A system administrator must add the user to the **DatabaseMailUserRole** database role for the user to send e-mail messages.</span></span>  
  
 <span data-ttu-id="7b5a8-154">プロファイルを使用すると、電子メール サーバーへのメッセージ配信や電子メール サーバーでのメッセージ処理ができなくなった場合の信頼性が高まります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-154">Profiles improve reliability in cases where an e-mail server becomes unreachable or unable to process messages.</span></span> <span data-ttu-id="7b5a8-155">プロファイル内のアカウントには、通し番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-155">Each account in the profile has a sequence number.</span></span> <span data-ttu-id="7b5a8-156">シーケンス番号によって、データベース メールではプロファイル内のアカウントがどの順番で使用されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-156">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="7b5a8-157">新しい電子メール メッセージが作成されると、メッセージを正常に送信した最後のアカウントが使用されます。ただしその時点で正常に送信されたメッセージが 1 通もない場合は、最も番号が小さいアカウントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-157">For a new e-mail message, Database Mail uses the last account that sent a message successfully, or the account that has the lowest sequence number if no message has yet been sent.</span></span> <span data-ttu-id="7b5a8-158">そのアカウントが失敗すると、データベース メールでは、このアカウントよりも大きいシーケンス番号を持つアカウントに処理が移ります。このように、データベース メールによってメッセージが正常に送信されるか、一番大きなシーケンス番号のアカウントが失敗するまで順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-158">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="7b5a8-159">最も番号が大きいアカウントで失敗した場合、 **sysmail_configure_sp** の **AccountRetryDelay**パラメーターで構成した時間、メールの送信が一時停止されます。その後、最も番号が小さいアカウントからメールの送信プロセスが再開されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-159">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the **AccountRetryDelay** parameter of **sysmail_configure_sp**, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="7b5a8-160">**sysmail_configure_sp** の **AccountRetryAttempts**パラメーターは、指定されたプロファイルの各アカウントを使用して外部メール プロセスが電子メール メッセージを送信する回数を構成します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-160">Use the **AccountRetryAttempts** parameter of **sysmail_configure_sp**, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="7b5a8-161">同じシーケンス番号を持つアカウントが複数存在する場合、データベース メールでは、指定された電子メール メッセージに対して、これらのアカウントのいずれか 1 つのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-161">If more than one account exists with the same sequence number, Database Mail only uses one of those accounts for a given e-mail message.</span></span> <span data-ttu-id="7b5a8-162">この場合、そのシーケンス番号に対してどのアカウントが使用されるか、またメッセージごとに同じアカウントが使用されるかついては、データベース メールでは保証されません。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-162">In this case, Database Mail makes no guarantees as to which of the accounts is used for that sequence number or that the same account is used from message to message.</span></span>  
  
  
##  <a name="database-mail-configuration-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7b5a8-163">データベース メール構成タスク</span><span class="sxs-lookup"><span data-stu-id="7b5a8-163">Database Mail Configuration Tasks</span></span>  
 <span data-ttu-id="7b5a8-164">データベース メールの構成タスクを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-164">The following table describes the Database Mail configuration tasks.</span></span>  
  
|<span data-ttu-id="7b5a8-165">構成タスク</span><span class="sxs-lookup"><span data-stu-id="7b5a8-165">Configuration Task</span></span>|<span data-ttu-id="7b5a8-166">トピック</span><span class="sxs-lookup"><span data-stu-id="7b5a8-166">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="7b5a8-167">データベース メール アカウントの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-167">Describes how to create a Database Mail accounts</span></span>|[<span data-ttu-id="7b5a8-168">データベース メール アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="7b5a8-168">Create a Database Mail Account</span></span>](create-a-database-mail-account.md)|  
|<span data-ttu-id="7b5a8-169">データベース メール プロファイルの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-169">Describes how to Create Database Mail profiles</span></span>|[<span data-ttu-id="7b5a8-170">データベース メール プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="7b5a8-170">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)|  
|<span data-ttu-id="7b5a8-171">データベース メールの構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-171">Describes how to Configure Database mail</span></span>|[<span data-ttu-id="7b5a8-172">データベース メールを構成する</span><span class="sxs-lookup"><span data-stu-id="7b5a8-172">Configure Database Mail</span></span>](configure-database-mail.md)|  
|<span data-ttu-id="7b5a8-173">テンプレートを使用してデータベース メール構成スクリプトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-173">Describes how to create a Database Mail configuration script using templates</span></span>||  
  
  
##  <a name="additional-database-configuration-tasks-system-stored-procedures"></a><a name="Add_Tasks"></a> <span data-ttu-id="7b5a8-174">その他のデータベース構成タスク (システム ストアド プロシージャ)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-174">Additional Database Configuration Tasks (System Stored Procedures)</span></span>  
 <span data-ttu-id="7b5a8-175">データベース メール構成のストアド プロシージャは、 **msdb** データベースにあります。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-175">Database Mail configuration stored procedures are located in the **msdb** database.</span></span>  
  
 <span data-ttu-id="7b5a8-176">次の表は、データベース メールの構成および管理に使用するストアド プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-176">The following tables list the stored procedures used for configuring and managing Database Mail.</span></span>  
  
### <a name="database-mail-settings"></a><span data-ttu-id="7b5a8-177">データベース メール設定</span><span class="sxs-lookup"><span data-stu-id="7b5a8-177">Database Mail Settings</span></span>  
  
|<span data-ttu-id="7b5a8-178">名前</span><span class="sxs-lookup"><span data-stu-id="7b5a8-178">Name</span></span>|<span data-ttu-id="7b5a8-179">説明</span><span class="sxs-lookup"><span data-stu-id="7b5a8-179">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="7b5a8-180">sysmail_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-180">sysmail_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|<span data-ttu-id="7b5a8-181">データベース メールの構成設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-181">Changes configuration settings for Database Mail.</span></span>|  
|[<span data-ttu-id="7b5a8-182">sysmail_help_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-182">sysmail_help_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql)|<span data-ttu-id="7b5a8-183">データベース メールの構成設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-183">Displays configuration settings for Database Mail.</span></span>|  
  
### <a name="accounts-and-profiles"></a><span data-ttu-id="7b5a8-184">アカウントおよびプロファイル</span><span class="sxs-lookup"><span data-stu-id="7b5a8-184">Accounts and Profiles</span></span>  
  
|<span data-ttu-id="7b5a8-185">名前</span><span class="sxs-lookup"><span data-stu-id="7b5a8-185">Name</span></span>|<span data-ttu-id="7b5a8-186">説明</span><span class="sxs-lookup"><span data-stu-id="7b5a8-186">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="7b5a8-187">sysmail_add_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-187">sysmail_add_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)|<span data-ttu-id="7b5a8-188">データベース メール プロファイルにメール アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-188">Adds a mail account to a Database Mail profile.</span></span>|  
|[<span data-ttu-id="7b5a8-189">sysmail_delete_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-189">sysmail_delete_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-account-sp-transact-sql)|<span data-ttu-id="7b5a8-190">データベース メール アカウントを削除します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-190">Deletes a Database Mail account.</span></span>|  
|[<span data-ttu-id="7b5a8-191">sysmail_delete_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-191">sysmail_delete_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql)|<span data-ttu-id="7b5a8-192">データベース メール プロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-192">Deletes a Database Mail profile.</span></span>|  
|[<span data-ttu-id="7b5a8-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql)|<span data-ttu-id="7b5a8-194">データベース メール プロファイルからアカウントを削除します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-194">Removes an account from a Database Mail profile.</span></span>|  
|[<span data-ttu-id="7b5a8-195">sysmail_help_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-195">sysmail_help_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql)|<span data-ttu-id="7b5a8-196">データベース メール アカウントに関する情報を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-196">Lists information about Database Mail accounts.</span></span>|  
|[<span data-ttu-id="7b5a8-197">sysmail_help_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-197">sysmail_help_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql)|<span data-ttu-id="7b5a8-198">1 つ以上のデータベース メール プロファイルに関する情報を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-198">Lists information about one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="7b5a8-199">sysmail_help_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-199">sysmail_help_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql)|<span data-ttu-id="7b5a8-200">1 つ以上のデータベース メール プロファイルに関連付けられているアカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-200">Lists the accounts associated with one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="7b5a8-201">sysmail_update_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-201">sysmail_update_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-account-sp-transact-sql)|<span data-ttu-id="7b5a8-202">既存のデータベース メール アカウントの情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-202">Updates the information in an existing Database Mail account.</span></span>|  
|[<span data-ttu-id="7b5a8-203">sysmail_update_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-203">sysmail_update_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profile-sp-transact-sql)|<span data-ttu-id="7b5a8-204">データベース メール プロファイルの説明または名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-204">Changes the description or name of a Database Mail profile.</span></span>|  
|[<span data-ttu-id="7b5a8-205">sysmail_update_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-205">sysmail_update_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql)|<span data-ttu-id="7b5a8-206">データベース メール プロファイル内のアカウントのシーケンス番号を更新します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-206">Updates the sequence number of an account within a Database Mail profile.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="7b5a8-207">Security</span><span class="sxs-lookup"><span data-stu-id="7b5a8-207">Security</span></span>  
  
|<span data-ttu-id="7b5a8-208">名前</span><span class="sxs-lookup"><span data-stu-id="7b5a8-208">Name</span></span>|<span data-ttu-id="7b5a8-209">説明</span><span class="sxs-lookup"><span data-stu-id="7b5a8-209">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="7b5a8-210">sysmail_add_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-210">sysmail_add_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)|<span data-ttu-id="7b5a8-211">データベース プリンシパルがデータベース メール プロファイルを使用するための権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-211">Grants permission for a database principal to use a Database Mail profile.</span></span>|  
|[<span data-ttu-id="7b5a8-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-principalprofile-sp-transact-sql)|<span data-ttu-id="7b5a8-213">データベース ユーザーがパブリックまたはプライベートのデータベース メール プロファイルを使用するための権限を削除します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-213">Removes permission for a database user to use a public or private Database Mail profile.</span></span>|  
|[<span data-ttu-id="7b5a8-214">sysmail_help_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-214">sysmail_help_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-principalprofile-sp-transact-sql)|<span data-ttu-id="7b5a8-215">特定のデータベース ユーザーのデータベース メール プロファイル情報を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-215">Lists Database Mail profile information for a given database user.</span></span>|  
|[<span data-ttu-id="7b5a8-216">sysmail_update_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7b5a8-216">sysmail_update_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-principalprofile-sp-transact-sql)|<span data-ttu-id="7b5a8-217">特定のデータベース ユーザーの権限情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-217">Updates the permission information for a given database user.</span></span>|  
  
### <a name="system-state"></a><span data-ttu-id="7b5a8-218">システム状態</span><span class="sxs-lookup"><span data-stu-id="7b5a8-218">System State</span></span>  
  
|<span data-ttu-id="7b5a8-219">名前</span><span class="sxs-lookup"><span data-stu-id="7b5a8-219">Name</span></span>|<span data-ttu-id="7b5a8-220">説明</span><span class="sxs-lookup"><span data-stu-id="7b5a8-220">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="7b5a8-221">sysmail_start_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7b5a8-221">sysmail_start_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|<span data-ttu-id="7b5a8-222">データベース メール外部プログラムおよび関連付けられている SQL Service Broker のキューを開始します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-222">Starts the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="7b5a8-223">sysmail_stop_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7b5a8-223">sysmail_stop_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|<span data-ttu-id="7b5a8-224">データベース メール外部プログラムおよび関連付けられている SQL Service Broker のキューを停止します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-224">Stops the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="7b5a8-225">sysmail_help_status_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7b5a8-225">sysmail_help_status_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|<span data-ttu-id="7b5a8-226">データベース メールが開始されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7b5a8-226">Indicates if Database Mail is started.</span></span>|  
  
##  <a name="additional-references"></a><a name="RelatedContent"></a> <span data-ttu-id="7b5a8-227">その他のリファレンス</span><span class="sxs-lookup"><span data-stu-id="7b5a8-227">Additional References</span></span>  
  
-   [<span data-ttu-id="7b5a8-228">データベース メールのログ記録と監査</span><span class="sxs-lookup"><span data-stu-id="7b5a8-228">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
  

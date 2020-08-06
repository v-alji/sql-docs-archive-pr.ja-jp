---
title: データベース メール | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
ms.assetid: 9e4563dd-4799-4b32-a78a-048ea44a44c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97a5a459fafd80956a2b8d31c27b86169c6fa850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742241"
---
# <a name="database-mail"></a><span data-ttu-id="94e85-102">データベース メール</span><span class="sxs-lookup"><span data-stu-id="94e85-102">Database Mail</span></span>
  <span data-ttu-id="94e85-103">データベース メールは、[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]から電子メールを送信するためのエンタープライズ ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="94e85-103">Database Mail is an enterprise solution for sending e-mail messages from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="94e85-104">データベース メールを使用すると、データベース アプリケーションからユーザーに電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-104">Using Database Mail, your database applications can send e-mail messages to users.</span></span> <span data-ttu-id="94e85-105">メッセージにはクエリ結果を含めることができ、ネットワーク上にあるリソースのファイルも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="94e85-105">The messages can contain query results, and can also include files from any resource on your network.</span></span>  
  
 
  
##  <a name="benefits-of-using-database-mail"></a><a name="Benefits"></a><span data-ttu-id="94e85-106">データベースメールを使用する利点</span><span class="sxs-lookup"><span data-stu-id="94e85-106">Benefits of using Database Mail</span></span>  
 <span data-ttu-id="94e85-107">データベース メールは、信頼性、スケーラビリティ、セキュリティ、およびサポート性を念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="94e85-107">Database Mail is designed for reliability, scalability, security, and supportability.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="94e85-108">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="94e85-108">Reliability</span></span>  
  
-   <span data-ttu-id="94e85-109">データベース メールでは、標準的な簡易メール転送プロトコル (SMTP) を使用してメールを送信します。</span><span class="sxs-lookup"><span data-stu-id="94e85-109">Database Mail uses the standard Simple Mail Transfer Protocol (SMTP) to send mail.</span></span> <span data-ttu-id="94e85-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行するコンピューターに拡張 MAPI クライアントをインストールしなくても、データベース メールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-110">You can use Database Mail without installing an Extended MAPI client on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="94e85-111">プロセスの分離。</span><span class="sxs-lookup"><span data-stu-id="94e85-111">Process isolation.</span></span> <span data-ttu-id="94e85-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への影響を最小限にするために、電子メールを配信するコンポーネントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]外部の別個のプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-112">To minimize the impact on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the component that delivers e-mail runs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in a separate process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="94e85-113">は、外部プロセスが停止または失敗しても、電子メールのキューを続行します。</span><span class="sxs-lookup"><span data-stu-id="94e85-113">will continue to queue e-mail messages even if the external process stops or fails.</span></span> <span data-ttu-id="94e85-114">キューに登録されたメッセージは、外部プロセスまたは SMTP サーバーがオンラインになると送信されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-114">The queued messages will be sent once the outside process or SMTP server comes online.</span></span>  
  
-   <span data-ttu-id="94e85-115">フェールオーバー アカウント。</span><span class="sxs-lookup"><span data-stu-id="94e85-115">Failover accounts.</span></span> <span data-ttu-id="94e85-116">データベース メール プロファイルを使用すると、複数の SMTP サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-116">A Database Mail profile allows you to specify more than one SMTP server.</span></span> <span data-ttu-id="94e85-117">ある SMTP サーバーが使用できない場合は、別の SMTP サーバーにメールを配信できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-117">Should an SMTP server be unavailable, mail can still be delivered to another SMTP server.</span></span>  
  
-   <span data-ttu-id="94e85-118">クラスター サポート。</span><span class="sxs-lookup"><span data-stu-id="94e85-118">Cluster support.</span></span> <span data-ttu-id="94e85-119">データベース メールはクラスターに対応しており、クラスターで完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="94e85-119">Database Mail is cluster-aware and is fully supported on a cluster.</span></span>  
  
### <a name="scalability"></a><span data-ttu-id="94e85-120">スケーラビリティ</span><span class="sxs-lookup"><span data-stu-id="94e85-120">Scalability</span></span>  
  
-   <span data-ttu-id="94e85-121">バックグラウンド配信: データベース メールでは、バックグラウンド配信または非同期配信が提供されています。</span><span class="sxs-lookup"><span data-stu-id="94e85-121">Background Delivery: Database Mail provides background, or asynchronous, delivery.</span></span> <span data-ttu-id="94e85-122">**sp_send_dbmail** を呼び出してメッセージを送信すると、データベース メールによって [!INCLUDE[ssSB](../../includes/sssb-md.md)] のキューに要求が追加されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-122">When you call **sp_send_dbmail** to send a message, Database Mail adds a request to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] queue.</span></span> <span data-ttu-id="94e85-123">ストアド プロシージャが直ちに返されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-123">The stored procedure returns immediately.</span></span> <span data-ttu-id="94e85-124">外部の電子メール コンポーネントが要求を受信し、電子メールを配信します。</span><span class="sxs-lookup"><span data-stu-id="94e85-124">The external e-mail component receives the request and delivers the e-mail.</span></span>  
  
-   <span data-ttu-id="94e85-125">複数のプロファイル: データベース メールを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内に複数のプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-125">Multiple profiles: Database Mail allows you to create multiple profiles within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="94e85-126">オプションで、メッセージを送信するときにデータベース メールが使用するプロファイルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-126">Optionally, you can choose the profile that Database Mail uses when you send a message.</span></span>  
  
-   <span data-ttu-id="94e85-127">複数のアカウント: 各プロファイルに、複数のフェールオーバー アカウントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="94e85-127">Multiple accounts: Each profile can contain multiple failover accounts.</span></span> <span data-ttu-id="94e85-128">別々のアカウントを持つ別々のプロファイルを構成して、複数の電子メール サーバーで電子メールを配信できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-128">You can configure different profiles with different accounts to distribute e-mail across multiple e-mail servers.</span></span>  
  
-   <span data-ttu-id="94e85-129">64 ビット互換性: データベース メールは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の 64 ビット インストールで完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="94e85-129">64-bit compatibility: Database Mail is fully supported on 64-bit installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="security"></a><span data-ttu-id="94e85-130">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="94e85-130">Security</span></span>  
  
-   <span data-ttu-id="94e85-131">既定でオフ: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の外部からのアクセスを縮小するために、データベース メールのストアド プロシージャは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="94e85-131">Off by default: To reduce the surface area of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Database Mail stored procedures are disabled by default.</span></span>  
  
-   <span data-ttu-id="94e85-132">メールのセキュリティ: データベース メールを送信するには、 **msdb** データベースの **DatabaseMailUserRole** データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="94e85-132">Mail Security:To send Database Mail, you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="94e85-133">プロファイルのセキュリティ: データベース メールでは、メール プロファイルにセキュリティが適用されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-133">Profile security: Database Mail enforces security for mail profiles.</span></span> <span data-ttu-id="94e85-134">データベース メール プロファイルにアクセスする **msdb** データベース ユーザーまたはグループを選択することによって、</span><span class="sxs-lookup"><span data-stu-id="94e85-134">You choose the **msdb** database users or groups that have access to a Database Mail profile.</span></span> <span data-ttu-id="94e85-135">特定のユーザーまたは **msdb**のすべてのユーザーにアクセスを許可できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-135">You can grant access to either specific users, or all users in **msdb**.</span></span> <span data-ttu-id="94e85-136">プライベート プロファイルでは、指定した一覧のユーザーにアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-136">A private profile restricts access to a specified list of users.</span></span> <span data-ttu-id="94e85-137">パブリック プロファイルは、データベースのすべてのユーザーがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="94e85-137">A public profile is available to all users in a database.</span></span>  
  
-   <span data-ttu-id="94e85-138">添付ファイル サイズ ガバナー: データベース メールでは、添付ファイル サイズの制限を構成できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-138">Attachment size governor: Database Mail enforces a configurable limit on the attachment file size.</span></span> <span data-ttu-id="94e85-139">この制限は、 [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) ストアド プロシージャを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-139">You can change this limit by using the [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="94e85-140">禁止するファイル拡張子: データベース メールでは、禁止するファイル拡張子の一覧が保持されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-140">Prohibited file extensions: Database Mail maintains a list of prohibited file extensions.</span></span> <span data-ttu-id="94e85-141">ユーザーは、一覧に含まれている拡張子を持つファイルを添付できません。</span><span class="sxs-lookup"><span data-stu-id="94e85-141">Users cannot attach files with an extension that appears in the list.</span></span> <span data-ttu-id="94e85-142">この一覧は、sysmail_configure_sp を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-142">You can change this list by using sysmail_configure_sp.</span></span>  
  
-   <span data-ttu-id="94e85-143">データベース メールは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エンジン サービス アカウントで実行されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-143">Database Mail runs under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Engine service account.</span></span> <span data-ttu-id="94e85-144">フォルダー内のファイルを電子メールに添付するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エンジンのアカウントに、対象ファイルのあるフォルダーへのアクセス権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="94e85-144">To attach a file from a folder to an email, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] engine account should have permissions to access the folder with the file.</span></span>  
  
### <a name="supportability"></a><span data-ttu-id="94e85-145">サポート</span><span class="sxs-lookup"><span data-stu-id="94e85-145">Supportability</span></span>  
  
-   <span data-ttu-id="94e85-146">統合された構成: データベース メールでは、電子メール アカウントの情報が [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)]に保存されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-146">Integrated configuration: Database Mail maintains the information for e-mail accounts within [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="94e85-147">ログ記録。</span><span class="sxs-lookup"><span data-stu-id="94e85-147">Logging.</span></span> <span data-ttu-id="94e85-148">電子メールの利用状況は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Microsoft Windows アプリケーション イベント ログ、および **msdb** データベースのテーブルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-148">Database Mail logs e-mail activity to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Microsoft Windows application event log, and to tables in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="94e85-149">監査: データベース メールでは、送信したメッセージおよび添付ファイルのコピーが **msdb** データベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-149">Auditing: Database Mail keeps copies of messages and attachments sent in the **msdb** database.</span></span> <span data-ttu-id="94e85-150">データベース メールの利用状況の監査や、保存されているメッセージの確認を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="94e85-150">You can easily audit Database Mail usage and review the retained messages.</span></span>  
  
-   <span data-ttu-id="94e85-151">HTML のサポート: データベース メールを使用すると、HTML 形式の電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-151">Support for HTML: Database Mail allows you to send e-mail formatted as HTML.</span></span>  
  

  
##  <a name="database-mail-architecture"></a><a name="VisualElement"></a><span data-ttu-id="94e85-152">データベースメールアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="94e85-152">Database Mail Architecture</span></span>  
 <span data-ttu-id="94e85-153">データベース メールは、Service Broker テクノロジを使用するキュー アーキテクチャを基に設計されています。</span><span class="sxs-lookup"><span data-stu-id="94e85-153">Database Mail is designed on a queued architecture that uses service broker technologies.</span></span> <span data-ttu-id="94e85-154">ユーザーが **sp_send_dbmail**を実行すると、アイテムがメール キューに挿入され、電子メール メッセージを格納したレコードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="94e85-154">When users execute **sp_send_dbmail**, the stored procedure inserts an item into the mail queue and creates a record that contains the e-mail message.</span></span> <span data-ttu-id="94e85-155">メール キューに新しいエントリが挿入されると、データベース メールの外部プロセス (DatabaseMail.exe) が起動します。</span><span class="sxs-lookup"><span data-stu-id="94e85-155">Inserting the new entry in the mail queue starts the external Database Mail process (DatabaseMail.exe).</span></span> <span data-ttu-id="94e85-156">外部プロセスは、電子メール情報を読み取り、電子メール メッセージを適切な電子メール サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="94e85-156">The external process reads the e-mail information and sends the e-mail message to the appropriate e-mail server or servers.</span></span> <span data-ttu-id="94e85-157">また、送信操作の結果の状態キューにアイテムを挿入します。</span><span class="sxs-lookup"><span data-stu-id="94e85-157">The external process inserts an item in the Status queue for the outcome of the send operation.</span></span> <span data-ttu-id="94e85-158">状態キューに新しいエントリが挿入されると、電子メール メッセージの状態を更新する内部ストアド プロシージャが起動します。</span><span class="sxs-lookup"><span data-stu-id="94e85-158">Inserting the new entry in the status queue starts an internal stored procedure that updates the status of the e-mail message.</span></span> <span data-ttu-id="94e85-159">データベース メールは、システム テーブルに送信済み (または未送信) の電子メール メッセージを格納するだけでなく、電子メールの添付ファイルも記録します。</span><span class="sxs-lookup"><span data-stu-id="94e85-159">Besides storing the sent, or unsent, e-mail message, Database Mail also records any e-mail attachments in the system tables.</span></span> <span data-ttu-id="94e85-160">データベース メール ビューには、トラブルシューティングのためにメッセージの状態が表示されます。また、ストアド プロシージャにより、データベース メール キューの管理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="94e85-160">Database Mail views provide the status of messages for troubleshooting, and stored procedures allow for administration of the Database Mail queue.</span></span>  
  
 <span data-ttu-id="94e85-161">![msdb から SMTP メール サーバーへのメッセージ送信](../../database-engine/media/databasemail.gif "msdb から SMTP メール サーバーへのメッセージ送信")</span><span class="sxs-lookup"><span data-stu-id="94e85-161">![msdb sends messages to an SMTP mail server](../../database-engine/media/databasemail.gif "msdb sends messages to an SMTP mail server")</span></span>  
  

  
##  <a name="introduction-to-database-mail-components"></a><a name="ComponentsAndConcepts"></a><span data-ttu-id="94e85-162">データベースメールコンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="94e85-162">Introduction to Database Mail Components</span></span>  
 <span data-ttu-id="94e85-163">データベース メールは次に示す主要なコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="94e85-163">Database Mail consists of the following main components:</span></span>  
  
-   <span data-ttu-id="94e85-164">構成およびセキュリティ関連コンポーネント</span><span class="sxs-lookup"><span data-stu-id="94e85-164">Configuration and security components</span></span>  
  
     <span data-ttu-id="94e85-165">データベース メールは、 **msdb** データベースに構成情報とセキュリティ情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="94e85-165">Database Mail stores configuration and security information in the **msdb** database.</span></span> <span data-ttu-id="94e85-166">構成オブジェクトおよびセキュリティ オブジェクトは、データベース メールで使用されるプロファイルおよびアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="94e85-166">Configuration and security objects create profiles and accounts used by Database Mail.</span></span>  
  
-   <span data-ttu-id="94e85-167">メッセージング関連コンポーネント</span><span class="sxs-lookup"><span data-stu-id="94e85-167">Messaging components</span></span>  
  
     <span data-ttu-id="94e85-168">**msdb** データベースは、データベース メールでの電子メール送信に使用されるメッセージング オブジェクトを保持するメール ホスト データベースとして機能します。</span><span class="sxs-lookup"><span data-stu-id="94e85-168">The **msdb** database acts as the mail-host database that holds the messaging objects that Database Mail uses to send e-mail.</span></span> <span data-ttu-id="94e85-169">これらのオブジェクトには、 **sp_send_dbmail** ストアド プロシージャと、メッセージに関する情報を格納するデータ構造が含まれています。</span><span class="sxs-lookup"><span data-stu-id="94e85-169">These objects include the **sp_send_dbmail** stored procedure and the data structures that hold information about messages.</span></span>  
  
-   <span data-ttu-id="94e85-170">データベース メール実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="94e85-170">Database Mail executable</span></span>  
  
     <span data-ttu-id="94e85-171">データベース メール実行可能ファイルは、 **msdb** データベース内のキューからメッセージを読み取り、電子メール サーバーにメッセージを送信する外部プログラムです。</span><span class="sxs-lookup"><span data-stu-id="94e85-171">The Database Mail executable is an external program that reads from a queue in the **msdb** database and sends messages to e-mail servers.</span></span>  
  
-   <span data-ttu-id="94e85-172">ログおよび監査関連コンポーネント</span><span class="sxs-lookup"><span data-stu-id="94e85-172">Logging and auditing components</span></span>  
  
     <span data-ttu-id="94e85-173">データベース メールは、 **msdb** データベースおよび [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション イベント ログにログ情報を記録します。</span><span class="sxs-lookup"><span data-stu-id="94e85-173">Database Mail records logging information in the **msdb** database and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application event log.</span></span>  
  
 <span data-ttu-id="94e85-174">**データベース メールを使用するためのエージェントの構成:**</span><span class="sxs-lookup"><span data-stu-id="94e85-174">**Configuring Agent to use Database Mail:**</span></span>  
  
 <span data-ttu-id="94e85-175">SQL Server エージェントは、データベース メールを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-175">SQL Server Agent can be configured to use Database Mail.</span></span> <span data-ttu-id="94e85-176">警告通知およびジョブ完了時の自動通知には、この構成が必要です。</span><span class="sxs-lookup"><span data-stu-id="94e85-176">This is required for alert notifications and automatic notification when a job completes.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="94e85-177">また、ジョブ内の個別のジョブ ステップでは、データベース メールを使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成しなくても、電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-177">Individual job steps within a job can also send e-mail without configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail.</span></span> <span data-ttu-id="94e85-178">たとえば、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ジョブ ステップでは、データベース メールを使用してクエリ結果を受信者の一覧に送信できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-178">For example, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] job step can use Database Mail to send the results of a query to a list of recipients.</span></span>  
  
 <span data-ttu-id="94e85-179">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成して、次のような場合に電子メール メッセージが指定のオペレーターに送信されるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-179">You can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send e-mail messages to predefined operators when:</span></span>  
  
-   <span data-ttu-id="94e85-180">警告が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="94e85-180">An alert is triggered.</span></span> <span data-ttu-id="94e85-181">特定のイベントが発生したときに電子メールによる通知を送信するように警告を構成できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-181">Alerts can be configured to send e-mail notification of specific events that occur.</span></span> <span data-ttu-id="94e85-182">たとえば、すぐに対処しなければならない可能性がある特定のデータベース イベントまたはオペレーティング システムの状態がオペレーターに通知されるように、警告を構成できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-182">For example, alerts can be configured to notify an operator of a particular database event or operating system condition that may need immediate action.</span></span> <span data-ttu-id="94e85-183">警告の構成の詳細については、「 [警告](../../ssms/agent/alerts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94e85-183">For more information about configuring alerts, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
-   <span data-ttu-id="94e85-184">データベースのバックアップやレプリケーション イベントなどの定期タスクが成功または失敗したとき。</span><span class="sxs-lookup"><span data-stu-id="94e85-184">A scheduled task, such as a database backup or replication event, succeeds or fails.</span></span> <span data-ttu-id="94e85-185">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント メールを使用して、月末に実行する処理でエラーが発生した場合にオペレーターに通知できます。</span><span class="sxs-lookup"><span data-stu-id="94e85-185">For example, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail to notify operators if an error occurs during processing at the end of a month.</span></span>  
  
 
  
##  <a name="database-mail-component-topics"></a><a name="RelatedContent"></a><span data-ttu-id="94e85-186">データベースメールコンポーネントに関するトピック</span><span class="sxs-lookup"><span data-stu-id="94e85-186">Database Mail Component Topics</span></span>  
  
-   [<span data-ttu-id="94e85-187">データベース メール構成オブジェクト</span><span class="sxs-lookup"><span data-stu-id="94e85-187">Database Mail Configuration Objects</span></span>](database-mail-configuration-objects.md)  
  
-   [<span data-ttu-id="94e85-188">データベース メール メッセージング オブジェクト</span><span class="sxs-lookup"><span data-stu-id="94e85-188">Database Mail Messaging Objects</span></span>](database-mail-messaging-objects.md)  
  
-   [<span data-ttu-id="94e85-189">データベース メール外部プログラム</span><span class="sxs-lookup"><span data-stu-id="94e85-189">Database Mail External Program</span></span>](database-mail-external-program.md)  
  
-   [<span data-ttu-id="94e85-190">データベース メールのログ記録と監査</span><span class="sxs-lookup"><span data-stu-id="94e85-190">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
-   [<span data-ttu-id="94e85-191">データベース メールを使用するように SQL Server エージェント メールを構成する</span><span class="sxs-lookup"><span data-stu-id="94e85-191">Configure SQL Server Agent Mail to Use Database Mail</span></span>](configure-sql-server-agent-mail-to-use-database-mail.md)  
  

  
  

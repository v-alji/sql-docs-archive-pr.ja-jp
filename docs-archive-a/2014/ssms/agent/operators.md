---
title: オペレーター | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- operators (users) [Database Engine]
- fail-safe operator [SQL Server]
- aliases [SQL Server], operators
- SQL Server Agent alerts, operators
- contact information [SQL Server Agent]
- net send [SQL Server]
- e-mail [SQL Server], SQL Server Agent operators
- pager notifications [SQL Server Agent]
- mail [SQL Server], SQL Server Agent operators
- operators (users) [Database Engine], defining
- jobs [SQL Server Agent], operators
- alerts [SQL Server], operators
ms.assetid: 38e8488f-2669-4cea-b9c3-5f394a663678
author: stevestein
ms.author: sstein
ms.openlocfilehash: d141a2db9a69603701200bc50dcac57ef402968a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720792"
---
# <a name="operators"></a><span data-ttu-id="004a7-102">オペレーター</span><span class="sxs-lookup"><span data-stu-id="004a7-102">Operators</span></span>
  <span data-ttu-id="004a7-103">オペレーターとは、ジョブの完了時や警告の発生時に電子通知を受け取ることのできる人またはグループの別名です。</span><span class="sxs-lookup"><span data-stu-id="004a7-103">Operators are aliases for people or groups that can receive electronic notification when jobs have completed or alerts have been raised.</span></span> <span data-ttu-id="004a7-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスでは、オペレーターを経由した管理者の通知がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="004a7-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service supports the notification of administrators through operators.</span></span> <span data-ttu-id="004a7-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの通知機能および監視機能はオペレーターが有効にします。</span><span class="sxs-lookup"><span data-stu-id="004a7-105">Operators enable notification and monitoring capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="operator-attributes-and-concepts"></a><span data-ttu-id="004a7-106">オペレーターの属性と概念</span><span class="sxs-lookup"><span data-stu-id="004a7-106">Operator Attributes and Concepts</span></span>  
 <span data-ttu-id="004a7-107">オペレーターの主な属性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="004a7-107">The primary attributes of an operator are:</span></span>  
  
-   <span data-ttu-id="004a7-108">オペレーター名</span><span class="sxs-lookup"><span data-stu-id="004a7-108">Operator name</span></span>  
  
-   <span data-ttu-id="004a7-109">連絡先情報</span><span class="sxs-lookup"><span data-stu-id="004a7-109">Contact information</span></span>  
  
### <a name="naming-an-operator"></a><span data-ttu-id="004a7-110">オペレーターの名前付け</span><span class="sxs-lookup"><span data-stu-id="004a7-110">Naming an Operator</span></span>  
 <span data-ttu-id="004a7-111">すべてのオペレーターに名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-111">Every operator must have a name.</span></span> <span data-ttu-id="004a7-112">オペレーター名は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意である必要があります。使用できる文字数は最大 **128** 文字です。</span><span class="sxs-lookup"><span data-stu-id="004a7-112">Operator names must be unique within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and can be no longer than **128** characters.</span></span>  
  
### <a name="contact-information"></a><span data-ttu-id="004a7-113">連絡先情報</span><span class="sxs-lookup"><span data-stu-id="004a7-113">Contact Information</span></span>  
 <span data-ttu-id="004a7-114">オペレーターの連絡先情報では、オペレーターに通知する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="004a7-114">An operator's contact information defines how the operator is notified.</span></span> <span data-ttu-id="004a7-115">オペレーターへの通知には、電子メール、ポケットベル、または **net send** コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="004a7-115">Operators can be notified by e-mail, pager, or through the **net send** command:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="004a7-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のバージョンでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからポケットベル オプションと **net send** オプションが削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="004a7-116">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="004a7-117">新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="004a7-117">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="004a7-118">**電子メールによる通知**</span><span class="sxs-lookup"><span data-stu-id="004a7-118">**E-mail notification**</span></span>  
  
     <span data-ttu-id="004a7-119">電子メールによる通知では、電子メール メッセージがオペレーターに送信されます。</span><span class="sxs-lookup"><span data-stu-id="004a7-119">E-mail notification sends an e-mail message to the operator.</span></span> <span data-ttu-id="004a7-120">電子メールによる通知を使用するには、オペレーターの電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="004a7-120">For e-mail notification, you provide the e-mail address for the operator.</span></span>  
  
-   <span data-ttu-id="004a7-121">**ポケットベルによる通知**</span><span class="sxs-lookup"><span data-stu-id="004a7-121">**Pager notification**</span></span>  
  
     <span data-ttu-id="004a7-122">ポケットベル機能は、電子メールによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="004a7-122">Paging is implemented by e-mail.</span></span> <span data-ttu-id="004a7-123">ポケットベルによる通知を使用するには、オペレーターがポケットベルのメッセージを受信する電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="004a7-123">For pager notification, you provide the e-mail address where the operator receives pager messages.</span></span> <span data-ttu-id="004a7-124">ポケットベルによる通知を設定するには、受信メールを処理してポケットベル メッセージに変換するソフトウェアをメール サーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-124">To set up pager notification, you must install software on the mail server that processes inbound mail and converts it to a pager message.</span></span> <span data-ttu-id="004a7-125">このソフトウェアは、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="004a7-125">The software can take one of several approaches, including:</span></span>  
  
    -   <span data-ttu-id="004a7-126">ポケットベル プロバイダーのサイトにあるリモート メール サーバーにメールを転送します。</span><span class="sxs-lookup"><span data-stu-id="004a7-126">Forwarding the mail to a remote mail server at the site of the pager provider.</span></span>  
  
         <span data-ttu-id="004a7-127">必要なソフトウェアは、一般にローカル メール システムの一部として使用できますが、ポケットベル プロバイダーがこのサービスを提供している必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-127">The pager provider must offer this service, although the software required is generally available as part of the local mail system.</span></span> <span data-ttu-id="004a7-128">詳細については、ポケットベルのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="004a7-128">For more information, see your pager documentation.</span></span>  
  
    -   <span data-ttu-id="004a7-129">インターネット経由でポケットベル プロバイダーのサイトにある電子メール サーバーに電子メールをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="004a7-129">Routing the e-mail by way of the Internet to an e-mail server at the pager provider's site.</span></span>  
  
         <span data-ttu-id="004a7-130">これは第 1 の方法の変形です。</span><span class="sxs-lookup"><span data-stu-id="004a7-130">This is a variation on the first approach.</span></span>  
  
    -   <span data-ttu-id="004a7-131">接続されているモデムを使用して、着信電子メールを処理し、ポケットベルにダイヤルします。</span><span class="sxs-lookup"><span data-stu-id="004a7-131">Processing the inbound e-mail and dialing the pager by using an attached modem.</span></span>  
  
         <span data-ttu-id="004a7-132">このソフトウェアは、ポケットベル サービスのプロバイダーがライセンスを持っています。</span><span class="sxs-lookup"><span data-stu-id="004a7-132">This software is proprietary to pager service providers.</span></span> <span data-ttu-id="004a7-133">このソフトウェアは、ポケットベルの番号として電子メール アドレス情報の全部または一部を解釈するか、変換テーブルで電子メールの名前をポケットベル番号と照合することによって、定期的に受信トレイを処理する電子メール クライアントとして動作します。</span><span class="sxs-lookup"><span data-stu-id="004a7-133">The software acts as a e-mail client that periodically processes its inbox either by interpreting all or part of the e-mail address information as a pager number, or by matching the e-mail name to a pager number in a translation table.</span></span>  
  
         <span data-ttu-id="004a7-134">すべてのオペレーターが同じポケットベル プロバイダーを利用している場合は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、ポケットベル電子メール間システムが要求する特別な電子メール書式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="004a7-134">If all of the operators share a pager provider, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to specify any special e-mail formatting that is required by the pager-to-e-mail system.</span></span> <span data-ttu-id="004a7-135">この特別な書式は、プレフィックスまたはサフィックスの形式で、電子メールの次の行に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="004a7-135">The special formatting can be a prefix or a suffix and can be included in the following lines of the e-mail:</span></span>  
  
         <span data-ttu-id="004a7-136">**Subject:**</span><span class="sxs-lookup"><span data-stu-id="004a7-136">**Subject:**</span></span>  
  
         <span data-ttu-id="004a7-137">**Cc**:</span><span class="sxs-lookup"><span data-stu-id="004a7-137">**Cc**:</span></span>  
  
         <span data-ttu-id="004a7-138">**[宛先]** :</span><span class="sxs-lookup"><span data-stu-id="004a7-138">**To**:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="004a7-139">容量の小さい英数字のポケットベル システムを使用している場合は、エラーのテキストをポケットベルの通知から除外することで、送信されるテキストを短縮できます。</span><span class="sxs-lookup"><span data-stu-id="004a7-139">If you use a low-capacity alphanumeric paging system, you can shorten the text that is sent by excluding the error text from the pager notification.</span></span> <span data-ttu-id="004a7-140">容量の小さい英数字のポケットベル システムには、1 ページあたりのバイト数が 64 バイトに制限されているものなどがあります。</span><span class="sxs-lookup"><span data-stu-id="004a7-140">An example of a low-capacity alphanumeric paging system is one that is limited to 64 characters per page.</span></span>  
  
-   <span data-ttu-id="004a7-141">**net sendnotification**</span><span class="sxs-lookup"><span data-stu-id="004a7-141">**net sendnotification**</span></span>  
  
     <span data-ttu-id="004a7-142">この方法では、 **net send** コマンドを使用して、オペレーターにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="004a7-142">This sends a message to the operator by means of the **net send** command.</span></span> <span data-ttu-id="004a7-143">**net send**では、ネットワーク メッセージの受信者 (コンピューターまたはユーザー) を指定します。</span><span class="sxs-lookup"><span data-stu-id="004a7-143">For **net send**, specify the recipient (computer or user) of a network message.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="004a7-144">**net send** コマンドでは、Microsoft Windows Messenger を使用します。</span><span class="sxs-lookup"><span data-stu-id="004a7-144">The **net send** command uses Microsoft Windows Messenger.</span></span> <span data-ttu-id="004a7-145">警告を正しく送信するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターと、オペレーターが使用しているコンピューターの両方で、このサービスを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-145">To successfully send alerts, this service must be running on both the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running and the computer that the operator uses.</span></span>  
  
## <a name="alerting-and-fail-safe-operators"></a><span data-ttu-id="004a7-146">警告通知先オペレーターと緊急時のオペレーター</span><span class="sxs-lookup"><span data-stu-id="004a7-146">Alerting and Fail-Safe Operators</span></span>  
 <span data-ttu-id="004a7-147">警告に応答して通知を受けるオペレーターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="004a7-147">You can choose which operators are to be notified in response to an alert.</span></span> <span data-ttu-id="004a7-148">警告のスケジュールを設定して、オペレーターへの通知を順番に割り当てることも可能です。</span><span class="sxs-lookup"><span data-stu-id="004a7-148">For example, you can assign rotating responsibilities for operator notification by scheduling alerts.</span></span> <span data-ttu-id="004a7-149">たとえば、月曜日、水曜日、金曜日に発生した警告は管理者 A に通知し、火曜日、木曜日、土曜日に発生した警告は管理者 B に通知することができます。</span><span class="sxs-lookup"><span data-stu-id="004a7-149">For example, Individual A is notified of alerts that occur on Monday, Wednesday, or Friday, and Individual B is notified of alerts that occur on Tuesday, Thursday, or Saturday.</span></span>  
  
 <span data-ttu-id="004a7-150">緊急時のオペレーターは、指定されているオペレーターに対するすべてのポケットベルによる通知が失敗した後で警告の通知を受けます。</span><span class="sxs-lookup"><span data-stu-id="004a7-150">The fail-safe operator receives an alert notification after all pager notifications to the designated operators have failed.</span></span> <span data-ttu-id="004a7-151">たとえば、ポケットベルによる通知のために 3 人のオペレーターを定義し、そのいずれのオペレーターにもポケットベルで通知できなかった場合、緊急時のオペレーターが通知を受けます。</span><span class="sxs-lookup"><span data-stu-id="004a7-151">For example, if you have defined three operators for pager notifications and none of the designated operators can be paged, the fail-safe operator is notified.</span></span>  
  
 <span data-ttu-id="004a7-152">緊急時のオペレーターは、次の場合に通知を受けます。</span><span class="sxs-lookup"><span data-stu-id="004a7-152">The fail-safe operator is notified when:</span></span>  
  
-   <span data-ttu-id="004a7-153">警告を管理するオペレーターにポケットベルで通知できなかった場合</span><span class="sxs-lookup"><span data-stu-id="004a7-153">The operators responsible for the alert could not be paged.</span></span>  
  
     <span data-ttu-id="004a7-154">プライマリ オペレーターに通知できなかった理由には、ポケットベル アドレスが誤っているか、オペレーターが非番であるなどがあります。</span><span class="sxs-lookup"><span data-stu-id="004a7-154">Reasons for failure to reach primary operators include incorrect pager addresses and off-duty operators.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="004a7-155">エージェントが **msdb** データベースのシステム テーブルにアクセスできない場合</span><span class="sxs-lookup"><span data-stu-id="004a7-155">Agent cannot access system tables in the **msdb** database.</span></span>  
  
     <span data-ttu-id="004a7-156">**sysnotifications** システム テーブルは、警告に関してオペレーターが担う責任を指定します。</span><span class="sxs-lookup"><span data-stu-id="004a7-156">The **sysnotifications** system table specifies operator responsibilities for alerts.</span></span>  
  
 <span data-ttu-id="004a7-157">緊急時のオペレーターは、安全のための機能です。</span><span class="sxs-lookup"><span data-stu-id="004a7-157">The fail-safe operator is a security feature.</span></span> <span data-ttu-id="004a7-158">緊急時の職務を他のオペレーターに割り当て直すか、または緊急時の割り当てを削除しなければ、緊急時の職務に割り当てられたオペレーターを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="004a7-158">You cannot delete the operator assigned to fail-safe duty without reassigning fail-safe duty to another operator, or deleting the fail-safe assignment altogether.</span></span>  
  
## <a name="notifying-an-operator"></a><span data-ttu-id="004a7-159">オペレーターへの通知</span><span class="sxs-lookup"><span data-stu-id="004a7-159">Notifying an Operator</span></span>  
 <span data-ttu-id="004a7-160">オペレーターに通知するには、次のうち 1 つまたは複数をセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-160">You must set up one or more of the following in order to notify an operator:</span></span>  
  
-   <span data-ttu-id="004a7-161">データベース メール機能を使用して電子メールを送信するには、SMTP をサポートしている電子メール サーバーにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-161">To send e-mail with Database Mail functionality, you must have access to an e-mail server that supports SMTP.</span></span>  
  
-   <span data-ttu-id="004a7-162">ポケットベル通知機能を使用する場合は、サードパーティによるポケットベルとメール間のソフトウェアとハードウェアが必要です。</span><span class="sxs-lookup"><span data-stu-id="004a7-162">For paging, you must have third-party pager-to-e-mail software and/or hardware.</span></span>  
  
-   <span data-ttu-id="004a7-163">**net send**を使用するには、指定のコンピューターにオペレーターがログオンしており、そのコンピューターで Windows Messenger からのメッセージの受信が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="004a7-163">To use **net send**, the operator must be logged on to the specified computer, and the specified computer must allow messages from Windows Messenger.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="004a7-164">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="004a7-164">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="004a7-165">**タスク**</span><span class="sxs-lookup"><span data-stu-id="004a7-165">**Tasks**</span></span>|<span data-ttu-id="004a7-166">**トピック**</span><span class="sxs-lookup"><span data-stu-id="004a7-166">**Topic**</span></span>|  
|<span data-ttu-id="004a7-167">オペレーターの作成に関連するタスク</span><span class="sxs-lookup"><span data-stu-id="004a7-167">Tasks related to creating an operator</span></span>|[<span data-ttu-id="004a7-168">オペレーターの作成</span><span class="sxs-lookup"><span data-stu-id="004a7-168">Create an Operator</span></span>](create-an-operator.md)<br /><br /> [<span data-ttu-id="004a7-169">Designate a Fail-Safe Operator</span><span class="sxs-lookup"><span data-stu-id="004a7-169">Designate a Fail-Safe Operator</span></span>](designate-a-fail-safe-operator.md)|  
|<span data-ttu-id="004a7-170">警告の割り当てに関連するタスク</span><span class="sxs-lookup"><span data-stu-id="004a7-170">Tasks related to assigning alerts</span></span>|[<span data-ttu-id="004a7-171">オペレーターへの警告の割り当て</span><span class="sxs-lookup"><span data-stu-id="004a7-171">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)<br /><br /> [<span data-ttu-id="004a7-172">警告への応答の定義 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="004a7-172">Define the Response to an Alert &#40;SQL Server Management Studio&#41;</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)<br /><br /> [<span data-ttu-id="004a7-173">sp_add_notification &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="004a7-173">sp_add_notification &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)<br /><br /> [<span data-ttu-id="004a7-174">オペレーターへの警告の割り当て</span><span class="sxs-lookup"><span data-stu-id="004a7-174">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="004a7-175">参照</span><span class="sxs-lookup"><span data-stu-id="004a7-175">See Also</span></span>  
 [<span data-ttu-id="004a7-176">データベース メール</span><span class="sxs-lookup"><span data-stu-id="004a7-176">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  

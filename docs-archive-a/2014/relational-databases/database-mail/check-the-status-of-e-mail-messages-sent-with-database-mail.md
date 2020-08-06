---
title: データベース メールから送信された電子メール メッセージの状態の確認 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1642c456cd64484dede64f8127ff2f979f2242e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645634"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a><span data-ttu-id="21c65-102">データベース メールから送信された電子メール メッセージの状態の確認</span><span class="sxs-lookup"><span data-stu-id="21c65-102">Check the Status of E-Mail Messages Sent With Database Mail</span></span>
  <span data-ttu-id="21c65-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベース メール経由で送信された電子メール メッセージの状態を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21c65-103">This topic describes how to check the status of the e-mail message sent using Database Mail  in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="21c65-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="21c65-104">**Before you begin:**</span></span>  
  
-   <span data-ttu-id="21c65-105">**データベース メールを使用して送信された電子メールの状態を表示するには、** を使用[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="21c65-105">**To view the status of the e-mail sent using Database Mail, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21c65-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="21c65-106">Before You Begin</span></span>  
 <span data-ttu-id="21c65-107">データベース メールは、送信する電子メール メッセージのコピーを保持し、 **msdb**データベースの **sysmail_allitems**、 **sysmail_sentitems**、 **sysmail_unsentitems** 、および **sysmail_faileditems** の各ビューに表示します。</span><span class="sxs-lookup"><span data-stu-id="21c65-107">Database Mail keeps copies of outgoing e-mail messages and displays them in the **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems**, **sysmail_faileditems** views of the **msdb** database.</span></span> <span data-ttu-id="21c65-108">データベース メール外部プログラムは、利用状況をログに記録し、Windows アプリケーション イベント ログや **msdb** データベースの **sysmail_event_log** ビューでそのログを表示します。</span><span class="sxs-lookup"><span data-stu-id="21c65-108">The Database Mail external program logs activity and displays the log through the Windows Application Event Log and the **sysmail_event_log** view in the **msdb** database.</span></span> <span data-ttu-id="21c65-109">電子メール メッセージの状態を確認するには、このビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="21c65-109">To check the status of an e-mail message, run a query against this view.</span></span> <span data-ttu-id="21c65-110">電子メール メッセージの状態は、 **sent**、 **unsent**、 **retrying**、および **failed**のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="21c65-110">E-mail messages have one of four possible statuses: **sent**, **unsent**, **retrying**, and **failed**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="21c65-111">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="21c65-111">Using Transact-SQL</span></span>  
 <span data-ttu-id="21c65-112">**データベース メールを使用して送信された電子メールの状態を表示するには**</span><span class="sxs-lookup"><span data-stu-id="21c65-112">**To view the status of the e-mail sent using Database Mail**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21c65-113">この手順の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21c65-113">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="21c65-114">**sysmail_allitems** テーブルから選択して、 **mailitem_id** または **sent_status**で対象のメッセージを指定します。</span><span class="sxs-lookup"><span data-stu-id="21c65-114">Select from the **sysmail_allitems** table, specifying the messages of interest by **mailitem_id** or **sent_status**.</span></span>  
  
2.  <span data-ttu-id="21c65-115">その電子メール メッセージについてデータベース メール外部プログラムから返される状態を確認するには、次のセクションに示すように、 **mailitem_id** 列で **sysmail_allitems** と **sysmail_event_log** ビューを結合します。</span><span class="sxs-lookup"><span data-stu-id="21c65-115">To check the status returned from the external program for the e-mail messages, join **sysmail_allitems** to **sysmail_event_log** view on the **mailitem_id** column, as shown in the following section.</span></span>  
  
     <span data-ttu-id="21c65-116">データベース メール外部プログラムの既定では、正常に送信されたメッセージについての情報がログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="21c65-116">By default, the external program does not log information about messages that were successfully sent.</span></span> <span data-ttu-id="21c65-117">すべてのメッセージをログに記録するには、 **データベース メール構成ウィザード** の **[システム パラメーターの構成]** ページを使用して、ログのレベルを詳細に設定します。</span><span class="sxs-lookup"><span data-stu-id="21c65-117">To log all messages, set the logging level to verbose using the **Configure System Parameters** page of the **Database Mail Configuration Wizard.**</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="21c65-118">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="21c65-118">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="21c65-119">次の例では、外部プログラムが正常に送信できなかった、 `danw` への電子メール メッセージに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="21c65-119">The following example lists information about any e-mail messages sent to `danw` that the external program could not send successfully.</span></span> <span data-ttu-id="21c65-120">このステートメントは、件名、外部プログラムでメッセージの送信に失敗した日時、およびデータベース メール ログに記録されているエラー メッセージの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="21c65-120">The statement lists the subject, the date and time that the external program failed to send the message, and the error message from the Database Mail log.</span></span>  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="21c65-121">参照</span><span class="sxs-lookup"><span data-stu-id="21c65-121">See Also</span></span>  
 [<span data-ttu-id="21c65-122">データベース メールのログ記録と監査</span><span class="sxs-lookup"><span data-stu-id="21c65-122">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  

---
title: データベース メールのログ記録と監査 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- Database Mail [SQL Server], auditing
- logs [Database Mail]
- audits [SQL Server], Database Mail
- Database Mail [SQL Server], logging
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6267389f187b955982ec1c18c411f703b4562f3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742253"
---
# <a name="database-mail-log-and-audits"></a><span data-ttu-id="c764a-102">データベース メールのログ記録と監査</span><span class="sxs-lookup"><span data-stu-id="c764a-102">Database Mail Log and Audits</span></span>
  <span data-ttu-id="c764a-103">データベース メールのログ記録機能は、問題の特定および修正の手段を提供する目的でデザインされました。</span><span class="sxs-lookup"><span data-stu-id="c764a-103">The Database Mail logging functionality is designed to provide a way to isolate and correct problems.</span></span> <span data-ttu-id="c764a-104">データベース メールは、 **msdb** データベースにログ情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="c764a-104">Database Mail stores the log information in the **msdb** database.</span></span> <span data-ttu-id="c764a-105">データベース メールの電子メールの内容、電子メールの状態、エラーなどの受信メッセージがデータベース メールによってログに記録され、トラブルシューティングや監査のために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c764a-105">Information about Database Mail e-mail content, status of e-mails, and any messages received, such as errors  are logged by Database Mail and can be used for troubleshooting and auditing purposes.</span></span>  
  
## <a name="database-mail-logs"></a><span data-ttu-id="c764a-106">データベース メールのログ</span><span class="sxs-lookup"><span data-stu-id="c764a-106">Database Mail Logs</span></span>  
 <span data-ttu-id="c764a-107">**データベース メール外部プログラム** の [msdb](database-mail-external-program.md)データベース ログ情報の表。</span><span class="sxs-lookup"><span data-stu-id="c764a-107">Tables in the **msdb** database log information from the [Database Mail External Program](database-mail-external-program.md).</span></span> <span data-ttu-id="c764a-108">[データベース メール ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) は、トラブルシューティング用のテーブルを公開します。</span><span class="sxs-lookup"><span data-stu-id="c764a-108">[Database Mail Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) expose the tables for troubleshooting purposes.</span></span> <span data-ttu-id="c764a-109">Service Broker によって外部プログラムをアクティブにできない場合、外部プログラムでネットワーク エラーが発生した場合、簡易メール転送プロトコル (SMTP) サーバーで電子メール メッセージが拒否された場合などに、エラーが [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c764a-109">Errors appear in the [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) view if Service Broker cannot activate the external program, if the external program encounters networking errors or if the Simple Mail Transport Protocol (SMTP) server refuses an e-mail message.</span></span> <span data-ttu-id="c764a-110">外部プログラムが **msdb** テーブルにログを記録できない場合は、Windows アプリケーション イベント ログにエラーが記録されます。</span><span class="sxs-lookup"><span data-stu-id="c764a-110">In the event that the external program cannot log to the **msdb** tables, the program logs errors to the Windows application event log.</span></span>  
  
 <span data-ttu-id="c764a-111">**msdb** データベースの内部テーブルには、データベース メールから送信された電子メール メッセージと添付ファイルが各メッセージの現在の状態と共に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c764a-111">Internal tables in the **msdb** database contain the e-mail messages and attachments sent from Database Mail, together with the current status of each message.</span></span> <span data-ttu-id="c764a-112">メッセージが処理されるたびに、データベース メールによってこれらのテーブルが更新されます。</span><span class="sxs-lookup"><span data-stu-id="c764a-112">Database Mail updates these tables as each message is processed.</span></span>  
  
## <a name="database-mail-auditing-tasks"></a><span data-ttu-id="c764a-113">データベース メールの監査タスク</span><span class="sxs-lookup"><span data-stu-id="c764a-113">Database Mail Auditing tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c764a-114">**データベース メールのログの確認と管理**</span><span class="sxs-lookup"><span data-stu-id="c764a-114">**Reviewing and managing Database Mail logs**</span></span>|<span data-ttu-id="c764a-115">**トピックへのリンク**</span><span class="sxs-lookup"><span data-stu-id="c764a-115">**Link to Topic**</span></span>|  
|<span data-ttu-id="c764a-116">個々のメッセージの配信状態の確認</span><span class="sxs-lookup"><span data-stu-id="c764a-116">Check the delivery status of an individual message</span></span>|[<span data-ttu-id="c764a-117">データベース メールから送信された電子メール メッセージの状態の確認</span><span class="sxs-lookup"><span data-stu-id="c764a-117">Check the Status of E-Mail Messages Sent With Database Mail</span></span>](check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|<span data-ttu-id="c764a-118">データベース メールのメッセージ、添付ファイル、およびログ エントリのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="c764a-118">Clean up Database Mail messages, attachments, and log entries</span></span>|[<span data-ttu-id="c764a-119">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c764a-119">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)<br /><br /> [<span data-ttu-id="c764a-120">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c764a-120">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|  
|<span data-ttu-id="c764a-121">データベース メールのメッセージとログのアーカイブ</span><span class="sxs-lookup"><span data-stu-id="c764a-121">Archive the Database Email Messages and Logs</span></span>|[<span data-ttu-id="c764a-122">データベース メール メッセージやイベント ログをアーカイブする SQL Server エージェント ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="c764a-122">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>](create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c764a-123">参照</span><span class="sxs-lookup"><span data-stu-id="c764a-123">See Also</span></span>  
 [<span data-ttu-id="c764a-124">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="c764a-124">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](../performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  

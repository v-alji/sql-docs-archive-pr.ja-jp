---
title: '[SQL Server エージェント エラー ログの再利用] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea9a723695c6993f4f07897f49d8014a86ce78b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714998"
---
# <a name="sql-server-agent-error-log"></a><span data-ttu-id="29e0f-102">SQL Server エージェント エラー ログ</span><span class="sxs-lookup"><span data-stu-id="29e0f-102">SQL Server Agent Error Log</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="29e0f-103">エージェントでは、既定で、警告とエラーを記録するエラー ログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="29e0f-103">Agent creates an error log that records warnings and errors by default.</span></span> <span data-ttu-id="29e0f-104">次の警告とエラーがログに表示されます。</span><span class="sxs-lookup"><span data-stu-id="29e0f-104">The following warnings and errors are displayed in the log:</span></span>  
  
-   <span data-ttu-id="29e0f-105">"ジョブの \<*job_name*> 実行中にジョブが削除されました。" などの潜在的な問題に関する情報を提供する警告メッセージ。</span><span class="sxs-lookup"><span data-stu-id="29e0f-105">Warning messages that provide information about potential problems, such as "Job \<*job_name*> was deleted while it was running."</span></span>  
  
-   <span data-ttu-id="29e0f-106">エラー メッセージ。"メール セッションを開始できません。" など、通常はシステム管理者による介入が必要となります。</span><span class="sxs-lookup"><span data-stu-id="29e0f-106">Error messages that usually require intervention by a system administrator, such as "Unable to start mail session."</span></span> <span data-ttu-id="29e0f-107">エラー メッセージは、 **net send**によって、特定のユーザーまたはコンピューターに送信可能です。</span><span class="sxs-lookup"><span data-stu-id="29e0f-107">Error messages can be sent to a specific user or computer by **net send**.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="29e0f-108">では、最大 9 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログが保持されます。</span><span class="sxs-lookup"><span data-stu-id="29e0f-108">maintains up to nine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs.</span></span> <span data-ttu-id="29e0f-109">アーカイブ処理された各ログには、作成順を示す拡張子が付けられます。</span><span class="sxs-lookup"><span data-stu-id="29e0f-109">Each archived log has an extension that indicates the relative age of the log.</span></span> <span data-ttu-id="29e0f-110">たとえば、拡張子 .1 は、それが最も最近アーカイブ処理されたエラー ログであり、拡張子 .9 は、それが一番古いエラー ログであることを示します。</span><span class="sxs-lookup"><span data-stu-id="29e0f-110">For example, an extension of .1 indicates the newest archived error log and an extension of .9 indicates the oldest archived error log.</span></span>  
  
 <span data-ttu-id="29e0f-111">実行トレース メッセージで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログがいっぱいになる可能性があるので、既定では、これらのメッセージはエラー ログに書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="29e0f-111">By default, execution trace messages are not written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log, because they can fill it.</span></span> <span data-ttu-id="29e0f-112">エラー ログがいっぱいになった場合、より困難なエラーを選別し分析する能力が低下します。</span><span class="sxs-lookup"><span data-stu-id="29e0f-112">When the error log is full, your ability to select and analyze more difficult errors is reduced.</span></span> <span data-ttu-id="29e0f-113">ログによってサーバーの処理負荷が増加するので、実行トレース メッセージをエラー ログに記録する場合は、その価値を十分に検討することが重要です。</span><span class="sxs-lookup"><span data-stu-id="29e0f-113">Because the log adds to the server's processing load, it is important to consider carefully what value you obtain by capturing execution trace messages to the error log.</span></span> <span data-ttu-id="29e0f-114">一般に、すべてのメッセージを記録するのは、特定の問題をデバッグするときのみに限定します。</span><span class="sxs-lookup"><span data-stu-id="29e0f-114">Generally, it is best to capture all messages only when you are debugging a specific problem.</span></span>  
  
 <span data-ttu-id="29e0f-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが停止している間に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログの場所を変更できます。</span><span class="sxs-lookup"><span data-stu-id="29e0f-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is stopped, you can modify the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log.</span></span> <span data-ttu-id="29e0f-116">エラー ログが空の場合は、ログを開くことができません。</span><span class="sxs-lookup"><span data-stu-id="29e0f-116">When the error log is empty, the log cannot be opened.</span></span> <span data-ttu-id="29e0f-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止しなくても [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ログをいつでも使い回すことができます。</span><span class="sxs-lookup"><span data-stu-id="29e0f-117">You can cycle the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent log at any time without stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="29e0f-118">**SQL Server エージェントのエラー ログを表示するには**</span><span class="sxs-lookup"><span data-stu-id="29e0f-118">**To view the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="29e0f-119">View SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="29e0f-119">View SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 <span data-ttu-id="29e0f-120">**SQL Server エージェント エラー ログの名前を変更するには**</span><span class="sxs-lookup"><span data-stu-id="29e0f-120">**To rename a SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="29e0f-121">SQL Server エージェントのエラー ログの名前の変更 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="29e0f-121">Rename a SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 <span data-ttu-id="29e0f-122">**SQL Server エージェントのエラー メッセージを送信するには**</span><span class="sxs-lookup"><span data-stu-id="29e0f-122">**To send SQL Server Agent error messages**</span></span>  
  
-   [<span data-ttu-id="29e0f-123">Send SQL Server Agent Error Messages</span><span class="sxs-lookup"><span data-stu-id="29e0f-123">Send SQL Server Agent Error Messages</span></span>](send-sql-server-agent-error-messages.md)  
  
 <span data-ttu-id="29e0f-124">**SQL Server エージェントのエラー ログに実行トレース メッセージを書き込むには**</span><span class="sxs-lookup"><span data-stu-id="29e0f-124">**To write execution trace messages to the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="29e0f-125">SQL Server エージェント エラー ログへの実行トレース メッセージの書き込み (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="29e0f-125">Write Execution Trace Messages to the SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  

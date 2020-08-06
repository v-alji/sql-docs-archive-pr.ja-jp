---
title: エラーログの監視 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a47891599dbe735bd437f5239c73bfd34c422ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640301"
---
# <a name="monitoring-the-error-logs"></a><span data-ttu-id="17cf1-102">エラー ログの監視</span><span class="sxs-lookup"><span data-stu-id="17cf1-102">Monitoring the Error Logs</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="17cf1-103">は、特定のシステム イベントとユーザー定義イベントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログに記録します。</span><span class="sxs-lookup"><span data-stu-id="17cf1-103">logs certain system events and user-defined events to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span> <span data-ttu-id="17cf1-104">両方のログで、記録されるすべてのイベントのタイムスタンプが自動的に記録されます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-104">Both logs automatically timestamp all recorded events.</span></span> <span data-ttu-id="17cf1-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログの情報を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関連する問題のトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-105">Use the information in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to troubleshoot problems related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="17cf1-106">Windows アプリケーション ログでは、Windows オペレーティング システムで発生したイベントと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] や [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでのイベントの全体像が示されます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-106">The Windows application log provides an overall picture of events that occur on the Windows operating system, as well as events in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="17cf1-107">Windows イベント ビューアーを使用すると、Windows アプリケーション ログを表示して情報をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-107">Use the Windows Event Viewer to view the Windows application log and to filter the information.</span></span> <span data-ttu-id="17cf1-108">たとえば、情報、警告、エラー、および成功または失敗の監査などのイベントをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-108">For example, you can filter events, such as information, warning, error, success audit, and failure audit.</span></span>  
  
## <a name="comparing-error-and-application-log-output"></a><span data-ttu-id="17cf1-109">エラー ログとアプリケーション ログの出力の比較</span><span class="sxs-lookup"><span data-stu-id="17cf1-109">Comparing Error and Application Log Output</span></span>  
 <span data-ttu-id="17cf1-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと Windows アプリケーション ログの両方を使用して、問題の原因を特定できます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-110">You can use both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows application log to identify the cause of problems.</span></span> <span data-ttu-id="17cf1-111">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログの監視中、原因に関する情報が含まれていないエラー メッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="17cf1-111">For example, while monitoring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, you may encounter error messages that do not contain cause information.</span></span> <span data-ttu-id="17cf1-112">これらのログの間でイベントの日付と時刻を比較することにより、可能性のある原因の範囲を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="17cf1-112">By comparing the dates and times for events between these logs, you can narrow the list of probable causes.</span></span> <span data-ttu-id="17cf1-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ログ ファイル ビューアーにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、および Windows ログが 1 つの一覧に統合され、関連するサーバー イベントや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントの把握が容易になります。</span><span class="sxs-lookup"><span data-stu-id="17cf1-113">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Log File Viewer lets you integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and the Windows logs into a single list, making it easy to understand related server events and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="17cf1-114">詳細については、SQL Server オンライン ブックの「[ログ ファイルの表示]」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17cf1-114">For more information, see the topic "Log File Viewer" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17cf1-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="17cf1-115">In This Section</span></span>  
  
|<span data-ttu-id="17cf1-116">トピック</span><span class="sxs-lookup"><span data-stu-id="17cf1-116">Topic</span></span>|<span data-ttu-id="17cf1-117">説明</span><span class="sxs-lookup"><span data-stu-id="17cf1-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="17cf1-118">SQL Server エラー ログの表示</span><span class="sxs-lookup"><span data-stu-id="17cf1-118">Viewing the SQL Server Error Log</span></span>](../../../2014/tools/configuration-manager/viewing-the-sql-server-error-log.md)|<span data-ttu-id="17cf1-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとその表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17cf1-119">Contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and how to view it.</span></span>|  
|[<span data-ttu-id="17cf1-120">Windows アプリケーション ログの表示</span><span class="sxs-lookup"><span data-stu-id="17cf1-120">Viewing the Windows Application Log</span></span>](viewing-the-windows-application-log.md)|<span data-ttu-id="17cf1-121">Windows アプリケーション ログとその表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17cf1-121">Contains information about the Windows application log and how to view it.</span></span>|  
  
  

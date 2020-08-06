---
title: イベント転送サーバーを指定する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc5f01507bf893d1bffc682f65a01b9ff48ffa9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737453"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a><span data-ttu-id="6a2d6-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6a2d6-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6a2d6-103">このトピックでは、を使用して、でイベントを転送するサーバーを指定する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-103">This topic describes how to designate a server to which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forwards events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span></span> <span data-ttu-id="6a2d6-104">イベントの転送の適用対象は、単一のコンピューターでホストされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間で転送されるイベントではなく、サーバー間で転送されるイベントであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-104">Note that event forwarding applies to events forwarded between servers, not to events forwarded between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hosted on a single computer.</span></span> <span data-ttu-id="6a2d6-105">また、転送されたイベントを受信するには、警告管理サーバーが SQL Server の既定のインスタンスでなければならないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-105">Also note that in order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
 <span data-ttu-id="6a2d6-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6a2d6-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6a2d6-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6a2d6-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6a2d6-108">Security</span><span class="sxs-lookup"><span data-stu-id="6a2d6-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6a2d6-109">**イベントの転送先サーバーを指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="6a2d6-109">**To designate an events forwarding server, using:**</span></span>  
  
     [<span data-ttu-id="6a2d6-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6a2d6-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6a2d6-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="6a2d6-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6a2d6-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6a2d6-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6a2d6-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="6a2d6-113">Permissions</span></span>  
 <span data-ttu-id="6a2d6-114">**sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6a2d6-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6a2d6-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-an-events-forwarding-server"></a><span data-ttu-id="6a2d6-116">イベントの転送先サーバーを指定するには</span><span class="sxs-lookup"><span data-stu-id="6a2d6-116">To designate an events forwarding server</span></span>  
  
1.  <span data-ttu-id="6a2d6-117">**オブジェクト エクスプ ローラー** で、プラス記号をクリックして、別のサーバーにイベントを転送するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-117">In **Object Explorer,** click the plus sign to expand the server from which you want to forward events to another server.</span></span>  
  
2.  <span data-ttu-id="6a2d6-118">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-118">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="6a2d6-119">\*\*[SQL Server エージェントのプロパティ - \*\*_<サーバー名>]_ ダイアログ ボックスの **[ページの選択]** で **[詳細設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-119">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Advanced**.</span></span>  

4.  <span data-ttu-id="6a2d6-120">**[SQL Server イベントの転送]** で、 **[イベントを別のサーバーに転送する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-120">Under **SQL Server event forwarding**, select the **Forward events to a different server** check box.</span></span>  
  
5.  <span data-ttu-id="6a2d6-121">**[サーバー]** ボックスの一覧でサーバーを選択し、 **[イベント]** で次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-121">In the **Server** list, select a server, and then, under **Events**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="6a2d6-122">ローカルの警告で処理されていないイベントのみを転送する場合は、 **[未処理のイベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-122">Select **Unhandled events** to forward only the events that have not been handled by local alerts.</span></span>  
  
    -   <span data-ttu-id="6a2d6-123">ローカルの警告によって処理されたかどうかにかかわらず、すべてのイベントを転送する場合は、 **[すべてのイベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-123">Select **All events** to forward all events regardless of whether they have been handled by local alerts.</span></span>  
  
6.  <span data-ttu-id="6a2d6-124">**[次のレベル以上のイベント発生時]** ボックスの一覧で、選択したサーバーにイベントを転送するときの重大度レベルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-124">In the **If event has severity at or above** list, click the severity level at which events are forwarded to the selected server.</span></span>  
  
7.  <span data-ttu-id="6a2d6-125">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a2d6-125">When finished, click **OK**.</span></span>  
  
  

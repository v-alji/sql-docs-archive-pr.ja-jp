---
title: シャットダウン メッセージのブロードキャスト (コマンド プロンプト) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 540baada4a78d7b5caf54cbabb9196ce5a79780e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716809"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a><span data-ttu-id="544d0-102">シャットダウン メッセージのブロードキャスト (コマンド プロンプト)</span><span class="sxs-lookup"><span data-stu-id="544d0-102">Broadcast a Shutdown Message (Command Prompt)</span></span>
  <span data-ttu-id="544d0-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で **net send** コマンドを使用して、シャットダウン メッセージをブロードキャストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="544d0-103">This topic describes how to broadcast a shutdown message in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using the **net send** command.</span></span> <span data-ttu-id="544d0-104">このメッセージには、ユーザーが現在行っている作業を終了できるように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが停止する時間を含めてください。</span><span class="sxs-lookup"><span data-stu-id="544d0-104">In the message, include the time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be stopped so that users can finish their tasks.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a><span data-ttu-id="544d0-105">シャットダウン メッセージをブロードキャストするには</span><span class="sxs-lookup"><span data-stu-id="544d0-105">To broadcast a shutdown message</span></span>  
  
1.  <span data-ttu-id="544d0-106">コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="544d0-106">From a command prompt, enter:</span></span>  
  
     <span data-ttu-id="544d0-107">**net send /users "message"**</span><span class="sxs-lookup"><span data-stu-id="544d0-107">**net send /users "message"**</span></span>  
  
     <span data-ttu-id="544d0-108">**/users** オプションを指定すると、サーバーに接続されたすべてのユーザーにメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="544d0-108">The **/users** option specifies that the message be sent to all users connected to the server</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="544d0-109">**net send** コマンドを使用するには、メッセンジャー サービスを送信用コンピューターと受信用コンピューターの両方で実行しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="544d0-109">The **net send** command requires the messenger service to be running on both the sending and the receiving computers.</span></span> <span data-ttu-id="544d0-110">メッセンジャー サービスは Windows Server 2003 では既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="544d0-110">The messenger service is disabled by default on Windows Server 2003.</span></span> <span data-ttu-id="544d0-111">**net send**の詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="544d0-111">For information about **net send**, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="544d0-112">使用しているネットワークによっては、電子メールや電話でユーザーに連絡する方が適している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="544d0-112">On your network, it may be more appropriate to contact users by e-mail or the telephone.</span></span> <span data-ttu-id="544d0-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に現在接続しているユーザーを確認するには、利用状況モニターを使用します。</span><span class="sxs-lookup"><span data-stu-id="544d0-113">To determine which users are currently connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the Activity Monitor.</span></span> <span data-ttu-id="544d0-114">利用状況モニターの詳細については、「[利用状況モニター](../../relational-databases/performance-monitor/activity-monitor.md)」および「[利用状況モニターを開く方法 &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="544d0-114">For information on the Activity Monitor, see [Activity Monitor](../../relational-databases/performance-monitor/activity-monitor.md) and [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544d0-115">参照</span><span class="sxs-lookup"><span data-stu-id="544d0-115">See Also</span></span>  
 [<span data-ttu-id="544d0-116">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="544d0-116">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  

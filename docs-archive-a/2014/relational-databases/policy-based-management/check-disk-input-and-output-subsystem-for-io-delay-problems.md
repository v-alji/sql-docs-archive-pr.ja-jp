---
title: ディスク I/O サブシステムの I/O 遅延問題の確認 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0ae8dc0d1a93f8150ccbeab73ed8aa918d1f495
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715205"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a><span data-ttu-id="1b210-102">ディスク I/O サブシステムの I/O 遅延問題の確認</span><span class="sxs-lookup"><span data-stu-id="1b210-102">Check Disk Input and Output Subsystem for IO Delay Problems</span></span>
  <span data-ttu-id="1b210-103">このルールでは、イベント ログのエラー メッセージ 833 を確認します。</span><span class="sxs-lookup"><span data-stu-id="1b210-103">This rule checks the event log for error message 833.</span></span> <span data-ttu-id="1b210-104">このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスクからの読み取り要求やディスクへの書き込み要求を発行してからその要求が完了するまでの時間が 15 秒を超えたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="1b210-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="1b210-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からこのエラーが報告された場合は、ディスク I/O サブシステムに問題があります。</span><span class="sxs-lookup"><span data-stu-id="1b210-105">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the disk I/O subsystem.</span></span> <span data-ttu-id="1b210-106">この長い遅延が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境のパフォーマンスに深刻な悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1b210-106">Delays this long can severely damage the performance of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="1b210-107">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="1b210-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="1b210-108">このエラーのトラブルシューティングを行うには、システム イベント ログを参照し、ハードウェア関連のエラー メッセージが記録されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="1b210-108">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="1b210-109">また、可能な場合はハードウェア固有のログも調べます。</span><span class="sxs-lookup"><span data-stu-id="1b210-109">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="1b210-110">パフォーマンス モニターを使用して、次のカウンターを調べます。</span><span class="sxs-lookup"><span data-stu-id="1b210-110">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="1b210-111">Avg. Disk sec/Transfer</span><span class="sxs-lookup"><span data-stu-id="1b210-111">Average Disk Sec/Transfer</span></span>  
  
-   <span data-ttu-id="1b210-112">Avg. Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="1b210-112">Average Disk Queue Length</span></span>  
  
-   <span data-ttu-id="1b210-113">Current Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="1b210-113">Current Disk Queue Length</span></span>  
  
 <span data-ttu-id="1b210-114">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの Avg. Disk sec/Transfer の時間は、通常 15 ミリ秒未満です。</span><span class="sxs-lookup"><span data-stu-id="1b210-114">For example, the Average Disk Sec/Transfer time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="1b210-115">Avg. Disk sec/Transfer の値が増加している場合、ディスク I/O サブシステムが I/O 要求を最適な速度で処理できていません。</span><span class="sxs-lookup"><span data-stu-id="1b210-115">If the Average Disk Sec/Transfer value increases, this indicates that the disk I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="1b210-116">詳細情報</span><span class="sxs-lookup"><span data-stu-id="1b210-116">For More Information</span></span>  
 [<span data-ttu-id="1b210-117">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="1b210-117">MSSQLSERVER_833</span></span>](../errors-events/mssqlserver-833-database-engine-error.md)  
  
 [<span data-ttu-id="1b210-118">サポート技術情報の資料 897284</span><span class="sxs-lookup"><span data-stu-id="1b210-118">Microsoft Knowledge Base article 897284</span></span>](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 <span data-ttu-id="1b210-119">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="1b210-119">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  

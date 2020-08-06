---
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e20018c0fe1cd0748f4930e0022622adcbfad10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640949"
---
# <a name="mssqlserver_833"></a><span data-ttu-id="e2f00-102">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="e2f00-102">MSSQLSERVER_833</span></span>
    
## <a name="details"></a><span data-ttu-id="e2f00-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e2f00-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2f00-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e2f00-104">Product Name</span></span>|<span data-ttu-id="e2f00-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e2f00-105">SQL Server</span></span>|  
|<span data-ttu-id="e2f00-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e2f00-106">Event ID</span></span>|<span data-ttu-id="e2f00-107">833</span><span class="sxs-lookup"><span data-stu-id="e2f00-107">833</span></span>|  
|<span data-ttu-id="e2f00-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e2f00-108">Event Source</span></span>|<span data-ttu-id="e2f00-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e2f00-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e2f00-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e2f00-110">Component</span></span>|<span data-ttu-id="e2f00-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e2f00-111">SQLEngine</span></span>|  
|<span data-ttu-id="e2f00-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e2f00-112">Symbolic Name</span></span>|<span data-ttu-id="e2f00-113">BUF_LONG_IO</span><span class="sxs-lookup"><span data-stu-id="e2f00-113">BUF_LONG_IO</span></span>|  
|<span data-ttu-id="e2f00-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e2f00-114">Message Text</span></span>|<span data-ttu-id="e2f00-115">SQL Server が、データベースのファイル [% ls] で完了するまでに% d 秒以上かかった i/o 要求を% d 個検出しました `[%ls] (%d)` 。</span><span class="sxs-lookup"><span data-stu-id="e2f00-115">SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database`[%ls] (%d)`.</span></span>  <span data-ttu-id="e2f00-116">OS ファイル ハンドルは 0x%p です。</span><span class="sxs-lookup"><span data-stu-id="e2f00-116">The OS file handle is 0x%p.</span></span>  <span data-ttu-id="e2f00-117">最新の実行時間の長い I/O のオフセットは %#016I64x です。</span><span class="sxs-lookup"><span data-stu-id="e2f00-117">The offset of the latest long I/O is: %#016I64x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e2f00-118">説明</span><span class="sxs-lookup"><span data-stu-id="e2f00-118">Explanation</span></span>  
 <span data-ttu-id="e2f00-119">このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスクからの読み取り要求やディスクへの書き込み要求を発行してからその要求が完了するまでの時間が 15 秒を超えたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="e2f00-119">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="e2f00-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からこのエラーが報告された場合は、IO サブシステムに問題があります。</span><span class="sxs-lookup"><span data-stu-id="e2f00-120">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the IO subsystem.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="e2f00-121">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="e2f00-121">Possible Causes</span></span>  
 <span data-ttu-id="e2f00-122">この問題の原因としては、システム パフォーマンスの問題、ハードウェア エラー、ファームウェア エラー、デバイス ドライバーの問題、IO プロセスへのフィルター ドライバーの介入などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="e2f00-122">This problem can be caused system performance issues, hardware errors, firmware errors, device driver problems, or filter driver intervention in the IO process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e2f00-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e2f00-123">User Action</span></span>  
 <span data-ttu-id="e2f00-124">このエラーのトラブルシューティングを行うには、システム イベント ログを参照し、ハードウェア関連のエラー メッセージが記録されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="e2f00-124">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="e2f00-125">また、可能な場合はハードウェア固有のログも調べます。</span><span class="sxs-lookup"><span data-stu-id="e2f00-125">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="e2f00-126">パフォーマンス モニターを使用して、次のカウンターを調べます。</span><span class="sxs-lookup"><span data-stu-id="e2f00-126">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="e2f00-127">**Average Disk Sec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="e2f00-127">**Average Disk Sec/Transfer**</span></span>  
  
-   <span data-ttu-id="e2f00-128">**Average Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="e2f00-128">**Average Disk Queue Length**</span></span>  
  
-   <span data-ttu-id="e2f00-129">**Current Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="e2f00-129">**Current Disk Queue Length**</span></span>  
  
 <span data-ttu-id="e2f00-130">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの **Average Disk Sec/Transfer** の時間は、通常 15 ミリ秒未満です。</span><span class="sxs-lookup"><span data-stu-id="e2f00-130">For example, the **Average Disk Sec/Transfer** time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="e2f00-131">**Avg. Disk sec/Transfer** の値が増加している場合、I/O サブシステムが I/O 要求を最適な速度で処理できていません。</span><span class="sxs-lookup"><span data-stu-id="e2f00-131">If the **Average Disk Sec/Transfer** value increases, this indicates that the I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2f00-132">ディスク アクセス速度は、ウイルス対策プログラムによって低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2f00-132">Disk access can be slowed by an antivirus program.</span></span> <span data-ttu-id="e2f00-133">アクセスを高速化するには、エラー メッセージに示されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ファイルをアクティブ ウイルス スキャンの対象から除外します。</span><span class="sxs-lookup"><span data-stu-id="e2f00-133">To increase access speed, exclude the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that are specified in the error message from active virus scans.</span></span>  
  
 <span data-ttu-id="e2f00-134">I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))」と、[https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284) にあるサポート技術情報の資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2f00-134">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) and the Knowledge Base article at [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).</span></span>  
  
  

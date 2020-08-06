---
title: '[スレッド] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f3460c892c182996a753c2a16076418a6b2008f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714137"
---
# <a name="threads-window"></a><span data-ttu-id="77d05-102">[スレッド] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="77d05-102">Threads Window</span></span>
  <span data-ttu-id="77d05-103">**[スレッド]** ウィンドウには、デバッグ中の [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター セッションで使用されている [!INCLUDE[ssDE](../../includes/ssde-md.md)] スレッドに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77d05-103">The **Threads** window displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] thread that is used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor session that is being debugged.</span></span> <span data-ttu-id="77d05-104">スレッドの情報を表示するには、デバッグ モードである必要があります。</span><span class="sxs-lookup"><span data-stu-id="77d05-104">You must be in debug mode to display the thread information.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="77d05-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="77d05-105">Task List</span></span>  
 <span data-ttu-id="77d05-106">**[スレッド] ウィンドウにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="77d05-106">**To access the Threads window**</span></span>  
  
-   <span data-ttu-id="77d05-107">**[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[スレッド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77d05-107">On the **Debug** menu, click **Windows**, and then click **Threads**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="77d05-108">[列]</span><span class="sxs-lookup"><span data-stu-id="77d05-108">Columns</span></span>  
 <span data-ttu-id="77d05-109">**ID**</span><span class="sxs-lookup"><span data-stu-id="77d05-109">**ID**</span></span>  
 <span data-ttu-id="77d05-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーがスレッドに割り当てる一意な識別番号。</span><span class="sxs-lookup"><span data-stu-id="77d05-110">Is a unique identifying number that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger assigns to the thread.</span></span> <span data-ttu-id="77d05-111">スレッドの詳細情報を参照するには、sys.dm_os_threads 動的管理ビューから行を選択します。</span><span class="sxs-lookup"><span data-stu-id="77d05-111">You can find more information about the thread by selecting a row from the sys.dm_os_threads dynamic management view.</span></span>  
  
 <span data-ttu-id="77d05-112">簡易プーリング モードで実行していない場合は、os_thread_id の値が **[ID]** 列の値に一致する行を選択します。</span><span class="sxs-lookup"><span data-stu-id="77d05-112">If you are not running in lightweight pooling mode, select the row in which the value in os_thread_id matches the value in the **ID** column.</span></span> <span data-ttu-id="77d05-113">簡易プーリング モードで実行している場合は、fiber_context_address の値が **[ID]** 列の値に一致する行を選択します。</span><span class="sxs-lookup"><span data-stu-id="77d05-113">If you are running in lightweight pooling mode, select the row in which the value in fiber_context_address matches the value in the **ID** column.</span></span>  
  
 <span data-ttu-id="77d05-114">**Name**</span><span class="sxs-lookup"><span data-stu-id="77d05-114">**Name**</span></span>  
 <span data-ttu-id="77d05-115">[!INCLUDE[ssDE](../../includes/ssde-md.md)] セッションの情報を **ComputerName/InstanceName [SPID]** の形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="77d05-115">Displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] session in the format **ComputerName/InstanceName [SPID]**.</span></span>  
  
 <span data-ttu-id="77d05-116">**[ComputerName]**</span><span class="sxs-lookup"><span data-stu-id="77d05-116">**ComputerName**</span></span>  
 <span data-ttu-id="77d05-117">クエリ エディター セッションが接続している [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを実行しているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="77d05-117">The name of the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="77d05-118">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="77d05-118">**InstanceName**</span></span>  
 <span data-ttu-id="77d05-119">クエリ エディター セッションが接続している [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="77d05-119">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="77d05-120">**[SPID]**</span><span class="sxs-lookup"><span data-stu-id="77d05-120">**[SPID]**</span></span>  
 <span data-ttu-id="77d05-121">このセッションを一意に識別する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセッション プロセス ID。</span><span class="sxs-lookup"><span data-stu-id="77d05-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session process ID that uniquely identifies this session.</span></span> <span data-ttu-id="77d05-122">セッションの詳細情報を参照するには、spid 列と同じ値を持つ sys.sysprocesses ビューの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="77d05-122">You can obtain more information about the session by selecting the row in the sys.sysprocesses view that has the same value in the spid column.</span></span>  
  
 <span data-ttu-id="77d05-123">**Location**</span><span class="sxs-lookup"><span data-stu-id="77d05-123">**Location**</span></span>  
 <span data-ttu-id="77d05-124">デバッグ中のクエリ エディター セッションで使用されているスクリプト ファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="77d05-124">Displays the name of the script file that is used in the Query Editor session that is being debugged.</span></span>  
  
 <span data-ttu-id="77d05-125">**優先順位**</span><span class="sxs-lookup"><span data-stu-id="77d05-125">**Priority**</span></span>  
 <span data-ttu-id="77d05-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="77d05-126">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="77d05-127">**[中断]**</span><span class="sxs-lookup"><span data-stu-id="77d05-127">**Suspend**</span></span>  
 <span data-ttu-id="77d05-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="77d05-128">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d05-129">参照</span><span class="sxs-lookup"><span data-stu-id="77d05-129">See Also</span></span>  
 <span data-ttu-id="77d05-130">[Transact-SQL デバッガー](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="77d05-130">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="77d05-131">[Transact-SQL デバッガー情報](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="77d05-131">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="77d05-132">[sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77d05-132">[sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span></span>  
 [<span data-ttu-id="77d05-133">sys.sysprocesses &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="77d05-133">sys.sysprocesses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  

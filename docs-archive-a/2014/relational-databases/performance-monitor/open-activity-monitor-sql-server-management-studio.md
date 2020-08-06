---
title: 利用状況モニターを開く方法 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea74122ad18a0a1ede5eef1e09684606ca0ce073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739733"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a><span data-ttu-id="73787-102">利用状況モニターを開く方法 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="73787-102">Open Activity Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="73787-103">このトピックでは、利用状況モニターを開いて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスおよびこれらのプロセスが現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに与える影響に関する情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73787-103">This topic describes how to open the Activity Monitor to obtain information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="73787-104">また、利用状況モニターの更新間隔の設定方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="73787-104">It also describes how to set the refresh interval of the Activity Monitor.</span></span>  
  
 <span data-ttu-id="73787-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="73787-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="73787-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="73787-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="73787-107">Security</span><span class="sxs-lookup"><span data-stu-id="73787-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="73787-108">**利用状況モニターを開くための方法:**</span><span class="sxs-lookup"><span data-stu-id="73787-108">**To open the Activity Monitor using:**</span></span>  
  
     [<span data-ttu-id="73787-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="73787-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="73787-110">**更新間隔を設定する方法:**  [SQL Server Management Studio](#Refresh)</span><span class="sxs-lookup"><span data-stu-id="73787-110">**To set the refresh interval using:**  [SQL Server Management Studio](#Refresh)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="73787-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="73787-111">Before You Begin</span></span>  
 <span data-ttu-id="73787-112">利用状況モニターでは、監視対象となるインスタンスでクエリを実行し、[利用状況モニター] 表示ペインに表示する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="73787-112">Activity Monitor runs queries on the monitored instance to obtain information for the Activity Monitor display panes.</span></span> <span data-ttu-id="73787-113">更新間隔を 10 秒未満に設定すると、これらのクエリを実行する時間がサーバーのパフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73787-113">When the refresh interval is set to less than 10 seconds, the time that is used to run these queries can affect server performance</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73787-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="73787-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="73787-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="73787-115">Permissions</span></span>  
 <span data-ttu-id="73787-116">利用状況モニターを表示するには、VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="73787-116">To view the Activity Monitor, a user must have VIEW SERVER STATE permission.</span></span> <span data-ttu-id="73787-117">利用状況モニターの [データ ファイル I/O] セクションを表示するには、VIEW SERVER STATE に加えて、CREATE DATABASE、ALTER ANY DATABASE、VIEW ANY DEFINITION のいずれかの権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="73787-117">To view the Data File I/O section of Activity Monitor, you must have CREATE DATABASE, ALTER ANY DATABASE, or VIEW ANY DEFINITION permission in addition to VIEW SERVER STATE.</span></span>  
  
 <span data-ttu-id="73787-118">プロセスを強制終了するには、sysadmin 固定サーバー ロールまたは processadmin 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="73787-118">To KILL a process, a user must be a member of the sysadmin or processadmin fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="73787-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="73787-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a><span data-ttu-id="73787-120">SQL Server Management Studio で利用状況モニターを開くには</span><span class="sxs-lookup"><span data-stu-id="73787-120">To open Activity Monitor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="73787-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [標準] ツール バーの **[利用状況モニター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73787-121">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] standard toolbar, click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="73787-122">**[サーバーへの接続]** ダイアログ ボックスで、サーバー名と認証モードを選択して **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73787-122">In the **Connect to Server** dialog box, select the server name and authentication mode, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="73787-123">また、Ctrl キーと Alt キーを押しながら A キーを押すと、いつでも利用状況モニターを表示できます。</span><span class="sxs-lookup"><span data-stu-id="73787-123">You can also open Activity Monitor at any time by pressing CTRL+ALT A.</span></span>  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a><span data-ttu-id="73787-124">オブジェクト エクスプローラーで利用状況モニターを開くには</span><span class="sxs-lookup"><span data-stu-id="73787-124">To open Activity Monitor in Object Explorer</span></span>  
  
-   <span data-ttu-id="73787-125">オブジェクトエクスプローラーで、インスタンス名を右クリックし、[**利用状況モニター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="73787-125">In Object Explorer, right-click the instance name, and then select **Activity Monitor**.</span></span>  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a><span data-ttu-id="73787-126">SQL Server Management Studio を開くときに利用状況モニターを開くには</span><span class="sxs-lookup"><span data-stu-id="73787-126">To open Activity Monitor when opening SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="73787-127">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73787-127">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="73787-128">**[オプション]** ダイアログ ボックスで **[環境]** を展開し、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73787-128">In the **Options** dialog box, expand **Environment**, and then select **General**.</span></span>  
  
3.  <span data-ttu-id="73787-129">**[スタートアップ時]** ボックスで **[オブジェクト エクスプローラーと利用状況モニターを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73787-129">In the **At startup** box, select **Open Object Explorer and Activity Monitor**.</span></span>  
  
4.  <span data-ttu-id="73787-130">変更を有効にするには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を閉じて再度開きます。</span><span class="sxs-lookup"><span data-stu-id="73787-130">To activate the changes, close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-set-the-activity-monitor-refresh-interval"></a><a name="Refresh"></a><span data-ttu-id="73787-131">利用状況モニターの更新間隔を設定するには</span><span class="sxs-lookup"><span data-stu-id="73787-131">To Set the Activity Monitor Refresh Interval</span></span>  
  
-   <span data-ttu-id="73787-132">利用状況モニターを開きます。</span><span class="sxs-lookup"><span data-stu-id="73787-132">Open the Activity Monitor.</span></span>  
  
-   <span data-ttu-id="73787-133">**[概要]** を右クリックして **[更新間隔]** をクリックし、利用状況モニターで新しいインスタンス情報を取得する間隔を選択します。</span><span class="sxs-lookup"><span data-stu-id="73787-133">Right-click **Overview**, select **Refresh Interval**, and then select the interval in which Activity Monitor should obtain new instance information.</span></span>  
  
  

---
title: データベース メールを使用するように SQL Server エージェント メールを構成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31d116c0bc8d7e148fc2ef6d2e344400516ad923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712026"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a><span data-ttu-id="8ae2a-102">データベース メールを使用するように SQL Server エージェント メールを構成する</span><span class="sxs-lookup"><span data-stu-id="8ae2a-102">Configure SQL Server Agent Mail to Use Database Mail</span></span>
  <span data-ttu-id="8ae2a-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の通知と警告をデータベース メールを使用して送信するように [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-103">This topic describes how to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail to send notification and alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="8ae2a-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="8ae2a-104">**Before you begin:**</span></span>  
  
-   [<span data-ttu-id="8ae2a-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="8ae2a-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="8ae2a-106">Security</span><span class="sxs-lookup"><span data-stu-id="8ae2a-106">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="8ae2a-107">SQL Server Management Studio でデータベース メールを使用するように SQL Server エージェントを構成するには</span><span class="sxs-lookup"><span data-stu-id="8ae2a-107">To Configure SQL Server Agent to use Database Mail, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="8ae2a-108">フォローアップタスク</span><span class="sxs-lookup"><span data-stu-id="8ae2a-108">Follow-up Tasks</span></span>](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8ae2a-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="8ae2a-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8ae2a-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="8ae2a-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="8ae2a-111">データベース メールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-111">Enable Database Mail.</span></span>  
  
-   <span data-ttu-id="8ae2a-112">使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのデータベース メール アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-112">Create a Database Mail account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use.</span></span>  
  
-   <span data-ttu-id="8ae2a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのデータベース メール プロファイルを作成し、ユーザーを **msdb** データベースの **DatabaseMailUserRole** に追加します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-113">Create a Database Mail profile for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use and add the user to the **DatabaseMailUserRole** in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="8ae2a-114">作成したプロファイルを **msdb** データベースの既定のプロファイルに設定します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-114">Set the profile as the default profile for the **msdb** database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8ae2a-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8ae2a-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8ae2a-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="8ae2a-116">Permissions</span></span>  
 <span data-ttu-id="8ae2a-117">プロファイル アカウントを作成し、ストアド プロシージャを実行するユーザーは、sysadmin 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-117">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8ae2a-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8ae2a-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8ae2a-119">**データベース メールを使用するように SQL Server エージェントを構成するには**</span><span class="sxs-lookup"><span data-stu-id="8ae2a-119">**To configure SQL Server Agent to use Database Mail**</span></span>  
  
-   <span data-ttu-id="8ae2a-120">オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-120">In Object Explorer, expand a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="8ae2a-121">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-121">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="8ae2a-122">**[警告システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-122">Click **Alert System**.</span></span>  
  
-   <span data-ttu-id="8ae2a-123">**[メール プロファイルを有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-123">Select **Enable Mail Profile**.</span></span>  
  
-   <span data-ttu-id="8ae2a-124">**[メール システム]** ボックスの一覧で、 **[データベース メール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-124">In the **Mail system** list, select **Database Mail**.</span></span>  
  
-   <span data-ttu-id="8ae2a-125">**[メール プロファイル]** ボックスの一覧で、データベース メールのメール プロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-125">In the **Mail profile list**, select a mail profile for Database Mail.</span></span>  
  
-   <span data-ttu-id="8ae2a-126">SQL Server エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-126">Restart SQL Server Agent.</span></span>  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> <span data-ttu-id="8ae2a-127">フォロー アップ タスク</span><span class="sxs-lookup"><span data-stu-id="8ae2a-127">Follow-up Tasks</span></span>  
 <span data-ttu-id="8ae2a-128">警告および通知を送信できるようにエージェントを構成するには、次のタスクが必要となります。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-128">The following tasks are necessary to complete the configuration of Agent to send alerts and notifications.</span></span>  
  
-   [<span data-ttu-id="8ae2a-129">アラート</span><span class="sxs-lookup"><span data-stu-id="8ae2a-129">Alerts</span></span>](../../ssms/agent/alerts.md)  
  
     <span data-ttu-id="8ae2a-130">特定のデータベース イベントまたはオペレーティング システムの状態がオペレーターに通知されるように、警告を構成できます。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-130">Alerts can be configured to notify an operator of a particular database event or operating system condition.</span></span>  
  
-   [<span data-ttu-id="8ae2a-131">オペレーター</span><span class="sxs-lookup"><span data-stu-id="8ae2a-131">Operators</span></span>](../../ssms/agent/operators.md)  
  
     <span data-ttu-id="8ae2a-132">オペレーターとは、電子通知を受け取ることのできる人またはグループの別名です。</span><span class="sxs-lookup"><span data-stu-id="8ae2a-132">Operators are aliases for people or groups that can receive electronic notification</span></span>  
  
  

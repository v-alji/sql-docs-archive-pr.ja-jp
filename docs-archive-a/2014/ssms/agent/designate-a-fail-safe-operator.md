---
title: 緊急時のオペレーターを指定する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 714ed78875bd289f2fe2d64a5699c59bce58ced0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737459"
---
# <a name="designate-a-fail-safe-operator"></a><span data-ttu-id="f86c4-102">Designate a Fail-Safe Operator</span><span class="sxs-lookup"><span data-stu-id="f86c4-102">Designate a Fail-Safe Operator</span></span>
  <span data-ttu-id="f86c4-103">緊急時のオペレーターとは、指定オペレーターが不在の場合に警告を受信するユーザーのことです。</span><span class="sxs-lookup"><span data-stu-id="f86c4-103">A fail-safe operator is a user who receives the alert if the designated operator cannot be reached.</span></span> <span data-ttu-id="f86c4-104">このトピックでは、を使用して、でエージェントの警告通知を受信する緊急時のオペレーターを設定する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f86c4-104">This topic describes how to set a fail-safe operator to receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f86c4-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f86c4-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f86c4-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f86c4-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f86c4-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f86c4-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f86c4-108">Security</span><span class="sxs-lookup"><span data-stu-id="f86c4-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f86c4-109">**緊急時のオペレーターを指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="f86c4-109">**To designate a fail-safe operator, using:**</span></span>  
  
     [<span data-ttu-id="f86c4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f86c4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f86c4-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="f86c4-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f86c4-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f86c4-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f86c4-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のバージョンでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからポケットベル オプションと **net send** オプションが削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="f86c4-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f86c4-114">新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="f86c4-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="f86c4-115">SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86c4-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="f86c4-116">詳細については、「 [オペレーターへの警告の割り当て](assign-alerts-to-an-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86c4-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f86c4-117">は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f86c4-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f86c4-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f86c4-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f86c4-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="f86c4-119">Permissions</span></span>  
 <span data-ttu-id="f86c4-120">緊急時のオペレーターを指定できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="f86c4-120">Only members of the **sysadmin** fixed server role can designate fail-safe operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f86c4-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f86c4-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-a-fail-safe-operator"></a><span data-ttu-id="f86c4-122">緊急時のオペレーターを指定するには</span><span class="sxs-lookup"><span data-stu-id="f86c4-122">To designate a fail-safe operator</span></span>  
  
1.  <span data-ttu-id="f86c4-123">**オブジェクト エクスプローラー** で、緊急時のオペレーターとして指定する SQL Server エージェント オペレーターを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="f86c4-123">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent operator that you want to designate as a fail-safe.</span></span>  
  
2.  <span data-ttu-id="f86c4-124">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f86c4-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="f86c4-125">[ **SQL Server エージェントのプロパティ-**_server_name_ ] ダイアログボックスの [**ページの選択**] で、[**警告システム**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f86c4-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Alert System**.</span></span>  
 
4.  <span data-ttu-id="f86c4-126">**[緊急時のオペレーター]** の **[緊急時のオペレーターを有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f86c4-126">Under **Fail-safe operator**, select **Enable fail-safe operator**.</span></span>  
  
5.  <span data-ttu-id="f86c4-127">**[オペレーター]** 一覧から、緊急時のオペレーターにするオペレーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="f86c4-127">In the **Operator** list, select the operator that you want to make a fail-safe.</span></span>  
  
6.  <span data-ttu-id="f86c4-128">**[電子メール]**、 **[ポケットベル]**、 **[Net send]** チェック ボックスのいずれかまたはすべてを選択して、オペレーターへの通知方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f86c4-128">Select either any or all of the following check boxes to specify how the operator will be notified: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="f86c4-129">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f86c4-129">When finished, click **OK**.</span></span>  
  
  

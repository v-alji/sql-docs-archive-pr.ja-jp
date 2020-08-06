---
title: DQS のプロファイル通知の有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b3b5e8cec1cac3eb1ce4357480c0f994a33d4c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715730"
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a><span data-ttu-id="95303-102">DQS のプロファイル通知の有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="95303-102">Enable or Disable Profiling Notifications in DQS</span></span>
  <span data-ttu-id="95303-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のプロファイル通知を有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95303-103">This topic describes how to enable or disable profiling notifications in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="95303-104">既定では、DQS のプロファイル通知は有効です。</span><span class="sxs-lookup"><span data-stu-id="95303-104">By default, profiling notifications are enabled in DQS.</span></span> <span data-ttu-id="95303-105">プロファイル通知によって、データ ソースについての重要な情報と、データに対して行われている現在のアクティビティの有効性が伝えられます。</span><span class="sxs-lookup"><span data-stu-id="95303-105">Profiling notifications tell you important facts about the data source and the effectiveness of the current activity performed on the data.</span></span> <span data-ttu-id="95303-106">詳細については、「 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="95303-106">For more information, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="95303-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="95303-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95303-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="95303-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95303-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="95303-109">Permissions</span></span>  
 <span data-ttu-id="95303-110">通知を有効にするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="95303-110">You must have the dqs_administrator role on the DQS_MAIN database to enable notifications.</span></span>  
  
##  <a name="enable-or-disable-profiling-notifications"></a><a name="Enable"></a><span data-ttu-id="95303-111">プロファイル通知を有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="95303-111">Enable or Disable Profiling Notifications</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="95303-112">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="95303-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="95303-113">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95303-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="95303-114">次に **[全般設定]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="95303-114">Next, click the **General Settings** tab.</span></span>  
  
4.  <span data-ttu-id="95303-115">DQS のさまざまなアクティビティのプロファイル通知を無効または有効にするには、 **[通知の有効化]** チェック ボックスをオフまたはオンにします。</span><span class="sxs-lookup"><span data-stu-id="95303-115">Clear or select the **Enable Notifications** check box to disable or enable profiling notifications for various activities in DQS.</span></span>  
  
5.  <span data-ttu-id="95303-116">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95303-116">Click **Close**.</span></span>  
  
  

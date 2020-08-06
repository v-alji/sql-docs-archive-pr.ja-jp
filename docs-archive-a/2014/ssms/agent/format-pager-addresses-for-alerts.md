---
title: 警告用のポケットベル アドレスの形式設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471f9a4958f51491b312d89239a2204c907e25e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631470"
---
# <a name="format-pager-addresses-for-alerts"></a><span data-ttu-id="d565e-102">Format Pager Addresses for Alerts</span><span class="sxs-lookup"><span data-stu-id="d565e-102">Format Pager Addresses for Alerts</span></span>
  <span data-ttu-id="d565e-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] またはを使用して、エージェントの警告のポケットベルアドレスの形式を設定する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d565e-103">This topic describes how to format pager addresses for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d565e-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d565e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d565e-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d565e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d565e-106">Security</span><span class="sxs-lookup"><span data-stu-id="d565e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d565e-107">**ポケットベル アドレスの形式を設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="d565e-107">**To format pager addresses, using:**</span></span>  
  
     [<span data-ttu-id="d565e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d565e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d565e-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="d565e-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d565e-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d565e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d565e-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="d565e-111">Permissions</span></span>  
 <span data-ttu-id="d565e-112">既定では、警告に関する情報を表示できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="d565e-112">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="d565e-113">それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="d565e-113">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d565e-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d565e-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-format-pager-addresses"></a><span data-ttu-id="d565e-115">ポケットベル アドレスの形式を設定するには</span><span class="sxs-lookup"><span data-stu-id="d565e-115">To format pager addresses</span></span>  
  
1.  <span data-ttu-id="d565e-116">**オブジェクト エクスプローラー**で、ポケットベルに送信する警告を含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="d565e-116">In **Object Explorer**, click the plus sign to expand the server that contains the alert that you want to send to a pager.</span></span>  
  
2.  <span data-ttu-id="d565e-117">**SQL Server エージェント**を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d565e-117">Right-click **SQL Server Agent** and select **Properties**</span></span>  
  
3.  <span data-ttu-id="d565e-118">**[ページの選択]** の **[警告システム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d565e-118">Under **Select a page**, select **Alert System**.</span></span>  
  
4.  <span data-ttu-id="d565e-119">**[ポケットベル メールのアドレス形式]** フィールドの **[[宛先] 行]** ボックスおよび **[[CC] 行]** ボックスに、ポケットベル アドレスのプレフィックスまたはサフィックスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d565e-119">In the **To line** and **CC line** boxes of the **Address formatting for pager e-mails** field, enter the pager address prefix or suffix.</span></span> <span data-ttu-id="d565e-120">オペレーターの実際のポケットベル アドレスは、通知の送信時に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d565e-120">The operator's actual pager address is inserted when a notification is sent.</span></span>  
  
5.  <span data-ttu-id="d565e-121">**[件名]** ボックスに、件名行のプレフィックスまたはサフィックスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d565e-121">In the **Subject** box, enter the subject line prefix or suffix.</span></span>  
  
6.  <span data-ttu-id="d565e-122">**[通知メッセージに電子メールの本文を含める]** チェック ボックスをオンにして、ポケットベルのメッセージに (件名行のみではなく) 完全な電子メール メッセージを含めます。</span><span class="sxs-lookup"><span data-stu-id="d565e-122">Select the **Include body of e-mail in notification page** check box to include the full e-mail message with the pager message (as opposed to the subject line only).</span></span>  
  
7.  <span data-ttu-id="d565e-123">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d565e-123">When finished, click **OK**.</span></span>  
  
  

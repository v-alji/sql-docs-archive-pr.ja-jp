---
title: ポリシー管理者にポリシー エラーを通知する警告の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9eb84ced3bb6313dd5920deaf479925556f08fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711897"
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a><span data-ttu-id="d59be-102">ポリシー管理者にポリシー エラーを通知する警告の構成</span><span class="sxs-lookup"><span data-stu-id="d59be-102">Configure Alerts to Notify Policy Administrators of Policy Failures</span></span>
  <span data-ttu-id="d59be-103">ポリシー ベースの管理ポリシーが 3 つの自動評価モードのいずれかで実行された場合にポリシー違反が発生すると、メッセージがイベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d59be-103">When Policy-Based Management policies are executed in one of the three automated evaluation modes, if a policy violation occurs, a message is written to the event log.</span></span> <span data-ttu-id="d59be-104">このメッセージがイベント ログに書き込まれたときに通知を受けるには、メッセージを検出してアクションを実行する警告を作成します。</span><span class="sxs-lookup"><span data-stu-id="d59be-104">To be notified when this message is written to the event log, you can create an alert to detect the message and perform an action.</span></span> <span data-ttu-id="d59be-105">警告は、次の表に示すようにメッセージを検出します。</span><span class="sxs-lookup"><span data-stu-id="d59be-105">The alert should detect the messages as shown in the following table.</span></span>  
  
|<span data-ttu-id="d59be-106">実行モード</span><span class="sxs-lookup"><span data-stu-id="d59be-106">Execution mode</span></span>|<span data-ttu-id="d59be-107">メッセージ番号</span><span class="sxs-lookup"><span data-stu-id="d59be-107">Message number</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="d59be-108">変更中 - 禁止</span><span class="sxs-lookup"><span data-stu-id="d59be-108">On change: prevent</span></span><br /><br /> <span data-ttu-id="d59be-109">(自動の場合)</span><span class="sxs-lookup"><span data-stu-id="d59be-109">(if automatic)</span></span>|<span data-ttu-id="d59be-110">34050</span><span class="sxs-lookup"><span data-stu-id="d59be-110">34050</span></span>|  
|<span data-ttu-id="d59be-111">変更中 - 禁止</span><span class="sxs-lookup"><span data-stu-id="d59be-111">On change: prevent</span></span><br /><br /> <span data-ttu-id="d59be-112">(要求時に実行する場合)</span><span class="sxs-lookup"><span data-stu-id="d59be-112">(if On demand)</span></span>|<span data-ttu-id="d59be-113">34051</span><span class="sxs-lookup"><span data-stu-id="d59be-113">34051</span></span>|  
|<span data-ttu-id="d59be-114">スケジュールで実行</span><span class="sxs-lookup"><span data-stu-id="d59be-114">On schedule</span></span>|<span data-ttu-id="d59be-115">34052</span><span class="sxs-lookup"><span data-stu-id="d59be-115">34052</span></span>|  
|<span data-ttu-id="d59be-116">変更中</span><span class="sxs-lookup"><span data-stu-id="d59be-116">On change</span></span>|<span data-ttu-id="d59be-117">34053</span><span class="sxs-lookup"><span data-stu-id="d59be-117">34053</span></span>|  
  
 <span data-ttu-id="d59be-118">ポリシー ベースの管理のエラー メッセージに対処するように警告を設定するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d59be-118">To set up an alert to respond to the Policy-Based Management error messages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d59be-119">オペレーターの作成</span><span class="sxs-lookup"><span data-stu-id="d59be-119">Create an Operator</span></span>](../../ssms/agent/create-an-operator.md)  
  
-   [<span data-ttu-id="d59be-120">エラー番号を使用して警告を作成する</span><span class="sxs-lookup"><span data-stu-id="d59be-120">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="d59be-121">オペレーターへの警告の割り当て</span><span class="sxs-lookup"><span data-stu-id="d59be-121">Assign Alerts to an Operator</span></span>](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## <a name="permissions"></a><span data-ttu-id="d59be-122">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="d59be-122">Permissions</span></span>  
 <span data-ttu-id="d59be-123">要求時に評価されるポリシーは、ユーザーのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="d59be-123">When policies are evaluated on demand, they execute in the security context of the user.</span></span> <span data-ttu-id="d59be-124">エラー ログに書き込むには、ALTER TRACE 権限を持っているか、固定サーバー ロール sysadmin のメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d59be-124">To write to the error log, the user must have ALTER TRACE permissions or be a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="d59be-125">権限が不十分なユーザーがポリシーを評価した場合、イベント ログへの書き込みは行われず、警告は発生しません。</span><span class="sxs-lookup"><span data-stu-id="d59be-125">Policies that are evaluated by a user that has less privileges will not write to the event log, and will not fire an alert.</span></span>  
  
 <span data-ttu-id="d59be-126">自動実行モードは、sysadmin ロールのメンバーとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="d59be-126">The automated execution modes execute as a member of the sysadmin role.</span></span> <span data-ttu-id="d59be-127">これにより、エラー ログへの書き込みと警告の生成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d59be-127">This allows the policy to write to the error log and raise an alert.</span></span>  
  
## <a name="additional-considerations-about-alerts"></a><span data-ttu-id="d59be-128">警告に関するその他の注意点</span><span class="sxs-lookup"><span data-stu-id="d59be-128">Additional Considerations About Alerts</span></span>  
 <span data-ttu-id="d59be-129">警告に関するその他の注意点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d59be-129">Be aware of the following additional considerations about alerts:</span></span>  
  
-   <span data-ttu-id="d59be-130">警告は、有効になっているポリシーに対してのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="d59be-130">Alerts are raised only for policies that are enabled.</span></span> <span data-ttu-id="d59be-131">**[要求時]** ポリシーは有効にできないので、要求時に実行されるポリシーに対して警告は発生しません。</span><span class="sxs-lookup"><span data-stu-id="d59be-131">Because **On demand** policies cannot be enabled, alerts are not raised for policies that are executed on demand.</span></span>  
  
-   <span data-ttu-id="d59be-132">実行するアクションに電子メール メッセージの送信が含まれる場合は、メール アカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d59be-132">If the action you want to take includes sending an e-mail message, you must configure a mail account.</span></span> <span data-ttu-id="d59be-133">データベース メールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d59be-133">We recommend that you use Database Mail.</span></span> <span data-ttu-id="d59be-134">データベース メールをセットアップする方法の詳細については、「 [データベース メール アカウントの作成](../database-mail/create-a-database-mail-account.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d59be-134">For more information about how to set up Database Mail, see [Create a Database Mail Account](../database-mail/create-a-database-mail-account.md).</span></span>  
  
  

---
title: ポリシー ベースの管理ポリシーがスケジュールに従っていることの評価 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f1c6b1a7d13d14c02f4b4e537c2dbdb2df39d02c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715194"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a><span data-ttu-id="650d9-102">ポリシー ベースの管理ポリシーがスケジュールに従っていることの評価</span><span class="sxs-lookup"><span data-stu-id="650d9-102">Evaluate a Policy-Based Management Policy on a Schedule</span></span>
  <span data-ttu-id="650d9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシーがスケジュールに従っていることを評価する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="650d9-103">This topic describes how to evaluate a Policy-Based Management policy on a schedule in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="650d9-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="650d9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="650d9-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="650d9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="650d9-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="650d9-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="650d9-107">**以下を使用してポリシーがスケジュールに従っていることを評価するには:**</span><span class="sxs-lookup"><span data-stu-id="650d9-107">**To evaluate a policy on a schedule, using:**</span></span>  
  
     [<span data-ttu-id="650d9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="650d9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="650d9-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="650d9-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="650d9-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="650d9-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="650d9-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="650d9-111">Permissions</span></span>  
 <span data-ttu-id="650d9-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="650d9-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="650d9-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="650d9-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a><span data-ttu-id="650d9-114">ポリシーがスケジュールに従っていることを評価するには</span><span class="sxs-lookup"><span data-stu-id="650d9-114">To evaluate a policy on a schedule</span></span>  
  
1.  <span data-ttu-id="650d9-115">**オブジェクト エクスプローラー**で、評価するポリシーのスケジュールを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="650d9-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy schedule that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="650d9-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="650d9-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="650d9-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="650d9-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="650d9-118">プラス記号をクリックして **[ポリシー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="650d9-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="650d9-119">スケジュールを評価するポリシーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="650d9-119">Right-click the policy whose schedule you what to evaluate and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="650d9-120">**[ポリシーを開く - <_ポリシー名_>]** ダイアログ ボックスで、 **[評価モード]** ボックスの一覧の **[スケジュールで実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="650d9-120">On the **Open Policy -**_policy_name_ dialog box, in the **Evaluation Mode** list, select **On schedule**.</span></span>  
  
7.  <span data-ttu-id="650d9-121">**[スケジュール]** で、 **[選択]** をクリックして既存のスケジュールを指定するか、 **[新規作成]** をクリックして新しいスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="650d9-121">Under **Schedule**, click either **Pick** to specify an existing schedule or **New** to create a new schedule.</span></span>  
  
8.  <span data-ttu-id="650d9-122">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="650d9-122">When finished, click **OK**.</span></span>  
  
  

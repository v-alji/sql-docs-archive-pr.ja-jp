---
title: ポリシー ベースの管理ポリシーのエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15f554aeeebfd47c3fa1ea13b100fbe6bcfcc055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641630"
---
# <a name="export-a-policy-based-management-policy"></a><span data-ttu-id="c2993-102">ポリシー ベースの管理ポリシーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="c2993-102">Export a Policy-Based Management Policy</span></span>
  <span data-ttu-id="c2993-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシーをエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c2993-103">This topic describes how to export a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="c2993-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c2993-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c2993-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c2993-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c2993-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c2993-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c2993-107">**以下を使用してポリシーをエクスポートするには:**</span><span class="sxs-lookup"><span data-stu-id="c2993-107">**To export a policy, using:**</span></span>  
  
     [<span data-ttu-id="c2993-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c2993-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c2993-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="c2993-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c2993-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c2993-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c2993-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="c2993-111">Permissions</span></span>  
 <span data-ttu-id="c2993-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="c2993-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c2993-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c2993-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-export-a-policy"></a><span data-ttu-id="c2993-114">ポリシーをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="c2993-114">To export a policy</span></span>  
  
1.  <span data-ttu-id="c2993-115">オブジェクト エクスプローラーで、エクスポートするポリシー ベースの管理ポリシーを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="c2993-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to export.</span></span>  
  
2.  <span data-ttu-id="c2993-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c2993-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="c2993-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="c2993-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="c2993-118">プラス記号をクリックして **[ポリシー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c2993-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="c2993-119">エクスポートするポリシーを右クリックし、 **[ポリシーのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2993-119">Right-click the policy that you want to export and select **Export Policy**.</span></span>  
  
6.  <span data-ttu-id="c2993-120">**[ポリシーのエクスポート]** ダイアログ ボックスで、アドレス バーにファイルのパスと名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2993-120">In the **Export Policy** dialog box, type the path and name of the file in the address bar.</span></span> <span data-ttu-id="c2993-121">または、ダイアログ ボックスのナビゲーション ウィンドウでファイルの適切な場所を見つけ、 **[ファイル名]** ボックスに XML ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2993-121">Alternately, find a suitable location for the file in the dialog box's navigation pane, and then type the name of the XML file in the **File Name** box.</span></span>  
  
7.  <span data-ttu-id="c2993-122">完了したら、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2993-122">When finished, click **Save**.</span></span>  
  
  

---
title: 新しいポリシー ベースの管理条件の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4fe206c9a82b69101508f6f0a760ca9c1bc423d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641637"
---
# <a name="create-a-new-policy-based-management-condition"></a><span data-ttu-id="f7e28-102">新しいポリシー ベースの管理条件の作成</span><span class="sxs-lookup"><span data-stu-id="f7e28-102">Create a New Policy-Based Management Condition</span></span>
  <span data-ttu-id="f7e28-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] でポリシー ベースの管理条件を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-103">This topic describes how to create a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f7e28-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f7e28-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f7e28-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f7e28-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f7e28-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f7e28-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f7e28-107">**以下を使用して条件を作成するには:**</span><span class="sxs-lookup"><span data-stu-id="f7e28-107">**To create a condition, using:**</span></span>  
  
     [<span data-ttu-id="f7e28-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f7e28-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f7e28-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="f7e28-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f7e28-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f7e28-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f7e28-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="f7e28-111">Permissions</span></span>  
 <span data-ttu-id="f7e28-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="f7e28-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f7e28-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f7e28-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-condition"></a><span data-ttu-id="f7e28-114">条件を作成するには</span><span class="sxs-lookup"><span data-stu-id="f7e28-114">To create a condition</span></span>  
  
1.  <span data-ttu-id="f7e28-115">**オブジェクト エクスプローラー**で、プラス記号をクリックして、ポリシー ベースの管理条件を作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a Policy-based Management condition.</span></span>  
  
2.  <span data-ttu-id="f7e28-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="f7e28-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="f7e28-118">プラス記号をクリックして **[ファセット]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="f7e28-119">新しい条件を作成するファセットを右クリックし、 **[新しい条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e28-119">Right-click the facet in which you want to create a new condition and select **New Condition**.</span></span>  
  
6.  <span data-ttu-id="f7e28-120">**[新しい条件の作成]** ダイアログ ボックスで、 **[名前]** ボックスに新しい条件の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-120">In the **Create New Condition** dialog box, in the **Name** box, type the name of the new condition.</span></span>  
  
7.  <span data-ttu-id="f7e28-121">**[ファセット]** ボックスの一覧で正しいファセットが選択されていることを確認します。正しくない場合は、別のファセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-121">Confirm the correct facet in the **Facet** list, or select a different facet.</span></span>  
  
8.  <span data-ttu-id="f7e28-122">**[式]** の **[フィールド]** ボックスで、ファセット プロパティとそれに関連する演算子および値を選択して条件式を構築します。</span><span class="sxs-lookup"><span data-stu-id="f7e28-122">Under **Expression**, construct condition expressions by selecting a facet property in the **Field** box, together with its associated operator and value.</span></span> <span data-ttu-id="f7e28-123">複数の式を追加する場合は、 **And** または **Or**を使用して式を結合できます。</span><span class="sxs-lookup"><span data-stu-id="f7e28-123">When you add multiple expressions, the expressions can be joined by using **And** or **Or**.</span></span> <span data-ttu-id="f7e28-124">[新しい条件の作成] ダイアログ ボックスで使用可能なオプションの詳細については、「[[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md)」、「[[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [説明] ページ](create-new-condition-or-open-condition-dialog-box-description-page.md)」、および 「[[高度な編集] &#40;条件&#41; ダイアログ ボックス](advanced-edit-condition-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7e28-124">For more information on the available options in this dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
9. <span data-ttu-id="f7e28-125">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7e28-125">When finished, click **OK**.</span></span>  
  
  

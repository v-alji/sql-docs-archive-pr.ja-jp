---
title: テンプレートを使用したリソース ガバナーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62edb23cf55a953cb0fef54f002f8eaaa16f58ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644429"
---
# <a name="configure-resource-governor-using-a-template"></a><span data-ttu-id="cc3e0-102">テンプレートを使用してリソース ガバナーを構成する</span><span class="sxs-lookup"><span data-stu-id="cc3e0-102">Configure Resource Governor Using a Template</span></span>
  <span data-ttu-id="cc3e0-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に用意されているテンプレートを使用してリソース ガバナーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-103">You can configure Resource Governor by using a template that is provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="cc3e0-104">**作業を開始する準備:** [アクセス許可](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="cc3e0-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="cc3e0-105">**ワークロード グループの作成に使用するもの:** [テンプレート](#ConfRGTemplate)</span><span class="sxs-lookup"><span data-stu-id="cc3e0-105">**To create a workload group, using:**  [a template](#ConfRGTemplate)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc3e0-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="cc3e0-106">Before You Begin</span></span>  
 <span data-ttu-id="cc3e0-107">次の手順に従って、リソース プールおよびそのプールのワークロード グループを作成するテンプレートを開いて変更します。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-107">Use the following steps to open and modify a template that creates a resource pool and a workload group for the pool.</span></span> <span data-ttu-id="cc3e0-108">また、このテンプレートを使用すると、既定のグループまたは作成したワークロード グループへの新しい接続をルーティングするための、ユーザー定義の分類子関数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-108">In addition, this template enables you to create a classifier user-defined function that routes new connections to either the default group or the workload group that you create.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cc3e0-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="cc3e0-109">Permissions</span></span>  
 <span data-ttu-id="cc3e0-110">テンプレートでリソース ガバナーの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するには、CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-110">The resource governor [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the template require CONTROL SERVER permission.</span></span>  
  
##  <a name="configure-resource-governor-using-a-template"></a><a name="ConfRGTemplate"></a> <span data-ttu-id="cc3e0-111">テンプレートを使用してリソース ガバナーを構成する</span><span class="sxs-lookup"><span data-stu-id="cc3e0-111">Configure Resource Governor Using a Template</span></span>  
 <span data-ttu-id="cc3e0-112">**のテンプレートを使用してリソース ガバナーを構成するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="cc3e0-112">**To configure resource governor by using a template in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="cc3e0-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="cc3e0-114">**テンプレート エクスプローラー**で、 **[リソース ガバナー]** を展開して、 **[リソース ガバナーの構成]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-114">In **Template Explorer**, expand **Resource Governor**, and then double-click **Configure Resource Governor**.</span></span>  
  
3.  <span data-ttu-id="cc3e0-115">**[データベース エンジンへの接続]** で、必要な情報を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-115">In **Connect to Database Engine**, enter the required information, and then click **OK**.</span></span> <span data-ttu-id="cc3e0-116">テンプレート Configure Resource Governor.sql がクエリ エディターに示されます。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-116">The template Configure Resource Governor.sql is provided in the Query Editor.</span></span> <span data-ttu-id="cc3e0-117">このテンプレートを使用して、リソース プール、ワークロード グループ、および分類子関数を構成します。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-117">Use this template to create and configure a resource pool, a workload group, and a classifier function.</span></span>  
  
4.  <span data-ttu-id="cc3e0-118">テンプレートの値を変更するには、Ctrl キーと Shift キーを押しながら M キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-118">To change the values in the template, press CTRL+SHIFT+M.</span></span> <span data-ttu-id="cc3e0-119">**[テンプレート パラメーターの値の指定]** ウィンドウで、使用する値を入力します。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-119">In the **Specify Values for Template Parameters** window, enter the values that you want to use.</span></span>  
  
5.  <span data-ttu-id="cc3e0-120">テンプレートに加えた変更を保存するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-120">To save the changes that you make to the template, click **OK**.</span></span>  
  
6.  <span data-ttu-id="cc3e0-121">クエリを実行するには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cc3e0-121">To run the query, click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3e0-122">参照</span><span class="sxs-lookup"><span data-stu-id="cc3e0-122">See Also</span></span>  
 <span data-ttu-id="cc3e0-123">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-123">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="cc3e0-124">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-124">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="cc3e0-125">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-125">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="cc3e0-126">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-126">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="cc3e0-127">[リソース ガバナーの分類子関数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-127">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="cc3e0-128">[リソース ガバナー プロパティの表示](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-128">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="cc3e0-129">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-129">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="cc3e0-130">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-130">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="cc3e0-131">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc3e0-131">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="cc3e0-132">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc3e0-132">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  

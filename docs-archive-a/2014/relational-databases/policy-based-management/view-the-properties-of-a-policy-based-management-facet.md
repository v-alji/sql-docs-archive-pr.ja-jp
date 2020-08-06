---
title: ポリシー ベースの管理ファセットのプロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea24ff2768ecaeec426a8689455912d848b54813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634435"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a><span data-ttu-id="8067d-102">ポリシー ベースの管理ファセットのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="8067d-102">View the Properties of a Policy-Based Management Facet</span></span>
  <span data-ttu-id="8067d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ファセットのプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8067d-103">This topic describes how to view the properties of a Policy-Based Management facet in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8067d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="8067d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8067d-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="8067d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8067d-106">Security</span><span class="sxs-lookup"><span data-stu-id="8067d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8067d-107">**以下を使用してファセットのプロパティを表示するには:**</span><span class="sxs-lookup"><span data-stu-id="8067d-107">**To view the properties of a facet, using:**</span></span>  
  
     [<span data-ttu-id="8067d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8067d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8067d-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="8067d-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8067d-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8067d-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8067d-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="8067d-111">Permissions</span></span>  
 <span data-ttu-id="8067d-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="8067d-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8067d-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8067d-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-facet"></a><span data-ttu-id="8067d-114">ファセットのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="8067d-114">To view the properties of a facet</span></span>  
  
1.  <span data-ttu-id="8067d-115">**オブジェクト エクスプローラー**で、プロパティを表示するファセットを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="8067d-115">In **Object Explorer**, click the plus sign to expand the server that contains the facet whose properties you want to view.</span></span>  
  
2.  <span data-ttu-id="8067d-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8067d-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="8067d-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="8067d-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="8067d-118">プラス記号をクリックして **[ファセット]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8067d-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="8067d-119">プロパティを表示するファセットを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8067d-119">Right-click the facet whose properties you want to view and select **Properties**.</span></span> <span data-ttu-id="8067d-120">\*\*[ファセットのプロパティ - \*\*facet_name _]_ ダイアログ ボックスで使用可能なオプションの詳細については、「[[ファセットのプロパティ] ダイアログ ボックスの [全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md)」、「[[ファセットのプロパティ] ダイアログ ボックスの [依存ポリシー] ページ](facet-properties-dialog-box-dependent-policies-page.md)」、「[[ファセットのプロパティ] ダイアログ ボックスの [依存条件] ページ](facet-properties-dialog-box-dependent-conditions-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8067d-120">For more information on the available options in the **Facet Properties -**_facet_name_ dialog box, see [Facet Properties Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Facet Properties Dialog Box, Dependent Policies Page](facet-properties-dialog-box-dependent-policies-page.md), and [Facet Properties Dialog Box, Dependent Conditions Page](facet-properties-dialog-box-dependent-conditions-page.md).</span></span>  
  
6.  <span data-ttu-id="8067d-121">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8067d-121">When finished, click **Close**.</span></span>  
  
  

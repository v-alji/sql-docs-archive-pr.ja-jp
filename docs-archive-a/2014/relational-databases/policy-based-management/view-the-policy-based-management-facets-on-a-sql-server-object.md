---
title: SQL Server オブジェクトのポリシー ベースの管理ファセットの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9137971a79e9e5a18e0ef5d901184133a4c3eff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634436"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a><span data-ttu-id="2b8c7-102">SQL Server オブジェクトのポリシー ベースの管理ファセットの表示</span><span class="sxs-lookup"><span data-stu-id="2b8c7-102">View the Policy-Based Management Facets on a SQL Server Object</span></span>
  <span data-ttu-id="2b8c7-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で特定の SQL Server オブジェクトに適用されているすべてのポリシー ベースの管理ファセットを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b8c7-103">This topic describes how to view all of the Policy-Based Management facets applied to a specific SQL Server object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2b8c7-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2b8c7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2b8c7-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2b8c7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2b8c7-106">Security</span><span class="sxs-lookup"><span data-stu-id="2b8c7-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2b8c7-107">**以下を使用してオブジェクトのすべてのファセットを表示するには:**</span><span class="sxs-lookup"><span data-stu-id="2b8c7-107">**To view all of the facets in an object, using:**</span></span>  
  
     [<span data-ttu-id="2b8c7-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2b8c7-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2b8c7-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="2b8c7-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2b8c7-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2b8c7-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2b8c7-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="2b8c7-111">Permissions</span></span>  
 <span data-ttu-id="2b8c7-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="2b8c7-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2b8c7-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2b8c7-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a><span data-ttu-id="2b8c7-114">オブジェクトのすべてのファセットを表示するには</span><span class="sxs-lookup"><span data-stu-id="2b8c7-114">To view all of the facets in an object</span></span>  
  
1.  <span data-ttu-id="2b8c7-115">オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8c7-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="2b8c7-116">[ファ**セットの表示-**_object_name_ ] ダイアログボックスの [**ファセット**] ボックスの一覧で、プロパティを表示するファセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="2b8c7-116">In the **View Facets -**_object_name_ dialog box, in the **Facet** list, select a facet to view its properties.</span></span> <span data-ttu-id="2b8c7-117">このダイアログ ボックスで利用可能なオプションの詳細については、「 [View Facets Dialog Box](view-facets-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b8c7-117">For more information on the available options in this dialog box, see [View Facets Dialog Box](view-facets-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="2b8c7-118">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b8c7-118">When finished, click **OK**.</span></span>  
  
  

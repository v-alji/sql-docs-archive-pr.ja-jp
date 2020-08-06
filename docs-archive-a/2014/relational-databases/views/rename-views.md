---
title: ビューの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc76ced033a69788270c3fa9277bcca6972e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713001"
---
# <a name="rename-views"></a><span data-ttu-id="ab2e9-102">ビューの名前の変更</span><span class="sxs-lookup"><span data-stu-id="ab2e9-102">Rename Views</span></span>
  <span data-ttu-id="ab2e9-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ビューの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-103">You can rename a view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ab2e9-104">ビューの名前を変更すると、そのビューに依存するコードやアプリケーションの実行が失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-104">If you rename a view, code and applications that depend on the view may fail.</span></span> <span data-ttu-id="ab2e9-105">これには、他のビュー、クエリ、ストアド プロシージャ、ユーザー定義関数、およびクライアント アプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-105">These include other views, queries, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="ab2e9-106">このようなエラーは連鎖するので注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-106">Note that these failures will cascade.</span></span>  
  
 <span data-ttu-id="ab2e9-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ab2e9-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab2e9-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ab2e9-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab2e9-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="ab2e9-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ab2e9-110">Security</span><span class="sxs-lookup"><span data-stu-id="ab2e9-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab2e9-111">**以下を使用してビューの名前を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="ab2e9-111">**To rename a view, using:**</span></span>  
  
     [<span data-ttu-id="ab2e9-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab2e9-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab2e9-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab2e9-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ab2e9-114">**補足情報:** [ビューの名を変更した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ab2e9-114">**Follow Up:**  [After renaming a view](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab2e9-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="ab2e9-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ab2e9-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="ab2e9-116">Prerequisites</span></span>  
 <span data-ttu-id="ab2e9-117">ビューのすべての依存関係の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-117">Obtain a list of all dependencies on the view.</span></span> <span data-ttu-id="ab2e9-118">ビューを参照するすべてのオブジェクト、スクリプト、またはアプリケーションは、ビューの新しい名前を反映するように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-118">Any objects, scripts or applications that reference the view must be modified to reflect the new name of the view.</span></span> <span data-ttu-id="ab2e9-119">詳しくは、「 [Get Information About a View](get-information-about-a-view.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-119">For more information, see [Get Information About a View](get-information-about-a-view.md).</span></span> <span data-ttu-id="ab2e9-120">ビューの名前を変更するのではなく、ビューを削除してから新しい名前で作成し直すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-120">We recommend that you drop the view and recreate it with a new name instead of renaming the view.</span></span> <span data-ttu-id="ab2e9-121">ビューを再作成することにより、ビューで参照されているオブジェクトの依存情報が更新されます。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-121">By recreating the view, you update the dependency information for the objects that are referenced in the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab2e9-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ab2e9-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab2e9-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="ab2e9-123">Permissions</span></span>  
 <span data-ttu-id="ab2e9-124">SCHEMA に対する ALTER 権限または OBJECT に対する CONTROL 権限と、データベースの CREATE VIEW 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-124">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT is required, and CREATE VIEW permission in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab2e9-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ab2e9-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-view"></a><span data-ttu-id="ab2e9-126">ビューの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="ab2e9-126">To rename a view</span></span>  
  
1.  <span data-ttu-id="ab2e9-127">**オブジェクト エクスプローラー**で、名前を変更するビューを含むデータベースを展開します。次に、 **[ビュー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-127">In **Object Explorer**, expand the database that contains the view you wish to rename and then expand the **View** folder.</span></span>  
  
2.  <span data-ttu-id="ab2e9-128">名前を変更するビューを右クリックし、 **[名前の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-128">Right-click the view you wish to rename and select **Rename**.</span></span>  
  
3.  <span data-ttu-id="ab2e9-129">ビューの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-129">Enter the view's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab2e9-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ab2e9-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="ab2e9-131">**ビューの名前を変更するには**</span><span class="sxs-lookup"><span data-stu-id="ab2e9-131">**To rename a view**</span></span>  
  
 <span data-ttu-id="ab2e9-132">ビューの名前は **sp_rename** を使用して変更できますが、既存のビューを削除した後、新しい名前でビューを再作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-132">While you can use **sp_rename** to change the name of the view, we recommend that you delete the existing view and then re-create it with the new name.</span></span>  
  
 <span data-ttu-id="ab2e9-133">詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)」および「[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-133">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) and [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a><span data-ttu-id="ab2e9-134">補足情報: ビューの名を変更した後</span><span class="sxs-lookup"><span data-stu-id="ab2e9-134">Follow Up: After Renaming a View</span></span>  
 <span data-ttu-id="ab2e9-135">ビューの古い名前を参照するすべてのオブジェクト、スクリプト、およびアプリケーションで新しい名前が使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab2e9-135">Ensure that all objects, scripts, and applications that reference the view's old name now use the new name.</span></span>  
  
  

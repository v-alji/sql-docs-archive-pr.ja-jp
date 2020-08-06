---
title: CHECK 制約の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8377c80590612c8b68c315f7c37823eb8f5c5093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641994"
---
# <a name="modify-check-constraints"></a><span data-ttu-id="1f618-102">CHECK 制約の変更</span><span class="sxs-lookup"><span data-stu-id="1f618-102">Modify Check Constraints</span></span>
  <span data-ttu-id="1f618-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、制約式を変更するとき、または特定の条件の制約を有効または無効にするオプションを変更するときは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して CHECK 制約を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1f618-103">You can modify a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] when you want to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>  
  
 <span data-ttu-id="1f618-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1f618-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1f618-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1f618-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1f618-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1f618-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1f618-107">**CHECK 制約を変更するための方法:**</span><span class="sxs-lookup"><span data-stu-id="1f618-107">**To modify a check constraint using:**</span></span>  
  
     [<span data-ttu-id="1f618-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f618-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1f618-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f618-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1f618-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="1f618-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1f618-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1f618-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f618-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="1f618-112">Permissions</span></span>  
 <span data-ttu-id="1f618-113">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f618-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1f618-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1f618-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-check-constraint"></a><span data-ttu-id="1f618-115">CHECK 制約を変更するには</span><span class="sxs-lookup"><span data-stu-id="1f618-115">To modify a check constraint</span></span>  
  
1.  <span data-ttu-id="1f618-116">**オブジェクト エクスプローラー**で、CHECK 制約を含むテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f618-116">In the **Object Explorer**, right-click the table containing the check constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="1f618-117">**[テーブル デザイナー]** メニューの **[CHECK 制約]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f618-117">On the **Table Designer** menu, click **Check Constraints...**.</span></span>  
  
3.  <span data-ttu-id="1f618-118">**[CHECK 制約]** ダイアログ ボックスの **[選択された制約のチェック]** で、編集する制約を選択します。</span><span class="sxs-lookup"><span data-stu-id="1f618-118">In the **Check Constraints** dialog box, under **Selected Check Constraint**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="1f618-119">次の表の操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="1f618-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="1f618-120">ターゲット</span><span class="sxs-lookup"><span data-stu-id="1f618-120">To</span></span>|<span data-ttu-id="1f618-121">手順</span><span class="sxs-lookup"><span data-stu-id="1f618-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="1f618-122">制約式を編集する。</span><span class="sxs-lookup"><span data-stu-id="1f618-122">Edit the constraint expression</span></span>|<span data-ttu-id="1f618-123">**[式]** フィールドに新しい式を入力します。</span><span class="sxs-lookup"><span data-stu-id="1f618-123">Type the new expression in the **Expression** field.</span></span>|  
    |<span data-ttu-id="1f618-124">制約名を変更する。</span><span class="sxs-lookup"><span data-stu-id="1f618-124">Rename the constraint</span></span>|<span data-ttu-id="1f618-125">**[名前]** フィールドに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="1f618-125">Type a new name in the **Name** field.</span></span>|  
    |<span data-ttu-id="1f618-126">既存のデータに制約を適用する。</span><span class="sxs-lookup"><span data-stu-id="1f618-126">Apply the constraint to existing data</span></span>|<span data-ttu-id="1f618-127">**[作成時または再度有効化するときに既存データを確認]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1f618-127">Select the **Check Existing Data on Creation or Enabling** option.</span></span>|  
    |<span data-ttu-id="1f618-128">テーブルに新しいデータを追加する場合、またはテーブル内の既存のデータを更新する場合に、制約を無効にする。</span><span class="sxs-lookup"><span data-stu-id="1f618-128">Disable the constraint when new data is added to the table or when existing data is updated in the table.</span></span>|<span data-ttu-id="1f618-129">**[INSERTs および UPDATEs に適用]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="1f618-129">Clear the **Enforce Constraint for INSERTs and UPDATEs** option.</span></span>|  
    |<span data-ttu-id="1f618-130">レプリケーション エージェントによってテーブルにデータが挿入された場合やデータが更新された場合に制約を無効にする。</span><span class="sxs-lookup"><span data-stu-id="1f618-130">Disable the constraint when a replication agent inserts or updates data in your table.</span></span>|<span data-ttu-id="1f618-131">**[レプリケーションに対して適用]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="1f618-131">Clear the **Enforce For Replication** option.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f618-132">CHECK 制約に対して異なる機能を持つデータベースもあります。</span><span class="sxs-lookup"><span data-stu-id="1f618-132">Some databases have different functionality for check constraints.</span></span>  
  
5.  <span data-ttu-id="1f618-133">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f618-133">Click **Close**.</span></span>  
  
6.  <span data-ttu-id="1f618-134">**[ファイル]** メニューの **[ _<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f618-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1f618-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1f618-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="1f618-136">**CHECK 制約を変更するには**</span><span class="sxs-lookup"><span data-stu-id="1f618-136">**To modify a check constraint**</span></span>  
  
 <span data-ttu-id="1f618-137">`CHECK` を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]制約を変更するには、最初に既存の `CHECK` 制約を削除してから、新しい定義を使用して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f618-137">To modify a `CHECK` constraint using [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first delete the existing `CHECK` constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="1f618-138">詳細については、「 [CHECK 制約の削除](delete-check-constraints.md) 」および「 [CHECK 制約の作成](create-check-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f618-138">For more information, see [Delete Check Constraints](delete-check-constraints.md) and [Create Check Constraints](create-check-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  

---
title: UNIQUE 制約の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74b044202f7e8e9bc762f025833cf2d0ff84c4c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646091"
---
# <a name="modify-unique-constraints"></a><span data-ttu-id="13402-102">UNIQUE 制約の変更</span><span class="sxs-lookup"><span data-stu-id="13402-102">Modify Unique Constraints</span></span>
  <span data-ttu-id="13402-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して UNIQUE 制約を変更できます。</span><span class="sxs-lookup"><span data-stu-id="13402-103">You can modify a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="13402-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="13402-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="13402-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="13402-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="13402-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="13402-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="13402-107">**UNIQUE 制約を変更するための方法:**</span><span class="sxs-lookup"><span data-stu-id="13402-107">**To modify a unique constraint using:**</span></span>  
  
     [<span data-ttu-id="13402-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13402-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="13402-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13402-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="13402-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="13402-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="13402-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="13402-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="13402-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="13402-112">Permissions</span></span>  
 <span data-ttu-id="13402-113">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="13402-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="13402-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="13402-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-unique-constraint"></a><span data-ttu-id="13402-115">UNIQUE 制約を変更するには</span><span class="sxs-lookup"><span data-stu-id="13402-115">To modify a unique constraint</span></span>  
  
1.  <span data-ttu-id="13402-116">**オブジェクト エクスプローラー**で、UNIQUE 制約を含むテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13402-116">In the **Object Explorer**, right-click the table containing the unique constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="13402-117">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13402-117">On the **Table Designer** menu, click **Indexes/Keys...**.</span></span>  
  
3.  <span data-ttu-id="13402-118">**[インデックス/キー]** ダイアログ ボックスの **[選択された主/一意キーまたはインデックス]** で、編集する制約を選択します。</span><span class="sxs-lookup"><span data-stu-id="13402-118">In the **Indexes/Keys** dialog box, under **Selected Primary/Unique Key or Index**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="13402-119">次の表の操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="13402-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="13402-120">ターゲット</span><span class="sxs-lookup"><span data-stu-id="13402-120">To</span></span>|<span data-ttu-id="13402-121">手順</span><span class="sxs-lookup"><span data-stu-id="13402-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="13402-122">制約を適用する列を変更する。</span><span class="sxs-lookup"><span data-stu-id="13402-122">Change the columns that the constraint is associated with</span></span>|<span data-ttu-id="13402-123">1) **[(全般)]** の下のグリッドで、 **[列]** をクリックし、プロパティの右にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13402-123">1) In the grid under **(General)**, click **Columns** and then click the ellipses **(...)** to the right of the property.</span></span><br /><br /> <span data-ttu-id="13402-124">2) **[インデックス列]** ダイアログ ボックスで、インデックスの新しい列または並べ替え順序、あるいはその両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="13402-124">2) In the **Index Columns** dialog box, specify the new column or sort order or both for the index.</span></span>|  
    |<span data-ttu-id="13402-125">制約名を変更する。</span><span class="sxs-lookup"><span data-stu-id="13402-125">Rename the constraint</span></span>|<span data-ttu-id="13402-126">**[ID]** の下のグリッドで、 **[名前]** ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="13402-126">In the grid under **Identity**, type a new name in the **Name** box.</span></span> <span data-ttu-id="13402-127">新しい名前が **[選択された主/一意キーまたはインデックス]** ボックスの一覧の名前と重複していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="13402-127">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="13402-128">クラスター化オプションを設定する。</span><span class="sxs-lookup"><span data-stu-id="13402-128">Set the clustered option</span></span>|<span data-ttu-id="13402-129">**[テーブル デザイナー]** の下のグリッドで、 **[CLUSTERED として作成]** をクリックします。クラスター化インデックスを作成するには、ドロップダウン メニューの [はい] をクリックし、非クラスター化インデックスを作成する場合は [いいえ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13402-129">In the grid under **Table Designer**, select **Create As Clustered** and from the dropdown choose Yes to create a clustered index and No to create a nonclustered one.</span></span> <span data-ttu-id="13402-130">1 つのテーブルには、クラスター化インデックスを 1 つだけ作成できます。</span><span class="sxs-lookup"><span data-stu-id="13402-130">Only one clustered index can exist per table.</span></span> <span data-ttu-id="13402-131">このテーブルにクラスター化インデックスが既に存在する場合は、元のインデックスに対してこの設定をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="13402-131">If a clustered index already exists in this table, you must clear this setting on the original index.</span></span>|  
    |<span data-ttu-id="13402-132">FILL FACTOR を定義する。</span><span class="sxs-lookup"><span data-stu-id="13402-132">Define a fill factor</span></span>|<span data-ttu-id="13402-133">**[テーブル デザイナー]** の下のグリッドで、 **[FILL の指定]** カテゴリを展開し、 **[FILL FACTOR]** ボックスに 0 ～ 100 の整数を入力します。</span><span class="sxs-lookup"><span data-stu-id="13402-133">In the grid under **Table Designer**, expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill Factor** box.</span></span>|  
  
5.  <span data-ttu-id="13402-134">**[ファイル]** メニューの **[ _<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13402-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="to-modify-a-unique-constraint"></a><a name="TsqlProcedure"></a> <span data-ttu-id="13402-135">**UNIQUE 制約を変更するには**</span><span class="sxs-lookup"><span data-stu-id="13402-135">**To modify a unique constraint**</span></span>  
  
 <span data-ttu-id="13402-136">Transact-SQL を使用して UNIQUE 制約を変更するには、まず既存の UNIQUE 制約を削除してから、新しい定義を使用して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13402-136">To modify a UNIQUE constraint using Transact-SQL, you must first delete the existing UNIQUE constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="13402-137">詳細については、「 [Delete Unique Constraints](delete-unique-constraints.md) 」および「 [Create Unique Constraints](create-unique-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13402-137">For more information, see [Delete Unique Constraints](delete-unique-constraints.md) and [Create Unique Constraints](create-unique-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  

---
title: 主キーの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
author: stevestein
ms.author: sstein
ms.openlocfilehash: f24deeac45491f9097d90ee0407464f928a0713b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630851"
---
# <a name="modify-primary-keys"></a><span data-ttu-id="993b0-102">主キーの変更</span><span class="sxs-lookup"><span data-stu-id="993b0-102">Modify Primary Keys</span></span>
  <span data-ttu-id="993b0-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して主キーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="993b0-103">You can modify a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="993b0-104">列の順序、インデックス名、クラスター化オプション、または FILL FACTOR を変更することで、テーブルの主キーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="993b0-104">You can modify the primary key of a table by changing the column order, index name, clustered option, or fill factor.</span></span>  
  
 <span data-ttu-id="993b0-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="993b0-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="993b0-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="993b0-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="993b0-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="993b0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="993b0-108">**主キーを変更するための方法:**</span><span class="sxs-lookup"><span data-stu-id="993b0-108">**To modify a primary key, using:**</span></span>  
  
     [<span data-ttu-id="993b0-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="993b0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="993b0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="993b0-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="993b0-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="993b0-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="993b0-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="993b0-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="993b0-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="993b0-113">Permissions</span></span>  
 <span data-ttu-id="993b0-114">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="993b0-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="993b0-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="993b0-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-primary-key"></a><span data-ttu-id="993b0-116">主キーを変更するには</span><span class="sxs-lookup"><span data-stu-id="993b0-116">To modify a primary key</span></span>  
  
1.  <span data-ttu-id="993b0-117">主キーを変更するテーブルのテーブル デザイナーを開き、テーブル デザイナー内を右クリックして、ショートカット メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="993b0-117">Open the Table Designer for the table whose primary key you want to modify, right-click in the Table Designer, and choose **Indexes/Keys** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="993b0-118">**[インデックス/キー]** ダイアログ ボックスで、 **[選択された主/一意キーまたはインデックス]** ボックスから主キー インデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="993b0-118">In the **Indexes/Keys** dialog box, select the primary key index from the **Selected Primary/Unique Key or Index** list.</span></span>  
  
3.  <span data-ttu-id="993b0-119">次の表の操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="993b0-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="993b0-120">ターゲット</span><span class="sxs-lookup"><span data-stu-id="993b0-120">To</span></span>|<span data-ttu-id="993b0-121">手順</span><span class="sxs-lookup"><span data-stu-id="993b0-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="993b0-122">主キーの名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="993b0-122">Rename the primary key</span></span>|<span data-ttu-id="993b0-123">**[オブジェクト名]** ボックスに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="993b0-123">Type a new name in the **Name** box.</span></span> <span data-ttu-id="993b0-124">新しい名前が **[選択された主/一意キーまたはインデックス]** ボックスの一覧の名前と重複していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="993b0-124">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="993b0-125">クラスター化オプションを設定する。</span><span class="sxs-lookup"><span data-stu-id="993b0-125">Set the clustered option</span></span>|<span data-ttu-id="993b0-126">主キーのクラスター化インデックスを作成するには、 **[CLUSTERED として作成]** を選択し、ドロップダウン リスト ボックスからオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="993b0-126">To create a clustered index for the primary key, select **Create as CLUSTERED**, and select the option from the drop-down list box.</span></span> <span data-ttu-id="993b0-127">1 つのテーブルには、クラスター化インデックスを 1 つだけ作成できます。</span><span class="sxs-lookup"><span data-stu-id="993b0-127">Only one clustered index can exist per table.</span></span> <span data-ttu-id="993b0-128">インデックスにこのオプションを使用できない場合は、まず既存のクラスター化インデックスでこのチェック ボックスをオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="993b0-128">If this option is not available for your index, you must first clear this setting on the existing clustered index.</span></span><br /><br /> <span data-ttu-id="993b0-129">このオプションを選択しない場合、一意の非クラスター化インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="993b0-129">If this option is not selected, a unique nonclustered index is created.</span></span>|  
    |<span data-ttu-id="993b0-130">FILL FACTOR を定義する。</span><span class="sxs-lookup"><span data-stu-id="993b0-130">Define a fill factor</span></span>|<span data-ttu-id="993b0-131">**[FILL の指定]** カテゴリを展開して、 **[FILL FACTOR]** ボックスに 0 ～ 100 の整数を入力します。</span><span class="sxs-lookup"><span data-stu-id="993b0-131">Expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill factor** box.</span></span> <span data-ttu-id="993b0-132">Fill Factor の詳細とその使用方法については、「 [インデックスの FILL FACTOR の指定](../indexes/specify-fill-factor-for-an-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="993b0-132">For more information about fill factors and their uses, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>|  
    |<span data-ttu-id="993b0-133">列の順序を変更する。</span><span class="sxs-lookup"><span data-stu-id="993b0-133">Change the column order</span></span>|<span data-ttu-id="993b0-134">**[列]** をクリックして、プロパティの右にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="993b0-134">Select **Columns**, and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="993b0-135">**[インデックスの列]** ダイアログ ボックスで、主キーから列を削除します。</span><span class="sxs-lookup"><span data-stu-id="993b0-135">In the  **Index Columns** dialog box, remove the columns from the primary key.</span></span> <span data-ttu-id="993b0-136">次に、削除した列を必要な順序で再度追加します。</span><span class="sxs-lookup"><span data-stu-id="993b0-136">Then add the columns back in the order you want.</span></span> <span data-ttu-id="993b0-137">**[列名]** ボックスの一覧から列名を削除するだけで、キーから列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="993b0-137">To remove a column from the key, simply remove the column name from the **Column** name list.</span></span>|  
  
4.  <span data-ttu-id="993b0-138">**[ファイル]** メニューの **[ _<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="993b0-138">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="993b0-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="993b0-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="993b0-140">**主キーを変更するには**</span><span class="sxs-lookup"><span data-stu-id="993b0-140">**To modify a primary key**</span></span>  
  
 <span data-ttu-id="993b0-141">Transact-SQL を使用して PRIMARY KEY 制約を変更するには、最初に既存の PRIMARY KEY 制約を削除してから、新しい定義を使用して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="993b0-141">To modify a PRIMARY KEY constraint using Transact-SQL, you must first delete the existing PRIMARY KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="993b0-142">詳細については、「 [Delete Primary Keys](delete-primary-keys.md) 」および「 [Create Primary Keys](create-primary-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="993b0-142">For more information, see [Delete Primary Keys](delete-primary-keys.md) and [Create Primary Keys](create-primary-keys.md).</span></span>  
  
###  <a name="TsqlExample"></a>  

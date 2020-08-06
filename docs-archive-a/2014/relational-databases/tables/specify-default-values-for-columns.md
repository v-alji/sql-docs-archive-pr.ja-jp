---
title: 列の既定値の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 650347c29e1175c5a1fe646fc079478520dc8c6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643719"
---
# <a name="specify-default-values-for-columns"></a><span data-ttu-id="dc648-102">列の既定値の指定</span><span class="sxs-lookup"><span data-stu-id="dc648-102">Specify Default Values for Columns</span></span>
  <span data-ttu-id="dc648-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して列に入力される既定値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="dc648-103">You can specify a default value that will be entered in the column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="dc648-104">既定値を割り当てなかった場合、ユーザーが列に何も入力しないと、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dc648-104">If you do not assign a default value and the user leaves the column blank, then:</span></span>  
  
-   <span data-ttu-id="dc648-105">NULL 値を許可するオプションを設定している場合は、列に NULL が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="dc648-105">If you set the option to allow null values, NULL will be inserted into the column.</span></span>  
  
-   <span data-ttu-id="dc648-106">NULL 値を許可するオプションを設定していない場合は、列が空白のままになります。ただし、列に値を指定しないと、行を保存できません。</span><span class="sxs-lookup"><span data-stu-id="dc648-106">If you do not set the option to allow null values, the column will remain blank, but the user will not be able to save the row until they supply a value for the column.</span></span>  
  
 <span data-ttu-id="dc648-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="dc648-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dc648-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="dc648-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dc648-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="dc648-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="dc648-110">Security</span><span class="sxs-lookup"><span data-stu-id="dc648-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dc648-111">**既定値を指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="dc648-111">**To specify a default value, using:**</span></span>  
  
     [<span data-ttu-id="dc648-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dc648-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dc648-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dc648-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dc648-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="dc648-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="dc648-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="dc648-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="dc648-116">バインドされた既定値 (かっこなしで表示されている値) を **[既定値]** フィールドに入力した値で置き換える場合は、既定値のバインドを解除し、新しい既定値で置き換えるかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc648-116">If your entry in the **Default Value** field replaces a bound default (which is shown without parentheses), you will be prompted to unbind the default and replace it with your new default.</span></span>  
  
-   <span data-ttu-id="dc648-117">文字列を入力するには、値を単一引用符 (') で囲みます。二重引用符 (") では囲まないでください。二重引用符は、二重引用符で囲む必要がある識別子のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="dc648-117">To enter a text string, enclose the value in single quotation marks ('); do not use double quotation marks (") because they are reserved for quoted identifiers.</span></span>  
  
-   <span data-ttu-id="dc648-118">数値の既定値を入力するには、引用符で囲まずに番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc648-118">To enter a numeric default, enter the number without quotation marks around it.</span></span>  
  
-   <span data-ttu-id="dc648-119">オブジェクトまたは関数を入力するには、引用符で囲まずにオブジェクト名または関数名を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc648-119">To enter an object/function, enter the name of the object/function without quotation marks around it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dc648-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="dc648-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dc648-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="dc648-121">Permissions</span></span>  
 <span data-ttu-id="dc648-122">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dc648-122">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dc648-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="dc648-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="dc648-124">列の既定値を指定するには</span><span class="sxs-lookup"><span data-stu-id="dc648-124">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="dc648-125">**オブジェクト エクスプローラー**で、有効桁数を変更する列が含まれているテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc648-125">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="dc648-126">既定値を指定する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc648-126">Select the column for which you want to specify a default value.</span></span>  
  
3.  <span data-ttu-id="dc648-127">**[列のプロパティ]** タブで、 **[既定値またはバインド]** プロパティに新たな既定値を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc648-127">In the **Column Properties** tab, enter the new default value in the **Default Value or Binding** property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc648-128">数値の既定値を入力するには、数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc648-128">To enter a numeric default value, enter the number.</span></span> <span data-ttu-id="dc648-129">オブジェクトまたは関数の場合は、その名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc648-129">For an object or function enter its name.</span></span> <span data-ttu-id="dc648-130">英数字の場合は、その値を単一引用符で囲んで入力します。</span><span class="sxs-lookup"><span data-stu-id="dc648-130">For an alphanumeric default enter the value inside single quotes.</span></span>  
  
4.  <span data-ttu-id="dc648-131">**[ファイル]** メニューの **[_<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc648-131">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dc648-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="dc648-132">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="dc648-133">列の既定値を指定するには</span><span class="sxs-lookup"><span data-stu-id="dc648-133">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="dc648-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="dc648-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="dc648-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc648-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="dc648-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc648-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 <span data-ttu-id="dc648-137">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc648-137">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  

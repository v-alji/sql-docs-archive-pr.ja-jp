---
title: ユーザー定義データ型の別名の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.userdefineddatatype.general.f1
- sql12.swb.new.datatype.properties.general.f1
helpviewer_keywords:
- alias data types [SQL Server], creating
ms.assetid: b1dd8413-0cd0-411b-a79b-1bb043ccc62d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35db332c23e2df5a8e67c3677cd2411768816765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631080"
---
# <a name="create-a-user-defined-data-type-alias"></a><span data-ttu-id="185a9-102">ユーザー定義データ型の別名の作成</span><span class="sxs-lookup"><span data-stu-id="185a9-102">Create a User-Defined Data Type Alias</span></span>
  <span data-ttu-id="185a9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]にユーザー定義データ型の別名を新しく作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="185a9-103">This topic describes how to create a new user-defined data type alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="185a9-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="185a9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="185a9-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="185a9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="185a9-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="185a9-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="185a9-107">Security</span><span class="sxs-lookup"><span data-stu-id="185a9-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="185a9-108">**以下を使用してユーザー定義データ型の別名を作成するには:**</span><span class="sxs-lookup"><span data-stu-id="185a9-108">**To create a user-defined data type alias, using:**</span></span>  
  
     [<span data-ttu-id="185a9-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="185a9-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="185a9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="185a9-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="185a9-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="185a9-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="185a9-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="185a9-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="185a9-113">ユーザー定義データ型の別名は、識別子のルールに準拠した名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="185a9-113">The name of a user-defined data type alias must comply with the rules for identifiers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="185a9-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="185a9-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="185a9-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="185a9-115">Permissions</span></span>  
 <span data-ttu-id="185a9-116">現在のデータベース内の CREATE TYPE 権限、および *schema_name*に対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="185a9-116">Requires CREATE TYPE permission in the current database and ALTER permission on *schema_name*.</span></span> <span data-ttu-id="185a9-117">*schema_name* を指定しなかった場合は、現在のユーザーのスキーマを判断するための既定の名前解決ルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="185a9-117">If *schema_name* is not specified, the default name resolution rules for determining the schema for the current user apply.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="185a9-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="185a9-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-user-defined-data-type"></a><span data-ttu-id="185a9-119">ユーザー定義データ型を作成するには</span><span class="sxs-lookup"><span data-stu-id="185a9-119">To create a user-defined data type</span></span>  
  
1.  <span data-ttu-id="185a9-120">オブジェクト エクスプローラーで、 **[データベース]** を展開し、データベースを展開します。次に、 **[プログラミング]** 、 **[種類]** を順に展開し、 **[ユーザー定義データ型]** を右クリックして、 **[新しいユーザー定義データ型]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="185a9-120">In Object Explorer, expand **Databases**, expand a database, expand **Programmability**, expand **Types**, right-click **User-Defined Data Types**, and then click **New User-Defined Data Type**.</span></span>  
  
     <span data-ttu-id="185a9-121">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="185a9-121">**Allow NULLs**</span></span>  
     <span data-ttu-id="185a9-122">ユーザー定義データ型が NULL 値を受け入れるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="185a9-122">Specify whether the user-defined data type can accept NULL values.</span></span> <span data-ttu-id="185a9-123">既存のユーザー定義データ型に対する NULL 値の許容/非許容は編集できません。</span><span class="sxs-lookup"><span data-stu-id="185a9-123">The nullability of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="185a9-124">**データの種類**</span><span class="sxs-lookup"><span data-stu-id="185a9-124">**Data type**</span></span>  
     <span data-ttu-id="185a9-125">基本データ型をリスト ボックスから選択します。</span><span class="sxs-lookup"><span data-stu-id="185a9-125">Select the base data type from the list box.</span></span> <span data-ttu-id="185a9-126">リスト ボックスには、`geography`、`geometry`、`hierarchyid`、`sysname`、`timestamp`、`xml` の各データ型を除くすべてのデータ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="185a9-126">The list box displays all data types except for the `geography`, `geometry`, `hierarchyid`, `sysname`, `timestamp` , and `xml` data types.</span></span> <span data-ttu-id="185a9-127">既存のユーザー定義データ型のデータ型は編集できません。</span><span class="sxs-lookup"><span data-stu-id="185a9-127">The data type of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="185a9-128">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="185a9-128">**Default**</span></span>  
     <span data-ttu-id="185a9-129">必要に応じて、ユーザー定義データ型の別名にバインドするルールまたは既定値を選択します。</span><span class="sxs-lookup"><span data-stu-id="185a9-129">Optionally select a rule or a default to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="185a9-130">**[長さ]/[有効桁数]**</span><span class="sxs-lookup"><span data-stu-id="185a9-130">**Length/Precision**</span></span>  
     <span data-ttu-id="185a9-131">データ型の長さまたは有効桁数を表示します (適用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="185a9-131">Displays the length or precision of the data type as applicable.</span></span> <span data-ttu-id="185a9-132">**[長さ]** は、文字ベースのユーザー定義データ型に適用されます。 **[有効桁数]** は、数値に基づくユーザー定義データ型にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="185a9-132">**Length** applies to character-based user-defined data types; **Precision** applies only to numeric-based user-defined data types.</span></span> <span data-ttu-id="185a9-133">ラベルは、先に選択されたデータ型によって変わります。</span><span class="sxs-lookup"><span data-stu-id="185a9-133">The label changes depending on the data type selected earlier.</span></span> <span data-ttu-id="185a9-134">選択されているデータ型の長さまたは有効桁数が固定されている場合、このボックスは変更できません。</span><span class="sxs-lookup"><span data-stu-id="185a9-134">This box is not editable if the length or precision of the selected data type is fixed.</span></span>  
  
     <span data-ttu-id="185a9-135">長さは、`nvarchar(max)`、`varchar(max)`、`varbinary(max)` の各データ型に対しては表示されません。</span><span class="sxs-lookup"><span data-stu-id="185a9-135">Length is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
     <span data-ttu-id="185a9-136">**名前**</span><span class="sxs-lookup"><span data-stu-id="185a9-136">**Name**</span></span>  
     <span data-ttu-id="185a9-137">ユーザー定義データ型の別名を新規に作成する場合、ユーザー定義データ型を表すためにデータベース全体で使用する一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="185a9-137">If you are creating a new user-defined data type alias, type a unique name to be used across the database to represent the user-defined data type.</span></span> <span data-ttu-id="185a9-138">最大文字数は、システムデータ型と一致している必要があり `sysname` ます。</span><span class="sxs-lookup"><span data-stu-id="185a9-138">The maximum number of characters must match the system `sysname` data type.</span></span> <span data-ttu-id="185a9-139">既存のユーザー定義データ型の別名は編集できません。</span><span class="sxs-lookup"><span data-stu-id="185a9-139">The name of an existing user-defined data type alias is not editable.</span></span>  
  
     <span data-ttu-id="185a9-140">**Rule**</span><span class="sxs-lookup"><span data-stu-id="185a9-140">**Rule**</span></span>  
     <span data-ttu-id="185a9-141">必要に応じて、ユーザー定義データ型の別名にバインドするルールを選択します。</span><span class="sxs-lookup"><span data-stu-id="185a9-141">Optionally select a rule to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="185a9-142">**スケール**</span><span class="sxs-lookup"><span data-stu-id="185a9-142">**Scale**</span></span>  
     <span data-ttu-id="185a9-143">小数点の右側にとることのできる 10 進数の最大桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="185a9-143">Specify the maximum number of decimal digits that can be stored to the right of the decimal point.</span></span>  
  
     <span data-ttu-id="185a9-144">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="185a9-144">**Schema**</span></span>  
     <span data-ttu-id="185a9-145">現在のユーザーが使用できるすべてのスキーマの一覧からスキーマを選択します。</span><span class="sxs-lookup"><span data-stu-id="185a9-145">Select a schema from a list of all schemas available to the current user.</span></span> <span data-ttu-id="185a9-146">既定の選択は、現在のユーザーの既定のスキーマです。</span><span class="sxs-lookup"><span data-stu-id="185a9-146">The default selection is the default schema for the current user.</span></span>  
  
     <span data-ttu-id="185a9-147">**Storage**</span><span class="sxs-lookup"><span data-stu-id="185a9-147">**Storage**</span></span>  
     <span data-ttu-id="185a9-148">ユーザー定義データ型の別名に対応するストレージの最大サイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="185a9-148">Displays the maximum storage size for the user-defined data type alias.</span></span> <span data-ttu-id="185a9-149">ストレージの最大サイズは、有効桁数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="185a9-149">Maximum storage sizes vary, based on precision.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="185a9-150">1 - 9</span><span class="sxs-lookup"><span data-stu-id="185a9-150">1 - 9</span></span>|<span data-ttu-id="185a9-151">5</span><span class="sxs-lookup"><span data-stu-id="185a9-151">5</span></span>|  
    |<span data-ttu-id="185a9-152">10 - 19</span><span class="sxs-lookup"><span data-stu-id="185a9-152">10 - 19</span></span>|<span data-ttu-id="185a9-153">9</span><span class="sxs-lookup"><span data-stu-id="185a9-153">9</span></span>|  
    |<span data-ttu-id="185a9-154">20 - 28</span><span class="sxs-lookup"><span data-stu-id="185a9-154">20 - 28</span></span>|<span data-ttu-id="185a9-155">13</span><span class="sxs-lookup"><span data-stu-id="185a9-155">13</span></span>|  
    |<span data-ttu-id="185a9-156">29 - 38</span><span class="sxs-lookup"><span data-stu-id="185a9-156">29 - 38</span></span>|<span data-ttu-id="185a9-157">17</span><span class="sxs-lookup"><span data-stu-id="185a9-157">17</span></span>|  
  
     <span data-ttu-id="185a9-158">`nchar`およびデータ型の場合、 `nvarchar` ストレージ値は常に**長さ**の2倍の値になります。</span><span class="sxs-lookup"><span data-stu-id="185a9-158">For `nchar` and `nvarchar` data types, the storage value is always two times the value in **Length**.</span></span>  
  
     <span data-ttu-id="185a9-159">ストレージは、`nvarchar(max)`、`varchar(max)`、`varbinary(max)` の各データ型に対しては表示されません。</span><span class="sxs-lookup"><span data-stu-id="185a9-159">Storage is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
2.  <span data-ttu-id="185a9-160">**[新しいユーザー定義データ型]** ダイアログ ボックスで、 **[スキーマ]** ボックスに、このデータ型の別名を所有するスキーマを入力するか、参照ボタン [...] を使用してスキーマを選択します。</span><span class="sxs-lookup"><span data-stu-id="185a9-160">In the **New User-defined Data Type** dialog box, in the **Schema** box, type the schema to own this data type alias, or use the browse button to select the schema.</span></span>  
  
3.  <span data-ttu-id="185a9-161">**[名前]** ボックスに新しいデータ型の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="185a9-161">In the **Name** box, type a name for the new data type alias.</span></span>  
  
4.  <span data-ttu-id="185a9-162">**[データ型]** ボックスで、新しいデータ型の別名の基になるデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="185a9-162">In the **Data type** box, select the data type that the new data type alias will be based on.</span></span>  
  
5.  <span data-ttu-id="185a9-163">選択したデータ型に該当する場合は、 **[長さ]** 、 **[有効桁数]** 、および **[小数点以下桁数]** ボックスへの設定を完了します。</span><span class="sxs-lookup"><span data-stu-id="185a9-163">Complete the **Length**, **Precision**, and **Scale** boxes if appropriate for that data type.</span></span>  
  
6.  <span data-ttu-id="185a9-164">新しいデータ型の別名で NULL 値を許可する場合は、 **[NULL を許容]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="185a9-164">Check **Allow NULLs** if the new data type alias can permit NULL values.</span></span>  
  
7.  <span data-ttu-id="185a9-165">新しいデータ型の別名に既定値またはルールをバインドする場合は、 **[バインド]** で、 **[既定値]** または **[ルール]** ボックスへの設定を完了します。</span><span class="sxs-lookup"><span data-stu-id="185a9-165">In the **Binding** area, complete the **Default** or **Rule** boxes if you want to bind a default or rule to the new data type alias.</span></span> <span data-ttu-id="185a9-166">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、既定値やルールを作成できません。</span><span class="sxs-lookup"><span data-stu-id="185a9-166">Defaults and rules cannot be created in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="185a9-167">[!INCLUDE[tsql](../../includes/tsql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="185a9-167">Use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="185a9-168">既定値やルールを作成するためのサンプル コードは、テンプレート エクスプローラーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="185a9-168">Example code for creating defaults and rules are available in Template Explorer.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="185a9-169">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="185a9-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-user-defined-data-type-alias"></a><span data-ttu-id="185a9-170">ユーザー定義データ型の別名を作成するには</span><span class="sxs-lookup"><span data-stu-id="185a9-170">To create a user-defined data type alias</span></span>  
  
1.  <span data-ttu-id="185a9-171">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="185a9-171">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="185a9-172">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="185a9-172">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="185a9-173">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="185a9-173">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="185a9-174">この例では、システムから提供されている `varchar` データ型に基づいて、データ型の別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="185a9-174">This example creates a data type alias based on the system-supplied `varchar` data type.</span></span> <span data-ttu-id="185a9-175">データ型の別名 `ssn` 型は、11 桁の社会保障番号 (999-99-9999) を格納する列で使用されます。</span><span class="sxs-lookup"><span data-stu-id="185a9-175">The `ssn` data type alias is used for columns holding 11-digit social security numbers (999-99-9999).</span></span> <span data-ttu-id="185a9-176">この列で NULL 値は許容されません。</span><span class="sxs-lookup"><span data-stu-id="185a9-176">The column cannot be NULL.</span></span>  
  
```sql  
CREATE TYPE ssn  
FROM varchar(11) NOT NULL ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="185a9-177">参照</span><span class="sxs-lookup"><span data-stu-id="185a9-177">See Also</span></span>  
 <span data-ttu-id="185a9-178">[データベース識別子](database-identifiers.md) </span><span class="sxs-lookup"><span data-stu-id="185a9-178">[Database Identifiers](database-identifiers.md) </span></span>  
 [<span data-ttu-id="185a9-179">CREATE TYPE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="185a9-179">CREATE TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-type-transact-sql)  
  
  

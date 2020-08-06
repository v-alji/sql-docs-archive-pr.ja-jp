---
title: 列マッピング (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7994de1292677421447d441c1ac5aeb2b6fbc618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642902"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a><span data-ttu-id="5a40c-102">[列マッピング]\(SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="5a40c-102">Column Mappings (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="5a40c-103">[**列マッピング**] ダイアログボックスを使用すると、変換パラメーターを編集できます。</span><span class="sxs-lookup"><span data-stu-id="5a40c-103">Use the **Column Mappings** dialog box to edit transformation parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a40c-104">テーブルをコピーするオプションを選択する際に、テーブル内のすべての列をコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5a40c-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="5a40c-105">**\<ignore>** スキップする列については、このダイアログボックスの [**変換先**] 列でを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-105">Select **\<ignore>** in the **Destination** column of this dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="5a40c-106">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a40c-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="5a40c-107">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a40c-107">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="5a40c-108">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="5a40c-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="5a40c-109">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="5a40c-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="5a40c-110">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5a40c-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="5a40c-111">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a40c-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a40c-112">Options</span><span class="sxs-lookup"><span data-stu-id="5a40c-112">Options</span></span>  
 <span data-ttu-id="5a40c-113">**ソース**</span><span class="sxs-lookup"><span data-stu-id="5a40c-113">**Source**</span></span>  
 <span data-ttu-id="5a40c-114">選択した変換元のテーブル、ビュー、またはクエリを識別します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-114">Identifies the selected source table, view, or query.</span></span>  
  
 <span data-ttu-id="5a40c-115">**宛先**</span><span class="sxs-lookup"><span data-stu-id="5a40c-115">**Destination**</span></span>  
 <span data-ttu-id="5a40c-116">選択した変換先のテーブル、ビュー、またはクエリを識別します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-116">Identifies the selected destination table, view, or query.</span></span>  
  
 <span data-ttu-id="5a40c-117">**[変換先テーブルを作成する]**</span><span class="sxs-lookup"><span data-stu-id="5a40c-117">**Create destination table/file**</span></span>  
 <span data-ttu-id="5a40c-118">変換先テーブルが存在しない場合、変換先テーブルを作成するかするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-118">Specify whether to create the destination table if it does not already exist.</span></span>  
  
 <span data-ttu-id="5a40c-119">**[変換先テーブル内の行を削除する]**</span><span class="sxs-lookup"><span data-stu-id="5a40c-119">**Delete rows in destination table/file**</span></span>  
 <span data-ttu-id="5a40c-120">新しいデータを読み込む前に、既存のテーブルからデータを削除するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-120">Specify whether to clear the data from an existing table before loading new data.</span></span>  
  
 <span data-ttu-id="5a40c-121">**変換先テーブル/ファイルに行を追加する**</span><span class="sxs-lookup"><span data-stu-id="5a40c-121">**Append rows to destination table/file**</span></span>  
 <span data-ttu-id="5a40c-122">既存のテーブルに存在するデータに、新しいデータを追加するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-122">Specify whether to append the new data to the data already present in an existing table.</span></span>  
  
 <span data-ttu-id="5a40c-123">**SQL の編集**</span><span class="sxs-lookup"><span data-stu-id="5a40c-123">**Edit SQL**</span></span>  
 <span data-ttu-id="5a40c-124">[**テーブル作成 SQL ステートメント**] ダイアログボックスの既定のステートメントを使用するか、目的に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-124">Use the default statement in the **Create Table SQL Statement** dialog box, or modify it for your purposes.</span></span> <span data-ttu-id="5a40c-125">このステートメントを変更する場合、テーブル マップに関連する変更を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a40c-125">If you modify this statement, you must also make associated changes to table mapping.</span></span>  
  
 <span data-ttu-id="5a40c-126">**変換先テーブルを削除した後、再作成する**</span><span class="sxs-lookup"><span data-stu-id="5a40c-126">**Drop and re-create destination table**</span></span>  
 <span data-ttu-id="5a40c-127">変換先テーブルを上書きします。</span><span class="sxs-lookup"><span data-stu-id="5a40c-127">Choose this option to overwrite the destination table.</span></span> <span data-ttu-id="5a40c-128">このオプションは、ウィザードを使用して変換先テーブルを作成する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a40c-128">This option is only available when you use the wizard to create the destination table.</span></span> <span data-ttu-id="5a40c-129">ウィザードによって作成されたパッケージを保存し、その後パッケージを再び実行すると、変換先テーブルは削除されて、再作成されます。</span><span class="sxs-lookup"><span data-stu-id="5a40c-129">The destination table is only dropped and re-created if you save the package that the wizard creates, and then run the package again.</span></span>  
  
 <span data-ttu-id="5a40c-130">**ID 挿入を許可する**</span><span class="sxs-lookup"><span data-stu-id="5a40c-130">**Enable identity insert**</span></span>  
 <span data-ttu-id="5a40c-131">変換元データの既存の ID 値を変換先テーブルの ID 列に挿入します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-131">Choose this option to allow existing identity values in the source data to be inserted into an identity column in the destination table.</span></span> <span data-ttu-id="5a40c-132">既定では、変換先の ID 列に対して挿入は許可されません。</span><span class="sxs-lookup"><span data-stu-id="5a40c-132">By default, the destination identity column does not allow this.</span></span>  
  
 <span data-ttu-id="5a40c-133">**マッピング**</span><span class="sxs-lookup"><span data-stu-id="5a40c-133">**Mappings**</span></span>  
 <span data-ttu-id="5a40c-134">データ ソースの各列が変換先の列にどのようにマップされるかを表示します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-134">Displays how each column in the data source maps to a column in the destination.</span></span>  
  
 <span data-ttu-id="5a40c-135">この一覧には、次の列があります。</span><span class="sxs-lookup"><span data-stu-id="5a40c-135">This list has the following columns:</span></span>  
  
 <span data-ttu-id="5a40c-136">**ソース**</span><span class="sxs-lookup"><span data-stu-id="5a40c-136">**Source**</span></span>  
 <span data-ttu-id="5a40c-137">変換パラメーターを設定する各変換元列を表示します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-137">View each source column for which you can set transformation parameters.</span></span>  
  
 <span data-ttu-id="5a40c-138">**宛先**</span><span class="sxs-lookup"><span data-stu-id="5a40c-138">**Destination**</span></span>  
 <span data-ttu-id="5a40c-139">コピー操作中に列を無視するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-139">Specify whether you want to ignore a column during the copy operation.</span></span> <span data-ttu-id="5a40c-140">スキップする列に対してこの列を選択すると、列のサブセットのみをコピーでき **\<ignore>** ます。</span><span class="sxs-lookup"><span data-stu-id="5a40c-140">You can copy only a subset of columns by selecting **\<ignore>** in this column for columns that you want to skip.</span></span> <span data-ttu-id="5a40c-141">列をマップする前に、マップされないすべての列を無視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a40c-141">Before you map columns, you must ignore all columns that will not be mapped.</span></span>  
  
 <span data-ttu-id="5a40c-142">**Type**</span><span class="sxs-lookup"><span data-stu-id="5a40c-142">**Type**</span></span>  
 <span data-ttu-id="5a40c-143">列のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-143">Select a data type for the column.</span></span>  
  
 <span data-ttu-id="5a40c-144">**NULL 値の使用**</span><span class="sxs-lookup"><span data-stu-id="5a40c-144">**Nullable**</span></span>  
 <span data-ttu-id="5a40c-145">列が NULL 値を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-145">Specify whether a column will allow a null value.</span></span>  
  
 <span data-ttu-id="5a40c-146">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="5a40c-146">**Size**</span></span>  
 <span data-ttu-id="5a40c-147">列の文字数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-147">Specify the number of characters in the column.</span></span>  
  
 <span data-ttu-id="5a40c-148">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="5a40c-148">**Precision**</span></span>  
 <span data-ttu-id="5a40c-149">桁数を参照して、表示されるデータの有効桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-149">Specify the precision of displayed data, referring to the number of digits.</span></span>  
  
 <span data-ttu-id="5a40c-150">**スケール**</span><span class="sxs-lookup"><span data-stu-id="5a40c-150">**Scale**</span></span>  
 <span data-ttu-id="5a40c-151">桁数を参照して、表示されるデータの小数点以下桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a40c-151">Specify the scale of displayed data, referring to the number of decimal places.</span></span>  
  
  

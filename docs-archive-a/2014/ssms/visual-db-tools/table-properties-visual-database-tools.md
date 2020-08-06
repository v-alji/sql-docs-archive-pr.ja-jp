---
title: '[テーブルのプロパティ] (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.tabledesigner
- vdt.designers.properties.Table
ms.assetid: cc392987-1aab-45f5-b5af-a26be53409bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: df4a0332ebc622b069c468e51c461b7cba20aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720702"
---
# <a name="table-properties-visual-database-tools"></a><span data-ttu-id="95f3d-102">[テーブルのプロパティ] \(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="95f3d-102">Table Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="95f3d-103">以下のプロパティは、テーブル デザイナーで右クリックして [プロパティ] をクリックすると開く [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-103">These properties appear in the Properties window when you right click in Table Designer and select Properties.</span></span> <span data-ttu-id="95f3d-104">特に断りのない限り、テーブルが選択されているときにこれらのプロパティを [プロパティ] ウィンドウで編集できます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-104">Unless otherwise noted, you can edit these properties in the Properties window when the table is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95f3d-105">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95f3d-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="95f3d-106">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="95f3d-107">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="show-table-properties-in-table-designer"></a><span data-ttu-id="95f3d-108">テーブル デザイナーでのテーブル プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="95f3d-108">Show Table Properties in Table Designer</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95f3d-109">このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。</span><span class="sxs-lookup"><span data-stu-id="95f3d-109">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
 <span data-ttu-id="95f3d-110">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="95f3d-110">**Identity Category**</span></span>  
 <span data-ttu-id="95f3d-111">展開して **[名前]** 、 **[説明]** 、および **[スキーマ]** の各プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-111">Expands to show properties for **Name**, **Description**, and **Schema**.</span></span>  
  
 <span data-ttu-id="95f3d-112">**Name**</span><span class="sxs-lookup"><span data-stu-id="95f3d-112">**Name**</span></span>  
 <span data-ttu-id="95f3d-113">テーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-113">Displays the name of the table.</span></span> <span data-ttu-id="95f3d-114">名前を編集するには、テキスト ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-114">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="95f3d-115">テーブルを参照するクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムがある場合は、テーブル名を変更すると、各オブジェクトが無効になります。</span><span class="sxs-lookup"><span data-stu-id="95f3d-115">If existing queries, views, user-defined functions, stored procedures, or programs refer to the table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="95f3d-116">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="95f3d-116">**Database Name**</span></span>  
 <span data-ttu-id="95f3d-117">選択したテーブルのデータ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-117">Shows the name of the data source of the selected table.</span></span>  
  
 <span data-ttu-id="95f3d-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="95f3d-118">**Description**</span></span>  
 <span data-ttu-id="95f3d-119">選択したテーブルの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-119">Shows a description of the selected table.</span></span> <span data-ttu-id="95f3d-120">説明全体を表示したり、説明を編集したりするには、説明をクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95f3d-120">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="95f3d-121">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-121">**Schema**</span></span>  
 <span data-ttu-id="95f3d-122">このテーブルが所属するスキーマの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-122">Shows the name of the schema to which this table belongs.</span></span> <span data-ttu-id="95f3d-123">Microsoft SQL Server だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-123">(Applies only to Microsoft SQL Server.)</span></span>  
  
 <span data-ttu-id="95f3d-124">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-124">**Server Name**</span></span>  
 <span data-ttu-id="95f3d-125">データ ソースのサーバーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-125">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="95f3d-126">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="95f3d-126">**Table Designer Category**</span></span>  
 <span data-ttu-id="95f3d-127">展開して **[IDENTITY 列]** 、 **[Indexable]** 、および **[Replicated]** の各プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-127">Expands to show properties for **Identity Column**, **Is Indexable**, and **Is Replicated**.</span></span>  
  
 <span data-ttu-id="95f3d-128">**[IDENTITY 列]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-128">**Identity Column**</span></span>  
 <span data-ttu-id="95f3d-129">テーブルの ID 列として使用されている列を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-129">Shows the column used as the table's identity column.</span></span> <span data-ttu-id="95f3d-130">ID 列を変更するには、ドロップダウン リストから列を選択します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-130">To change the identity column, choose from the drop-down list.</span></span> <span data-ttu-id="95f3d-131">数値データ型の列だけが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-131">Only columns of a numeric data type will show in the list.</span></span>  
  
 <span data-ttu-id="95f3d-132">**[Indexable]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-132">**Is Indexable**</span></span>  
 <span data-ttu-id="95f3d-133">テーブルにインデックスを付けることができるかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-133">Shows whether the table can be indexed.</span></span> <span data-ttu-id="95f3d-134">テーブルにインデックスを付けることができない場合、テーブルの所有者でないか、データ型が text、ntext、または image の列がテーブルに含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="95f3d-134">If the table is not indexable it may be because you are not the table owner or because the table contains columns with data types of text, ntext, or image.</span></span>  
  
 <span data-ttu-id="95f3d-135">**[Replicated]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-135">**Is Replicated**</span></span>  
 <span data-ttu-id="95f3d-136">テーブルが別の場所でレプリケートされているかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-136">Shows whether the table is replicated in another location.</span></span>  
  
 <span data-ttu-id="95f3d-137">**[標準データ スペースの指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="95f3d-137">**Regular Data Space Specification Category**</span></span>  
 <span data-ttu-id="95f3d-138">展開して **[(データ スペースの種類)]** 、 **[ファイル グループまたはパーティション スキーム名]** 、および **[パーティション列の一覧]** の各プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-138">Expands to show properties for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="95f3d-139">**[(データ スペースの種類)]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-139">**(Data Space Type)**</span></span>  
 <span data-ttu-id="95f3d-140">テーブルがファイル グループまたはパーティション スキームを使用して保存されるかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-140">Shows whether this table is stored using a filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="95f3d-141">**[ファイル グループまたはパーティション スキーム名]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-141">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="95f3d-142">ファイル グループまたはパーティション スキームの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-142">Shows the name of the filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="95f3d-143">**[パーティション列の一覧]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-143">**Partition Column List**</span></span>  
 <span data-ttu-id="95f3d-144">**[パーティション列の一覧]** ダイアログ ボックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-144">Provides access to the **Partition Column List** dialog box.</span></span>  
  
 <span data-ttu-id="95f3d-145">**[行 GUID 列]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-145">**Row GUID Column**</span></span>  
 <span data-ttu-id="95f3d-146">Microsoft SQL Server がテーブルの ROWGUID 列として使用する列を表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-146">Shows the column used by Microsoft SQL Server as the table's ROWGUID column.</span></span> <span data-ttu-id="95f3d-147">ROWGUID 列を変更するには、ドロップダウン リストから列を選択します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-147">To change the ROWGUID column, choose from the drop-down list.</span></span> <span data-ttu-id="95f3d-148">SQL Server 7.0 以降だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="95f3d-148">(Applies only to SQL Server 7.0 or higher.)</span></span>  
  
 <span data-ttu-id="95f3d-149">**[テキスト/イメージのファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="95f3d-149">**Text/Image Filegroup**</span></span>  
 <span data-ttu-id="95f3d-150">text データ型、または image データ型の列について、ファイル グループを選択できるドロップダウン リストを表示します。</span><span class="sxs-lookup"><span data-stu-id="95f3d-150">Provides a drop-down list from which you can choose the filegroup for columns that have text or image data types.</span></span> <span data-ttu-id="95f3d-151">パーティション スキームを使用してテーブルを保存する場合は、このフィールドを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="95f3d-151">If the table is stored using a partition scheme, leave this field blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f3d-152">参照</span><span class="sxs-lookup"><span data-stu-id="95f3d-152">See Also</span></span>  
 [<span data-ttu-id="95f3d-153">テーブルのデザイン (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="95f3d-153">Design Tables &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  

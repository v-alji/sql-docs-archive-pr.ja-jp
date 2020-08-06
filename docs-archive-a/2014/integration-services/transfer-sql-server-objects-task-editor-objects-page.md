---
title: '[オブジェクトの転送タスクエディター] ([オブジェクト] ページ) SQL ServerMicrosoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjects.objects.f1
helpviewer_keywords:
- Transfer SQL Server Objects Task Editor
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7038939b02d17b2449a374be51f7f9fa42eae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718452"
---
# <a name="transfer-sql-server-objects-task-editor-objects-page"></a><span data-ttu-id="f84c0-102">[SQL Server オブジェクトの転送タスク エディター] ([オブジェクト] ページ)</span><span class="sxs-lookup"><span data-stu-id="f84c0-102">Transfer SQL Server Objects Task Editor (Objects Page)</span></span>
  <span data-ttu-id="f84c0-103">**[SQL Server オブジェクトの転送タスク エディター]** ダイアログ ボックスの **[オブジェクト]** ページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス間で 1 つまたは複数の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトをコピーするためのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-103">Use the **Objects** page of the **Transfer SQL Server Objects Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="f84c0-104">コピーできる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトには、テーブル、ビュー、ストアド プロシージャ、およびユーザー定義関数などがあります。</span><span class="sxs-lookup"><span data-stu-id="f84c0-104">Tables, views, stored procedures, and user-defined functions are a few examples of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects that you can copy.</span></span> <span data-ttu-id="f84c0-105">このタスクの詳細については、「 [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f84c0-105">For more information about this task, see [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f84c0-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの転送タスクを作成するユーザーは、転送元サーバー オブジェクトをコピー用に選択するために必要な権限と、オブジェクトの転送先の転送先サーバー データベースにアクセスするために必要な権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f84c0-106">The user who creates the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task must have sufficient permissions on the source server objects to select them for copying, and permission to access the destination server database where the objects will be transferred.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="f84c0-107">静的オプション</span><span class="sxs-lookup"><span data-stu-id="f84c0-107">Static Options</span></span>  
 <span data-ttu-id="f84c0-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="f84c0-108">**SourceConnection**</span></span>  
 <span data-ttu-id="f84c0-109">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして、転送元サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="f84c0-110">**[SourceDatabase]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-110">**SourceDatabase**</span></span>  
 <span data-ttu-id="f84c0-111">オブジェクトのコピー元の転送元サーバー上のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-111">Select a database on the source server from which objects will be copied.</span></span>  
  
 <span data-ttu-id="f84c0-112">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="f84c0-112">**DestinationConnection**</span></span>  
 <span data-ttu-id="f84c0-113">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして、転送先サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-113">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="f84c0-114">**[DestinationDatabase]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-114">**DestinationDatabase**</span></span>  
 <span data-ttu-id="f84c0-115">オブジェクトのコピー先の転送先サーバー上のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-115">Select a database on the destination server to which objects will be copied.</span></span>  
  
 <span data-ttu-id="f84c0-116">**[DropObjectsFirst]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-116">**DropObjectsFirst**</span></span>  
 <span data-ttu-id="f84c0-117">選択したオブジェクトをコピーを開始する前に転送先サーバー上で削除するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-117">Select whether the selected objects will be dropped first on the destination server before copying.</span></span>  
  
 <span data-ttu-id="f84c0-118">**[IncludeExtendedProperties]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-118">**IncludeExtendedProperties**</span></span>  
 <span data-ttu-id="f84c0-119">転送元サーバーから転送先サーバーにオブジェクトをコピーするときに拡張プロパティを含めるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-119">Select whether extended properties will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="f84c0-120">**[CopyData]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-120">**CopyData**</span></span>  
 <span data-ttu-id="f84c0-121">転送元サーバーから転送先サーバーにオブジェクトをコピーするときにデータを含めるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-121">Select whether data will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="f84c0-122">**[ExistingData]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-122">**ExistingData**</span></span>  
 <span data-ttu-id="f84c0-123">転送先サーバーにデータをどのようにコピーするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-123">Specify how data will be copied to the destination server.</span></span> <span data-ttu-id="f84c0-124">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="f84c0-124">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="f84c0-125">値</span><span class="sxs-lookup"><span data-stu-id="f84c0-125">Value</span></span>|<span data-ttu-id="f84c0-126">説明</span><span class="sxs-lookup"><span data-stu-id="f84c0-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f84c0-127">**Replace**</span><span class="sxs-lookup"><span data-stu-id="f84c0-127">**Replace**</span></span>|<span data-ttu-id="f84c0-128">転送先サーバー上のデータは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-128">Data on the destination server will be overwritten.</span></span>|  
|<span data-ttu-id="f84c0-129">**Append**</span><span class="sxs-lookup"><span data-stu-id="f84c0-129">**Append**</span></span>|<span data-ttu-id="f84c0-130">転送元サーバーからコピーされたデータは、転送先サーバー上の既存のデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-130">Data copied from the source server will be appended to existing data on the destination server.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f84c0-131">**[ExistingData]** オプションは、 **[CopyData]** が **[True]** に設定されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-131">The **ExistingData** option is only available when **CopyData** is set to **True**.</span></span>  
  
 <span data-ttu-id="f84c0-132">**[CopySchema]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-132">**CopySchema**</span></span>  
 <span data-ttu-id="f84c0-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの転送タスクによる処理中にスキーマをコピーするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-133">Select whether the schema is copied during the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f84c0-134">**[CopySchema]** は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-134">**CopySchema** is only available for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-135">**[UseCollation]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-135">**UseCollation**</span></span>  
 <span data-ttu-id="f84c0-136">転送元サーバー上で指定されている照合順序をオブジェクトの転送に含めるかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-136">Select whether the transfer of objects should include the collation specified on the source server.</span></span>  
  
 <span data-ttu-id="f84c0-137">**[IncludeDependentObjects]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-137">**IncludeDependentObjects**</span></span>  
 <span data-ttu-id="f84c0-138">コピーの対象として選択されたオブジェクトをコピーするときに、そのオブジェクトに依存している他のオブジェクトもコピーするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-138">Select whether copying the selected objects will cascade to include other objects that depend on the objects selected for copying.</span></span>  
  
 <span data-ttu-id="f84c0-139">**[CopyAllObjects]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-139">**CopyAllObjects**</span></span>  
 <span data-ttu-id="f84c0-140">指定した転送元データベース内のすべてのオブジェクトをコピーするか、選択したオブジェクトだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-140">Select whether the task will copy all objects in the specified source database or only selected objects.</span></span>  <span data-ttu-id="f84c0-141">このオプションを [False] に設定すると、オブジェクトを転送するためのオプションが表示され、さらに **[CopyAllObjects]** セクションに動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-141">Setting this option to False gives you the option to select the objects to transfer, and displays the dynamic options in the section, **CopyAllObjects**.</span></span>  
  
 <span data-ttu-id="f84c0-142">**[ObjectsToCopy]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-142">**ObjectsToCopy**</span></span>  
 <span data-ttu-id="f84c0-143">**[ObjectsToCopy]** を展開して、転送元データベースから転送先データベースにコピーするオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-143">Expand **ObjectsToCopy** to specify which objects should be copied from the source database to the destination database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f84c0-144">**[ObjectsToCopy]** は、 **[CopyAllObjects]** が **[False]** に設定されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-144">**ObjectsToCopy** is only available when **CopyAllObjects** is set to **False**.</span></span>  
  
 <span data-ttu-id="f84c0-145">次の種類のオブジェクトをコピーするオプションは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-145">The options to copy the following types of objects are supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="f84c0-146">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="f84c0-146">Assemblies</span></span>  
  
 <span data-ttu-id="f84c0-147">パーティション関数</span><span class="sxs-lookup"><span data-stu-id="f84c0-147">Partition functions</span></span>  
  
 <span data-ttu-id="f84c0-148">パーティション構成</span><span class="sxs-lookup"><span data-stu-id="f84c0-148">Partition schemes</span></span>  
  
 <span data-ttu-id="f84c0-149">スキーマ</span><span class="sxs-lookup"><span data-stu-id="f84c0-149">Schemas</span></span>  
  
 <span data-ttu-id="f84c0-150">ユーザー定義集計</span><span class="sxs-lookup"><span data-stu-id="f84c0-150">User-defined aggregates</span></span>  
  
 <span data-ttu-id="f84c0-151">ユーザー定義データ型</span><span class="sxs-lookup"><span data-stu-id="f84c0-151">User-defined types</span></span>  
  
 <span data-ttu-id="f84c0-152">XML スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="f84c0-152">XML schema collections</span></span>  
  
 <span data-ttu-id="f84c0-153">**[CopyDatabaseUsers]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-153">**CopyDatabaseUsers**</span></span>  
 <span data-ttu-id="f84c0-154">データベース ユーザーを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-154">Specify whether database users should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-155">**[CopyDatabaseRoles]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-155">**CopyDatabaseRoles**</span></span>  
 <span data-ttu-id="f84c0-156">データベース ロールを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-156">Specify whether database roles should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-157">**[CopySqlServerLogins]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-157">**CopySqlServerLogins**</span></span>  
 <span data-ttu-id="f84c0-158">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-158">Specify whether [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-159">**[CopyObjectLevelPermissions]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-159">**CopyObjectLevelPermissions**</span></span>  
 <span data-ttu-id="f84c0-160">オブジェクトレベルの権限を転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-160">Specify whether object-level permissions should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-161">**[CopyIndexes]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-161">**CopyIndexes**</span></span>  
 <span data-ttu-id="f84c0-162">インデックスを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-162">Specify whether indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-163">**[CopyTriggers]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-163">**CopyTriggers**</span></span>  
 <span data-ttu-id="f84c0-164">トリガーを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-164">Specify whether triggers should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-165">**[CopyFullTextIndexes]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-165">**CopyFullTextIndexes**</span></span>  
 <span data-ttu-id="f84c0-166">フルテキスト インデックスを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-166">Specify whether full-text indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-167">**[CopyPrimaryKeys]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-167">**CopyPrimaryKeys**</span></span>  
 <span data-ttu-id="f84c0-168">主キーを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-168">Specify whether primary keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-169">**[CopyForeignKeys]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-169">**CopyForeignKeys**</span></span>  
 <span data-ttu-id="f84c0-170">外部キーを転送に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-170">Specify whether foreign keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="f84c0-171">**[GenerateScriptsInUnicode]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-171">**GenerateScriptsInUnicode**</span></span>  
 <span data-ttu-id="f84c0-172">転送スクリプトを Unicode 形式で生成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-172">Specify whether the generated transfer scripts are in Unicode format.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="f84c0-173">動的オプション</span><span class="sxs-lookup"><span data-stu-id="f84c0-173">Dynamic Options</span></span>  
  
### <a name="copyallobjects--false"></a><span data-ttu-id="f84c0-174">[CopyAllObjects] = [False]</span><span class="sxs-lookup"><span data-stu-id="f84c0-174">CopyAllObjects = False</span></span>  
 <span data-ttu-id="f84c0-175">**[CopyAllTables]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-175">**CopyAllTables**</span></span>  
 <span data-ttu-id="f84c0-176">指定した転送元データベース内のすべてのテーブルをコピーするか、選択したテーブルだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-176">Select whether the task will copy all tables in the specified source database or only the selected tables.</span></span>  
  
 <span data-ttu-id="f84c0-177">**[TablesList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-177">**TablesList**</span></span>  
 <span data-ttu-id="f84c0-178">**[テーブルの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-178">Click to open the **Select Tables** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-179">**[CopyAllViews]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-179">**CopyAllViews**</span></span>  
 <span data-ttu-id="f84c0-180">指定した転送元データベース内のすべてのビューをコピーするか、選択したビューだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-180">Select whether the task will copy all views in the specified source database or only the selected views.</span></span>  
  
 <span data-ttu-id="f84c0-181">**[ViewsList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-181">**ViewsList**</span></span>  
 <span data-ttu-id="f84c0-182">**[ビューの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-182">Click to open the **Select Views** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-183">**[CopyAllStoredProcedures]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-183">**CopyAllStoredProcedures**</span></span>  
 <span data-ttu-id="f84c0-184">指定した転送元データベース内のすべてのユーザー定義ストアド プロシージャをコピーするか、選択したプロシージャだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-184">Select whether the task will copy all user-defined stored procedures in the specified source database or only the selected procedures.</span></span>  
  
 <span data-ttu-id="f84c0-185">**[StoredProceduresList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-185">**StoredProceduresList**</span></span>  
 <span data-ttu-id="f84c0-186">**[ストアド プロシージャの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-186">Click to open the **Select Stored Procedures** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-187">**[CopyAllUserDefinedFunctions]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-187">**CopyAllUserDefinedFunctions**</span></span>  
 <span data-ttu-id="f84c0-188">指定した転送元データベース内のすべてのユーザー定義関数 (UDF) をコピーするか、選択した UDF だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-188">Select whether the task will copy all user-defined functions in the specified source database or only the selected UDFs.</span></span>  
  
 <span data-ttu-id="f84c0-189">**[UserDefinedFunctionsList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-189">**UserDefinedFunctionsList**</span></span>  
 <span data-ttu-id="f84c0-190">**[ユーザー定義関数の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-190">Click to open the **Select User Defined Functions** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-191">**[CopyAllDefaults]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-191">**CopyAllDefaults**</span></span>  
 <span data-ttu-id="f84c0-192">指定した転送元データベース内のすべての既定値をコピーするか、選択した既定値だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-192">Select whether the task will copy all defaults in the specified source database or only the selected defaults.</span></span>  
  
 <span data-ttu-id="f84c0-193">**[DefaultsList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-193">**DefaultsList**</span></span>  
 <span data-ttu-id="f84c0-194">**[既定値の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-194">Click to open the **Select Defaults** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-195">**[CopyAllUserDefinedDataTypes]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-195">**CopyAllUserDefinedDataTypes**</span></span>  
 <span data-ttu-id="f84c0-196">指定した転送元データベース内のすべてのユーザー定義データ型をコピーするか、選択したユーザー定義データ型だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-196">Select whether the task will copy all user-defined data types in the specified source database or only the selected user-defined data types.</span></span>  
  
 <span data-ttu-id="f84c0-197">**[UserDefinedDataTypesList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-197">**UserDefinedDataTypesList**</span></span>  
 <span data-ttu-id="f84c0-198">**[ユーザー定義データ型の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-198">Click to open the **Select User-Defined Data Types** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-199">**[CopyAllPartitionFunctions]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-199">**CopyAllPartitionFunctions**</span></span>  
 <span data-ttu-id="f84c0-200">指定した転送元データベース内のすべてのユーザー定義パーティション関数をコピーするか、選択したパーティション関数だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-200">Select whether the task will copy all user-defined partition functions in the specified source database or only the selected partition functions.</span></span> <span data-ttu-id="f84c0-201">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-201">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-202">**[PartitionFunctionsList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-202">**PartitionFunctionsList**</span></span>  
 <span data-ttu-id="f84c0-203">**[パーティション関数の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-203">Click to open the **Select Partition Functions** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-204">**[CopyAllPartitionSchemes]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-204">**CopyAllPartitionSchemes**</span></span>  
 <span data-ttu-id="f84c0-205">指定した転送元データベース内のすべてのパーティション構成をコピーするか、選択したパーティション構成だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-205">Select whether the task will copy all partition schemes in the specified source database or only the selected partition schemes.</span></span> <span data-ttu-id="f84c0-206">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-206">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-207">**[PartitionSchemesList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-207">**PartitionSchemesList**</span></span>  
 <span data-ttu-id="f84c0-208">**[パーティション構成の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-208">Click to open the **Select Partition Schemes** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-209">**[CopyAllSchemas]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-209">**CopyAllSchemas**</span></span>  
 <span data-ttu-id="f84c0-210">指定した転送元データベース内のすべてのスキーマをコピーするか、選択したスキーマだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-210">Select whether the task will copy all schemas in the specified source database or only the selected schemas.</span></span> <span data-ttu-id="f84c0-211">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-211">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-212">**[SchemasList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-212">**SchemasList**</span></span>  
 <span data-ttu-id="f84c0-213">**[スキーマの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-213">Click to open the **Select Schemas** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-214">**[CopyAllSqlAssemblies]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-214">**CopyAllSqlAssemblies**</span></span>  
 <span data-ttu-id="f84c0-215">指定した転送元データベース内のすべての SQL アセンブリをコピーするか、選択した SQL アセンブリだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-215">Select whether the task will copy all SQL assemblies in the specified source database or only the selected SQL assemblies.</span></span> <span data-ttu-id="f84c0-216">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-216">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-217">**[SqlAssembliesList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-217">**SqlAssembliesList**</span></span>  
 <span data-ttu-id="f84c0-218">**[SQL アセンブリの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-218">Click to open the **Select SQL Assemblies** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-219">**[CopyAllUserDefinedAggregates]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-219">**CopyAllUserDefinedAggregates**</span></span>  
 <span data-ttu-id="f84c0-220">指定した転送元データベース内のすべてのユーザー定義集計をコピーするか、選択したユーザー定義集計だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-220">Select whether the task will copy all user-defined aggregates in the specified source database or only the selected user-defined aggregates.</span></span> <span data-ttu-id="f84c0-221">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-221">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-222">**[UserDefinedAggregatesList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-222">**UserDefinedAggregatesList**</span></span>  
 <span data-ttu-id="f84c0-223">**[ユーザー定義集計の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-223">Click to open the **Select User-Defined Aggregates** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-224">**[CopyAllUserDefinedTypes]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-224">**CopyAllUserDefinedTypes**</span></span>  
 <span data-ttu-id="f84c0-225">指定した転送元データベース内のすべてのユーザー定義型 (UDT) をコピーするか、選択した UDT だけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-225">Select whether the task will copy all user-defined types in the specified source database or only the selected UDTs.</span></span> <span data-ttu-id="f84c0-226">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-226">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-227">**[UserDefinedTypes]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-227">**UserDefinedTypes**</span></span>  
 <span data-ttu-id="f84c0-228">**[ユーザー定義型の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-228">Click to open the **Select User-Defined Types** dialog box.</span></span>  
  
 <span data-ttu-id="f84c0-229">**[CopyAllXmlSchemaCollections]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-229">**CopyAllXmlSchemaCollections**</span></span>  
 <span data-ttu-id="f84c0-230">指定した転送元データベース内のすべての XML スキーマ コレクションをコピーするか、選択した XML スキーマ コレクションだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84c0-230">Select whether the task will copy all XML Schema collections in the specified source database or only the selected XML schema collections.</span></span> <span data-ttu-id="f84c0-231">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-231">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f84c0-232">**[XmlSchemaCollectionsList]**</span><span class="sxs-lookup"><span data-stu-id="f84c0-232">**XmlSchemaCollectionsList**</span></span>  
 <span data-ttu-id="f84c0-233">**[XML スキーマ コレクションの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f84c0-233">Click to open the **Select XML Schema Collections** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f84c0-234">参照</span><span class="sxs-lookup"><span data-stu-id="f84c0-234">See Also</span></span>  
 <span data-ttu-id="f84c0-235">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f84c0-235">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f84c0-236">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="f84c0-236">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="f84c0-237">[[SQL Server オブジェクトの転送タスク エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="f84c0-237">[Transfer SQL Server Objects Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="f84c0-238">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="f84c0-238">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="f84c0-239">[一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f84c0-239">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="f84c0-240">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="f84c0-240">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  

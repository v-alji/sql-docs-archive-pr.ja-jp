---
title: '[コピー元のテーブルおよびビューを選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e18f9f34db7965033d4e1e62964060a26404a45e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642881"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a><span data-ttu-id="066c8-102">[コピー元のテーブルおよびビューを選択]\(SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="066c8-102">Select Source Tables and Views (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="066c8-103">[コピー**元のテーブルおよびビューを選択**] ページを使用すると、データソースから変換先にコピーするテーブルとビューを指定できます。</span><span class="sxs-lookup"><span data-stu-id="066c8-103">Use the **Select Source Tables and Views** page to specify the tables and views to be copied from the data source to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="066c8-104">テーブルをコピーするオプションを選択する際に、テーブル内のすべての列をコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="066c8-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="066c8-105">変換先テーブルを選択したら、[マッピングの編集] をクリックして [**列マッピング**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="066c8-105">After selecting a destination table, click Edit Mappings to display the **Column Mappings** dialog box.</span></span> <span data-ttu-id="066c8-106">**\<ignore>** スキップする列については、[**列マッピング**] ダイアログボックスの [**変換先**] 列でを選択します。</span><span class="sxs-lookup"><span data-stu-id="066c8-106">Select **\<ignore>** in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="066c8-107">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="066c8-107">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="066c8-108">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="066c8-108">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="066c8-109">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="066c8-109">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="066c8-110">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="066c8-110">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="066c8-111">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="066c8-111">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="066c8-112">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="066c8-112">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="066c8-113">Options</span><span class="sxs-lookup"><span data-stu-id="066c8-113">Options</span></span>  
  
### <a name="tables-and-views-list"></a><span data-ttu-id="066c8-114">[テーブルとビュー] の一覧</span><span class="sxs-lookup"><span data-stu-id="066c8-114">Tables and views List</span></span>  
 <span data-ttu-id="066c8-115">**ソース**</span><span class="sxs-lookup"><span data-stu-id="066c8-115">**Source**</span></span>  
 <span data-ttu-id="066c8-116">チェック ボックスを使用して、コピー先にコピーできるテーブルとビューを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="066c8-116">Using the check boxes, select from the list of available tables and views to copy to the destination.</span></span> <span data-ttu-id="066c8-117">コピー元のテーブルとビューを選択していて他のアクションは何も実行しない場合は、コピー元のスキーマとデータは変更なしでコピーされます。</span><span class="sxs-lookup"><span data-stu-id="066c8-117">If you select a source table or view and perform no other action, the schema and data from the source are copied without changes.</span></span>  
  
 <span data-ttu-id="066c8-118">**宛先**</span><span class="sxs-lookup"><span data-stu-id="066c8-118">**Destination**</span></span>  
 <span data-ttu-id="066c8-119">コピー元のテーブルごとに、一覧からコピー先のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="066c8-119">Select a destination table from the list for each source table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="066c8-120">この時点でウィザードを一時停止し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または別のツールを使用して [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の変換先テーブルを作成した場合、新しいテーブルは使用可能な変換先テーブルの一覧にすぐには表示されません。</span><span class="sxs-lookup"><span data-stu-id="066c8-120">If you pause at this point in the wizard to create a destination table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or another tool, the new table is not immediately visible in the list of available destination tables.</span></span> <span data-ttu-id="066c8-121">変換先テーブルの一覧を更新するには、2つのページを [**変換先の選択**] ページに戻り、変換先データベースを再選択してから、 **[コピー元のテーブルおよびビューを選択]** にもう一度進みます。</span><span class="sxs-lookup"><span data-stu-id="066c8-121">To refresh the list of destination tables, step back two pages to the **Choose a Destination** page, re-select the destination database, then step forward again to the **Select Source Tables and Views**.</span></span>  
  
### <a name="other-options"></a><span data-ttu-id="066c8-122">その他のオプション</span><span class="sxs-lookup"><span data-stu-id="066c8-122">Other Options</span></span>  
 <span data-ttu-id="066c8-123">**[マッピングの編集]**</span><span class="sxs-lookup"><span data-stu-id="066c8-123">**Edit mappings**</span></span>  
 <span data-ttu-id="066c8-124">[**列マッピング**] ダイアログボックスを使用すると、ソースデータを受け取る変換先列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="066c8-124">Use the **Column Mappings** dialog box to specify destination columns to receive the source data.</span></span> <span data-ttu-id="066c8-125">\<ignore>スキップする列については、[**列マッピング**] ダイアログボックスの [**変換先**] 列でを選択すると、列のサブセットのみをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="066c8-125">You can copy only a subset of columns by selecting \<ignore> in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="066c8-126">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="066c8-126">**Preview**</span></span>  
 <span data-ttu-id="066c8-127">インポートまたはエクスポートを実行する前に確認するには、[**データのプレビュー** ] ダイアログボックスでソースデータをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="066c8-127">Preview source data in the **Preview Data** dialog box to verify it before performing the import or export.</span></span> <span data-ttu-id="066c8-128">[**データのプレビュー** ] ダイアログボックスには、最大200行のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="066c8-128">The **Preview Data** dialog box displays up to 200 rows of data.</span></span>  
  
 <span data-ttu-id="066c8-129">データをプレビューした後に、データのコピー元およびコピー先に対して選択したオプションを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="066c8-129">After previewing the data, you might want to change the options that you have selected for the data source and destination.</span></span> <span data-ttu-id="066c8-130">これらの変更を行うには、**[コピー元のテーブルおよびビューを選択]** ページで **[戻る]** をクリックし、選択の変更が可能な前のページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="066c8-130">To make these changes, on the **Select Source Tables and Views** page, click **Back** to return to previous pages where you can change your selections.</span></span>  
  
  

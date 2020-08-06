---
title: テーブルのコピーまたはクエリの指定 (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a3d1eafb57475ed6a0f9fb20894fcc9718d1f0c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642878"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="f1080-102">[テーブルのコピーまたはクエリの指定] \(SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="f1080-102">Specify Table Copy or Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="f1080-103">[**テーブルのコピーまたはクエリの指定**] ページを使用すると、データのコピー方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1080-103">Use the **Specify Table Copy or Query** page to specify how to copy data.</span></span> <span data-ttu-id="f1080-104">グラフィカル インターフェイスを使用して、コピーする既存データベースを選択したり、Transact-SQL を使用してさらに複雑なクエリを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="f1080-104">You can use a graphical interface to select the existing database objects you want to copy, or you can use Transact-SQL to create a more complex query.</span></span>  
  
 <span data-ttu-id="f1080-105">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1080-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="f1080-106">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1080-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="f1080-107">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="f1080-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="f1080-108">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="f1080-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="f1080-109">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f1080-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="f1080-110">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1080-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f1080-111">Options</span><span class="sxs-lookup"><span data-stu-id="f1080-111">Options</span></span>  
 <span data-ttu-id="f1080-112">**1 つ以上のテーブルまたはビューからデータをコピーする**</span><span class="sxs-lookup"><span data-stu-id="f1080-112">**Copy data from one or more tables or views**</span></span>  
 <span data-ttu-id="f1080-113">**[コピー元のテーブルおよびビューを選択**] ダイアログボックスを使用して、選択したコピー元のテーブルおよびビューから、指定した変換先にフィールドをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f1080-113">Copy fields from selected source tables and views to the specified destination or destinations by using the **Select Source Tables and Views** dialog box.</span></span> <span data-ttu-id="f1080-114">レコードのフィルター選択や並べ替えを実行せず、コピー元のすべてのデータをコピーする場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1080-114">Use this option if you want to copy all data in the source without filtering or ordering records.</span></span>  
  
 <span data-ttu-id="f1080-115">データプロバイダーを使用し [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] てデータソースに接続する場合、[ **1 つ以上のテーブルまたはビューからデータをコピー**する] オプションが使用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f1080-115">When you use a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to connect to your data source, the **Copy data from one or more tables or views** option might not be available.</span></span> <span data-ttu-id="f1080-116">このオプションは、ProviderDescriptors.xml ファイルに ProviderDescription セクションがあるプロバイダーでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1080-116">This option is available only for those providers that have a ProviderDescription section in the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="f1080-117">各 ProviderDescription セクションには、対応するプロバイダーからメタデータを取得するのに必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1080-117">Each ProviderDescription section contains the information that is required to retrieve metadata from the corresponding provider.</span></span> <span data-ttu-id="f1080-118">既定では、ProviderDescriptors.xml ファイルには、次のプロバイダーの ProviderDescription セクションのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1080-118">By default, the ProviderDescriptors.xml file contains a ProviderDescription section for only the following providers:</span></span>  
  
-   <span data-ttu-id="f1080-119">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="f1080-119">System.Data.SqlClient</span></span>  
  
-   <span data-ttu-id="f1080-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="f1080-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="f1080-121">System.Data.OleDb</span><span class="sxs-lookup"><span data-stu-id="f1080-121">System.Data.OleDb</span></span>  
  
-   <span data-ttu-id="f1080-122">System.Data.Odbc</span><span class="sxs-lookup"><span data-stu-id="f1080-122">System.Data.Odbc</span></span>  
  
 <span data-ttu-id="f1080-123">追加のプロバイダーに対して [ **1 つ以上のテーブルまたはビューからデータをコピー**する] オプションを使用できるようにするために、サードパーティは独自の providerdescriptor セクションを ProviderDescriptors.xml ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f1080-123">To make the **Copy data from one or more tables or views** option available for additional providers, third parties can add their own ProviderDescriptor sections to the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="f1080-124">既定では、このファイルは、次のファイルに \<*drive*> あります。</span><span class="sxs-lookup"><span data-stu-id="f1080-124">By default, this file is in \<*drive*>:\Program Files\Microsoft SQL Server\100\DTS\ProviderDescriptors.</span></span> <span data-ttu-id="f1080-125">ProviderDescriptor セクションの要件については、ProviderDescriptors.xsd スキーマ ファイルを参照してください。既定では、このファイルは、ProviderDescriptors.xml ファイルと同じフォルダーに格納されています。</span><span class="sxs-lookup"><span data-stu-id="f1080-125">To review the requirements for the ProviderDescriptor section, see the ProviderDescriptors.xsd schema file that is, by default, in the same folder as the ProviderDescriptors.xml file.</span></span>  
  
 <span data-ttu-id="f1080-126">**転送するデータを指定するためのクエリを記述する**</span><span class="sxs-lookup"><span data-stu-id="f1080-126">**Write a query to specify the data to transfer**</span></span>  
 <span data-ttu-id="f1080-127">[基になる**クエリの指定**] ダイアログボックスを使用して、行を取得する SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1080-127">Build SQL statements to retrieve rows by using the **Provide a Source Query** dialog box.</span></span> <span data-ttu-id="f1080-128">コピー操作中にコピー元データを変更したり、制限したりする場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1080-128">Use this option if you want to modify or restrict the source data during the copy operation.</span></span> <span data-ttu-id="f1080-129">選択条件に一致する行のみをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="f1080-129">Only the rows matching the selection criteria are available for copying.</span></span>  
  
  

---
title: '[テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3fc2054711708a27691f2d7219c33749f11b977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642901"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a><span data-ttu-id="fd88f-102">[テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="fd88f-102">Create Table SQL Statement (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="fd88f-103">[**テーブル作成 SQL ステートメント**] ダイアログボックスを使用すると、自動的に生成されたステートメントを表示したり、目的に合わせて変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="fd88f-103">Use the **Create Table SQL Statement** dialog box to view the statement that was generated automatically, or to modify it for your purposes.</span></span> <span data-ttu-id="fd88f-104">このステートメントを変更する場合、それに関連して、列のマッピングにも変更を加えなければならない場合があります。それ以降も、編集した SQL ステートメントは手動で保守する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd88f-104">If you modify this statement, you may also have to make associated changes to column mapping, and you will have to maintain the edited SQL statement manually thereafter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="fd88f-105">により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fd88f-105">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="fd88f-106">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="fd88f-106">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="fd88f-107">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="fd88f-107">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="fd88f-108">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="fd88f-108">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="fd88f-109">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd88f-109">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="fd88f-110">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd88f-110">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="fd88f-111">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd88f-111">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="fd88f-112">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="fd88f-112">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="fd88f-113">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="fd88f-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="fd88f-114">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fd88f-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="fd88f-115">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd88f-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd88f-116">Options</span><span class="sxs-lookup"><span data-stu-id="fd88f-116">Options</span></span>  
 <span data-ttu-id="fd88f-117">**SQL ステートメント**</span><span class="sxs-lookup"><span data-stu-id="fd88f-117">**SQL statement**</span></span>  
 <span data-ttu-id="fd88f-118">自動生成された SQL ステートメントが表示され、編集できます。</span><span class="sxs-lookup"><span data-stu-id="fd88f-118">Displays the auto-generated SQL statement and lets it be edited.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd88f-119">SQL ステートメントにキャリッジ リターンを含める場合は、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら &lt;localizedText&gt;Enter&lt;/localizedText&gt; キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fd88f-119">If you want to include a carriage return in the SQL statement, press CTRL+ENTER.</span></span> <span data-ttu-id="fd88f-120">Enter&lt;/localizedText&gt; キーだけを押すと、ダイアログ ボックスが終了します。</span><span class="sxs-lookup"><span data-stu-id="fd88f-120">If you press only ENTER, the dialog box closes.</span></span>  
  
 <span data-ttu-id="fd88f-121">**生成**</span><span class="sxs-lookup"><span data-stu-id="fd88f-121">**Autogenerate**</span></span>  
 <span data-ttu-id="fd88f-122">既定の SQL ステートメントを変更していた場合、**[自動生成]** をクリックすると復元されます。</span><span class="sxs-lookup"><span data-stu-id="fd88f-122">Restore the default SQL statement, if you have modified it, by clicking **Autogenerate**.</span></span>  
  
  

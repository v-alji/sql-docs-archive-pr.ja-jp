---
title: '[データのプレビュー] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 17debc001d8ba7826fe845c006e944e5a3dc87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642890"
---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="a7e59-102">[データのプレビュー] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="a7e59-102">Preview Data Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="a7e59-103">[**データのプレビュー** ] ダイアログボックスを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポートウィザードによってデータソースに送信されるクエリを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a7e59-103">Use the **Preview Data** dialog box to see the query that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard will send to the data source.</span></span> <span data-ttu-id="a7e59-104">また、このダイアログ ボックスでは、サンプル データを最大 200 行プレビューできます。</span><span class="sxs-lookup"><span data-stu-id="a7e59-104">You can also use this dialog box to preview up to 200 rows of sample data.</span></span>  
  
 <span data-ttu-id="a7e59-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポートウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e59-105">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="a7e59-106">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e59-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="a7e59-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="a7e59-107">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="a7e59-108">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="a7e59-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="a7e59-109">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="a7e59-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="a7e59-110">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e59-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
 <span data-ttu-id="a7e59-111">**[データのプレビュー] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="a7e59-111">**To open the Preview Data dialog box**</span></span>  
  
-   <span data-ttu-id="a7e59-112">インポートおよびエクスポートウィザードの [**コピー元のテーブルおよびビューを選択**] ページで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、[**プレビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e59-112">On the **Select Source Tables and Views** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, click **Preview**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7e59-113">Options</span><span class="sxs-lookup"><span data-stu-id="a7e59-113">Options</span></span>  
 <span data-ttu-id="a7e59-114">**ソース**</span><span class="sxs-lookup"><span data-stu-id="a7e59-114">**Source**</span></span>  
 <span data-ttu-id="a7e59-115">ウィザードからデータ ソースに送信するクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e59-115">Displays the query that the wizard will send to the data source.</span></span>  
  
 <span data-ttu-id="a7e59-116">**[サンプル データ グリッド]**</span><span class="sxs-lookup"><span data-stu-id="a7e59-116">**Sample data grid**</span></span>  
 <span data-ttu-id="a7e59-117">クエリから返されたサンプル データが最大 200 行表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7e59-117">Displays up to 200 rows of sample data that the query returned.</span></span>  
  
  

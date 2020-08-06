---
title: '[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9207e76191060c56acad37db734827579a83aae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642907"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a><span data-ttu-id="b3f15-102">[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="b3f15-102">Column Conversion Details Dialog Box (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="b3f15-103">[**列変換の詳細**] ダイアログボックスを使用すると、個々の列に関する詳細な変換情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="b3f15-103">Use the **Column Conversion Details** dialog box to review detailed conversion information about an individual column.</span></span> <span data-ttu-id="b3f15-104">この変換情報には、変換元および変換先での列のデータ型や、ウィザードが実行する変換が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b3f15-104">This conversion information contains the column's data type at the source and the destination, and the conversion that the wizard will perform.</span></span> <span data-ttu-id="b3f15-105">このページには、必要なデータ型変換を判断するためにウィザードで使用されるデータ型マッピング ファイルも一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="b3f15-105">This page also lists the data type mapping files that the wizard uses to determine the data type conversions that are required.</span></span> <span data-ttu-id="b3f15-106">これらのデータ型マッピング ファイルは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってセットアップ時にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b3f15-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs these data type mapping files during setup.</span></span>  
  
 <span data-ttu-id="b3f15-107">**[列変換の詳細] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="b3f15-107">**To open the Column Conversion Details dialog box**</span></span>  
  
1.  <span data-ttu-id="b3f15-108">インポートおよびエクスポートウィザードの [**データ型の問題の確認**] ページで、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **テーブル**] ボックスの一覧からテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b3f15-108">On the **Review Data Type Issues** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, in the **Table** list, select a table.</span></span>  
  
2.  <span data-ttu-id="b3f15-109">[**データ型マッピング**] の一覧で、変換の詳細を表示する列が含まれている行をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3f15-109">In the **Data type mapping** list, double-click the row that contains the column for which you want to view conversion details.</span></span>  
  
 <span data-ttu-id="b3f15-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポートウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3f15-110">To learn more about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="b3f15-111">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3f15-111">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="b3f15-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="b3f15-112">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="b3f15-113">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="b3f15-113">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="b3f15-114">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b3f15-114">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="b3f15-115">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3f15-115">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  

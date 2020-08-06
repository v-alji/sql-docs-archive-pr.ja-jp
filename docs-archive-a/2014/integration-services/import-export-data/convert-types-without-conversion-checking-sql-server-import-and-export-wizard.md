---
title: 変換の確認を伴わない型変換 (SQL Server インポートおよびエクスポートウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.nomappingfile.f1
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3874bcad23994fdcf69ade948239760d5c871917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642900"
---
# <a name="convert-types-without-conversion-checking-sql-server-import-and-export-wizard"></a><span data-ttu-id="6a28a-102">[変換の確認を伴わない型変換] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="6a28a-102">Convert Types without Conversion Checking (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="6a28a-103">[**変換の確認を伴わない型の変換**] ページを使用すると、ウィザードが1つ以上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型変換ファイルとマッピングファイルを見つけられなかった場合に、ウィザードで実行されるマッピングを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6a28a-103">Use the **Convert Types without Conversion Checking** page to review the mappings that the wizard performs when the wizard cannot locate one or more of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type conversion and mapping files.</span></span> <span data-ttu-id="6a28a-104">このページには、不足しているファイルの特定に役立つ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a28a-104">This page includes information that helps you identify the missing file or files.</span></span>  
  
 <span data-ttu-id="6a28a-105">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a28a-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="6a28a-106">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a28a-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="6a28a-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="6a28a-107">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="6a28a-108">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="6a28a-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="6a28a-109">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="6a28a-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="6a28a-110">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a28a-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
  

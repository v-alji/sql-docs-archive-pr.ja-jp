---
title: '[操作を実行しています] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6cdac605da2288149909a3fb6e9f245e10eebf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642897"
---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a><span data-ttu-id="d4cb6-102">[操作を実行しています] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="d4cb6-102">Performing Operation (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="d4cb6-103">[**操作の実行**] ページを使用すると、インポート/エクスポート操作の進行状況と結果を表示したり、必要に応じて操作を中断したりできます。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-103">Use the **Performing Operation** page to view the progress and the results of the import/export operation, and to interrupt the operation if necessary.</span></span>  
  
 <span data-ttu-id="d4cb6-104">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="d4cb6-105">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="d4cb6-106">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="d4cb6-107">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="d4cb6-108">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="d4cb6-109">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4cb6-110">Options</span><span class="sxs-lookup"><span data-stu-id="d4cb6-110">Options</span></span>  
 <span data-ttu-id="d4cb6-111">**操作**</span><span class="sxs-lookup"><span data-stu-id="d4cb6-111">**Action**</span></span>  
 <span data-ttu-id="d4cb6-112">操作の一部であるそれぞれのアクションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-112">Displays each action that is part of the operation.</span></span>  
  
 <span data-ttu-id="d4cb6-113">**状態**</span><span class="sxs-lookup"><span data-stu-id="d4cb6-113">**Status**</span></span>  
 <span data-ttu-id="d4cb6-114">各アクションが成功したか、失敗したかを表示します。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-114">Displays the success or failure of each action.</span></span>  
  
 <span data-ttu-id="d4cb6-115">**Message**</span><span class="sxs-lookup"><span data-stu-id="d4cb6-115">**Message**</span></span>  
 <span data-ttu-id="d4cb6-116">アクションによって生成された表示メッセージおよびエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-116">Displays informational and error messages that the action might generate.</span></span>  
  
 <span data-ttu-id="d4cb6-117">**Assert**</span><span class="sxs-lookup"><span data-stu-id="d4cb6-117">**Filter**</span></span>  
 <span data-ttu-id="d4cb6-118">エラー、警告、または成功したアクションのみを表示するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-118">Choose whether you want to display only errors, warnings, or successful actions.</span></span> <span data-ttu-id="d4cb6-119">[**すべてのアクションを表示]** を選択すると、既定の表示に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-119">You can revert to the default display by choosing **Show All Actions**.</span></span>  
  
 <span data-ttu-id="d4cb6-120">**Stop**</span><span class="sxs-lookup"><span data-stu-id="d4cb6-120">**Stop**</span></span>  
 <span data-ttu-id="d4cb6-121">必要に応じて、[**停止**] ボタンを使用して操作を中断します。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-121">Interrupt the operation, if necessary, by using the **Stop** button.</span></span>  
  
 <span data-ttu-id="d4cb6-122">**Report**</span><span class="sxs-lookup"><span data-stu-id="d4cb6-122">**Report**</span></span>  
 <span data-ttu-id="d4cb6-123">結果レポートを表示したり、ファイルに保存することができます。さらに、レポートをクリップボードにコピーすることも、電子メールで送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4cb6-123">View a report of the results, save the report to a file, copy the report to the clipboard, or send the report by e-mail.</span></span>  
  
  

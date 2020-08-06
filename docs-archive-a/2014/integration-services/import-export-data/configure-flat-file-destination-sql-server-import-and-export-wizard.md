---
title: フラット ファイルの変換先の構成 (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2af8a1653d9a1aef0828aa112a25825ed23b8bf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642903"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="76fd9-102">[フラット ファイルの変換先の構成] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="76fd9-102">Configure Flat File Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="76fd9-103">[**フラットファイル変換先の構成**] ページを使用すると、変換先フラットファイルの書式設定オプションを指定したり、結果をプレビューしてから続行することができます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-103">Use the **Configure Flat File Destination** page to specify formatting options for the destination flat file, and to preview results before continuing.</span></span>  
  
 <span data-ttu-id="76fd9-104">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76fd9-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="76fd9-105">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76fd9-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="76fd9-106">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="76fd9-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="76fd9-107">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="76fd9-108">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="76fd9-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="76fd9-109">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76fd9-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="76fd9-110">Options</span><span class="sxs-lookup"><span data-stu-id="76fd9-110">Options</span></span>  
 <span data-ttu-id="76fd9-111">**[変換元フラット ファイル]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-111">**Source flat file**</span></span>  
 <span data-ttu-id="76fd9-112">変換先ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="76fd9-112">The name of the destination file.</span></span>  
  
 <span data-ttu-id="76fd9-113">**[行区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-113">**Row delimiter**</span></span>  
 <span data-ttu-id="76fd9-114">行の区切り記号の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="76fd9-114">Select from the list of delimiters for rows.</span></span>  
  
|<span data-ttu-id="76fd9-115">値</span><span class="sxs-lookup"><span data-stu-id="76fd9-115">Value</span></span>|<span data-ttu-id="76fd9-116">説明</span><span class="sxs-lookup"><span data-stu-id="76fd9-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76fd9-117">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="76fd9-117">**{CR}{LF}**</span></span>|<span data-ttu-id="76fd9-118">行は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-118">The row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="76fd9-119">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="76fd9-119">**{CR}**</span></span>|<span data-ttu-id="76fd9-120">行は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-120">The row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="76fd9-121">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="76fd9-121">**{LF}**</span></span>|<span data-ttu-id="76fd9-122">行は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-122">The row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="76fd9-123">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-123">**Semicolon {;}**</span></span>|<span data-ttu-id="76fd9-124">行は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-124">The row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="76fd9-125">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-125">**Colon {:}**</span></span>|<span data-ttu-id="76fd9-126">行は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-126">The row is delimited by a colon.</span></span>|  
|<span data-ttu-id="76fd9-127">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-127">**Comma {,}**</span></span>|<span data-ttu-id="76fd9-128">行は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-128">The row is delimited by a comma.</span></span>|  
|<span data-ttu-id="76fd9-129">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-129">**Tab {t}**</span></span>|<span data-ttu-id="76fd9-130">行は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-130">The row is delimited by a tab.</span></span>|  
|<span data-ttu-id="76fd9-131">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-131">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="76fd9-132">行は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-132">The row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="76fd9-133">**列区切り記号**</span><span class="sxs-lookup"><span data-stu-id="76fd9-133">**Column delimiter**</span></span>  
 <span data-ttu-id="76fd9-134">列の区切り記号の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="76fd9-134">Select from the list of delimiters for columns.</span></span>  
  
|<span data-ttu-id="76fd9-135">値</span><span class="sxs-lookup"><span data-stu-id="76fd9-135">Value</span></span>|<span data-ttu-id="76fd9-136">説明</span><span class="sxs-lookup"><span data-stu-id="76fd9-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76fd9-137">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="76fd9-137">**{CR}{LF}**</span></span>|<span data-ttu-id="76fd9-138">列は、復帰と改行の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-138">The columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="76fd9-139">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="76fd9-139">**{CR}**</span></span>|<span data-ttu-id="76fd9-140">列は、復帰で区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-140">The columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="76fd9-141">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="76fd9-141">**{LF}**</span></span>|<span data-ttu-id="76fd9-142">列は、改行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-142">The columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="76fd9-143">**[セミコロン {;}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-143">**Semicolon {;}**</span></span>|<span data-ttu-id="76fd9-144">列は、セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-144">The columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="76fd9-145">**[コロン {:}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-145">**Colon {:}**</span></span>|<span data-ttu-id="76fd9-146">列は、コロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-146">The columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="76fd9-147">**[コンマ {,}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-147">**Comma {,}**</span></span>|<span data-ttu-id="76fd9-148">列はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-148">The columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="76fd9-149">**[タブ {t}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-149">**Tab {t}**</span></span>|<span data-ttu-id="76fd9-150">列は、タブで区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-150">The columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="76fd9-151">**[縦棒 {&#124;}]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-151">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="76fd9-152">列は、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="76fd9-152">The columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="76fd9-153">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="76fd9-153">**Preview**</span></span>  
 <span data-ttu-id="76fd9-154">[データの**プレビュー** ] ダイアログボックスで、変換先のフラットファイルに対して選択した書式設定オプションの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="76fd9-154">View in the **Preview Data** dialog box the results of the selected formatting options for the destination flat file.</span></span>  
  
 <span data-ttu-id="76fd9-155">**[変換の編集]**</span><span class="sxs-lookup"><span data-stu-id="76fd9-155">**Edit transform**</span></span>  
 <span data-ttu-id="76fd9-156">[**列マッピング**] ダイアログボックスを使用して、変換先ファイルの行の削除、行の追加、および列の構成を行います。</span><span class="sxs-lookup"><span data-stu-id="76fd9-156">Delete rows, append rows, and configure columns in the destination file by using the **Column Mappings** dialog box.</span></span>  
  
  

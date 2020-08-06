---
title: データベースからの DAC の抽出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.extractdacwizard.buildandsave.f1
- sql12.swb.extractdacwizard.setdacproperties.f1
- sql12.swb.extractdacwizard.validationandsummary.f1
- sql12.swb.extractdacwizard.introduction.f1
- sql12.swb.extractdacwizard.selectdatapage.f1
helpviewer_keywords:
- extract DAC
- How to [DAC], extract
- data-tier application [SQL Server], extract
- wizard [DAC], extract
ms.assetid: ae52a723-91c4-43fd-bcc7-f8de1d1f90e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd024af9c201563773e20bae7e5fded1985abbe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645130"
---
# <a name="extract-a-dac-from-a-database"></a><span data-ttu-id="e9a3c-102">データベースからの DAC の抽出</span><span class="sxs-lookup"><span data-stu-id="e9a3c-102">Extract a DAC From a Database</span></span>
  <span data-ttu-id="e9a3c-103">**データ層アプリケーションの抽出ウィザード** または Windows PowerShell スクリプトを使用すると、既存の SQL Server データベースからデータ層アプリケーション (DAC) パッケージを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-103">Use either the **Extract Data-tier Application Wizard** or a Windows PowerShell script to extract a data-tier application (DAC) package from an existing SQL Server database.</span></span> <span data-ttu-id="e9a3c-104">抽出プロセスでは、データベース オブジェクトの定義とそれに関連するインスタンスレベルの要素を格納した DAC パッケージ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-104">The extraction process creates a DAC package file that contains definitions of the database objects and their related instance-level elements.</span></span> <span data-ttu-id="e9a3c-105">たとえば、DAC パッケージ ファイルには、データベース テーブル、ストアド プロシージャ、ビュー、ユーザー、およびデータベース ユーザーにマップされているログインが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-105">For example, a DAC package file contains the database tables, stored procedures, views, and users, along with the logins that map to the database users.</span></span>  
  
-   <span data-ttu-id="e9a3c-106">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-106">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="e9a3c-107">**DAC を抽出するために使用するもの:**  [データ層アプリケーションの抽出ウィザード](#UsingDACExtractWizard)、 [PowerShell](#ExtractDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-107">**To extract a DAC, using:**  [The Extract Data-tier Application Wizard](#UsingDACExtractWizard), [PowerShell](#ExtractDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e9a3c-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="e9a3c-108">Before You Begin</span></span>  
 <span data-ttu-id="e9a3c-109">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]、または [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 以降のインスタンスに存在するデータベースから DAC を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-109">You can extract a DAC from databases residing on instances of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 or later.</span></span> <span data-ttu-id="e9a3c-110">DAC から配置されたデータベースに対して抽出プロセスが実行された場合、データベース内のオブジェクトの定義のみが抽出されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-110">If the extraction process is run against a database that was deployed from a DAC, only the definitions of the objects in the database are extracted.</span></span> <span data-ttu-id="e9a3c-111">このプロセスでは、に登録されている DAC `msdb` (の**マスター** ) は参照されません [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-111">The process does not reference the DAC registered in `msdb` (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]).</span></span> <span data-ttu-id="e9a3c-112">抽出プロセスは、データベース エンジンの現在のインスタンスの DAC 定義を登録しません。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-112">The extraction process does not register the DAC definition in the current instance of the Database Engine.</span></span> <span data-ttu-id="e9a3c-113">DAC の登録の詳細については、「 [Register a Database As a DAC](register-a-database-as-a-dac.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-113">For more information about registering a DAC, see [Register a Database As a DAC](register-a-database-as-a-dac.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e9a3c-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e9a3c-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e9a3c-115">DAC を抽出できるのは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 以降のデータベースに限られます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-115">A DAC can only be extracted from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="e9a3c-116">DAC でサポートされていないオブジェクトまたは包含ユーザーがデータベースに存在する場合は、DAC を抽出できません。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-116">You cannot extract a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="e9a3c-117">DAC でサポートされるオブジェクトの種類の詳細については、「 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e9a3c-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="e9a3c-118">Permissions</span></span>  
 <span data-ttu-id="e9a3c-119">DAC を抽出するには、少なくとも ALTER ANY LOGIN 権限とデータベース スコープの VIEW DEFINITION 権限、および **sys.sql_expression_dependencies**に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-119">Extracting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="e9a3c-120">DAC を抽出できるのは、DAC を抽出するデータベースの database_owner 固定データベース ロールのメンバーでもある、securityadmin 固定サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-120">Extracting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is extracted.</span></span> <span data-ttu-id="e9a3c-121">sysadmin 固定サーバー ロールのメンバーまたは **sa** という組み込みの SQL Server システム管理者アカウントも DAC を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also extract a DAC.</span></span>  
  
##  <a name="using-the-extract-data-tier-application-wizard"></a><a name="UsingDACExtractWizard"></a> <span data-ttu-id="e9a3c-122">データ層アプリケーションの抽出ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="e9a3c-122">Using the Extract Data-tier Application Wizard</span></span>  
 <span data-ttu-id="e9a3c-123">**ウィザードを使用して DAC を抽出するには**</span><span class="sxs-lookup"><span data-stu-id="e9a3c-123">**To Extract a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="e9a3c-124">**オブジェクト エクスプローラー**で、DAC の抽出元となるデータベースを含んだインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-124">In **Object Explorer**, expand the node for the instance containing the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="e9a3c-125">**[データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="e9a3c-126">DAC を抽出するデータベースのノードを右クリックし、[**タスク**] をポイントし、[**データ層アプリケーションの抽出**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-126">Right-click the node for the database from which the DAC is to be extracted, point to **Tasks**, and then select **Extract Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="e9a3c-127">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-127">Complete the wizard dialogs:</span></span>  
  
    1.  <span data-ttu-id="e9a3c-128">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-128">[Introduction Page](#Introduction)</span></span>  
  
    2.  <span data-ttu-id="e9a3c-129">[[データの選択] ページ](#SelectData)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-129">[Select Data Page](#SelectData)</span></span>  
  
    3.  <span data-ttu-id="e9a3c-130">[[プロパティの設定] ページ](#SetProperties)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-130">[Set Properties Page](#SetProperties)</span></span>  
  
    4.  <span data-ttu-id="e9a3c-131">[[検証と概要] ページ](#ValidateSummary)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-131">[Validation and Summary Page](#ValidateSummary)</span></span>  
  
    5.  <span data-ttu-id="e9a3c-132">[[パッケージのビルド] ページ](#BuildPackage)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-132">[Build Package Page](#BuildPackage)</span></span>  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="e9a3c-133">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="e9a3c-133">Introduction Page</span></span>  
 <span data-ttu-id="e9a3c-134">このページでは、データ層アプリケーションを抽出する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-134">This page describes the steps for extracting a data-tier application.</span></span>  
  
 <span data-ttu-id="e9a3c-135">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="e9a3c-135">**Do not show this page again.**</span></span> <span data-ttu-id="e9a3c-136">: 今後このページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-136">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="e9a3c-137">**[次へ >]**: **[方法の選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-137">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="e9a3c-138">**[キャンセル]** : データベースからデータ層アプリケーションを抽出せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-138">**Cancel** - Ends the wizard without extracting a data-tier application from the database.</span></span>  
  
###  <a name="select-data-page"></a><a name="SelectData"></a><span data-ttu-id="e9a3c-139">[データの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="e9a3c-139">Select Data Page</span></span>  
 <span data-ttu-id="e9a3c-140">ウィザードのこのページを使用して、データ層アプリケーション (DAC) パッケージ ファイルに含める参照データを選択できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-140">Use this page of the wizard to select the reference data that you want to include in your data-tier application (DAC) package file.</span></span> <span data-ttu-id="e9a3c-141">DAC パッケージにデータを含めることは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-141">Including data in your DAC package is optional.</span></span> <span data-ttu-id="e9a3c-142">DAC パッケージには、データベースに関連するサポート対象のデータベース オブジェクトおよびインスタンス オブジェクトのスキーマがすべて、既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-142">The DAC package will already include the schema of all supported database objects and instance objects related to your database.</span></span>  
  
 <span data-ttu-id="e9a3c-143">DAC パッケージ ファイルには最大 10 MB の参照データを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-143">You can include up to 10 MB of reference data in your DAC package file.</span></span> <span data-ttu-id="e9a3c-144">ただし、DAC に含まれるテーブルの場合、 **image** や **varchar(max)** などのバイナリ ラージ オブジェクト (BLOB) データ型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-144">However, for tables to be included in the DAC, they may not contain binary large object (BLOB) data types such as **image** or **varchar(max)**.</span></span> <span data-ttu-id="e9a3c-145">別のデータベースへ転送するためにより大量のデータを抽出するには、SQL Server Integration Services、一括コピー ユーティリティ、または他の多くのデータ移行方法のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-145">To extract larger amounts of data for transferring to another database, use SQL Server Integration Services, the bulk copy utility, or one of many other data migration techniques.</span></span>  
  
 <span data-ttu-id="e9a3c-146">**[データベース テーブル]** : DAC パッケージに含めるデータが含まれたデータベース テーブルの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-146">**Database table** - Select the check box next to the database tables which contain the data that you want to include in your DAC package.</span></span> <span data-ttu-id="e9a3c-147">10,000 行以下のテーブルを最大 10 個選択できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-147">You can select up to ten tables that have 10,000 rows or less.</span></span>  
  
###  <a name="set-properties-page"></a><a name="SetProperties"></a> <span data-ttu-id="e9a3c-148">[プロパティの設定] ページ</span><span class="sxs-lookup"><span data-stu-id="e9a3c-148">Set Properties Page</span></span>  
 <span data-ttu-id="e9a3c-149">ウィザードのこのページでは、データ層アプリケーション (DAC) に関する情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-149">Use this page of the wizard to describe the data-tier application (DAC).</span></span> <span data-ttu-id="e9a3c-150">これらのプロパティは、DAC を識別し、他の DAC と区別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-150">These properties are used to identify the DAC and help distinguish it from others.</span></span>  
  
 <span data-ttu-id="e9a3c-151">**[名前]** : この名前で、DAC を識別します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-151">**Name** - This name identifies the DAC.</span></span> <span data-ttu-id="e9a3c-152">DAC パッケージ ファイルと異なる名前を設定できますが、アプリケーションを識別できる名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-152">It can be different than the name of the DAC package file and should describe your application.</span></span> <span data-ttu-id="e9a3c-153">たとえば、データベースを財務アプリケーションで使用する場合は、"DAC Finance" などの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-153">For example, if the database is used for a finance application, you may wish to name the DAC Finance.</span></span>  
  
 <span data-ttu-id="e9a3c-154">**[バージョン (xx.xx.xx.xx という形式で、x は数字)]** : DAC のバージョンを表す数値。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-154">**Version (use xx.xx.xx.xx, where x is a number)** - A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="e9a3c-155">DAC のバージョンは、開発者が操作している DAC のバージョンを特定するために Visual Studio で使用します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-155">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="e9a3c-156">DAC を配置すると、バージョンがデータベースに格納され、 `msdb` 後での [**データ層アプリケーション**] ノードの下に表示されるようになり [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-156">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e9a3c-157">**[説明]** - 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-157">**Description:** - Optional.</span></span> <span data-ttu-id="e9a3c-158">DAC の説明です。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-158">Describes the DAC.</span></span> <span data-ttu-id="e9a3c-159">DAC を配置すると、説明はデータベースに格納され、 `msdb` 後での [**データ層アプリケーション**] ノードの下に表示でき [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-159">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="e9a3c-160">**[DAC パッケージ ファイルに保存 (.dacpac 拡張子をファイル名に含める)]** : DAC を拡張子が .dacpac の DAC パッケージ ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-160">**Save to DAC package file (include .dacpac extension with file name):** - Saves the DAC to a DAC package file, with a .dacpac extension.</span></span> <span data-ttu-id="e9a3c-161">**[参照]** ボタンをクリックしてファイルの名前と場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-161">Click the **Browse** button to specify a name and location for the file.</span></span>  
  
 <span data-ttu-id="e9a3c-162">**[既存のファイルの上書き]** : 同じ名前の DAC パッケージ ファイルが既に存在する場合にそのファイルを置き換えるには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-162">**Overwrite existing file** - Select this check box to replace the DAC package file if one already exists with the same name.</span></span>  
  
###  <a name="validation-and-summary-page"></a><a name="ValidateSummary"></a> <span data-ttu-id="e9a3c-163">[検証と概要] ページ</span><span class="sxs-lookup"><span data-stu-id="e9a3c-163">Validation and Summary Page</span></span>  
 <span data-ttu-id="e9a3c-164">このページでは、すべてのデータベース オブジェクトがデータ層アプリケーション (DAC) でサポートされているかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-164">On this page, the wizard validates that all database objects are supported by a data-tier application (DAC).</span></span> <span data-ttu-id="e9a3c-165">また、データベース オブジェクト間の依存関係を確認して、DAC に正常に含めることができるオブジェクトのセットを判断します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-165">It also checks dependencies across database objects to determine the set of objects that can be successfully included in the DAC.</span></span> <span data-ttu-id="e9a3c-166">その後、検証レポートと、このウィザードで選択したオプションの概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-166">After that, it displays the validation report and summarizes the options that you have selected in this wizard.</span></span> <span data-ttu-id="e9a3c-167">オプションを変更するには、 **[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-167">To change an option, click **Previous**.</span></span> <span data-ttu-id="e9a3c-168">DAC の抽出を開始するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-168">To begin extracting a DAC, click **Next**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9a3c-169">1 つ以上のオブジェクトが DAC でサポートされていない場合は、 **[次へ]** ボタンは無効になり、抽出プロセスを続行できません。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-169">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process may not continue.</span></span> <span data-ttu-id="e9a3c-170">その場合は、サポートされていないオブジェクトを削除した後に、このウィザードを再度実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-170">In such cases, it is recommended to remove the non-supported objects and then run this wizard again.</span></span>  
  
 <span data-ttu-id="e9a3c-171">**[概要]** : 選択したオプションの概要が **[DAC のプロパティ]** の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-171">**Summary** - A summary of the options you have selected are listed under **DAC properties**.</span></span> <span data-ttu-id="e9a3c-172">検証の結果は **[DAC オブジェクト]** の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-172">The results of the validation are listed under **DAC objects**.</span></span> <span data-ttu-id="e9a3c-173">検証の結果には、次の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-173">There are three types of results from the validation:</span></span>  
  
-   <span data-ttu-id="e9a3c-174">**[DAC に正常に含まれるオブジェクト]** : これらのオブジェクトとその依存関係はサポートされており、DAC に正常に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-174">**Objects included in DAC successfully**: these objects and their dependencies are supported, and can be included in the DAC successfully.</span></span>  
  
-   <span data-ttu-id="e9a3c-175">**[DAC に含まれるオブジェクト (警告あり)]** : これらのオブジェクトはサポートされていますが、DAC でサポートされていない他のオブジェクトに依存しています。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-175">**Objects included in DAC with warnings**: these objects are supported, but depend on other objects that are not supported in a DAC.</span></span>  
  
-   <span data-ttu-id="e9a3c-176">**[DAC に含まれないオブジェクト]** : これらのオブジェクトはサポートされていないため、DAC を正常に抽出する前にデータベースから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-176">**Objects not included in DAC**: these objects are not supported and must be removed from the database before successfully extracting a DAC.</span></span>  
  
 <span data-ttu-id="e9a3c-177">検証プロセスでは、複数レベルで依存関係の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-177">The validation process checks multiple levels of dependencies.</span></span> <span data-ttu-id="e9a3c-178">たとえば、あるストアド プロシージャがサポートされていない CLR データ型を使用するテーブルに依存している場合、そのストアド プロシージャは **[DAC に含まれるオブジェクト (警告あり)]** の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-178">For example, if a stored procedure depends on a table that uses the unsupported CLR data type, the stored procedure will be listed under **Objects included in DAC with warnings**.</span></span>  
  
 <span data-ttu-id="e9a3c-179">1 つ以上のオブジェクトが DAC でサポートされていない場合は、 **[次へ]** ボタンは無効になり、抽出プロセスを続行できません。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-179">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process will not continue.</span></span> <span data-ttu-id="e9a3c-180">その場合は、サポートされていないオブジェクトを削除した後に、このウィザードを再度実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-180">In such cases, it is recommended to remove the objects that are not supported and then run this wizard again.</span></span>  
  
 <span data-ttu-id="e9a3c-181">**[レポートの保存]** : 概要の **[DAC のオブジェクト]** ノードの下に表示されるすべてのオブジェクトの一覧を示す HTML ベースのファイルを保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-181">**Save Report** - Enables you to save an HTML-based file that lists all of the objects under the **DAC Objects** node in the summary.</span></span> <span data-ttu-id="e9a3c-182">このレポートは、データベース オブジェクトの一部が DAC でサポートされていない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-182">This report can be useful when some of your database objects are not supported in a DAC.</span></span> <span data-ttu-id="e9a3c-183">DAC の抽出を再試行する前に、このレポートを使用してサポートされていないオブジェクトを変更または削除します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-183">Use the report to change or remove objects that are not supported, before trying to extract the DAC again.</span></span>  
  
###  <a name="build-package-page"></a><a name="BuildPackage"></a><span data-ttu-id="e9a3c-184">[パッケージのビルド] ページ</span><span class="sxs-lookup"><span data-stu-id="e9a3c-184">Build Package Page</span></span>  
 <span data-ttu-id="e9a3c-185">このページでは、データ層アプリケーション (DAC) を抽出するウィザードの進行状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-185">Use this page to monitor the progress of the wizard as it extracts the data-tier application (DAC).</span></span>  
  
 <span data-ttu-id="e9a3c-186">**[アクション]** : **[DAC パッケージ ファイルの作成と保存]** では、SQL Server データベースから DAC が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-186">**Action** - During the **Create and save DAC package file** action, the wizard extracts a DAC from your SQL Server database.</span></span> <span data-ttu-id="e9a3c-187">その後、DAC パッケージがメモリ内に作成され、指定した場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-187">Then, a DAC package is created in memory and saved to the location you specified.</span></span> <span data-ttu-id="e9a3c-188">**[結果]** 列のリンクをクリックすると、対応する手順の結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-188">Click on the links in the **Result** column to see the outcome of the corresponding step.</span></span>  
  
 <span data-ttu-id="e9a3c-189">**[レポートの保存]** : クリックすると、ウィザードの進行状況の結果がファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-189">**Save Report** - Click to save the results of the wizard's progress to a file.</span></span>  
  
 <span data-ttu-id="e9a3c-190">**[完了]** - 処理が完了した後やエラーが発生した場合にクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-190">**Finish** - Click to close the wizard after processing has completed, or if an error occurs.</span></span>  
  
##  <a name="extract-a-dac-using-powershell"></a><a name="ExtractDACPowerShell"></a><span data-ttu-id="e9a3c-191">PowerShell を使用して DAC を抽出する</span><span class="sxs-lookup"><span data-stu-id="e9a3c-191">Extract a DAC Using PowerShell</span></span>  
 <span data-ttu-id="e9a3c-192">**PowerShell スクリプトで Extract() メソッドを使用してデータベースから DAC を抽出するには**</span><span class="sxs-lookup"><span data-stu-id="e9a3c-192">**To extract a DAC from a database using the Extract() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="e9a3c-193">SMO サーバー オブジェクトを作成し、それを DAC の抽出元データベースが含まれているインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-193">Create a SMO Server object and set it to the instance that contains the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="e9a3c-194">データベースの名前を指定する変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-194">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="e9a3c-195">DAC のメタデータ (DAC 名、バージョン、説明など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-195">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="e9a3c-196">抽出された DAC パッケージ ファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-196">Specify the path and file name for the extracted DAC package file.</span></span>  
  
5.  <span data-ttu-id="e9a3c-197">上で指定した情報を使用して Extract メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-197">Run the Extract method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="e9a3c-198">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="e9a3c-198">Example (PowerShell)</span></span>  
 <span data-ttu-id="e9a3c-199">次の例では、MyDB という名前のデータベースから MyApplication という名前の DAC を抽出します。</span><span class="sxs-lookup"><span data-stu-id="e9a3c-199">The following example extracts a DAC named MyApplication from a database named MyDB.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to extract to a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Specify the location and name for the extracted DAC package.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
  
## Extract the DAC.  
$extractionunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$extractionunit.Description = $description  
$extractionunit.Extract($dacpacPath)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9a3c-200">参照</span><span class="sxs-lookup"><span data-stu-id="e9a3c-200">See Also</span></span>  
 [<span data-ttu-id="e9a3c-201">データ層アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e9a3c-201">Data-tier Applications</span></span>](data-tier-applications.md)  

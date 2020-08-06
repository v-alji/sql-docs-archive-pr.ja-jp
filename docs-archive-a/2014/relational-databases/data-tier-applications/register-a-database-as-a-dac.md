---
title: データベースを DAC として登録する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerdacwizard.registerdac.f1
- sql12.swb.registerdacwizard.summary.f1
- sql12.swb.registerdacwizard.introduction.f1
- sql12.swb.registerdacwizard.setproperties.f1
helpviewer_keywords:
- wizard [DAC], register
- How to [DAC], register
- register DAC
- data-tier application [SQL Server], register
ms.assetid: 08e52aa6-12f3-41dd-a793-14b99a083fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4e8061362d013dbfbd6cbaba47d0f2cb4d8e83b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645643"
---
# <a name="register-a-database-as-a-dac"></a><span data-ttu-id="f8058-102">データベースを DAC として登録する方法</span><span class="sxs-lookup"><span data-stu-id="f8058-102">Register a Database As a DAC</span></span>
  <span data-ttu-id="f8058-103">**データ層アプリケーションの登録ウィザード**または Windows PowerShell スクリプトを使用して、既存のデータベース内のオブジェクトを表すデータ層アプリケーション (dac) 定義を作成し、その dac 定義を `msdb` システムデータベース (の**マスター** ) に登録し [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f8058-103">Use either the **Register Data-tier Application Wizard** or a Windows PowerShell script to build a data-tier application (DAC) definition that describes the objects in an existing database, and register the DAC definition in the `msdb` system database (**master** in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]).</span></span>  
  
-   <span data-ttu-id="f8058-104">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="f8058-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="f8058-105">**DAC のアップグレード:** [データ層アプリケーションの登録ウィザードの使用](#UsingRegisterDACWizard)、[PowerShell の使用](#RegisterDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="f8058-105">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="f8058-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="f8058-106">Before You Begin</span></span>  
 <span data-ttu-id="f8058-107">登録プロセスでデータベース オブジェクトを定義する DAC 定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="f8058-107">The registration process creates a DAC definition that defines the objects in the database.</span></span> <span data-ttu-id="f8058-108">DAC の定義とデータベースを組み合わせたものが DAC インスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="f8058-108">The combination of the DAC definition and the database form a DAC instance.</span></span> <span data-ttu-id="f8058-109">データベース エンジンのマネージド インスタンス上で DAC としてデータベースを登録した場合は、SQL Server ユーティリティ コレクション セットをこのインスタンスからユーティリティ コントロール ポイントへ次に送信するときに、登録した DAC が SQL Server ユーティリティに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f8058-109">If you register a database as a DAC on a managed instance of the Database Engine, the registered DAC will be incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the Utility Control Point.</span></span> <span data-ttu-id="f8058-110">その後、DAC は [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の**ユーティリティ エクスプローラー**の **[配置済みのデータ層アプリケーション]** ノードに現れるようになり、 **[配置済みのデータ層アプリケーション]** の詳細ページで報告されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-110">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="f8058-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f8058-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f8058-112">DAC は、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 以降のデータベースでのみ登録できます。</span><span class="sxs-lookup"><span data-stu-id="f8058-112">DAC registration can only be performed on a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="f8058-113">DAC が既にデータベースに登録されている場合は、DAC の登録を実行できません。</span><span class="sxs-lookup"><span data-stu-id="f8058-113">DAC registration cannot be performed if a DAC is already registered for the database.</span></span> <span data-ttu-id="f8058-114">たとえば、DAC を配置してデータベースを作成した場合、 **データ層アプリケーションの登録ウィザード**を実行できません。</span><span class="sxs-lookup"><span data-stu-id="f8058-114">For example, if the database was created by deploying a DAC, you cannot run the **Register Data-tier Application Wizard**.</span></span>  
  
 <span data-ttu-id="f8058-115">DAC でサポートされていないオブジェクトまたは包含ユーザーがデータベースに存在する場合は、DAC を登録できません。</span><span class="sxs-lookup"><span data-stu-id="f8058-115">You cannot register a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="f8058-116">DAC でサポートされるオブジェクトの種類の詳細については、「 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8058-116">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f8058-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="f8058-117">Permissions</span></span>  
 <span data-ttu-id="f8058-118">DAC を [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに登録するには、少なくとも ALTER ANY LOGIN 権限とデータベース スコープの VIEW DEFINITION 権限、 **sys.sql_expression_dependencies**に対する SELECT 権限、および **dbcreator** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8058-118">Registering a DAC in an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, SELECT permissions on **sys.sql_expression_dependencies**, and membership in the **dbcreator** fixed server role.</span></span> <span data-ttu-id="f8058-119">**sysadmin** 固定サーバー ロールのメンバーまたは **sa** という組み込みの SQL Server システム管理者アカウントも DAC を登録できます。</span><span class="sxs-lookup"><span data-stu-id="f8058-119">Members of the **sysadmin** fixed server role or the built-in SQL Server system administrator account named **sa** can also register a DAC.</span></span> <span data-ttu-id="f8058-120">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれない DAC を登録するには、 **dbmanager** ロールまたは **serveradmin** ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8058-120">Registering a DAC that does not contain logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **dbmanager** or **serveradmin** roles.</span></span> <span data-ttu-id="f8058-121">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれる DAC を登録するには、 **loginmanager** ロールまたは **serveradmin** ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8058-121">Registering a DAC that contains logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **loginmanager** or **serveradmin** roles.</span></span>  
  
##  <a name="using-the-register-data-tier-application-wizard"></a><a name="UsingRegisterDACWizard"></a> <span data-ttu-id="f8058-122">データ層アプリケーションの登録ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="f8058-122">Using the Register Data-tier Application Wizard</span></span>  
 <span data-ttu-id="f8058-123">**ウィザードを使用して DAC を登録するには**</span><span class="sxs-lookup"><span data-stu-id="f8058-123">**To Register a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="f8058-124">**オブジェクト エクスプローラー**で、DAC として登録するデータベースを含んだインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f8058-124">In **Object Explorer**, expand the node for the instance containing the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="f8058-125">**[データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f8058-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="f8058-126">登録するデータベースを右クリックし、 **[タスク]** をポイントして **[データ層アプリケーションとして登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8058-126">Right-click the database to be registered, point to **Tasks**, and then select **Register As Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="f8058-127">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8058-127">Complete the wizard dialogs:</span></span>  
  
    1.  <span data-ttu-id="f8058-128">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="f8058-128">[Introduction Page](#Introduction)</span></span>  
  
    2.  <span data-ttu-id="f8058-129">[[プロパティの設定] ページ](#Set_properties)</span><span class="sxs-lookup"><span data-stu-id="f8058-129">[Set Properties Page](#Set_properties)</span></span>  
  
    3.  <span data-ttu-id="f8058-130">[[検証と概要] ページ](#Summary)</span><span class="sxs-lookup"><span data-stu-id="f8058-130">[Validation and Summary Page](#Summary)</span></span>  
  
    4.  <span data-ttu-id="f8058-131">[[DAC の登録] ページ](#Register)</span><span class="sxs-lookup"><span data-stu-id="f8058-131">[Register DAC Page](#Register)</span></span>  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="f8058-132">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="f8058-132">Introduction Page</span></span>  
 <span data-ttu-id="f8058-133">このページには、データ層アプリケーションの登録手順が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-133">This page describes the steps for registering a data-tier application.</span></span>  
  
 <span data-ttu-id="f8058-134">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="f8058-134">**Do not show this page again.**</span></span> <span data-ttu-id="f8058-135">: 今後このページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f8058-135">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="f8058-136">**[次へ >]** : **[プロパティの設定]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="f8058-136">**Next >** - Proceeds to the **Set Properties** page.</span></span>  
  
 <span data-ttu-id="f8058-137">**[キャンセル]** : DAC を登録せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f8058-137">**Cancel** - Terminates the wizard without registering a DAC.</span></span>  
  
##  <a name="set-properties-page"></a><a name="Set_properties"></a> <span data-ttu-id="f8058-138">[プロパティの設定] ページ</span><span class="sxs-lookup"><span data-stu-id="f8058-138">Set Properties Page</span></span>  
 <span data-ttu-id="f8058-139">このページでは、アプリケーション名やバージョンなど DAC レベルのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8058-139">Use this page to specify DAC-level properties such as the application name and version.</span></span>  
  
 <span data-ttu-id="f8058-140">**[アプリケーション名]**</span><span class="sxs-lookup"><span data-stu-id="f8058-140">**Application name.**</span></span> <span data-ttu-id="f8058-141">: DAC 定義を識別するための名前。このフィールドには、選択したデータベースの名前が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-141">- A string that specifies the name used to identify the DAC definition, the field is been populated with the database name.</span></span>  
  
 <span data-ttu-id="f8058-142">**バージョン。**</span><span class="sxs-lookup"><span data-stu-id="f8058-142">**Version.**</span></span> <span data-ttu-id="f8058-143">: DAC のバージョンを表す数値。</span><span class="sxs-lookup"><span data-stu-id="f8058-143">- A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="f8058-144">DAC のバージョンは、開発者が操作している DAC のバージョンを特定するために Visual Studio で使用します。</span><span class="sxs-lookup"><span data-stu-id="f8058-144">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="f8058-145">DAC を配置すると、バージョンがデータベースに格納され、 `msdb` 後での [**データ層アプリケーション**] ノードの下に表示されるようになり [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f8058-145">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f8058-146">**説明**</span><span class="sxs-lookup"><span data-stu-id="f8058-146">**Description.**</span></span> <span data-ttu-id="f8058-147">: 省略可。</span><span class="sxs-lookup"><span data-stu-id="f8058-147">- Optional.</span></span> <span data-ttu-id="f8058-148">この DAC の目的についての説明。</span><span class="sxs-lookup"><span data-stu-id="f8058-148">Text that explains the purpose of the DAC.</span></span> <span data-ttu-id="f8058-149">DAC を配置すると、説明はデータベースに格納され、 `msdb` 後での [**データ層アプリケーション**] ノードの下に表示でき [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f8058-149">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="f8058-150">[ \*\* \< 戻る**]-[**概要\*\*] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f8058-150">**\< Previous** - Returns you to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="f8058-151">**[次へ >]** : データベースのオブジェクトから DAC を作成できるかどうかを検証し、その結果を **[検証と概要]** ページに表示します。</span><span class="sxs-lookup"><span data-stu-id="f8058-151">**Next >** - Verifies that a DAC can be built from the objects in the database, and displays the results in the **Validation and Summary** page.</span></span>  
  
 <span data-ttu-id="f8058-152">**[キャンセル]** : DAC を登録せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f8058-152">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="validation-and-summary-page"></a><a name="Summary"></a> <span data-ttu-id="f8058-153">[検証と概要] ページ</span><span class="sxs-lookup"><span data-stu-id="f8058-153">Validation and Summary Page</span></span>  
 <span data-ttu-id="f8058-154">このページでは、DAC の登録時にウィザードが行うアクションを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8058-154">Use this page to review the actions the wizard will take when registering the DAC.</span></span> <span data-ttu-id="f8058-155">データベース内のオブジェクトから DAC を作成できるかどうかを検証する際、次の 3 つの処理が順番に実行されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-155">The page transitions through three states as it verifies that a DAC can be built from the objects in the database.</span></span>  
  
### <a name="retrieving-objects"></a><span data-ttu-id="f8058-156">オブジェクトの取得</span><span class="sxs-lookup"><span data-stu-id="f8058-156">Retrieving Objects</span></span>  
 <span data-ttu-id="f8058-157">**[データベース オブジェクトとサーバー オブジェクトを取得しています。]**</span><span class="sxs-lookup"><span data-stu-id="f8058-157">**Retrieving database and server objects.**</span></span> <span data-ttu-id="f8058-158">: データベースおよびデータベース エンジンのインスタンスから必要なすべてのオブジェクトを取得する間、進行状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-158">- Displays a progress bar as the wizard retrieves all of the required objects from the database and the instance of the Database Engine.</span></span>  
  
 <span data-ttu-id="f8058-159">[ \*\* \< 戻る**]: [**プロパティの設定\*\*] ページに戻り、エントリを変更します。</span><span class="sxs-lookup"><span data-stu-id="f8058-159">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="f8058-160">**[次へ >]** : DAC が登録され、 **[DAC の登録]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-160">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="f8058-161">**[キャンセル]** : DAC を登録せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f8058-161">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="validating-objects"></a><span data-ttu-id="f8058-162">オブジェクトの検証</span><span class="sxs-lookup"><span data-stu-id="f8058-162">Validating Objects</span></span>  
 <span data-ttu-id="f8058-163">**Checking** _SchemaName_ **.**</span><span class="sxs-lookup"><span data-stu-id="f8058-163">**Checking**  _SchemaName_ **.**</span></span> <span data-ttu-id="f8058-164">_ObjectName_ **.**</span><span class="sxs-lookup"><span data-stu-id="f8058-164">_ObjectName_ **.**</span></span> <span data-ttu-id="f8058-165">: 取得したオブジェクトの依存関係を検証し、それらすべてのオブジェクトが DAC に対して有効かどうかを確認する間、進行状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-165">- Displays a progress bar as the wizard verifies the dependencies of the retrieved objects, and verifies that they are all valid objects for a DAC.</span></span> <span data-ttu-id="f8058-166">_SchemaName_ **.** _ObjectName_ は、現在検証されているオブジェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="f8058-166">_SchemaName_**.**_ObjectName_ identify which object is currently being verified.</span></span>  
  
 <span data-ttu-id="f8058-167">[ \*\* \< 戻る**]: [**プロパティの設定\*\*] ページに戻り、エントリを変更します。</span><span class="sxs-lookup"><span data-stu-id="f8058-167">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="f8058-168">**[次へ >]** : DAC が登録され、 **[DAC の登録]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-168">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="f8058-169">**[キャンセル]** : DAC を登録せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f8058-169">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="summary"></a><span data-ttu-id="f8058-170">まとめ</span><span class="sxs-lookup"><span data-stu-id="f8058-170">Summary</span></span>  
 <span data-ttu-id="f8058-171">**[次の設定を使用して DAC を登録します。]**</span><span class="sxs-lookup"><span data-stu-id="f8058-171">**The following setting will be used to register your DAC.**</span></span> <span data-ttu-id="f8058-172">: DAC に追加されるプロパティとオブジェクトのレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-172">- Displays a report of the properties and objects that will be included in the DAC.</span></span>  
  
 <span data-ttu-id="f8058-173">**[レポートの保存]** : 検証レポートのコピーを HTML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="f8058-173">**Save Report** - Select this button to save a copy of the validation report to an HTML file.</span></span> <span data-ttu-id="f8058-174">既定のフォルダーは、Windows アカウントの Documents フォルダーにある **SQL Server Management Studio\DAC Packages** フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="f8058-174">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="f8058-175">[ \*\* \< 戻る**]: [**プロパティの設定\*\*] ページに戻り、エントリを変更します。</span><span class="sxs-lookup"><span data-stu-id="f8058-175">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="f8058-176">**[次へ >]** : DAC が登録され、 **[DAC の登録]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-176">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="f8058-177">**[キャンセル]** : DAC を登録せずにウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f8058-177">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="register-dac-page"></a><a name="Register"></a> <span data-ttu-id="f8058-178">[DAC の登録] ページ</span><span class="sxs-lookup"><span data-stu-id="f8058-178">Register DAC Page</span></span>  
 <span data-ttu-id="f8058-179">このページには、登録の成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-179">This page reports the success or failure of the registration.</span></span>  
  
 <span data-ttu-id="f8058-180">**[DAC の登録]** : DAC を登録するために行った各アクションの成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-180">**Registering the DAC** - Reports the success or failure of each action taken to register the DAC.</span></span> <span data-ttu-id="f8058-181">内容を確認して、各アクションの成功または失敗を判断します。</span><span class="sxs-lookup"><span data-stu-id="f8058-181">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="f8058-182">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-182">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="f8058-183">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8058-183">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="f8058-184">**[レポートの保存]** : 登録レポートを HTML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="f8058-184">**Save Report** - Select this button to save the registration report to an HTML file.</span></span> <span data-ttu-id="f8058-185">ファイルには、アクションで発生したすべてのエラーを含む、各アクションのステータスが報告されます。</span><span class="sxs-lookup"><span data-stu-id="f8058-185">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="f8058-186">既定のフォルダーは、Windows アカウントの Documents フォルダーにある **SQL Server Management Studio\DAC Packages** フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="f8058-186">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span> <span data-ttu-id="f8058-187">ファイル名の形式は、\<DACPackageName>_RegisterDACReport_yyyymmdd.html です。ここで、\<*DACPackageName*> は配置するパッケージの名前、*yyyy* は現在の年、*mm* は現在の月、*dd* は現在の日です。</span><span class="sxs-lookup"><span data-stu-id="f8058-187">The file name is in the format \<DACPackageName>_RegisterDACReport_yyyymmdd.html, where \<*DACPackageName*> is the name of the package being deployed, *yyyy* = the current year, *mm* = the current month, and *dd* = the current day.</span></span>  
  
 <span data-ttu-id="f8058-188">**[完了]** : ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f8058-188">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="register-a-dac-using-powershell"></a><a name="RegisterDACPowerShell"></a> <span data-ttu-id="f8058-189">PowerShell を使用した DAC の登録</span><span class="sxs-lookup"><span data-stu-id="f8058-189">Register a DAC Using PowerShell</span></span>  
 <span data-ttu-id="f8058-190">**PowerShell スクリプトから Register() メソッドを使用してデータベースを DAC として登録するには**</span><span class="sxs-lookup"><span data-stu-id="f8058-190">**To register a database as a DAC using the Register() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="f8058-191">SMO サーバー オブジェクトを作成し、DAC として登録するデータベースを含んだインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="f8058-191">Create a SMO Server object and set it to the instance that contains the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="f8058-192">データベースの名前を指定する変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="f8058-192">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="f8058-193">DAC のメタデータ (DAC 名、バージョン、説明など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8058-193">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="f8058-194">上記で指定した情報を使用して Register メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8058-194">Run the Register method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="f8058-195">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f8058-195">Example (PowerShell)</span></span>  
 <span data-ttu-id="f8058-196">次の例は、DAC として MyDB というデータベースを登録します。</span><span class="sxs-lookup"><span data-stu-id="f8058-196">The following example registers a database named MyDB as a DAC.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to register as a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Register the DAC.  
$registerunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$registerunit.Description = $description  
$registerunit.Register()  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8058-197">参照</span><span class="sxs-lookup"><span data-stu-id="f8058-197">See Also</span></span>  
 [<span data-ttu-id="f8058-198">データ層アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f8058-198">Data-tier Applications</span></span>](data-tier-applications.md)  

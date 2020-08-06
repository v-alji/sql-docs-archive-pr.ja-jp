---
title: '[パッケージの保存および実行] (SQL Server インポートおよびエクスポートウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a23f69bf66ca3355f1e1c62cc42d51e4aea3da5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642886"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="d92a1-102">[パッケージの保存および実行] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="d92a1-102">Save and Execute Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="d92a1-103">[**パッケージの保存と実行**] ダイアログボックスを使用すると、すぐにパッケージを実行したり、後で実行するように保存したり、その両方を実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-103">Use the **Save and Execute Package** dialog box to run the package immediately, save it to run later, or both.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-104">パッケージの実行が完了する前に停止した場合、[**保存**] チェックボックスをオンにした場合でも、パッケージは保存されません。</span><span class="sxs-lookup"><span data-stu-id="d92a1-104">If you stop a package before it finishes running, the package is not saved, even if you selected the **Save** check box.</span></span>  
  
 <span data-ttu-id="d92a1-105">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92a1-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="d92a1-106">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92a1-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="d92a1-107">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="d92a1-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="d92a1-108">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="d92a1-109">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d92a1-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="d92a1-110">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92a1-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d92a1-111">Options</span><span class="sxs-lookup"><span data-stu-id="d92a1-111">Options</span></span>  
 <span data-ttu-id="d92a1-112">**直ちに実行**</span><span class="sxs-lookup"><span data-stu-id="d92a1-112">**Execute immediately**</span></span>  
 <span data-ttu-id="d92a1-113">このオプションを選択すると、すぐにパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="d92a1-113">Select this option to run the package immediately.</span></span>  
  
 <span data-ttu-id="d92a1-114">**[SSIS パッケージの保存]**</span><span class="sxs-lookup"><span data-stu-id="d92a1-114">**Save SSIS Package**</span></span>  
 <span data-ttu-id="d92a1-115">パッケージをすぐに実行するためのオプションを使用して、パッケージを後で実行するために保存します。</span><span class="sxs-lookup"><span data-stu-id="d92a1-115">Save the package to run later, with the option to run it immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-116">では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ウィザードによって作成されたパッケージを保存するオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d92a1-116">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="d92a1-117">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="d92a1-117">**SQL Server**</span></span>  
 <span data-ttu-id="d92a1-118">パッケージをデータベースに保存するには、このオプションを選択し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` ます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-118">Select this option to save the package to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-119">このオプションは、[ **SSIS パッケージの保存**] オプションを選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-119">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="d92a1-120">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="d92a1-120">**File system**</span></span>  
 <span data-ttu-id="d92a1-121">このオプションを選択して、.dtsx 拡張子を持つファイルとしてパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="d92a1-121">Select this option to save the package as a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-122">このオプションは、[ **SSIS パッケージの保存**] オプションを選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-122">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="d92a1-123">**パッケージの保護レベル**</span><span class="sxs-lookup"><span data-stu-id="d92a1-123">**Package protection level**</span></span>  
 <span data-ttu-id="d92a1-124">一覧から保護レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d92a1-124">Select a protection level from the list.</span></span>  
  
 <span data-ttu-id="d92a1-125">保護レベルによって、パッケージ保護の方法、パスワードまたはユーザー キー、適用範囲が決定されます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-125">The protection level determines the protection method, the password or user key, and the scope of package protection.</span></span> <span data-ttu-id="d92a1-126">保護対象には、すべてのデータを含めることも機密データのみを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-126">Protection can include all data or sensitive data only.</span></span> <span data-ttu-id="d92a1-127">パッケージのセキュリティの要件とオプションを理解するには、「パッケージとセキュリティの[概要 &#40;Integration Services&#41;](../security/security-overview-integration-services.md)の[機密データの Access Control](../security/access-control-for-sensitive-data-in-packages.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92a1-127">To understand the requirements and options for package security, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md) and [Security Overview &#40;Integration Services&#41;](../security/security-overview-integration-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-128">このオプションは、[ **SSIS パッケージの保存**] オプションを選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-128">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="d92a1-129">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="d92a1-129">**Password**</span></span>  
 <span data-ttu-id="d92a1-130">パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d92a1-130">Type a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-131">このオプションは、[**パッケージの保護レベル**] オプションで [**機微なデータをパスワードで暗号化**する] または [**すべてのデータをパスワードで暗号化**する] を設定した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-131">This option is available only if you have set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.</span></span>  
  
 <span data-ttu-id="d92a1-132">**[パスワードの再入力]**</span><span class="sxs-lookup"><span data-stu-id="d92a1-132">**Retype password**</span></span>  
 <span data-ttu-id="d92a1-133">パスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="d92a1-133">Type the password again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d92a1-134">このオプションは、[**パッケージの保護レベル**] オプションで [**機微なデータをパスワードで暗号化**する] または [**すべてのデータをパスワードで暗号化**する] を設定した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92a1-134">This option is available only if you have set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92a1-135">参照</span><span class="sxs-lookup"><span data-stu-id="d92a1-135">See Also</span></span>  
 <span data-ttu-id="d92a1-136">[プロジェクトとパッケージの実行](../packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="d92a1-136">[Execution of Projects and Packages](../packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="d92a1-137">パッケージを保存する</span><span class="sxs-lookup"><span data-stu-id="d92a1-137">Save Packages</span></span>](../save-packages.md)  
  
  

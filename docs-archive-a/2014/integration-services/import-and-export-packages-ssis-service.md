---
title: パッケージのインポートとエクスポート (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], importing
- packages [Integration Services], exporting
- importing packages
- exporting packages
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b69f9d23431ed86f6b84be6857b7104cd8ba3dcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642916"
---
# <a name="import-and-export-packages-ssis-service"></a><span data-ttu-id="b90bc-102">パッケージをインポートおよびエクスポートする (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="b90bc-102">Import and Export Packages (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="b90bc-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="b90bc-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b90bc-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="b90bc-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="b90bc-106">パッケージは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb データベースの sysssispackages テーブルまたはファイル システムに保存できます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-106">Packages can be saved either in the sysssispackages table in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database or in the file system.</span></span>  
  
 <span data-ttu-id="b90bc-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスによって監視および管理される論理ストレージであるパッケージ ストアには、msdb データベースと、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの構成ファイルに指定されているファイル システム フォルダーの両方を格納できます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-107">The package store, which is the logical storage that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service monitors and manages, can include both the msdb database and the file system folders specified in the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="b90bc-108">パッケージは、次の種類のストレージ間でインポートおよびエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-108">You can import and export packages between the following storage types:</span></span>  
  
-   <span data-ttu-id="b90bc-109">ファイル システム上の任意の場所にあるファイル システム フォルダー。</span><span class="sxs-lookup"><span data-stu-id="b90bc-109">File system folders anywhere in the file system.</span></span>  
  
-   <span data-ttu-id="b90bc-110">SSIS パッケージ ストア内のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="b90bc-110">Folders in the SSIS Package Store.</span></span> <span data-ttu-id="b90bc-111">[ファイル システム] と [MSDB] の 2 つの既定のフォルダーがあります。</span><span class="sxs-lookup"><span data-stu-id="b90bc-111">The two default folders are named File System and MSDB.</span></span>  
  
-   <span data-ttu-id="b90bc-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb データベース。</span><span class="sxs-lookup"><span data-stu-id="b90bc-112">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="b90bc-113">では、パッケージをインポートおよびエクスポートできます。これは、パッケージの保存形式と位置が変わることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-113">gives you the ability to import and export packages, and by doing this change the storage format and location of packages.</span></span> <span data-ttu-id="b90bc-114">インポートおよびエクスポート機能を使用すると、ファイル システム、パッケージ ストア、または msdb データベースにパッケージを追加したり、いずれかの保存形式から別の保存形式にパッケージをコピーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-114">Using the import and export features, you can add packages to the file system, package store, or msdb database, and copy packages from one storage format to another.</span></span> <span data-ttu-id="b90bc-115">たとえば、msdb に保存されているパッケージをファイル システムにコピーしたり、その逆の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-115">For example, packages saved in msdb can be copied to the file system and vice versa.</span></span>  
  
 <span data-ttu-id="b90bc-116">**dtutil** コマンド プロンプト ユーティリティ (dtutil.exe) を使用してパッケージを別の形式にコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-116">You can also copy a package to a different format using the **dtutil** command prompt utility (dtutil.exe).</span></span> <span data-ttu-id="b90bc-117">詳細については、「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b90bc-117">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="to-import-or-export-a-package"></a><span data-ttu-id="b90bc-118">パッケージをインポートまたはエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="b90bc-118">To import or export a package</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b90bc-119">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に含まれている [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-119">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that is part of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="b90bc-120">では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] との互換性を維持するために、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]サービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b90bc-120">supports the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for backward compatibility with [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="b90bc-121">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] でのパッケージ管理の詳細については、「[Integration Services (SSIS) Server](catalog/integration-services-ssis-server-and-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b90bc-121">For information about managing packages in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="b90bc-122">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージは、次の場所からインポートしたり、次の場所にエクスポートしたりできます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-122">You can import or export an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from or to the following locations:</span></span>  
  
-   <span data-ttu-id="b90bc-123">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス、ファイル システム、または [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストアに格納されているパッケージをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-123">You can import a package that is stored in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], in the file system, or in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span> <span data-ttu-id="b90bc-124">インポートしたパッケージは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、または [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストア内のフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-124">The imported package is saved to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to a folder in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span>  
  
-   <span data-ttu-id="b90bc-125">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンス、ファイル システム、または [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストアに格納されているパッケージを異なるストレージ形式および場所にエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-125">You can export a package that is stored in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the file system, or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store to a different storage format and location.</span></span>  
  
 <span data-ttu-id="b90bc-126">ただし、異なるバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]間でパッケージをインポートおよびエクスポートするには、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="b90bc-126">However, there are some restrictions on importing and exporting a package between different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b90bc-127">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]のインスタンスでは、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]のインスタンスからパッケージをインポートできますが、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]のインスタンスにパッケージをエクスポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b90bc-127">On an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], you can import packages from an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], but you cannot export packages to an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="b90bc-128">[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]のインスタンスでは、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]のインスタンスとの間で、パッケージをインポートすることも、エクスポートすることもできません。</span><span class="sxs-lookup"><span data-stu-id="b90bc-128">On an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you cannot import packages from, or export packages to, an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="b90bc-129">次の手順では、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用してパッケージをインポートまたはエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-129">The following procedures describe how to use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to import or export a package.</span></span>  
  
#### <a name="to-import-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="b90bc-130">SQL Server Management Studio を使用してパッケージをインポートするには</span><span class="sxs-lookup"><span data-stu-id="b90bc-130">To import a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b90bc-131">**[スタート]** ボタンをクリックし、 **[Microsoft** ] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をポイントして、 **[SQL Server Management Studio]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-131">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="b90bc-132">**[サーバーへの接続]** ダイアログ ボックスで、次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-132">In the **Connect to Server** dialog box set the following options:</span></span>  
  
    -   <span data-ttu-id="b90bc-133">**[サーバーの種類]** ボックスの一覧の **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-133">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="b90bc-134">**[サーバー名]** ボックスで、サーバー名を入力するか、 **[\<Browse for more...>]** をクリックして使用するサーバーの場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-134">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="b90bc-135">オブジェクト エクスプローラーが開いていない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-135">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="b90bc-136">オブジェクト エクスプローラーで、 **[格納されたパッケージ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-136">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="b90bc-137">サブフォルダーを展開し、パッケージのインポート先のフォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-137">Expand the subfolders to locate the folder into which you want to import a package.</span></span>  
  
6.  <span data-ttu-id="b90bc-138">フォルダーを右クリックし、 **[パッケージのインポート]** をクリックして、</span><span class="sxs-lookup"><span data-stu-id="b90bc-138">Right-click the folder, click **Import Package**.</span></span> <span data-ttu-id="b90bc-139">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b90bc-139">and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="b90bc-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスからインポートするには、 **[SQL Server]** をクリックし、サーバーを指定して認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-140">To import from an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="b90bc-141">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択した場合は、ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-141">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="b90bc-142">参照ボタン **[...]** をクリックし、インポートするパッケージを選択します。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-142">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
    -   <span data-ttu-id="b90bc-143">ファイル システムからインポートするには、 **[ファイル システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-143">To import from the file system, select the **File system** option.</span></span>  
  
         <span data-ttu-id="b90bc-144">参照ボタン **[...]** をクリックし、インポートするパッケージを選択します。次に、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-144">Click the browse button **(...)**, select the package to import, and then click **Open.**</span></span>  
  
    -   <span data-ttu-id="b90bc-145">[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストアからインポートするには、 **[SSIS パッケージ ストア]** をクリックし、サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-145">To import from the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, select the **SSIS Package Store** option and specify the server.</span></span>  
  
         <span data-ttu-id="b90bc-146">参照ボタン **[...]** をクリックし、インポートするパッケージを選択します。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-146">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
7.  <span data-ttu-id="b90bc-147">必要に応じて、パッケージ名を更新します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-147">Optionally, update the package name.</span></span>  
  
8.  <span data-ttu-id="b90bc-148">パッケージの保護レベルを更新するには、参照ボタン **[...]** をクリックし、 **[パッケージの保護レベル]** ダイアログ ボックスで別の保護レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-148">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="b90bc-149">**[機微なデータをパスワードで暗号化する]** または **[すべてのデータをパスワードで暗号化する]** をクリックした場合は、パスワードを入力して確認します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-149">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
9. <span data-ttu-id="b90bc-150">**[OK]** をクリックすると、インポートが完了します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-150">Click **OK** to complete the import.</span></span>  
  
#### <a name="to-export-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="b90bc-151">SQL Server Management Studio を使用してパッケージをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="b90bc-151">To export a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b90bc-152">**[スタート]** ボタンをクリックし、 **[Microsoft** ] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をポイントして、 **[SQL Server Management Studio]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-152">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="b90bc-153">**[サーバーへの接続]** ダイアログ ボックスで、次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-153">In the **Connect to Server** dialog box, set the following options:</span></span>  
  
    -   <span data-ttu-id="b90bc-154">**[サーバーの種類]** ボックスの一覧の **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-154">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="b90bc-155">**[サーバー名]** ボックスで、サーバー名を入力するか、 **[\<Browse for more...>]** をクリックして使用するサーバーの場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="b90bc-155">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="b90bc-156">オブジェクト エクスプローラーが開いていない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-156">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="b90bc-157">オブジェクト エクスプローラーで、 **[格納されたパッケージ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-157">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="b90bc-158">サブフォルダーを展開し、エクスポートするパッケージを探します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-158">Expand the subfolders to locate the package you want to export.</span></span>  
  
6.  <span data-ttu-id="b90bc-159">パッケージを右クリックして **[エクスポート]** をクリックし、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b90bc-159">Right-click the package, click **Export**, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="b90bc-160">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスにエクスポートするには、 **[SQL Server]** をクリックし、サーバーを指定して認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-160">To export to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="b90bc-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択した場合は、ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-161">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="b90bc-162">参照ボタン **[...]** をクリックして **[SSIS パッケージ]** フォルダーを展開し、パッケージを保存するフォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-162">Click the browse button **(...)**, and expand the **SSIS Packages** folder to locate the folder to which you want to save the package.</span></span> <span data-ttu-id="b90bc-163">必要に応じて、パッケージの既定の名前を更新し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-163">Optionally, update the default name of the package, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="b90bc-164">ファイル システムにエクスポートするには、 **[ファイル システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-164">To export to the file system, select the **File System** option.</span></span>  
  
         <span data-ttu-id="b90bc-165">参照ボタン **[...]** をクリックし、パッケージのエクスポート先のフォルダーを探します。次に、パッケージ ファイルの名前を入力して **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b90bc-165">Click the browse button **(...)** to locate the folder to which you want to export the package, type the name of the package file, and then click **Save.**</span></span>  
  
    -   <span data-ttu-id="b90bc-166">[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストアにエクスポートするには、 **[SSIS パッケージ ストア]** をクリックしてサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-166">To export to the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store, select the **SSIS Package Store** option, and specify the server.</span></span>  
  
         <span data-ttu-id="b90bc-167">参照ボタン **[...]** をクリックして **[SSIS パッケージ]** フォルダーを展開し、パッケージを保存するフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-167">Click the browse button **(...)**, expand the **SSIS Packages** folder, and select the folder to which you want to save the package.</span></span> <span data-ttu-id="b90bc-168">必要に応じて、パッケージの新しい名前を **[パッケージ名]** テキスト ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-168">Optionally, enter a new name for the package in the **Package Name** text box.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="b90bc-169">パッケージの保護レベルを更新するには、参照ボタン **[...]** をクリックし、 **[パッケージの保護レベル]** ダイアログ ボックスで別の保護レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-169">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="b90bc-170">**[機微なデータをパスワードで暗号化する]** または **[すべてのデータをパスワードで暗号化する]** をクリックした場合は、パスワードを入力して確認します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-170">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
8.  <span data-ttu-id="b90bc-171">**[OK]** をクリックすると、エクスポートが完了します。</span><span class="sxs-lookup"><span data-stu-id="b90bc-171">Click **OK** to complete the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90bc-172">参照</span><span class="sxs-lookup"><span data-stu-id="b90bc-172">See Also</span></span>  
 [<span data-ttu-id="b90bc-173">パッケージの管理 &#40;SSIS サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="b90bc-173">Package Management &#40;SSIS Service&#41;</span></span>](service/package-management-ssis-service.md)  
  
  

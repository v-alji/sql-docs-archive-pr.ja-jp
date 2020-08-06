---
title: パッケージのコピーを保存する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 02ee2374fddb7dbb6b17adc2a4a10707179c882d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714513"
---
# <a name="save-a-copy-of-a-package"></a><span data-ttu-id="9e93c-102">パッケージのコピーを保存する</span><span class="sxs-lookup"><span data-stu-id="9e93c-102">Save a Copy of a Package</span></span>
  <span data-ttu-id="9e93c-103">この手順では、パッケージのコピーをファイル システム、パッケージ ストア、または [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の **msdb** データベースに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-103">This procedure describes how to save a copy of a package to the file system, to the package store, or to the **msdb** database in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e93c-104">パッケージのコピーを保存する場所を指定するとき、パッケージの名前を更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-104">When you specify a location to save the package copy, you can also update the name of the package.</span></span>  
  
 <span data-ttu-id="9e93c-105">パッケージ ストアには、 **msdb** データベースとファイル システム内のフォルダーの両方、 **msdb**のみ、またはファイル システム内のフォルダーのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-105">The package store can include both the **msdb** database and the folders in the file system, only **msdb**, or only folders in the file system.</span></span> <span data-ttu-id="9e93c-106">**msdb**では、パッケージは **sysssispackages** テーブルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-106">In **msdb**, packages are saved to the **sysssispackages** table.</span></span> <span data-ttu-id="9e93c-107">このテーブルには、パッケージが属する論理フォルダーを識別する **folderid** 列があります。</span><span class="sxs-lookup"><span data-stu-id="9e93c-107">This table includes a **folderid** column that identifies the logical folder to which the package belongs.</span></span> <span data-ttu-id="9e93c-108">論理フォルダーは、 **msdb** に保存されるパッケージをグループ化するための便利な方法を提供します。これは、ファイル システムのフォルダーが、ファイル システムに保存されるパッケージをグループ化する方法を提供するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="9e93c-108">The logical folders provide a useful way to group packages saved to **msdb** in the same way that folders in the file system provide a way to group packages saved to the file system.</span></span> <span data-ttu-id="9e93c-109">**msdb** 内の **sysssispackagefolders** テーブルの行は、フォルダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-109">Rows in the **sysssispackagefolders** table in **msdb** define the folders.</span></span>  
  
 <span data-ttu-id="9e93c-110">**msdb** がパッケージ ストアの一部として定義されていない場合は、 **[パッケージのパス]** オプションで [SQL Server] を選択するときに、引き続きパッケージを既存の論理フォルダーに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-110">If **msdb** is not defined as part of the package store, you can continue to associate packages with existing logical folders when you select SQL Server in the **Package Path** option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e93c-111">パッケージのコピーを保存するには、事前にパッケージを [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e93c-111">The package must be opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer before you can save a copy of the package.</span></span>  
  
### <a name="to-save-a-copy-of-a-package"></a><span data-ttu-id="9e93c-112">パッケージのコピーを保存するには</span><span class="sxs-lookup"><span data-stu-id="9e93c-112">To save a copy of a package</span></span>  
  
1.  <span data-ttu-id="9e93c-113">ソリューション エクスプローラーで、コピーを保存するパッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-113">In Solution Explorer, double-click the package of which you want to save a copy.</span></span>  
  
2.  <span data-ttu-id="9e93c-114">**[ファイル]** メニューの **[\<package file> のコピーに名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-114">On the **File** menu, click **Save Copy of \<package file> As**.</span></span>  
  
3.  <span data-ttu-id="9e93c-115">**[パッケージのコピーの保存]** ダイアログ ボックスで、 **[パッケージの場所]** 一覧からパッケージの保存場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-115">In the **Save Copy of Package** dialog box, select a package location in the **Package location** list.</span></span>  
  
4.  <span data-ttu-id="9e93c-116">保存場所が **[SQL Server]** または **[SSIS パッケージ ストア]** の場合、サーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-116">If the location is **SQL Server** or **SSIS Package Store**, provide a server name.</span></span>  
  
5.  <span data-ttu-id="9e93c-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に保存する場合は、認証の種類を指定します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合、ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-117">If saving to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify the authentication type and, if using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and password.</span></span>  
  
6.  <span data-ttu-id="9e93c-118">パッケージのパスを指定するには、パスを入力するか、参照ボタン **[...]** をクリックしてパッケージの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-118">To specify the package path, either type the path or click the browse button **(...)** to specify the location of the package.</span></span> <span data-ttu-id="9e93c-119">パッケージの既定の名前は Package です。</span><span class="sxs-lookup"><span data-stu-id="9e93c-119">The default name of the package is Package.</span></span> <span data-ttu-id="9e93c-120">必要に応じて、パッケージの名前をニーズに合う名前に更新します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-120">Optionally, update the package name to one that suits your needs.</span></span>  
  
     <span data-ttu-id="9e93c-121">**[パッケージのパス]** オプションとして **[SQL Server]** を選択した場合、パッケージのパスは、 **msdb** 内の論理フォルダーとパッケージ名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-121">If you select **SQL Server** as the **Package Path** option, the package path consists of logical folders in **msdb** and the package name.</span></span> <span data-ttu-id="9e93c-122">たとえば、パッケージ DownloadMonthlyData が [MSDB] フォルダー ( **msdb**内のルート論理フォルダーの既定の名前) 内の [Finance] フォルダーと関連付けられている場合、DownloadMonthlyData という名前のパッケージのパッケージ パスは MSDB/Finance/DownloadMonthlyData になります。</span><span class="sxs-lookup"><span data-stu-id="9e93c-122">For example, if the package DownloadMonthlyData is associated with the Finance folder within the MSDB folder (the default name of the root logical folder in **msdb**), the package path for the package named DownloadMonthlyData is MSDB/Finance/DownloadMonthlyData</span></span>  
  
     <span data-ttu-id="9e93c-123">**[パッケージのパス]** オプションとして **[SSIS パッケージ ストア]** を選択した場合、パッケージのパスは、Integration Services サービスが管理するフォルダーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-123">If you select **SSIS Package Store** as the **Package Path** option, the package path consists of the folder that the Integration Services service manages.</span></span> <span data-ttu-id="9e93c-124">たとえば、パッケージ UpdateDeductions が、Integration Services サービスが管理するファイル システム フォルダー内の [HumanResources] フォルダーに存在する場合、パッケージのパスは /File System/HumanResources/UpdateDeductions になります。同様に、パッケージ PostResumes が [MSDB] フォルダー内の [HumanResources] フォルダーに関連付けられている場合、パッケージのパスは MSDB/HumanResources/PostResumes になります。</span><span class="sxs-lookup"><span data-stu-id="9e93c-124">For example, if the package UpdateDeductions is located in the HumanResources folder within the file system folder that the service manages, the package path is /File System/HumanResources/UpdateDeductions; likewise, if the package PostResumes is associated with the HumanResources folder within the MSDB folder, the package path is MSDB/HumanResources/PostResumes.</span></span>  
  
     <span data-ttu-id="9e93c-125">**[パッケージのパス]** オプションとして **[ファイル システム]** を選択した場合、パッケージのパスは、ファイル システム内の場所とファイル名になります。</span><span class="sxs-lookup"><span data-stu-id="9e93c-125">If you select **File System** as the **Package Path** option, the package path is the location in the file system and the file name.</span></span> <span data-ttu-id="9e93c-126">たとえば、パッケージ名が UpdateDemographics の場合、パッケージのパスは C:\HumanResources\Quarterly\UpdateDemographics.dtsx になります。</span><span class="sxs-lookup"><span data-stu-id="9e93c-126">For example, if the package name is UpdateDemographics the package path is C:\HumanResources\Quarterly\UpdateDemographics.dtsx.</span></span>  
  
7.  <span data-ttu-id="9e93c-127">パッケージの保護レベルを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-127">Review the package protection level.</span></span>  
  
8.  <span data-ttu-id="9e93c-128">必要に応じて、 **[保護レベル]** ボックスの近くの参照ボタン **[...]** をクリックし、保護レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-128">Optionally, click the browse button **(...)** by the **Protection level** box to change the protection level.</span></span>  
  
    -   <span data-ttu-id="9e93c-129">**[パッケージの保護レベル]** ダイアログ ボックスで、別の保護レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-129">In the **Package Protection Level** dialog box, select a different protection level.</span></span>  
  
    -   <span data-ttu-id="9e93c-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-130">Click **OK**.</span></span>  
  
9. <span data-ttu-id="9e93c-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-131">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e93c-132">参照</span><span class="sxs-lookup"><span data-stu-id="9e93c-132">See Also</span></span>  
 <span data-ttu-id="9e93c-133">[SSIS&#41; パッケージ &#40;Integration Services](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="9e93c-133">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="9e93c-134">Integration Services サービスの構成 (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="9e93c-134">Configuring the Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  

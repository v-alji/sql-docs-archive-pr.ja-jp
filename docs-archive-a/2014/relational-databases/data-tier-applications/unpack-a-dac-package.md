---
title: DAC パッケージのアンパック | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- wizard [DAC], unpack
- data-tier application [SQL Server], unpack
- How to [DAC], unpack
- unpack DAC
ms.assetid: 697b69b3-f157-4e22-ac4e-f65c5fc2d0ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ba0930f79a47696a6c9a9c1bfe028316601f64b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645640"
---
# <a name="unpack-a-dac-package"></a><span data-ttu-id="b5a86-102">DAC パッケージのアンパック</span><span class="sxs-lookup"><span data-stu-id="b5a86-102">Unpack a DAC Package</span></span>
  <span data-ttu-id="b5a86-103">[データ層アプリケーションのアンパック] ダイアログ ボックスでは、データ層アプリケーション (DAC) パッケージからスクリプトおよびファイルを解凍できます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-103">Use the Unpack Data-tier Application dialog box to unzip the scripts and files from a data-tier application (DAC) package.</span></span> <span data-ttu-id="b5a86-104">解凍されたスクリプトおよびファイルが配置されるフォルダーは、パッケージを使用して DAC を実稼働システムに配置する前に確認できます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-104">The scripts and files are placed in a folder where they can be reviewed before the package is used to deploy the DAC into a production system.</span></span> <span data-ttu-id="b5a86-105">また、DAC の内容は、別のフォルダーにアンパックされた別のパッケージの内容と比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-105">The contents of one DAC can also be compared with the contents of another package unpacked to another folder.</span></span>  
  
1.  <span data-ttu-id="b5a86-106">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="b5a86-106">**Before you begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="b5a86-107">**DAC のアンパック:** [[データ層アプリケーションのアンパック] ダイアログの使用](#UnpackDACDial)、[DAC パッケージの内容の確認](#ExamDACPack)</span><span class="sxs-lookup"><span data-stu-id="b5a86-107">**To unpack a DAC, using:**  [Unpack Data-tier Application Dialog](#UnpackDACDial), [Examine the Contents of a DAC Package](#ExamDACPack)</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b5a86-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b5a86-108">Security</span></span>  
 <span data-ttu-id="b5a86-109">ソースが不明または信頼されていない DAC パッケージは配置しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b5a86-109">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="b5a86-110">こうした DAC には、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマを変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5a86-110">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="b5a86-111">DAC のソースが不明または信頼されていない場合は、使用する前に、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の隔離されたテスト インスタンスに DAC を配置し、DAC をアンパックして、ストアド プロシージャやその他のユーザー定義コードなどのコードを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b5a86-111">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
##  <a name="unpack-data-tier-application-dialog"></a><a name="UnpackDACDial"></a> <span data-ttu-id="b5a86-112">[データ層アプリケーションのアンパック] ダイアログの使用</span><span class="sxs-lookup"><span data-stu-id="b5a86-112">Unpack Data-tier Application Dialog</span></span>  
 <span data-ttu-id="b5a86-113">**DAC パッケージ ファイルをアンパックするには**</span><span class="sxs-lookup"><span data-stu-id="b5a86-113">**To Unpack a DAC Package File**</span></span>  
  
-   <span data-ttu-id="b5a86-114">**Windows エクスプローラー**で、DAC パッケージ (.dacpac) ファイルの場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-114">In **Windows Explorer**, navigate to the location of a DAC package (.dacpac) file.</span></span>  
  
-   <span data-ttu-id="b5a86-115">[データ層アプリケーションのアンパック] ダイアログ ボックスを開くには、次の 2 つの方法のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-115">Use one of these two methods to open the Unpack Data-tier Application dialog:</span></span>  
  
    1.  <span data-ttu-id="b5a86-116">DAC パッケージ (.dacpac) ファイルを右クリックして、 **[アンパック]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5a86-116">Right-click the DAC package (.dacpac) file and select **Unpack**.</span></span>  
  
    2.  <span data-ttu-id="b5a86-117">DAC パッケージ ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5a86-117">Double-click the DAC package file.</span></span>  
  
-   <span data-ttu-id="b5a86-118">次のダイアログで必要な設定を行います。</span><span class="sxs-lookup"><span data-stu-id="b5a86-118">Complete the dialogs:</span></span>  
  
    -   <span data-ttu-id="b5a86-119">[[Microsoft SQL Server DAC パッケージ ファイルのアンパック]](#Unpack)</span><span class="sxs-lookup"><span data-stu-id="b5a86-119">[Unpack Microsoft SQL Server DAC Package File](#Unpack)</span></span>  
  
    -   <span data-ttu-id="b5a86-120">[[フォルダーの参照]](#Browse)</span><span class="sxs-lookup"><span data-stu-id="b5a86-120">[Browse for Folder](#Browse)</span></span>  
  
###  <a name="unpack-microsoft-sql-server-dac-package-file"></a><a name="Unpack"></a> <span data-ttu-id="b5a86-121">[Microsoft SQL Server DAC パッケージ ファイルのアンパック]</span><span class="sxs-lookup"><span data-stu-id="b5a86-121">Unpack Microsoft SQL Server DAC Package File</span></span>  
 <span data-ttu-id="b5a86-122">このページでは、アンパックされたファイルの配置先となるフォルダーを指定し、アンパック操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-122">Use this page to specify the destination folder in which to place the unpacked files, and then run the unpack operation.</span></span>  
  
 <span data-ttu-id="b5a86-123">**[ファイルがアンパックされるフォルダー]:** アンパックされたファイルのフォルダーへの完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-123">**Files will be unpacked to this folder:** - Specify the full path to the folder for the unpacked files.</span></span> <span data-ttu-id="b5a86-124">フォルダーが存在し、完全パスがわかっている場合は、このボックスにパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-124">If the folder exists and you know the full path, type the path in the box.</span></span> <span data-ttu-id="b5a86-125">それ以外の場合は、 **[参照]** をクリックしてフォルダーに移動するか、新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-125">If not, click the **Browse** button to navigate to a folder or create a new folder.</span></span>  
  
 <span data-ttu-id="b5a86-126">**[参照]** : **[フォルダーの参照]** ページを開きます。このページでは、ファイル階層を移動してフォルダーを選択したり、新しいフォルダーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-126">**Browse** - Opens the **Browse for Folder** page where you can choose a folder by navigating the file hierarchy, or create a new folder.</span></span>  
  
 <span data-ttu-id="b5a86-127">**[アンパック]** : アンパック操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-127">**Unpack** - Starts the unpack operation.</span></span>  
  
 <span data-ttu-id="b5a86-128">**[キャンセル]** : DAC パッケージをアンパックすることなく、ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-128">**Cancel** - Terminates the dialog box without unpacking the DAC package.</span></span>  
  
###  <a name="browse-for-folder"></a><a name="Browse"></a> <span data-ttu-id="b5a86-129">[フォルダーの参照]</span><span class="sxs-lookup"><span data-stu-id="b5a86-129">Browse for Folder</span></span>  
 <span data-ttu-id="b5a86-130">このページでは、アンパック操作の対象となるフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-130">Use this page to choose the destination folder for the unpack operation.</span></span> <span data-ttu-id="b5a86-131">また、必要に応じて、新しいフォルダーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-131">Optionally, you can also create a new folder.</span></span>  
  
 <span data-ttu-id="b5a86-132">**[フォルダー一覧]** : コンピューターのファイル階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-132">**Folder list** - Displays the file hierarchy for your computer.</span></span> <span data-ttu-id="b5a86-133">ノードを展開し、DAC パッケージをアンパックするフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-133">Expand the nodes to navigate to the folder in which to unpack the DAC package.</span></span> <span data-ttu-id="b5a86-134">フォルダーをクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5a86-134">Click on the folder and then click **OK**.</span></span>  
  
 <span data-ttu-id="b5a86-135">**[新しいフォルダーの作成]** : フォルダー階層で現在選択しているフォルダー内に作成する新しいフォルダーの名前を指定するダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-135">**Make New Folder** - Opens a dialog in which you can specify the name for a new folder to be created in the folder you have currently selected in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="b5a86-136">**[OK]** : **[DAC パッケージ ファイルのアンパック]** ページの **[ファイルがアンパックされるフォルダー]** ボックスで選択したフォルダーへのパスを配置して、そのページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b5a86-136">**OK** - Places the path to the folder you selected in the **Files will be unpacked to this folder** box of the **Unpack DAC Package File** page and returns you to that page.</span></span>  
  
 <span data-ttu-id="b5a86-137">**[キャンセル]** : フォルダーを選択することなく、ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="b5a86-137">**Cancel** - Terminates the dialog box without selecting a folder.</span></span>  
  
##  <a name="examine-the-contents-of-a-dac-package"></a><a name="ExamDACPack"></a> <span data-ttu-id="b5a86-138">DAC パッケージの内容の確認</span><span class="sxs-lookup"><span data-stu-id="b5a86-138">Examine the Contents of a DAC Package</span></span>  
 <span data-ttu-id="b5a86-139">パッケージをアンパックすると、 **[データ層アプリケーションのアンパック]** ダイアログ ボックスで作成されたファイルを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-139">After unpacking the package, you can examine the files produced by the **Unpack Data-tier Application** dialog.</span></span> <span data-ttu-id="b5a86-140">このダイアログ ボックスによって、選択した対象フォルダーに次のファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b5a86-140">The dialog box builds the following files in the selected destination folder:</span></span>  
  
1.  <span data-ttu-id="b5a86-141">DAC で定義されたオブジェクトを作成するためのステートメントを含む Transact-SQL スクリプト。</span><span class="sxs-lookup"><span data-stu-id="b5a86-141">A Transact-SQL script that contains the statements for creating the objects defined in the DAC.</span></span> <span data-ttu-id="b5a86-142">ファイル名は *DACName*.sql です。この場合、 *DACName* は DAC の名前になります。</span><span class="sxs-lookup"><span data-stu-id="b5a86-142">The file name is *DACName*.sql, where *DACName* is the name of the DAC.</span></span>  
  
2.  <span data-ttu-id="b5a86-143">パッケージのすべての XML ファイル。</span><span class="sxs-lookup"><span data-stu-id="b5a86-143">All XML files from the package.</span></span>  
  
3.  <span data-ttu-id="b5a86-144">DAC の配置前ファイルまたは配置後ファイルなど、DAC の Extra Files セクションにあるすべてのファイル。</span><span class="sxs-lookup"><span data-stu-id="b5a86-144">All files from the Extra Files section of the DAC, such as the DAC pre-deployment or post-deployment files.</span></span>  
  
 <span data-ttu-id="b5a86-145">詳細については、「 [Validate a DAC Package](validate-a-dac-package.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b5a86-145">For more information, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a86-146">参照</span><span class="sxs-lookup"><span data-stu-id="b5a86-146">See Also</span></span>  
 <span data-ttu-id="b5a86-147">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b5a86-147">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="b5a86-148">[データ層アプリケーションの配置](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="b5a86-148">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="b5a86-149">データ層アプリケーションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="b5a86-149">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
  
  

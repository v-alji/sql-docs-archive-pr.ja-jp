---
title: 複数ファイル接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9ebd45aa4f0794d98be6a79125bf1874913d491
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644099"
---
# <a name="multiple-files-connection-manager"></a><span data-ttu-id="fbdda-102">複数ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="fbdda-102">Multiple Files Connection Manager</span></span>
  <span data-ttu-id="fbdda-103">複数ファイル接続マネージャーを使用すると、パッケージで既存のファイルやフォルダーを参照したり、実行時にファイルやフォルダーを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-103">A Multiple Files connection manager enables a package to reference existing files and folders, or to create files and folders at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbdda-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の組み込みタスクとデータ フロー コンポーネントは、複数ファイル接続マネージャーを使用しません。</span><span class="sxs-lookup"><span data-stu-id="fbdda-104">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="fbdda-105">ただし、スクリプト タスクまたはスクリプト コンポーネントでは、この接続マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-105">However, you can use this connection manager in the Script task or Script component.</span></span> <span data-ttu-id="fbdda-106">スクリプト タスクで接続マネージャーを使用する方法については、「 [スクリプト タスクでのデータ ソースへの接続](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbdda-106">For information about how to use connection managers in the Script task, see [Connecting to Data Sources in the Script Task](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md).</span></span> <span data-ttu-id="fbdda-107">スクリプトコンポーネントで接続マネージャーを使用する方法の詳細については、「[スクリプトコンポーネントでのデータソースへの接続] (.)」を参照してください。/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="fbdda-107">For information about how to use connection managers in the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span></span>  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a><span data-ttu-id="fbdda-108">複数ファイル接続マネージャーの使用方法の種類</span><span class="sxs-lookup"><span data-stu-id="fbdda-108">Usage Types of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="fbdda-109">複数ファイル接続マネージャーの `FileUsageType` プロパティでは、接続の使用方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-109">The `FileUsageType` property of the Multiple Files connection manager specifies how the connection is used.</span></span> <span data-ttu-id="fbdda-110">複数ファイル接続マネージャーでは、ファイルの作成、フォルダーの作成、既存のファイルの使用、および既存のフォルダーの使用を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-110">The Multiple Files connection manager can create files, create folders, use existing files, and use existing folders.</span></span>  
  
 <span data-ttu-id="fbdda-111">次の表に、`FileUsageType` の値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-111">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="fbdda-112">値</span><span class="sxs-lookup"><span data-stu-id="fbdda-112">Value</span></span>|<span data-ttu-id="fbdda-113">説明</span><span class="sxs-lookup"><span data-stu-id="fbdda-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fbdda-114">**0**</span><span class="sxs-lookup"><span data-stu-id="fbdda-114">**0**</span></span>|<span data-ttu-id="fbdda-115">複数ファイル接続マネージャーは、既存のファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-115">Multiple Files connection manager uses an existing file.</span></span>|  
|<span data-ttu-id="fbdda-116">**1**</span><span class="sxs-lookup"><span data-stu-id="fbdda-116">**1**</span></span>|<span data-ttu-id="fbdda-117">複数ファイル接続マネージャーは、ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-117">Multiple Files connection manager creates a file.</span></span>|  
|<span data-ttu-id="fbdda-118">**2**</span><span class="sxs-lookup"><span data-stu-id="fbdda-118">**2**</span></span>|<span data-ttu-id="fbdda-119">複数ファイル接続マネージャーは、既存のフォルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-119">Multiple Files connection manager uses an existing folder.</span></span>|  
|<span data-ttu-id="fbdda-120">**3**</span><span class="sxs-lookup"><span data-stu-id="fbdda-120">**3**</span></span>|<span data-ttu-id="fbdda-121">複数ファイル接続マネージャーは、フォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-121">Multiple Files connection manager creates a folder.</span></span>|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a><span data-ttu-id="fbdda-122">複数ファイル接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="fbdda-122">Configuration of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="fbdda-123">複数ファイル接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に複数ファイルの接続を解決する接続マネージャーを作成し、複数ファイルの接続プロパティを設定して、複数ファイルの接続をパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-123">When you add a Multiple Files connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Files connection at run time, sets the Multiple Files connection properties, and adds the Multiple Files connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="fbdda-124">接続マネージャーの `ConnectionManagerType` プロパティは、`MULTIFILE` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-124">The `ConnectionManagerType` property of the connection manager is set to `MULTIFILE`.</span></span>  
  
 <span data-ttu-id="fbdda-125">複数ファイル接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-125">You can configure a Multiple Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="fbdda-126">ファイルとフォルダーの、使用法の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-126">Specify the usage type of files and folders.</span></span>  
  
-   <span data-ttu-id="fbdda-127">ファイルとフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-127">Specify files and folders.</span></span>  
  
-   <span data-ttu-id="fbdda-128">複数のファイルまたはフォルダーを使用する場合、ファイルとフォルダーのアクセス順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-128">If using multiple files or folders, specify the order in which the files and folders are accessed.</span></span>  
  
 <span data-ttu-id="fbdda-129">複数ファイル接続マネージャーが複数のファイルとフォルダーを参照する場合、そのファイルとフォルダーのパスは、パイプ (|) 文字で区切ります。</span><span class="sxs-lookup"><span data-stu-id="fbdda-129">If the Multiple Files connection manager references multiple files and folders, the paths of the files and folders are separated by the pipe (|) character.</span></span> <span data-ttu-id="fbdda-130">この接続マネージャーの `ConnectionString` プロパティの形式は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fbdda-130">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="fbdda-131">複数のファイルまたはフォルダーを指定する場合、ワイルドカード文字を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-131">You can also specify multiple files or folders using wildcard characters.</span></span> <span data-ttu-id="fbdda-132">たとえば、C ドライブ上のすべてのテキストファイルを参照するには、プロパティの値を `ConnectionString` c: \* .txt に設定します \\ 。</span><span class="sxs-lookup"><span data-stu-id="fbdda-132">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="fbdda-133">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="fbdda-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="fbdda-134">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](add-file-connection-manager-dialog-box-ui-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbdda-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add File Connection Manager Dialog Box UI Reference](add-file-connection-manager-dialog-box-ui-reference.md).</span></span>  
  
 <span data-ttu-id="fbdda-135">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fbdda-135">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  

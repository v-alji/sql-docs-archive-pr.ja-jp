---
title: ファイル接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cebb5438003c6b14c547d14012ff1bc1175a706d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738568"
---
# <a name="file-connection-manager"></a><span data-ttu-id="06247-102">ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="06247-102">File Connection Manager</span></span>
  <span data-ttu-id="06247-103">ファイル接続マネージャーを使用すると、パッケージで既存のファイルやフォルダーを参照したり、実行時にファイルやフォルダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="06247-103">A File connection manager enables a package to reference an existing file or folder, or to create a file or folder at run time.</span></span> <span data-ttu-id="06247-104">たとえば、Excel ファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="06247-104">For example, you can reference an Excel file.</span></span> <span data-ttu-id="06247-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の特定のコンポーネントでは、ファイルの情報を使用して作業が実行されます。</span><span class="sxs-lookup"><span data-stu-id="06247-105">Certain components in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] use information in files to perform their work.</span></span> <span data-ttu-id="06247-106">たとえば、SQL 実行タスクでは、そのタスクで実行する SQL ステートメントが含まれるファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="06247-106">For example, an Execute SQL task can reference a file that contains the SQL statements that the task executes.</span></span> <span data-ttu-id="06247-107">他のコンポーネントは、ファイルに対する操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="06247-107">Other components perform operations on files.</span></span> <span data-ttu-id="06247-108">たとえば、ファイル システム タスクは新しい場所にコピーするファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="06247-108">For example, the File System task can reference a file to copy it to a new location.</span></span>  
  
## <a name="usage-types-of-the-file-connection-manager"></a><span data-ttu-id="06247-109">ファイル接続マネージャーの使用法の種類</span><span class="sxs-lookup"><span data-stu-id="06247-109">Usage Types of the File Connection Manager</span></span>  
 <span data-ttu-id="06247-110">ファイル接続マネージャーの `FileUsageType` プロパティでは、ファイル接続の使用方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="06247-110">The `FileUsageType` property of the File connection manager specifies how the file connection is used.</span></span> <span data-ttu-id="06247-111">ファイル接続マネージャーでは、ファイルの作成、フォルダーの作成、既存のファイルの使用、または既存のフォルダーの使用を実行できます。</span><span class="sxs-lookup"><span data-stu-id="06247-111">The File connection manager can create a file, create a folder, use an existing file, or use an existing folder.</span></span>  
  
 <span data-ttu-id="06247-112">次の表に、`FileUsageType` の値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="06247-112">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="06247-113">値</span><span class="sxs-lookup"><span data-stu-id="06247-113">Value</span></span>|<span data-ttu-id="06247-114">説明</span><span class="sxs-lookup"><span data-stu-id="06247-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="06247-115">ファイル接続マネージャーは、既存のファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="06247-115">File connection manager uses an existing file.</span></span>|  
|`1`|<span data-ttu-id="06247-116">ファイル接続マネージャーは、ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="06247-116">File connection manager creates a file.</span></span>|  
|`2`|<span data-ttu-id="06247-117">ファイル接続マネージャーは、既存のフォルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="06247-117">File connection manager uses an existing folder.</span></span>|  
|`3`|<span data-ttu-id="06247-118">ファイル接続マネージャーは、フォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="06247-118">File connection manager creates a folder.</span></span>|  
  
## <a name="multiple-file-or-folder-connections"></a><span data-ttu-id="06247-119">複数のファイルまたはフォルダーの接続</span><span class="sxs-lookup"><span data-stu-id="06247-119">Multiple File or Folder Connections</span></span>  
 <span data-ttu-id="06247-120">ファイル接続マネージャーが参照できるファイルまたはフォルダーは、1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="06247-120">The File connection manager can reference only one file or folder.</span></span> <span data-ttu-id="06247-121">複数のファイルまたはフォルダーを参照するには、ファイル接続マネージャーではなく、複数ファイル接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="06247-121">To reference multiple files or folders, use a Multiple Files connection manager instead of a File connection manager.</span></span> <span data-ttu-id="06247-122">詳細については、「 [複数ファイル接続マネージャー](multiple-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06247-122">For more information, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
## <a name="configuration-of-the-file-connection-manager"></a><span data-ttu-id="06247-123">ファイル接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="06247-123">Configuration of the File Connection Manager</span></span>  
 <span data-ttu-id="06247-124">ファイル接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時にファイル接続を解決する接続マネージャーを作成し、ファイル接続プロパティを設定して、ファイル接続をパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="06247-124">When you add a File connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a File connection at run time, sets the File connection properties, and adds the File connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="06247-125">接続マネージャーの `ConnectionManagerType` プロパティは、`FILE` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="06247-125">The `ConnectionManagerType` property of the connection manager is set to `FILE`.</span></span>  
  
 <span data-ttu-id="06247-126">ファイル接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="06247-126">You can configure a File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="06247-127">使用法の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="06247-127">Specify the usage type.</span></span>  
  
-   <span data-ttu-id="06247-128">ファイルまたはフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="06247-128">Specify a file or folder.</span></span>  
  
 <span data-ttu-id="06247-129">ファイル接続マネージャーの ConnectionString プロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [プロパティ] ウィンドウで式を指定することで設定できます。</span><span class="sxs-lookup"><span data-stu-id="06247-129">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="06247-130">ただし、式を使用してファイルまたはフォルダーを指定するときに検証エラーが発生しないようにするには、[ファイル**接続マネージャーエディター**] の [ファイル **/フォルダー**] で、ファイルまたはフォルダーのパスを追加します。</span><span class="sxs-lookup"><span data-stu-id="06247-130">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="06247-131">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="06247-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="06247-132">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[ファイル接続マネージャー エディター] ダイアログ ボックス](../file-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06247-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [File Connection Manager Editor](../file-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="06247-133">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="06247-133">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  

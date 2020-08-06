---
title: ストアドプロシージャのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715842"
---
# <a name="debugging-stored-procedures"></a><span data-ttu-id="f6ee6-102">デバッグ系のストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f6ee6-102">Debugging Stored Procedures</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="f6ee6-103">のストアド プロシージャは、実際には C# (あるいは他の CLR または COM 言語) で作成されている CLR または COM ライブラリ (通常は DLL) です。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-103">stored procedures are actually CLR or COM libraries (normally DLLs) that are written in C# (or any other CLR or COM language).</span></span> <span data-ttu-id="f6ee6-104">このため、ストアド プロシージャのデバッグは、Visual Studio デバッグ環境で他のアプリケーションをデバッグする作業とほとんど同じになります。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-104">Therefore, debugging a stored procedure is much like debugging any other application in the Visual Studio debugging environment.</span></span> <span data-ttu-id="f6ee6-105">Visual Studio 開発環境でのストアド プロシージャのデバッグは、統合されたデバッグ機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-105">You debug stored procedures in the Visual Studio development environment using the integrated debugging functions.</span></span> <span data-ttu-id="f6ee6-106">これらの機能を使用すると、プロシージャ内のさまざまな場所で停止し、メモリやレジスタの値を調査し、変数を変更し、メッセージ トラフィックを観察し、コードの動作を詳細にわたって確認することができます。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-106">These allow you to stop at procedure locations, inspect memory and register values, change variables, observe message traffic and get a close look at how your code works.</span></span>  
  
### <a name="to-debug-a-stored-procedure"></a><span data-ttu-id="f6ee6-107">ストアド プロシージャをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="f6ee6-107">To debug a stored procedure</span></span>  
  
1.  <span data-ttu-id="f6ee6-108">DLL の作成に使用したプロジェクトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-108">Open the project used to create the DLL in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f6ee6-109">デバッグするプロシージャに対応するメソッドまたは関数内にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-109">Create breakpoints in the method or function corresponding to the procedure you want to debug.</span></span>  
  
3.  <span data-ttu-id="f6ee6-110">Visual Studio を使用して、ストアド プロシージャ DLL のデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-110">Use Visual Studio to create a debug build of a stored procedure DLL.</span></span>  
  
4.  <span data-ttu-id="f6ee6-111">DLL をサーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-111">Deploy the DLL to the server.</span></span> <span data-ttu-id="f6ee6-112">DLL をサーバーに配置する方法の詳細については、「[ストアドプロシージャの作成](creating-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-112">For more information about deploying the DLL to the server, see [Creating Stored Procedures](creating-stored-procedures.md).</span></span>  
  
5.  <span data-ttu-id="f6ee6-113">テストするストアド プロシージャを呼び出すアプリケーションが必要です。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-113">You need an application that calls the stored procedure that you want to test.</span></span> <span data-ttu-id="f6ee6-114">このようなアプリケーションを用意していない場合は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の MDX クエリ エディターを使用して、テストするストアド プロシージャを呼び出す MDX クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-114">If you do not have one ready, you can use the MDX Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create an MDX query that calls the stored procedure that you want to test.</span></span>  
  
6.  <span data-ttu-id="f6ee6-115">Visual Studio で、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロセス (Msmdsrv.exe) にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-115">In Visual Studio, attach to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process (Msmdsrv.exe).</span></span>  
  
    1.  <span data-ttu-id="f6ee6-116">[**デバッグ**] メニューの [**アタッチ toProcess**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-116">From the **Debug** menu, choose **Attatch toProcess**.</span></span>  
  
    2.  <span data-ttu-id="f6ee6-117">[**アタッチ toProcess** ] ダイアログボックスで、[**すべてのユーザーのプロセスを表示する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-117">In the **Attatch toProcess** dialog box, select **Show processes from all users**.</span></span>  
  
    3.  <span data-ttu-id="f6ee6-118">[**選択可能なプロセス**] の一覧で、[**処理**] 列の [ **Msmdsrv.exe**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-118">In the **Available Processes** list, in the **Process** column, click **Msmdsrv.exe**.</span></span> <span data-ttu-id="f6ee6-119">サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスが複数実行されている場合は、使用するインスタンスの ID を使用してプロセスを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-119">If there is more than one instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running on the server, you need to identify the process by the ID of the instance you want to use.</span></span>  
  
    4.  <span data-ttu-id="f6ee6-120">[**アタッチ先**] テキストボックスに、適切なプログラムの種類が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-120">In the **Attach to** text box, make sure that the appropriate program type is selected.</span></span> <span data-ttu-id="f6ee6-121">CLR DLL の場合は、[**選択**] をクリックし、[**次のコードの種類をデバッグ**] をクリックして、[**マネージ**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-121">For a CLR DLL, click **Select**, then click **Debug these code types**, then click **Managed**, then click **OK**.</span></span> <span data-ttu-id="f6ee6-122">COM DLL の場合は、[**選択**] をクリックし、[**次のコードの種類をデバッグ**] をクリックし、[**ネイティブ**] をクリックして、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-122">For a COM DLL, click **Select**, then click **Debug these code types**, then click **Native**, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="f6ee6-123">**[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-123">Click **Attach**.</span></span>  
  
7.  <span data-ttu-id="f6ee6-124">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、ストアド プロシージャを呼び出すプログラムまたは MDX スクリプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-124">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], invoke the program or MDX script that calls the stored procedure.</span></span> <span data-ttu-id="f6ee6-125">デバッガーは、ブレークポイントを含む行に達すると停止します。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-125">The debugger breaks when it reaches a line containing a breakpoint.</span></span> <span data-ttu-id="f6ee6-126">ウォッチ ウィンドウで変数を評価し、ロケールを表示し、コードをステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-126">You can evaluate variables in the watch window, view locals, and step through the code.</span></span>  
  
 <span data-ttu-id="f6ee6-127">ライブラリを正しくデバッグできない場合は、対応するプログラム データベース (PDB) ファイルがサーバーの配置場所にコピーされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-127">If you have problems debugging a library, make sure that the corresponding program database (PDB) file was copied to the deployment location on the server.</span></span> <span data-ttu-id="f6ee6-128">このファイルが登録または配置中にコピーされなかった場合には、DLL と同じ場所に手動でコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-128">If this file was not copied during registration or deployment, you must copy it manually to the same location as the DLL.</span></span> <span data-ttu-id="f6ee6-129">ネイティブ コード (COM DLL) の場合、PDB ファイルは \debug サブディレクトリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-129">For native code (COM DLL), the PDB file resides in the \debug subdirectory.</span></span> <span data-ttu-id="f6ee6-130">マネージド コード (CLR DLL) の場合、このファイルは \WINDEBUG サブディレクトリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f6ee6-130">For managed code (CLR DLL), it resides in the \WINDEBUG subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ee6-131">参照</span><span class="sxs-lookup"><span data-stu-id="f6ee6-131">See Also</span></span>  
 <span data-ttu-id="f6ee6-132">[多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="f6ee6-132">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="f6ee6-133">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="f6ee6-133">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  

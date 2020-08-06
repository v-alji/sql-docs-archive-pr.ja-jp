---
title: ストアドプロシージャの作成 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9a997244a2d54cca8732196107dd21927b5f9e2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715846"
---
# <a name="creating-stored-procedures"></a><span data-ttu-id="6be48-102">ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="6be48-102">Creating Stored Procedures</span></span>
  <span data-ttu-id="6be48-103">ストアド プロシージャを使用するには、これを共通言語ランタイム (CLR) クラスまたはコンポーネント オブジェクト モデル (COM) クラスに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="6be48-103">All stored procedures must be associated with a common language runtime (CLR) or Component Object Model (COM) class in order to be used.</span></span> <span data-ttu-id="6be48-104">クラスは、サーバーにインストールする必要があります。通常は [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX®ダイナミックリンクライブラリ (DLL) の形式で、サーバーまたはデータベースにアセンブリとして登録し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6be48-104">The class must be installed on the server - usually in the form of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® dynamic link library (DLL) - and registered as an assembly on the server or in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="6be48-105">ストアド プロシージャはサーバーまたはデータベースに登録されています。</span><span class="sxs-lookup"><span data-stu-id="6be48-105">Stored procedures are registered on a server or on a database.</span></span> <span data-ttu-id="6be48-106">サーバーのストアド プロシージャは、どのクエリ コンテキストからでも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6be48-106">Server stored procedures can be called from any query context.</span></span> <span data-ttu-id="6be48-107">データベースのストアド プロシージャは、データベース コンテキストが、ストアド プロシージャが定義されているデータベースの場合にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6be48-107">Database stored procedures can only be accessed if the database context is the database under which the stored procedure is defined.</span></span> <span data-ttu-id="6be48-108">あるアセンブリの関数が別のアセンブリの関数を呼び出す場合は、両方のアセンブリを同じコンテキスト (サーバーまたはデータベース) に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6be48-108">If functions in one assembly call functions in a different assembly, you must register both assemblies in the same context (server or database).</span></span> <span data-ttu-id="6be48-109">サーバーまたはサーバー上に配置されたデータベースの場合、を使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] アセンブリを登録できます。</span><span class="sxs-lookup"><span data-stu-id="6be48-109">For a server or a deployed [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to register an assembly.</span></span> <span data-ttu-id="6be48-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] デザイナーを使用してプロジェクトにアセンブリを登録できます。</span><span class="sxs-lookup"><span data-stu-id="6be48-110">For an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Designer to register an assembly in the project.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6be48-111">COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6be48-111">COM assemblies might pose a security risk.</span></span> <span data-ttu-id="6be48-112">このリスクやその他の考慮事項により、[!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)] では、COM アセンブリが非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="6be48-112">Due to this risk and other considerations, COM assemblies were deprecated in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)].</span></span> <span data-ttu-id="6be48-113">COM アセンブリは、今後のリリースではサポートされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6be48-113">COM assemblies might not be supported in future releases.</span></span>  
  
## <a name="registering-a-server-assembly"></a><span data-ttu-id="6be48-114">サーバー アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="6be48-114">Registering a Server Assembly</span></span>  
 <span data-ttu-id="6be48-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、サーバー アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの Assemblies フォルダーに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-115">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], server assemblies are listed in the Assemblies folder under an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="6be48-116">サーバー アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6be48-116">Server assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-server-assembly"></a><span data-ttu-id="6be48-117">サーバー アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="6be48-117">To create a server assembly</span></span>  
  
1.  <span data-ttu-id="6be48-118">オブジェクトエクスプローラーでのインスタンスを展開し、[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **アセンブリ**] フォルダーを右クリックして、[**新しいアセンブリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6be48-118">Expand the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="6be48-119">[**サーバーアセンブリの登録**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-119">This displays the **Register Server Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="6be48-120">[**種類**: アセンブリの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-120">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="6be48-121">マネージド コード (CLR) DLL の場合は、.NET アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-121">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="6be48-122">ネイティブコード (COM) DLL の場合は、COM DLL を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-122">For a native code (COM) DLL, specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="6be48-123">[**ファイル名**] に、ストアドプロシージャを含む DLL を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-123">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="6be48-124">[**アセンブリ名**] には、アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-124">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="6be48-125">これが、ストアドプロシージャのデバッグに使用するライブラリのデバッグビルドの場合は、[**デバッグ情報を含める**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6be48-125">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="6be48-126">ストアドプロシージャのデバッグの詳細については、「[ストアドプロシージャのデバッグ](debugging-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6be48-126">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="6be48-127">[ **OK** ] をクリックしてアセンブリをすぐに登録するか、ダイアログボックスのツールバーで [**スクリプト**] メニューのコマンドをクリックして、登録アクションをクエリウィンドウ、ファイル、またはクリップボードにスクリプト化することができます。</span><span class="sxs-lookup"><span data-stu-id="6be48-127">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="6be48-128">サーバーアセンブリを登録したら、オブジェクトエクスプローラーでアセンブリを右クリックし、[**プロパティ**] をクリックして構成できます。</span><span class="sxs-lookup"><span data-stu-id="6be48-128">After you register a server assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-on-the-server"></a><span data-ttu-id="6be48-129">サーバーへのデータベース アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="6be48-129">Registering a Database Assembly on the Server</span></span>  
 <span data-ttu-id="6be48-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、データベース アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの Assemblies フォルダーに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-130">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="6be48-131">データベース アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6be48-131">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-on-a-server"></a><span data-ttu-id="6be48-132">サーバーでデータベース アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="6be48-132">To create a database assembly on a server</span></span>  
  
1.  <span data-ttu-id="6be48-133">オブジェクトエクスプローラーでデータベースのインスタンスを展開し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、[**アセンブリ**] フォルダーを右クリックして、[**新しいアセンブリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6be48-133">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="6be48-134">[**データベースアセンブリの登録**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-134">This displays the **Register Database Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="6be48-135">[**種類**: アセンブリの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-135">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="6be48-136">マネージド コード (CLR) DLL の場合は、.NET アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-136">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="6be48-137">ネイティブ コード (COM) DLL の場合は、COM DLL を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-137">For a native code (COM) DLL), specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="6be48-138">[**ファイル名**] に、ストアドプロシージャを含む DLL を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-138">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="6be48-139">[**アセンブリ名**] には、アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6be48-139">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="6be48-140">これが、ストアドプロシージャのデバッグに使用するライブラリのデバッグビルドの場合は、[**デバッグ情報を含める**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6be48-140">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="6be48-141">ストアドプロシージャのデバッグの詳細については、「[ストアドプロシージャのデバッグ](debugging-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6be48-141">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="6be48-142">[ **OK** ] をクリックしてアセンブリをすぐに登録するか、ダイアログボックスのツールバーで [**スクリプト**] メニューのコマンドをクリックして、登録アクションをクエリウィンドウ、ファイル、またはクリップボードにスクリプト化することができます。</span><span class="sxs-lookup"><span data-stu-id="6be48-142">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="6be48-143">データベースアセンブリを登録したら、オブジェクトエクスプローラーでアセンブリを右クリックし、[**プロパティ**] をクリックして構成できます。</span><span class="sxs-lookup"><span data-stu-id="6be48-143">After you register a database assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-in-a-project"></a><span data-ttu-id="6be48-144">プロジェクトへのデータベース アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="6be48-144">Registering a Database Assembly in a Project</span></span>  
 <span data-ttu-id="6be48-145">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーで、データベース アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの Assemblies フォルダーに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-145">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="6be48-146">データベース アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6be48-146">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a><span data-ttu-id="6be48-147">Analysis Services プロジェクトにデータベース アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="6be48-147">To create a database assembly in an Analysis Service project</span></span>  
  
1.  <span data-ttu-id="6be48-148">オブジェクトエクスプローラーデータベースのインスタンスを展開し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、[**アセンブリ**] フォルダーを右クリックして、[**新しいアセンブリ参照**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6be48-148">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly Reference**.</span></span> <span data-ttu-id="6be48-149">[参照の**追加**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-149">This displays the **Add Reference** dialog box.</span></span> <span data-ttu-id="6be48-150">[**参照の追加**] ダイアログボックスの [ **.net** ] タブには、既存の .net (CLR) アセンブリの一覧が表示されます。 [**プロジェクト**] タブには、プロジェクトが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-150">The **.NET** tab of the **Add Reference** dialog box lists existing .NET (CLR) assemblies, while the **Projects** tab lists projects.</span></span>  
  
2.  <span data-ttu-id="6be48-151">既存のコンポーネントまたはプロジェクトをクリックし、[**追加**] をクリックしてプロジェクトに追加することができ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6be48-151">You can click an existing component or project and then click **Add** to add it to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="6be48-152">COM DLL への参照を追加するには、[**参照**] タブをクリックしてファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="6be48-152">To add a reference to a COM DLL, click the **Browse** tab to find the file.</span></span> <span data-ttu-id="6be48-153">[**選択されたプロジェクトとコンポーネント**] の一覧には、プロジェクトに追加する各コンポーネントの名前、種類、バージョン、および場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-153">The **Selected projects and components** list shows the name, type, version, and location for each component that you are adding to the project.</span></span>  
  
3.  <span data-ttu-id="6be48-154">追加するコンポーネントの選択が完了したら、[ **OK** ] をクリックしてプロジェクトに追加し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6be48-154">When you are finished selecting components to add, click **OK** to add them to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
## <a name="script-format-for-an-assembly"></a><span data-ttu-id="6be48-155">アセンブリのスクリプト形式</span><span class="sxs-lookup"><span data-stu-id="6be48-155">Script Format For an Assembly</span></span>  
 <span data-ttu-id="6be48-156">.NET アセンブリの登録は簡単です。</span><span class="sxs-lookup"><span data-stu-id="6be48-156">Registering a .NET assembly is fairly simple.</span></span> <span data-ttu-id="6be48-157">.NET アセンブリは次の形式を使用してバイナリ形式でデータベースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6be48-157">A .NET assembly is added to a database in binary format using the following format:</span></span>  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6be48-158">参照</span><span class="sxs-lookup"><span data-stu-id="6be48-158">See Also</span></span>  
 <span data-ttu-id="6be48-159">[多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="6be48-159">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="6be48-160">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="6be48-160">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  

---
title: Analysis Services データベースを ReadOnly モードと ReadWrite モードの間で切り替えます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
ms.openlocfilehash: 757aedd985d969f932deacf5599716078021a1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711070"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a><span data-ttu-id="db215-102">Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え</span><span class="sxs-lookup"><span data-stu-id="db215-102">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>
  <span data-ttu-id="db215-103">多くの場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース管理者 (dba) がテーブルまたは多次元データベースの読み取り/書き込みモードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db215-103">There are often situations when a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to change the read/write mode of a tabular or multidimensional database.</span></span> <span data-ttu-id="db215-104">こうした状況は、ユーザーが操作しやすくなるように一連の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー間でデータベースを共有するなどのビジネス上のニーズによって頻繁に発生します。</span><span class="sxs-lookup"><span data-stu-id="db215-104">These situations are often driven by business needs, such as sharing the database among a pool of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers for a better user experience.</span></span>  
  
 <span data-ttu-id="db215-105">データベースモードは、さまざまな方法で切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="db215-105">A database mode can be switched in many ways.</span></span> <span data-ttu-id="db215-106">このドキュメントでは、次の一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="db215-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="db215-107">の対話的な使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db215-107">Interactively using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="db215-108">AMO を使用したプログラム</span><span class="sxs-lookup"><span data-stu-id="db215-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="db215-109">XMLA を使用したスクリプト</span><span class="sxs-lookup"><span data-stu-id="db215-109">By script using XMLA</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="db215-110">手順</span><span class="sxs-lookup"><span data-stu-id="db215-110">Procedures</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a><span data-ttu-id="db215-111">Management Studio を使用してデータベースの読み取り/書き込みモードを対話的に切り替えるには</span><span class="sxs-lookup"><span data-stu-id="db215-111">To switch the read/write mode of a database interactively using Management Studio</span></span>  
  
1.  <span data-ttu-id="db215-112">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の左側または右側のペインで切り替えるデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="db215-112">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="db215-113">データベースを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="db215-113">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="db215-114">データベース フォルダーを検索し、場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="db215-114">Find the database folder and note the location.</span></span> <span data-ttu-id="db215-115">データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。</span><span class="sxs-lookup"><span data-stu-id="db215-115">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="db215-116">データベースがデタッチされるとすぐに、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データベースの位置を取得できなくなります。</span><span class="sxs-lookup"><span data-stu-id="db215-116">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="db215-117">データベースを右クリックし、[**デタッチ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="db215-117">Right-click the database and select **Detach...**</span></span>  
  
4.  <span data-ttu-id="db215-118">デタッチするデータベースにパスワードを割り当て、 **[OK]** をクリックしてデタッチ コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="db215-118">Assign a password to the database to be detached, and then click **OK** to execute the detach command.</span></span>  
  
5.  <span data-ttu-id="db215-119">の左側または右側のペインで、[**データベース**] フォルダーを探し [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="db215-119">Locate the **Databases** folder in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
6.  <span data-ttu-id="db215-120">[**データベース**] フォルダーを右クリックし、[**アタッチ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="db215-120">Right-click the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="db215-121">**[フォルダー]** ボックスに、データベース フォルダーの元の場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="db215-121">In the **folder** text box, type the original location of the database folder.</span></span> <span data-ttu-id="db215-122">または、参照ボタン ([.**..**]) を使用してデータベースフォルダーを検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="db215-122">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="db215-123">データベースの読み取り/書き込みモードを選択します。</span><span class="sxs-lookup"><span data-stu-id="db215-123">Select the read/write mode for the database.</span></span>  
  
9. <span data-ttu-id="db215-124">手順 3. で使用したパスワードを入力し、[ **OK** ] をクリックして attach コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="db215-124">Type the password that was used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a><span data-ttu-id="db215-125">プログラムで AMO を使用してデータベースの読み取り/書き込みモードを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="db215-125">To switch the read/write mode to a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="db215-126">C# アプリケーションで、次のサンプル コードを調整して、指定されたタスクを完了します。</span><span class="sxs-lookup"><span data-stu-id="db215-126">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="db215-127">C# アプリケーションで、必要なパラメーターを指定して `SwitchReadWrite()` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db215-127">In your C# application, invoke `SwitchReadWrite()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="db215-128">コードをコンパイルして実行し、データベースを移動します。</span><span class="sxs-lookup"><span data-stu-id="db215-128">Compile and execute your code to move the database.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a><span data-ttu-id="db215-129">XMLA を使用したスクリプトでデータベースの読み取り/書き込みモードを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="db215-129">To switch the read/write mode to a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="db215-130">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の左側または右側のペインで切り替えるデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="db215-130">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="db215-131">データベースを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="db215-131">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="db215-132">データベース フォルダーを検索し、場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="db215-132">Find the database folder and note the location.</span></span> <span data-ttu-id="db215-133">データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。</span><span class="sxs-lookup"><span data-stu-id="db215-133">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="db215-134">データベースがデタッチされるとすぐに、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データベースの位置を取得できなくなります。</span><span class="sxs-lookup"><span data-stu-id="db215-134">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="db215-135">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、新しい XMLA タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="db215-135">Open a new XMLA tab in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="db215-136">次の XMLA 用のスクリプト テンプレートをコピーします。</span><span class="sxs-lookup"><span data-stu-id="db215-136">Copy the following script template for XMLA:</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="db215-137">`%dbName%` をデータベースの名前に置き換え、 `%password%` をパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="db215-137">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="db215-138">テンプレートに含まれている文字 % は削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db215-138">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="db215-139">XMLA コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="db215-139">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="db215-140">新しい XMLA タブに、次の XMLA 用のスクリプト テンプレートをコピーします。</span><span class="sxs-lookup"><span data-stu-id="db215-140">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 <span data-ttu-id="db215-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span><span class="sxs-lookup"><span data-stu-id="db215-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span></span>  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="db215-142">`%dbFolder%` をデータベース フォルダーの完全な UNC パスに置き換え、`%ReadOnlyMode%` を対応する値 `ReadOnly` または `ReadWrite` に置き換え、`%password%` をパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="db215-142">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="db215-143">テンプレートに含まれている文字 % は削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db215-143">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="db215-144">XMLA コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="db215-144">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db215-145">参照</span><span class="sxs-lookup"><span data-stu-id="db215-145">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="db215-146">[Microsoft.analysisservices.sharepoint.integration.dll \* のようになります。](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="db215-146">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="db215-147">[Analysis Services データベースのアタッチとデタッチ](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="db215-147">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="db215-148">[データベースのストレージの場所](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="db215-148">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="db215-149">[データベース ReadWriteModes](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="db215-149">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="db215-150">[Attach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="db215-150">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="db215-151">[Detach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="db215-151">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="db215-152">[ReadWriteMode 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="db215-152">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="db215-153">DbStorageLocation 要素</span><span class="sxs-lookup"><span data-stu-id="db215-153">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  

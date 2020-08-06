---
title: Analysis Services Database | を移動するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- moving databases [Anlysis Services]
- moving databases
- operations [Analysis Services - multidimensional data]
ms.assetid: fa644e5d-e276-445e-98d9-673afcfb83fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd9b099ad6765d9caccb9b0af6622eb4aa77d38c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740549"
---
# <a name="move-an-analysis-services-database"></a><span data-ttu-id="f48ca-102">Analysis Services データベースの移動</span><span class="sxs-lookup"><span data-stu-id="f48ca-102">Move an Analysis Services Database</span></span>
  <span data-ttu-id="f48ca-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者 (DBA) が多次元式またはテーブル モデル データベースを別の場所に移動することは少なくありません。</span><span class="sxs-lookup"><span data-stu-id="f48ca-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to move a multidimensional or tabular model database to a different location.</span></span> <span data-ttu-id="f48ca-104">こうした状況は、パフォーマンス向上のためにデータベースを別のディスクに移動したり、データベース拡張のための領域を確保したり、製品をアップグレードしたりするなど、ビジネス上のニーズによって頻繁に発生します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span>  
  
 <span data-ttu-id="f48ca-105">データベースの移動方法は多数あります。</span><span class="sxs-lookup"><span data-stu-id="f48ca-105">A database can be moved in many ways.</span></span> <span data-ttu-id="f48ca-106">このドキュメントでは、次の一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="f48ca-107">SSMS の対話的使用</span><span class="sxs-lookup"><span data-stu-id="f48ca-107">Interactively using SSMS</span></span>  
  
-   <span data-ttu-id="f48ca-108">AMO を使用したプログラム</span><span class="sxs-lookup"><span data-stu-id="f48ca-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="f48ca-109">XMLA を使用したスクリプト</span><span class="sxs-lookup"><span data-stu-id="f48ca-109">By script using XMLA</span></span>  
  
 <span data-ttu-id="f48ca-110">どのシナリオにおいても、ユーザーはデータベース フォルダーにアクセスし、ファイルを目的の場所に移動する方法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f48ca-110">All scenarios require the user to access the database folder and to use a method for moving the files to the desired final destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f48ca-111">パスワードを割り当てずにデータベースをデタッチすると、そのデータベースはセキュリティで保護されていない状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="f48ca-111">Detaching a database without assigning a password to it leaves the database in an unsecured state.</span></span> <span data-ttu-id="f48ca-112">データベースにパスワードを割り当てて、機密情報を保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f48ca-112">We recommend assigning a password to the database to protect confidential information.</span></span> <span data-ttu-id="f48ca-113">また、対応するアクセス セキュリティをデータベース フォルダー、サブフォルダー、ファイルに適用して、不正アクセスを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="f48ca-113">Also, the corresponding access security should be applied to the database folder, sub-folders, and files to prevent unauthorized access to them.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f48ca-114">手順</span><span class="sxs-lookup"><span data-stu-id="f48ca-114">Procedures</span></span>  
  
#### <a name="moving-a-database-interactively-using-ssms"></a><span data-ttu-id="f48ca-115">SSMS を使用したデータベースの対話的移動</span><span class="sxs-lookup"><span data-stu-id="f48ca-115">Moving a database interactively using SSMS</span></span>  
  
1.  <span data-ttu-id="f48ca-116">SSMS の左側または右側のペインで、移動するデータベースを探します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-116">Locate the database to be moved in the left or right pane of SSMS.</span></span>  
  
2.  <span data-ttu-id="f48ca-117">データベースを右クリックし、[**デタッチ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-117">Right-click on the database and select **Detach...**</span></span>  
  
3.  <span data-ttu-id="f48ca-118">デタッチするデータベースにパスワードを割り当て、 **[OK]** をクリックしてデタッチ コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-118">Assign a password to the database to be detached, then click **OK** to execute the detach command.</span></span>  
  
4.  <span data-ttu-id="f48ca-119">ファイルを移動するための、オペレーティング システムのメカニズムまたは標準的な方法を使用して、データベース フォルダーを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-119">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
5.  <span data-ttu-id="f48ca-120">SSMS の左側または右側のペインで、 **[データベース]** フォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-120">Locate the **Databases** folder in the left or right pane of SSMS.</span></span>  
  
6.  <span data-ttu-id="f48ca-121">[**データベース**] フォルダーを右クリックし、[**アタッチ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-121">Right-click on the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="f48ca-122">**[フォルダー]** テキスト ボックスに、データベース フォルダーの移動先を入力します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-122">In the **folder** text box, type the new location of the database folder.</span></span> <span data-ttu-id="f48ca-123">または、参照ボタン ([.**..**]) を使用してデータベースフォルダーを検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="f48ca-123">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="f48ca-124">`ReadWrite`データベースのモードを選択します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-124">Select the `ReadWrite` mode for the database.</span></span>  
  
9. <span data-ttu-id="f48ca-125">手順 3. で使用したパスワードを入力し、 **[OK]** をクリックしてアタッチ コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-125">Type the password used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="moving-a-database-programmatically-using-amo"></a><span data-ttu-id="f48ca-126">AMO を使用したプログラムによるデータベースの移動</span><span class="sxs-lookup"><span data-stu-id="f48ca-126">Moving a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="f48ca-127">C# アプリケーションで、次のサンプル コードを調整して、指定されたタスクを完了します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-127">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void MoveDb(Server server, string dbName,`  
  
 `string dbInitialLocation, string dbFinalLocation,`  
  
 `string dbPassword, ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `//Verify dbInitialLocation exists before continuing`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `//Save current cursor and change cursor to Cursors.WaitCursor`  
  
 `db = server.Databases[dbName];`  
  
 `db.Detach(dbPassword);`  
  
 `//Add your own code to copy the database files to the destination where you intend to attach the database`  
  
 `//Verify dbFinalLocation exists before continuing`  
  
 `server.Attach(dbFinalLocation, dbReadWriteMode, dbPassword);`  
  
 `//Restore cursor to its original`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="f48ca-128">C# アプリケーションで、必要なパラメーターを指定して `MoveDb()` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-128">In your C# application, invoke `MoveDb()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="f48ca-129">コードをコンパイルして実行し、データベースを移動します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-129">Compile and execute your code to move the database.</span></span>  
  
#### <a name="moving-a-database-by-script-using-xmla"></a><span data-ttu-id="f48ca-130">XMLA を使用したスクリプトによるデータベースの移動</span><span class="sxs-lookup"><span data-stu-id="f48ca-130">Moving a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="f48ca-131">SSMS で新しい XMLA タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="f48ca-131">Open a new XMLA tab in SSMS.</span></span>  
  
2.  <span data-ttu-id="f48ca-132">次の XMLA 用のスクリプト テンプレートをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f48ca-132">Copy the following script template for XMLA</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="f48ca-133">`%dbName%` をデータベースの名前に置き換え、 `%password%` をパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f48ca-133">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="f48ca-134">テンプレートに含まれている文字 % は削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f48ca-134">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="f48ca-135">XMLA コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-135">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="f48ca-136">ファイルを移動するための、オペレーティング システムのメカニズムまたは標準的な方法を使用して、データベース フォルダーを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-136">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
4.  <span data-ttu-id="f48ca-137">新しい XMLA タブに、次の XMLA 用のスクリプト テンプレートをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f48ca-137">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="f48ca-138">`%dbFolder%` をデータベース フォルダーの完全な UNC パスに置き換え、`%ReadOnlyMode%` を対応する値 `ReadOnly` または `ReadWrite` に置き換え、`%password%` をパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f48ca-138">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="f48ca-139">テンプレートに含まれている文字 % は削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f48ca-139">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="f48ca-140">XMLA コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f48ca-140">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48ca-141">参照</span><span class="sxs-lookup"><span data-stu-id="f48ca-141">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="f48ca-142">[Microsoft.analysisservices.sharepoint.integration.dll \* のようになります。](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="f48ca-142">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="f48ca-143">[Analysis Services データベースのアタッチとデタッチ](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f48ca-143">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="f48ca-144">[データベースのストレージの場所](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="f48ca-144">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="f48ca-145">[データベース ReadWriteModes](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="f48ca-145">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="f48ca-146">[Attach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="f48ca-146">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="f48ca-147">[Detach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="f48ca-147">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="f48ca-148">[ReadWriteMode 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="f48ca-148">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="f48ca-149">DbStorageLocation 要素</span><span class="sxs-lookup"><span data-stu-id="f48ca-149">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  

---
title: SQL Server 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdest.f1
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcd65007e1e6af36386cb2ceba1f7242305b81a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713353"
---
# <a name="sql-server-destination"></a><span data-ttu-id="a4d03-102">SQL Server 変換先</span><span class="sxs-lookup"><span data-stu-id="a4d03-102">SQL Server Destination</span></span>
  <span data-ttu-id="a4d03-103">SQL Server 変換先はローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはビューに一括で読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-103">The SQL Server destination connects to a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and bulk loads data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and views.</span></span> <span data-ttu-id="a4d03-104">SQL Server 変換先は、リモート サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにアクセスするパッケージでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a4d03-104">You cannot use the SQL Server destination in packages that access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a remote server.</span></span> <span data-ttu-id="a4d03-105">代わりに、このパッケージでは OLE DB 変換先を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4d03-105">Instead, the packages should use the OLE DB destination.</span></span> <span data-ttu-id="a4d03-106">詳細については、「 [OLE DB 変換先](ole-db-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-106">For more information, see [OLE DB Destination](ole-db-destination.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="a4d03-107">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="a4d03-107">Permissions</span></span>  
 <span data-ttu-id="a4d03-108">SQL Server 変換先が含まれたパッケージを実行するユーザーには、"グローバル オブジェクトの作成" 権限が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4d03-108">Users who execute packages that include the SQL Server destination require the "Create global objects" permission.</span></span> <span data-ttu-id="a4d03-109">**[管理ツール]** のローカル セキュリティ ポリシー ツールを使用することにより、この権限をユーザーに許可できます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-109">You can grant this permission to users by using the Local Security Policy tool opened from the **Administrative Tools** menu.</span></span> <span data-ttu-id="a4d03-110">SQL Server 変換先を使用するパッケージの実行時にエラー メッセージが表示された場合は、パッケージを実行しているアカウントに "グローバル オブジェクトの作成" 権限が許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-110">If you receive an error message when executing a package that uses the SQL Server destination, make sure that the account running the package has the "Create global objects" permission.</span></span>  
  
## <a name="bulk-inserts"></a><span data-ttu-id="a4d03-111">一括挿入</span><span class="sxs-lookup"><span data-stu-id="a4d03-111">Bulk Inserts</span></span>  
 <span data-ttu-id="a4d03-112">SQL Server 変換先を使用してリモートの SQL Server データベースにデータを一括読み込みしようとすると、次のようなエラー メッセージが表示されることがあります。"OLE DB レコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-112">If you attempt to use the SQL Server destination to bulk load data into a remote SQL Server database, you may see an error message similar to the following: "An OLE DB record is available.</span></span> <span data-ttu-id="a4d03-113">ソース : "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 説明 : "SSIS ファイル マッピング オブジェクト 'Global\DTSQLIMPORT' を開けなかったので、一括読み込みできませんでした。</span><span class="sxs-lookup"><span data-stu-id="a4d03-113">Source: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 Description: "Could not bulk load because SSIS file mapping object 'Global\DTSQLIMPORT ' could not be opened.</span></span> <span data-ttu-id="a4d03-114">オペレーティング システム エラー コード 2 (指定されたファイルが見つかりません)。</span><span class="sxs-lookup"><span data-stu-id="a4d03-114">Operating system error code 2 (The system cannot find the file specified.).</span></span> <span data-ttu-id="a4d03-115">Windows セキュリティ経由でローカル サーバーにアクセスしていることを確認してください。""</span><span class="sxs-lookup"><span data-stu-id="a4d03-115">Make sure you are accessing a local server via Windows security.""</span></span>  
  
 <span data-ttu-id="a4d03-116">SQL Server 変換先で行われるのは、一括挿入タスクで行われるものと同じ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への高速なデータ挿入です。ただし、パッケージで SQL Server 変換先を使用することによって、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込まれる前に変換を列データに適用できます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-116">The SQL Server destination offers the same high-speed insertion of data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that the Bulk Insert task provides; however, by using the SQL Server destination, a package can apply transformations to column data before the data is loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a4d03-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にデータを読み込む場合は、OLE DB 変換先ではなく SQL Server 変換先を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4d03-117">For loading data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should consider using the SQL Server destination instead of the OLE DB destination.</span></span>  
  
### <a name="bulk-insert-options"></a><span data-ttu-id="a4d03-118">一括挿入オプション</span><span class="sxs-lookup"><span data-stu-id="a4d03-118">Bulk Insert Options</span></span>  
 <span data-ttu-id="a4d03-119">SQL Server 変換先で高速読み込みデータ アクセス モードを使用する場合、次の高速読み込みオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-119">If the SQL Server destination uses a fast-load data access mode, you can specify the following fast load options:</span></span>  
  
-   <span data-ttu-id="a4d03-120">インポートしたデータ ファイルの ID 値を保持します。または、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって割り当てられた一意の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-120">Retain identity values from the imported data file, or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a4d03-121">一括読み込み操作中に、NULL 値を保持します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-121">Retain null values during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="a4d03-122">一括インポート操作中に、インポート先のテーブルまたはビュー上の制約を確認します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-122">Verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="a4d03-123">一括読み込み操作中に、テーブルレベルのロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-123">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="a4d03-124">一括読み込み操作中に、変換先のテーブル上で定義されている挿入トリガーを実行します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-124">Execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="a4d03-125">一括挿入操作中に読み込む、入力の最初の行番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-125">Specify the number of the first row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="a4d03-126">一括挿入操作中に読み込む、入力の最後の行番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-126">Specify the number of the last row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="a4d03-127">一括読み込み操作が取り消されるまでに許可されるエラーの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-127">Specify the maximum number of errors allowed before the bulk load operation is canceled.</span></span> <span data-ttu-id="a4d03-128">インポートできない各行は、エラーとしてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-128">Each row that cannot be imported is counted as one error.</span></span>  
  
-   <span data-ttu-id="a4d03-129">並べ替えられたデータが含まれる入力内の列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-129">Specify the columns in the input that contain sorted data.</span></span>  
  
 <span data-ttu-id="a4d03-130">一括読み込みオプションの詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-130">For more information about bulk load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
#### <a name="performance-improvements"></a><span data-ttu-id="a4d03-131">パフォーマンスの強化</span><span class="sxs-lookup"><span data-stu-id="a4d03-131">Performance Improvements</span></span>  
 <span data-ttu-id="a4d03-132">一括挿入、および一括挿入操作中のテーブル データへのアクセスのパフォーマンスを向上するには、既定のオプションを次のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4d03-132">To improve the performance of a bulk insert and the access to table data during the bulk insert operation, you should change the default options as follows:</span></span>  
  
-   <span data-ttu-id="a4d03-133">一括インポート操作中に、インポート先のテーブルまたはビュー上の制約を確認しません。</span><span class="sxs-lookup"><span data-stu-id="a4d03-133">Do not verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="a4d03-134">一括読み込み操作中に、変換先のテーブル上で定義されている挿入トリガーを実行しません。</span><span class="sxs-lookup"><span data-stu-id="a4d03-134">Do not execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="a4d03-135">ロックをテーブルに適用しません。</span><span class="sxs-lookup"><span data-stu-id="a4d03-135">Do not apply a lock to the table.</span></span> <span data-ttu-id="a4d03-136">これにより、一括挿入操作中、他のユーザーおよびアプリケーションはテーブルを引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-136">That way, the table remains available to other users and applications during the bulk insert operation.</span></span>  
  
## <a name="configuration-of-the-sql-server-destination"></a><span data-ttu-id="a4d03-137">SQL Server 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="a4d03-137">Configuration of the SQL Server Destination</span></span>  
 <span data-ttu-id="a4d03-138">SQL Server 変換先は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-138">You can configure the SQL Server destination in the following ways:</span></span>  
  
-   <span data-ttu-id="a4d03-139">データの一括読み込み先となるテーブルまたはビューを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-139">Specify the table or view into which to bulk load the data.</span></span>  
  
-   <span data-ttu-id="a4d03-140">CHECK 制約を実行するかどうかなどのオプションを指定することにより、一括読み込み操作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="a4d03-140">Customize the bulk load operation by specifying options such as whether to check constraints.</span></span>  
  
-   <span data-ttu-id="a4d03-141">同じバッチ内ですべての行をコミットするか、バッチとしてコミットする行の最大数を設定するかのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-141">Specify whether all rows commit in one batch or set the maximum number of rows to commit as a batch.</span></span>  
  
-   <span data-ttu-id="a4d03-142">一括読み込み操作のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-142">Specify a time-out for the bulk load operation.</span></span>  
  
 <span data-ttu-id="a4d03-143">この変換先は、OLE DB 接続マネージャーを使用してデータ ソースに接続します。OLE DB 接続マネージャーでは、使用する OLE DB プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-143">This destination uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="a4d03-144">詳細については、「 [OLE DB 接続マネージャー](../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-144">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="a4d03-145">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトでは、OLE DB 接続マネージャーを作成できるデータ ソース オブジェクトも用意されます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-145">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager.</span></span> <span data-ttu-id="a4d03-146">これにより、SQL Server 変換先でデータ ソースとデータ ソース ビューが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a4d03-146">This makes data sources and data source views available to the SQL Server destination.</span></span>  
  
 <span data-ttu-id="a4d03-147">SQL Server 変換先は 1 つの入力をとります。</span><span class="sxs-lookup"><span data-stu-id="a4d03-147">The SQL Server destination has one input.</span></span> <span data-ttu-id="a4d03-148">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a4d03-148">It does not support an error output.</span></span>  
  
 <span data-ttu-id="a4d03-149">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="a4d03-149">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a4d03-150">**[SQL 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-150">For more information about the properties that you can set in the **SQL Server Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="a4d03-151">[[SQL 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../sql-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="a4d03-151">[SQL Destination Editor &#40;Connection Manager Page&#41;](../sql-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="a4d03-152">[[SQL 変換先エディター] &#40;[マッピング] ページ&#41;](../sql-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="a4d03-152">[SQL Destination Editor &#40;Mappings Page&#41;](../sql-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="a4d03-153">[[SQL 変換先エディター] &#40;[詳細設定] ページ&#41;](../sql-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="a4d03-153">[SQL Destination Editor &#40;Advanced Page&#41;](../sql-destination-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="a4d03-154">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="a4d03-154">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="a4d03-155">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-155">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a4d03-156">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a4d03-156">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="a4d03-157">SQL Server 変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="a4d03-157">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
 <span data-ttu-id="a4d03-158">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d03-158">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a4d03-159">SQL Server 変換先を使用してデータの一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="a4d03-159">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="a4d03-160">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="a4d03-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="a4d03-161">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a4d03-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a4d03-162">SQL Server 変換先を使用してデータの一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="a4d03-162">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="a4d03-163">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="a4d03-163">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="a4d03-164">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="a4d03-164">Related Content</span></span>  
  
-   <span data-ttu-id="a4d03-165">support.microsoft.com の技術記事: [UAC 対応システムで "データを挿入するための SSIS 一括挿入を準備できません" というエラーが発生することがある](https://go.microsoft.com/fwlink/?LinkId=199482)</span><span class="sxs-lookup"><span data-stu-id="a4d03-165">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=199482), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="a4d03-166">msdn.microsoft.com の技術記事: [Integration Services のパフォーマンス チューニング技法](https://go.microsoft.com/fwlink/?LinkId=233700)</span><span class="sxs-lookup"><span data-stu-id="a4d03-166">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="a4d03-167">simple-talk.com の技術記事: [SQL Server Integration Services を使用してデータの一括読み込みを行う](https://go.microsoft.com/fwlink/?LinkId=233701)</span><span class="sxs-lookup"><span data-stu-id="a4d03-167">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d03-168">参照</span><span class="sxs-lookup"><span data-stu-id="a4d03-168">See Also</span></span>  
 [<span data-ttu-id="a4d03-169">データ フロー</span><span class="sxs-lookup"><span data-stu-id="a4d03-169">Data Flow</span></span>](data-flow.md)  
  
  

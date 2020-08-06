---
title: '[SQL 変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f3a552968cb297de337e1f0c406b444d95dc5a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639557"
---
# <a name="sql-destination-editor-connection-manager-page"></a><span data-ttu-id="718e1-102">[SQL 変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="718e1-102">SQL Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="718e1-103">**[SQL 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、データ ソース情報を指定したり、結果をプレビューしたりできます。</span><span class="sxs-lookup"><span data-stu-id="718e1-103">Use the **Connection Manager** page of the **SQL Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="718e1-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]変換先は、データベース内のテーブルまたはビューにデータを読み込み [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="718e1-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destination loads data into tables or views in a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="718e1-105">SQL Server 変換先の詳細については、「 [SQL Server Destination](data-flow/sql-server-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="718e1-105">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="718e1-106">オプション</span><span class="sxs-lookup"><span data-stu-id="718e1-106">Options</span></span>  
 <span data-ttu-id="718e1-107">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="718e1-107">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="718e1-108">一覧から既存の接続を選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="718e1-108">Select an existing connection from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="718e1-109">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="718e1-109">**New**</span></span>  
 <span data-ttu-id="718e1-110">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="718e1-110">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="718e1-111">**[テーブルまたはビューを使用する]**</span><span class="sxs-lookup"><span data-stu-id="718e1-111">**Use a table or view**</span></span>  
 <span data-ttu-id="718e1-112">既存のテーブルまたはビューを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="718e1-112">Select an existing table or view from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="718e1-113">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="718e1-113">**New**</span></span>  
 <span data-ttu-id="718e1-114">**[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="718e1-114">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="718e1-115">**[新規作成]** をクリックすると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="718e1-115">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="718e1-116">基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。</span><span class="sxs-lookup"><span data-stu-id="718e1-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="718e1-117">FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。</span><span class="sxs-lookup"><span data-stu-id="718e1-117">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="718e1-118">次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="718e1-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="718e1-119">詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="718e1-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="718e1-120">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="718e1-120">**Preview**</span></span>  
 <span data-ttu-id="718e1-121">**[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="718e1-121">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="718e1-122">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="718e1-122">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="718e1-123">参照</span><span class="sxs-lookup"><span data-stu-id="718e1-123">See Also</span></span>  
 <span data-ttu-id="718e1-124">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="718e1-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="718e1-125">[SQL 変換先エディター &#40;マッピングページ&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="718e1-125">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="718e1-126">[SQL 変換先エディター &#40;詳細設定ページ&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="718e1-126">[SQL Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="718e1-127">SQL Server 変換先を使用してデータの一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="718e1-127">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  

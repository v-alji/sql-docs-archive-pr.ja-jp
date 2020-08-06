---
title: リレーショナルデータソースからのインポート (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93bb9ba9ba8d40262e4e90e840dcd15ac6826df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644685"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a><span data-ttu-id="76548-102">リレーショナル データ ソースからのインポート (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="76548-102">Import from a Relational Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="76548-103">テーブルのインポート ウィザードを使用して、さまざまなリレーショナル データベースからデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="76548-103">You can import data from a variety of relational databases by using the Table Import Wizard.</span></span> <span data-ttu-id="76548-104">このウィザードは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の **[モデル]** メニューで使用できます。</span><span class="sxs-lookup"><span data-stu-id="76548-104">The wizard is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Model** menu.</span></span> <span data-ttu-id="76548-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="76548-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="76548-106">サポートされているデータ ソースおよびプロバイダーの詳細については、「 [サポートされているデータ ソース (SSAS テーブル)](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76548-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="76548-107">テーブルのインポート ウィザードでは、次のデータ ソースからのデータのインポートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="76548-107">The Table Import Wizard supports importing data from the following data sources:</span></span>  
  
 <span data-ttu-id="76548-108">**リレーショナルデータベース**</span><span class="sxs-lookup"><span data-stu-id="76548-108">**Relational Databases**</span></span>  
  
-   <span data-ttu-id="76548-109">Microsoft SQL Server データベース</span><span class="sxs-lookup"><span data-stu-id="76548-109">Microsoft SQL Server database</span></span>  
  
-   <span data-ttu-id="76548-110">Microsoft SQL Azure</span><span class="sxs-lookup"><span data-stu-id="76548-110">Microsoft SQL Azure</span></span>  
  
-   <span data-ttu-id="76548-111">Microsoft Access データベース</span><span class="sxs-lookup"><span data-stu-id="76548-111">Microsoft Access database</span></span>  
  
-   <span data-ttu-id="76548-112">Microsoft SQL Server 並列データ ウェアハウス</span><span class="sxs-lookup"><span data-stu-id="76548-112">Microsoft SQL Server Parallel Data Warehouse</span></span>  
  
-   <span data-ttu-id="76548-113">Oracle</span><span class="sxs-lookup"><span data-stu-id="76548-113">Oracle</span></span>  
  
-   <span data-ttu-id="76548-114">Teradata</span><span class="sxs-lookup"><span data-stu-id="76548-114">Teradata</span></span>  
  
-   <span data-ttu-id="76548-115">Sybase</span><span class="sxs-lookup"><span data-stu-id="76548-115">Sybase</span></span>  
  
-   <span data-ttu-id="76548-116">Informix</span><span class="sxs-lookup"><span data-stu-id="76548-116">Informix</span></span>  
  
-   <span data-ttu-id="76548-117">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="76548-117">IBM DB2</span></span>  
  
-   <span data-ttu-id="76548-118">OLE DB/ODBC</span><span class="sxs-lookup"><span data-stu-id="76548-118">OLE DB/ODBC</span></span>  
  
 <span data-ttu-id="76548-119">**多次元ソース**</span><span class="sxs-lookup"><span data-stu-id="76548-119">**Multidimensional Sources**</span></span>  
  
-   <span data-ttu-id="76548-120">Microsoft SQL Server Analysis Services キューブ</span><span class="sxs-lookup"><span data-stu-id="76548-120">Microsoft SQL Server Analysis Services cube</span></span>  
  
 <span data-ttu-id="76548-121">テーブルのインポート ウィザードでは、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックをデータ ソースとするデータのインポートはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="76548-121">The Table Import Wizard does not support importing data from a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Workbook as a data source.</span></span>  
  
### <a name="to-import-data-from-a-database"></a><span data-ttu-id="76548-122">データベースからのデータをインポートするには</span><span class="sxs-lookup"><span data-stu-id="76548-122">To import data from a database</span></span>  
  
1.  <span data-ttu-id="76548-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76548-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="76548-124">**[データ ソースへの接続]** ページで接続するデータベースの種類を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76548-124">On the **Connect to a Data Source** page, select the type of database to connect to, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="76548-125">テーブルのインポート ウィザードの手順に従って操作します。</span><span class="sxs-lookup"><span data-stu-id="76548-125">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="76548-126">後続のページでは、 **[テーブルとビューの選択]** ページを使用するか、または **[SQL クエリの指定]** ページで SQL クエリを作成することにより、特定のテーブルおよびビューの選択や、フィルターの適用を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="76548-126">On subsequent pages, you will be able to select specific tables and views or apply filters by using the **Select Tables and Views** page or by creating a SQL query on **Specify a SQL Query** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76548-127">参照</span><span class="sxs-lookup"><span data-stu-id="76548-127">See Also</span></span>  
 <span data-ttu-id="76548-128">[SSAS 表形式&#41;&#40;データをインポートする](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="76548-128">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="76548-129">サポートされているデータ ソース &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="76548-129">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  

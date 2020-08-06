---
title: 多次元データソースからのインポート (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b26cc8ed7237f87fa5e23c6a2fd47e18de2c165
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645237"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a><span data-ttu-id="9fedc-102">多次元データ ソースからのインポート (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="9fedc-102">Import from a Multidimensional Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="9fedc-103">Analysis Services キューブ データベースは、テーブル モデルのデータ ソースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="9fedc-103">You can use an Analysis Services cube database as a data source for a tabular model.</span></span> <span data-ttu-id="9fedc-104">Analysis Services キューブからデータをインポートするには、インポートするデータを選択するための MDX クエリを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fedc-104">In order to import data from an Analysis Services cube, you must define an MDX Query to select data to import.</span></span>  
  
 <span data-ttu-id="9fedc-105">SQL Server Analysis Services データベースに含まれている任意のデータをモデルにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="9fedc-105">Any data that is contained in a SQL Server Analysis Services database can be imported into a model.</span></span> <span data-ttu-id="9fedc-106">ディメンションの一部またはすべてを抽出することも、キューブからスライスおよび集計 (現在の年の月ごとの売上合計など) を取得することもできます。ただし、キューブからインポートしたデータはすべてフラット化されていることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fedc-106">You can extract all or part of a dimension, or get slices and aggregates from the cube, such as the sum of sales, month by month, for the current year, etc. However, you should keep in mind all data that you import from a cube is flattened.</span></span> <span data-ttu-id="9fedc-107">したがって、複数のディメンションからメジャーを取得するクエリを定義した場合、インポートされるデータでは各ディメンションがそれぞれ別の列になります。</span><span class="sxs-lookup"><span data-stu-id="9fedc-107">Therefore, if you define a query that retrieves measures along multiple dimensions, the data will be imported with each dimension in a separate column.</span></span>  
  
 <span data-ttu-id="9fedc-108">Analysis Services キューブのバージョンは、SQL Server 2005、SQL Server 2008、SQL Server 2008 R2、 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fedc-108">Analysis Services cubes must be version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a><span data-ttu-id="9fedc-109">Analysis Services キューブからデータをインポートするには</span><span class="sxs-lookup"><span data-stu-id="9fedc-109">To import data from an Analysis Services cube</span></span>  
  
1.  <span data-ttu-id="9fedc-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9fedc-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="9fedc-111">**[データ ソースへの接続]** ページで、 **[Microsoft Analysis Services]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9fedc-111">On the **Connect to a Data Source** page, select **Microsoft Analysis Services**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="9fedc-112">テーブルのインポート ウィザードの手順に従って操作します。</span><span class="sxs-lookup"><span data-stu-id="9fedc-112">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="9fedc-113">**[MDX クエリの指定]** ページで MDX クエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9fedc-113">You will be able to specify an MDX query on the **Specify a MDX Query** page.</span></span> <span data-ttu-id="9fedc-114">MDX クエリ デザイナーを使用するには、[MDX クエリの指定] ページで **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9fedc-114">To use the MDX Query Designer, on the Specify a MDX Query page, click **Design**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fedc-115">参照</span><span class="sxs-lookup"><span data-stu-id="9fedc-115">See Also</span></span>  
 <span data-ttu-id="9fedc-116">[SSAS 表形式&#41;&#40;データをインポートする](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="9fedc-116">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="9fedc-117">サポートされているデータ ソース &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="9fedc-117">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  

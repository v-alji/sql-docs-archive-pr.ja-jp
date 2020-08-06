---
title: データソースビューでの論理主キーの定義 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25092e5d754381c572dcdbfc03e5ee0f29c1df24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641350"
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a><span data-ttu-id="a6a86-102">データ ソース ビューでの論理主キーの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a6a86-102">Define Logical Primary Keys in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="a6a86-103">データ ソース ビュー ウィザードとデータ ソース ビュー デザイナーでは、データベース テーブルから生成されたデータ ソース ビューにテーブルを追加した場合、そのテーブルの主キーが自動的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-103">The Data Source View Wizard and Data Source View Designer automatically define a primary key for a table that is added to a data source view based on underlying database table.</span></span>  
  
 <span data-ttu-id="a6a86-104">場合によっては、データ ソース ビューの主キーは手動で定義しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6a86-104">Occasionally, you may need to manually define a primary key in the data source view.</span></span> <span data-ttu-id="a6a86-105">たとえば、パフォーマンスまたは設計上の理由から、データ ソース内のテーブルに主キー列が明示的に定義されていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6a86-105">For example, for performance or design reasons, tables in a data source may not have explicitly defined primary key columns.</span></span> <span data-ttu-id="a6a86-106">名前付きクエリおよびビューでも、テーブルの主キー列が省略されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a6a86-106">Named queries and views may also omit the primary key column for a table.</span></span> <span data-ttu-id="a6a86-107">テーブル、ビュー、または名前付きクエリに物理主キーが定義されていない場合は、データ ソース ビュー デザイナーでテーブル、ビュー、または名前付きクエリの論理主キーを手動で定義できます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-107">If a table, view, or named query does not have a physical primary key defined, you can manually define a logical primary key on the table, view or named query in Data Source View Designer.</span></span>  
  
## <a name="set-a-logical-primary-key"></a><span data-ttu-id="a6a86-108">論理主キーの設定</span><span class="sxs-lookup"><span data-stu-id="a6a86-108">Set a Logical Primary Key</span></span>  
 <span data-ttu-id="a6a86-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、テーブル内のレコードの一意の識別、ディメンション テーブル内のキー列の識別、テーブル、ビュー、および名前付きクエリ間のリレーションシップのサポートのために主キーが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a6a86-109">Primary keys are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to uniquely identify records in a table, identify key columns in dimension tables and to support relationships between tables, views and named queries.</span></span> <span data-ttu-id="a6a86-110">これらのリレーションシップを使用して、基になるデータ ソースからデータやメタデータを取得するためのクエリを作成したり、高度なビジネス インテリジェンス機能を活用したりできます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-110">These relationships are used to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="a6a86-111">論理主キーには、名前付き計算を含む、任意の列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-111">Any column can be used for the logical primary key, including a named calculation.</span></span> <span data-ttu-id="a6a86-112">論理主キーを作成すると、データ ソース ビューに一意の制約が作成され、主キー制約として設定されます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-112">When you create a logical primary key, a unique constraint is created in the data source view and marked as a primary key constraint.</span></span> <span data-ttu-id="a6a86-113">選択したテーブルで指定されている他の既存の論理主キーは削除されます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-113">Any other existing logical primary key specified in the selected table is deleted.</span></span>  
  
1.  <span data-ttu-id="a6a86-114">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、論理主キーを設定するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="a6a86-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to set a logical primary key.</span></span>  
  
2.  <span data-ttu-id="a6a86-115">ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6a86-115">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
     <span data-ttu-id="a6a86-116">テーブルまたはビューを検索するには、[**データソースビュー** ] メニューをクリックするか、[**テーブル**] ペインまたは**ダイアグラム**ペインの空いている領域を右クリックして、[**テーブルの検索**] オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6a86-116">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View**  menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
3.  <span data-ttu-id="a6a86-117">**テーブル** ペインまたは **ダイアグラム** ペインで、論理主キーの定義に使用する列を右クリックし、 **[論理主キーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6a86-117">In either the **Tables** or the **Diagram** pane, right-click the column or columns that you want to use to define a logical primary key, and then click **Set Logical Primary Key**.</span></span>  
  
     <span data-ttu-id="a6a86-118">論理主キーを設定するオプションは、主キーを持たないテーブルにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6a86-118">The option to set a logical primary key is available only for tables that do not have a primary key.</span></span>  
  
     <span data-ttu-id="a6a86-119">これで、キーの設定後、キー アイコンによって主キー列を識別できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a6a86-119">Notice that after you set the key, a key icon now identifies the primary key columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a86-120">参照</span><span class="sxs-lookup"><span data-stu-id="a6a86-120">See Also</span></span>  
 <span data-ttu-id="a6a86-121">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a6a86-121">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="a6a86-122">データ ソース ビューでの名前付き計算の定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a6a86-122">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  

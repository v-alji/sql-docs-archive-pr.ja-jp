---
title: ソリューションエクスプローラーでのデータソースの削除 (SSAS 多次元) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6101c8704579894590994d88e0286197148b694
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645216"
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a><span data-ttu-id="2f8c9-102">ソリューション エクスプローラーでのデータ ソースの削除 (SSAS 多次元)</span><span class="sxs-lookup"><span data-stu-id="2f8c9-102">Delete a Data Source in Solution Explorer (SSAS Multidimensional)</span></span>
  <span data-ttu-id="2f8c9-103">データ ソース オブジェクトを削除して、Analysis Services 多次元モデル プロジェクトから完全に消去することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-103">You can delete a data source object to permanently remove it from an Analysis Services multidimensional model project.</span></span>  
  
 <span data-ttu-id="2f8c9-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、データ ソースに基づいてデータ ソース ビューが作成されます。さらに、そのデータ ソース ビューを使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のプロジェクトまたはデータベースのディメンション、キューブ、マイニング構造が定義されます。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-104">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], data sources provide the basis on which data source views are constructed, and data source views are in turn used to define dimensions, cubes, and mining structures in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="2f8c9-105">したがって、データ ソースを削除すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内の他の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが無効になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-105">Therefore, deleting a data source may invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="2f8c9-106">オブジェクトを削除する前に提供される依存オブジェクトの一覧を、常に確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-106">You should always review the list of dependent objects that is provided before deleting the object.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2f8c9-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってオンライン モードで開かれている [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースから、他のオブジェクトが依存しているデータ ソースを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-107">Data sources on which other objects depend cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="2f8c9-108">データ ソースを削除する前に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内でそのデータ ソースに依存しているすべてのオブジェクトを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-108">You must delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that data source before deleting the data source.</span></span> <span data-ttu-id="2f8c9-109">オンライン モードの詳細については、「 [Analysis Services データベースへのオンライン モードでの接続](connect-in-online-mode-to-an-analysis-services-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-109">For more information about online mode, see [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
### <a name="to-delete-a-data-source"></a><span data-ttu-id="2f8c9-110">データ ソースを削除するには</span><span class="sxs-lookup"><span data-stu-id="2f8c9-110">To delete a data source</span></span>  
  
1.  <span data-ttu-id="2f8c9-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、データ ソースを削除するデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database from which you want to delete a data source.</span></span>  
  
2.  <span data-ttu-id="2f8c9-112">**ソリューション エクスプローラー**で **[データ ソース]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-112">In **Solution Explorer**, expand the **Data Sources** folder.</span></span>  
  
3.  <span data-ttu-id="2f8c9-113">データ ソースを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-113">Right-click the data source, and then click **Delete**.</span></span> <span data-ttu-id="2f8c9-114">**[オブジェクトの削除]**  ダイアログ ボックスが表示され、データ ソースを削除すると無効になるオブジェクトが示されます。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-114">The **Delete Objects**  dialog box appears, showing the objects that will be invalidated if you delete the data source.</span></span> <span data-ttu-id="2f8c9-115">**[OK]** をクリックしてデータ ソースを削除する前に、この一覧を慎重に確認します。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-115">Review this list carefully before clicking **OK** to delete the data source.</span></span>  
  
4.  <span data-ttu-id="2f8c9-116">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-116">Save the project.</span></span>  
  
     <span data-ttu-id="2f8c9-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトからデータ ソースを削除した後で、変更されたプロジェクトを保存する必要があります。そうしないと、次回プロジェクトを開くときにエラーが表示されます。これは、プロジェクトで、削除されたデータ ソースを読み込もうとするときに、その基になる XML ファイルがないためです。</span><span class="sxs-lookup"><span data-stu-id="2f8c9-117">After deleting a data source from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you must save the modified project or you will receive an error the next time you open the project because the underlying XML file for the deleted data source will be missing when the project attempts to load the deleted data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8c9-118">参照</span><span class="sxs-lookup"><span data-stu-id="2f8c9-118">See Also</span></span>  
 <span data-ttu-id="2f8c9-119">[多次元モデルのデータソース](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="2f8c9-119">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="2f8c9-120">SSAS 多次元&#41;&#40;サポートされるデータソース</span><span class="sxs-lookup"><span data-stu-id="2f8c9-120">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  

---
title: '[処理およびストレージの場所] (パーティションウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00ab88bac184f57bd2b4dcfdb8d00909a85ece4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741353"
---
# <a name="processing-and-storage-locations-partition-wizard"></a><span data-ttu-id="6cc75-102">[処理およびストレージの場所] (パーティション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="6cc75-102">Processing and Storage Locations (Partition Wizard)</span></span>
  <span data-ttu-id="6cc75-103">**[処理およびストレージの場所]** ページを使用すると、パーティションを所有するキューブの [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスや、パーティションのデータを格納する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6cc75-103">Use the **Processing and Storage Locations** page to specify the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance of the cube that owns the partition, as well as the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that stores the data for the partition.</span></span> <span data-ttu-id="6cc75-104">リモートの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンス、または既定のストレージの場所とは異なるストレージの場所の、どちらかを指定することにより、リモート パーティションとしてパーティションを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="6cc75-104">You can define a partition as a remote partition by specifying either a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a storage location other than the default storage location.</span></span> <span data-ttu-id="6cc75-105">リモート パーティションの詳細については、「 [リモート パーティション](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6cc75-105">For more information about remote partitions, see [Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).</span></span>  
  
## <a name="processing-location-options"></a><span data-ttu-id="6cc75-106">[処理場所] オプション</span><span class="sxs-lookup"><span data-stu-id="6cc75-106">Processing location Options</span></span>  
 <span data-ttu-id="6cc75-107">**[現在のサーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="6cc75-107">**Current server instance**</span></span>  
 <span data-ttu-id="6cc75-108">現在の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスがパーティションを処理します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-108">Makes the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
 <span data-ttu-id="6cc75-109">**[リモート Analysis Services データ ソース]**</span><span class="sxs-lookup"><span data-stu-id="6cc75-109">**Remote Analysis Services data source**</span></span>  
 <span data-ttu-id="6cc75-110">リモート [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスがこのパーティションを処理します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-110">Makes a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing this partition.</span></span>  
  
 <span data-ttu-id="6cc75-111">ドロップダウン リストから、パーティションの処理を行うリモート [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスを表すデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-111">From the dropdown list, select the data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that will be responsible for processing the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6cc75-112">`Initial Catalog` 接続文字列プロパティで選択したデータ ソースに有効な [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースが設定されていない場合や、`Initial Catalog` 接続文字列プロパティに指定されたデータベースがリモート パーティションをサポートしていない (つまり、指定されたデータベースの `MasterDatasourceID` プロパティが有効な値に設定されていない) 場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-112">An error occurs if you select a data source in which the `Initial Catalog` connection string property is not set to a valid [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or if the database specified in the `Initial Catalog` connection string property does not support remote partitions (in other words, the `MasterDatasourceID` property of the specified database is not set to a valid value).</span></span>  
  
 <span data-ttu-id="6cc75-113">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="6cc75-113">**New**</span></span>  
 <span data-ttu-id="6cc75-114">パーティションを処理するリモート [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスを表す、新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-114">Creates a new data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
## <a name="storage-location-options"></a><span data-ttu-id="6cc75-115">[ストレージの場所] オプション</span><span class="sxs-lookup"><span data-stu-id="6cc75-115">Storage location Options</span></span>  
 <span data-ttu-id="6cc75-116">**[既定のサーバーの場所]**</span><span class="sxs-lookup"><span data-stu-id="6cc75-116">**Default server location**</span></span>  
 <span data-ttu-id="6cc75-117">現在の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのデータ フォルダーを、パーティションの集計データとインデックス付きデータの格納場所にします。</span><span class="sxs-lookup"><span data-stu-id="6cc75-117">Makes the data folder of the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="6cc75-118">**[指定のフォルダー]**</span><span class="sxs-lookup"><span data-stu-id="6cc75-118">**Specified folder**</span></span>  
 <span data-ttu-id="6cc75-119">パーティションの集計データとインデックス付きデータの格納場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-119">Specifies the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="6cc75-120">**...**</span><span class="sxs-lookup"><span data-stu-id="6cc75-120">**...**</span></span>  
 <span data-ttu-id="6cc75-121">**[指定のフォルダー]** のフォルダーを選択する、 **[リモート フォルダーの参照]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="6cc75-121">Displays the **Browse for Remote Folder** dialog box in which you can select a folder for **Specified folder**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc75-122">参照</span><span class="sxs-lookup"><span data-stu-id="6cc75-122">See Also</span></span>  
 <span data-ttu-id="6cc75-123">[パーティションウィザードの F1 ヘルプ &#40;Analysis Services-多次元データ&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6cc75-123">[Partition Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="6cc75-124">[パーティション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6cc75-124">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="6cc75-125">[[リモートフォルダーの参照] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="6cc75-125">[Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  

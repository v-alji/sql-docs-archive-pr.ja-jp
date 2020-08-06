---
title: データフローパスエディターでパスのメタデータを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d84e14c2bc42ac4b831a4d1a3321d3e8b4acf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631140"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a><span data-ttu-id="77855-102">データ フロー パス エディターでパスのメタデータを表示する</span><span class="sxs-lookup"><span data-stu-id="77855-102">View Path Metadata in the Data Flow Path Editor</span></span>
  <span data-ttu-id="77855-103">パスは、2 つのデータ フロー コンポーネントを連結します。</span><span class="sxs-lookup"><span data-stu-id="77855-103">Paths connect two data flow components.</span></span> <span data-ttu-id="77855-104">パスのメタデータを表示する場合、データ フローには、2 つ以上の連結されたデータ フロー コンポーネントをあらかじめ含めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="77855-104">Before you can view path metadata, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="77855-105">詳細については、「 [データ フローでコンポーネントを追加または削除する](data-flow/add-or-delete-a-component-in-a-data-flow.md) 」と「 [データ フロー内でコンポーネントを連結する](data-flow/connect-components-in-a-data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77855-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-view-path-metadata"></a><span data-ttu-id="77855-106">パスのメタデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="77855-106">To view path metadata</span></span>  
  
1.  <span data-ttu-id="77855-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="77855-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="77855-108">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="77855-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="77855-109">**[データ フロー]** タブをクリックし、パスをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="77855-109">Click the **Data Flow** tab and double-click a path.</span></span>  
  
4.  <span data-ttu-id="77855-110">**[データ フロー パス エディター]** ダイアログ ボックスで、 **[メタデータ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77855-110">In **Data Flow Path Editor** dialog box, click **Metadata**.</span></span>  
  
5.  <span data-ttu-id="77855-111">パスのメタデータが表示されます。メタデータには、各列の列名、データ型、有効桁数、小数点以下桁数、データ長、コード ページ、および基になるコンポーネントの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="77855-111">View path metadata, including the column names, data type, precision, scale, length, code page, and the name of the source component of each column.</span></span>  
  
6.  <span data-ttu-id="77855-112">メタデータをコピーするには、 **[クリップボードにコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77855-112">To copy the metadata, click **Copy to Clipboard**.</span></span>  
  
7.  <span data-ttu-id="77855-113">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77855-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77855-114">参照</span><span class="sxs-lookup"><span data-stu-id="77855-114">See Also</span></span>  
 <span data-ttu-id="77855-115">[Integration Services のパス](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="77855-115">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="77855-116">データ フロー</span><span class="sxs-lookup"><span data-stu-id="77855-116">Data Flow</span></span>](data-flow/data-flow.md)  
  
  

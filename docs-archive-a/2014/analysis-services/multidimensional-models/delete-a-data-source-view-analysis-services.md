---
title: データソースビューの削除 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
author: minewiskan
ms.author: owend
ms.openlocfilehash: 24b587e8d8961161ea803915c31d117c11f7cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645213"
---
# <a name="delete-a-data-source-view-analysis-services"></a><span data-ttu-id="b123a-102">データ ソース ビューの削除 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b123a-102">Delete a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="b123a-103">OLAP プロジェクトでデータ ソース ビュー (DSV) を使用していない場合、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でプロジェクトから DSV を削除できます。</span><span class="sxs-lookup"><span data-stu-id="b123a-103">If you are no longer using a data source view (DSV) in an OLAP project, you can delete it from the project in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b123a-104">DSV は、削除すると完全に失われます。</span><span class="sxs-lookup"><span data-stu-id="b123a-104">Deleting a DSV is permanent.</span></span> <span data-ttu-id="b123a-105">削除した DSV を、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のプロジェクトまたはデータベースに復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="b123a-105">You cannot restore a deleted DSV to a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="b123a-106">他のオブジェクトが依存している DSV は、オンライン モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって開かれた [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] データベースから削除できません。</span><span class="sxs-lookup"><span data-stu-id="b123a-106">DSVs that other objects depend on cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="b123a-107">サーバーで実行中のデータベースに接続されているプロジェクトから DSV を削除するには、DSV 自体を削除する前に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内でその DSV に依存しているすべてのオブジェクトを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b123a-107">To delete a DSV from a project that is connected o a database running on a server, you must first delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that DSV before deleting the DSV itself.</span></span>  
  
 <span data-ttu-id="b123a-108">DSV を削除すると、依存している他の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが無効になります。そのため、DSV を削除する前に、DSV を削除すると無効になるオブジェクトの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b123a-108">Deleting a DSV will invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects that depend on it, so before you delete the DSV, you will see the list of objects that will become invalid once the DSV is removed.</span></span> <span data-ttu-id="b123a-109">使用する予定のあるオブジェクトが含まれていないか、この一覧で確認します。</span><span class="sxs-lookup"><span data-stu-id="b123a-109">Review this list carefully to be sure that it does not include objects you still expect to use.</span></span>  
  
 <span data-ttu-id="b123a-110">![[オブジェクトの削除] ダイアログ ボックス](../media/ssas-olapdsv-deleteobjects.gif "[オブジェクトの削除] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="b123a-110">![Delete Objects dialog box](../media/ssas-olapdsv-deleteobjects.gif "Delete Objects dialog box")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b123a-111">参照</span><span class="sxs-lookup"><span data-stu-id="b123a-111">See Also</span></span>  
 <span data-ttu-id="b123a-112">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="b123a-112">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="b123a-113">データ ソース ビューのプロパティの変更 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b123a-113">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
  

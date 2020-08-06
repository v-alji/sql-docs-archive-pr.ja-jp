---
title: SRID (Spatial Reference Identifier) | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 15db59b43731b9a39ff4bef78e3a6cb6929e9b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642018"
---
# <a name="spatial-reference-identifiers-srids"></a><span data-ttu-id="d9089-102">SRID (Spatial Reference Identifier)</span><span class="sxs-lookup"><span data-stu-id="d9089-102">Spatial Reference Identifiers (SRIDs)</span></span>
  <span data-ttu-id="d9089-103">各空間インスタンスには SRID (spatial reference identifier) があります。</span><span class="sxs-lookup"><span data-stu-id="d9089-103">Each spatial instance has a spatial reference identifier (SRID).</span></span> <span data-ttu-id="d9089-104">SRID は、平面地球マッピングまたは球体地球マッピングに使用される特定の楕円体に基づく空間参照系に対応します。</span><span class="sxs-lookup"><span data-stu-id="d9089-104">The SRID corresponds to a spatial reference system based on the specific ellipsoid used for either flat-earth mapping or round-earth mapping.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9089-105">新しい SRID を含む、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入された空間機能の詳細な説明とサンプルについては、ホワイト ペーパー「 [New Spatial Features in SQL Server 2012 (SQL Server 2012 の新しい空間機能)](https://go.microsoft.com/fwlink/?LinkId=226407)」をダウンロードして参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9089-105">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including a new SRID, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="d9089-106">空間列には異なる SRID を持つオブジェクトを格納できますが、</span><span class="sxs-lookup"><span data-stu-id="d9089-106">A spatial column can contain objects with different SRIDs.</span></span> <span data-ttu-id="d9089-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の空間データ メソッドを使用してデータの操作を実行する際に使用できるのは、同じ SRID を持つ空間インスタンスだけです。</span><span class="sxs-lookup"><span data-stu-id="d9089-107">However, only spatial instances with the same SRID can be used when performing operations with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data methods on your data.</span></span> <span data-ttu-id="d9089-108">2 つの空間データ インスタンスから引き出される空間メソッドの結果は、それらのインスタンスが同じ SRID を持つ (同じ測定単位、データ、および投影を使用してインスタンスの座標が決定されている) 場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="d9089-108">The result of any spatial method derived from two spatial data instances is valid only if those instances have the same SRID that is based on the same unit of measurement, datum, and projection used to determine the coordinates of the instances.</span></span> <span data-ttu-id="d9089-109">SRID の最も一般的な測定単位はメートルまたは平方メートルです。</span><span class="sxs-lookup"><span data-stu-id="d9089-109">The most common units of measurement of a SRID are meters or square meters.</span></span>  
  
 <span data-ttu-id="d9089-110">2 つの空間インスタンスの SRID が同じでない場合に、それらのインスタンスに対して `geometry` データ型や `geography` データ型のメソッドを使用すると、NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="d9089-110">If two spatial instances do not have the same SRID, the results from a `geometry` or `geography` Data Type method used on the instances will return NULL.</span></span> <span data-ttu-id="d9089-111">たとえば、次の述語で NULL 以外の結果が返されるためには、`geometry1` および `geometry2` の 2 つの `geometry` インスタンスの SRID が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9089-111">For example, for the following predicate term to return a non-NULL result, the two `geometry` instances, `geometry1` and `geometry2`, must have the same SRID:</span></span>  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  <span data-ttu-id="d9089-112">空間参照識別系は、地図制作、測量、および測地のデータの格納のために開発された一連の標準である [European Petroleum Survey Group (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) 標準によって定義されています。</span><span class="sxs-lookup"><span data-stu-id="d9089-112">The spatial reference identification system is defined by the [European Petroleum Survey Group (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) standard, which is a set of standards developed for cartography, surveying, and geodetic data storage.</span></span> <span data-ttu-id="d9089-113">この標準は、Oil and Gas Producers (OGP) Surveying and Positioning Committee が所有しています。</span><span class="sxs-lookup"><span data-stu-id="d9089-113">This standard is owned by the Oil and Gas Producers (OGP) Surveying and Positioning Committee.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9089-114">参照</span><span class="sxs-lookup"><span data-stu-id="d9089-114">See Also</span></span>  
 [<span data-ttu-id="d9089-115">空間データ型の概要</span><span class="sxs-lookup"><span data-stu-id="d9089-115">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  

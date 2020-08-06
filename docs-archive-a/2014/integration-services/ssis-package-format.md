---
title: SSIS パッケージ形式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 524c65ac5682b8efe8c4191697eb540f9acca82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715561"
---
# <a name="ssis-package-format"></a><span data-ttu-id="656a5-102">SSIS パッケージの形式</span><span class="sxs-lookup"><span data-stu-id="656a5-102">SSIS Package Format</span></span>
  <span data-ttu-id="656a5-103">最新のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]では、形式の読み取りとパッケージの比較を容易にするために、パッケージの形式 (.dtsx file) に大幅な変更が加えられました。</span><span class="sxs-lookup"><span data-stu-id="656a5-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], significant changes were made to the package format (.dtsx file) to make it easier to read the format and to compare packages.</span></span> <span data-ttu-id="656a5-104">また、競合する変更やバイナリ形式での変更が含まれていないパッケージをより確実にマージすることもできます。</span><span class="sxs-lookup"><span data-stu-id="656a5-104">You can also more reliably merge packages that don't contain conflicting changes or changes stored in binary format.</span></span>  
  
 <span data-ttu-id="656a5-105">現在の .DTSX パッケージファイル形式を表示するには、「 [ \[ .Dtsx \] : データ変換サービスパッケージの XML ファイル形式の仕様](https://go.microsoft.com/fwlink/?LinkId=233251)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="656a5-105">To view the current DTSX package file format, see [\[MS-DTSX\]: Data Transformation Services Package XML File Format Specification](https://go.microsoft.com/fwlink/?LinkId=233251).</span></span>  
  
 <span data-ttu-id="656a5-106">ファイル形式の変更の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="656a5-106">The following list outlines the file format changes.</span></span> <span data-ttu-id="656a5-107">これらの変更のコード例については、「 [SQL Server 2012 のパッケージ形式の変更](https://go.microsoft.com/fwlink/?LinkId=233255)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="656a5-107">To view code examples of these changes, see [Package Format Changes in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=233255).</span></span>  
  
-   <span data-ttu-id="656a5-108">.dtsx ファイルの読みやすさとわかりやすさを向上させるために、形式規則が適用されています。</span><span class="sxs-lookup"><span data-stu-id="656a5-108">Formatting conventions have been applied to make it easier to read and understand the .dtsx file.</span></span>  
  
-   <span data-ttu-id="656a5-109">形式はより簡潔になっています。</span><span class="sxs-lookup"><span data-stu-id="656a5-109">The format is more concise.</span></span> <span data-ttu-id="656a5-110">プロパティごとの個別の要素は属性として残っています。ただし、PackageFormatVersion は除きます。</span><span class="sxs-lookup"><span data-stu-id="656a5-110">Separate elements for each property have been persisted as attributes, with the exception of the PackageFormatVersion.</span></span> <span data-ttu-id="656a5-111">属性はアルファベット順に一覧表示され、既定値を持つプロパティはもう残っていません。</span><span class="sxs-lookup"><span data-stu-id="656a5-111">Attributes are listed alphabetically, and properties that have default values are no longer persisted.</span></span> <span data-ttu-id="656a5-112">最後に、複数回出現する要素は親要素内に含まれています。</span><span class="sxs-lookup"><span data-stu-id="656a5-112">Finally, elements that can appear multiple times, are now contained within a parent element.</span></span>  
  
-   <span data-ttu-id="656a5-113">他のオブジェクトで参照できるパッケージ内のほとんどのオブジェクトに、パッケージ XML で定義された `refId` 属性が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="656a5-113">Most objects within a package that can be referred to by other objects now have a `refId` attribute defined in the package XML.</span></span> <span data-ttu-id="656a5-114">系列 ID の代わりに `refID`が残っています。</span><span class="sxs-lookup"><span data-stu-id="656a5-114">Instead of persisting lineage IDs, the `refID` is now persisted.</span></span> <span data-ttu-id="656a5-115">系列 ID は今でもランタイム内で使用され、パッケージを読み込むと再生成されます。</span><span class="sxs-lookup"><span data-stu-id="656a5-115">Lineage IDs are still used within the runtime and regenerated when the package is loaded.</span></span>  
  
     <span data-ttu-id="656a5-116">`refId` 値は、GUID または整数値よりも読みやすくわかりやすい一意の文字列です。</span><span class="sxs-lookup"><span data-stu-id="656a5-116">The `refId` value is a unique string that is readable and understandable, compared to GUIDs or integer values.</span></span> <span data-ttu-id="656a5-117">この文字列は、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]でパッケージ構成に使用されたパス値に似ています。</span><span class="sxs-lookup"><span data-stu-id="656a5-117">The string is similar to path values used for package configurations in previous releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="656a5-118">2 つのバージョンのパッケージ間の変更をマージする場合は、検索/置換操作で `refId` を使用して、そのオブジェクトへのすべての参照が正しく更新されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="656a5-118">If you are merging changes between two versions of a package, the `refId` can be used in find/replace operations to ensure that all references to that object have been correctly updated.</span></span>  
  
-   <span data-ttu-id="656a5-119">レイアウト情報は CData セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="656a5-119">The layout information is contained in a CData section.</span></span>  
  
-   <span data-ttu-id="656a5-120">注釈はクリア テキストで残ります。</span><span class="sxs-lookup"><span data-stu-id="656a5-120">Annotations are persisted in cleartext.</span></span> <span data-ttu-id="656a5-121">これにより、ドキュメントの自動生成に関する情報を簡単に抽出できます。</span><span class="sxs-lookup"><span data-stu-id="656a5-121">This makes it easier to extract the information for automated generation of documentation.</span></span>  
  
  

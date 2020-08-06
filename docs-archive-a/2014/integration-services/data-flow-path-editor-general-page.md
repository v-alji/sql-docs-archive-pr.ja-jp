---
title: '[データフローパスエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.general.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: 72a9ff1d-3748-41d1-a9b2-63f4a77bba24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71eca61b1454e2e8cb811bbe450f584191ae77b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713386"
---
# <a name="data-flow-path-editor-general-page"></a><span data-ttu-id="37196-102">[データ フロー パス エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="37196-102">Data Flow Path Editor (General Page)</span></span>
  <span data-ttu-id="37196-103">**[データ フロー パス エディター]** ダイアログ ボックスを使用すると、パス プロパティの設置、列メタデータの表示、およびパスにアタッチされるデータ ビューアーの管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="37196-103">Use the **Data Flow Path Editor** dialog box to set path properties, view column metadata, and manage the data viewers attached to the path.</span></span>  
  
 <span data-ttu-id="37196-104">**[データ フロー パス エディター]** ダイアログ ボックスの **[全般]** ノードを使用して、パスに名前を付けて説明を記述したり、パスの注釈のオプションを指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="37196-104">Use the **General** node of the **Data Flow Path Editor** dialog box to name and describe the path, and to specify the options for path annotation.</span></span>  
  
## <a name="options"></a><span data-ttu-id="37196-105">Options</span><span class="sxs-lookup"><span data-stu-id="37196-105">Options</span></span>  
 <span data-ttu-id="37196-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="37196-106">**Name**</span></span>  
 <span data-ttu-id="37196-107">パスの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="37196-107">Provide a unique name for the path.</span></span>  
  
 <span data-ttu-id="37196-108">**ID**</span><span class="sxs-lookup"><span data-stu-id="37196-108">**ID**</span></span>  
 <span data-ttu-id="37196-109">パスの系列 ID です。</span><span class="sxs-lookup"><span data-stu-id="37196-109">The lineage identifier of the path.</span></span> <span data-ttu-id="37196-110">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="37196-110">This property is read-only.</span></span>  
  
 <span data-ttu-id="37196-111">**[IdentificationString]**</span><span class="sxs-lookup"><span data-stu-id="37196-111">**IdentificationString**</span></span>  
 <span data-ttu-id="37196-112">パスを識別する文字列です。</span><span class="sxs-lookup"><span data-stu-id="37196-112">The string that identifies the path.</span></span> <span data-ttu-id="37196-113">上記で入力した名前から自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="37196-113">Automatically generated from the name entered above.</span></span>  
  
 <span data-ttu-id="37196-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="37196-114">**Description**</span></span>  
 <span data-ttu-id="37196-115">パスの説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="37196-115">Describe the path.</span></span>  
  
 <span data-ttu-id="37196-116">**[PathAnnotation]**</span><span class="sxs-lookup"><span data-stu-id="37196-116">**PathAnnotation**</span></span>  
 <span data-ttu-id="37196-117">使用する注釈の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="37196-117">Specify the type of annotation to use.</span></span> <span data-ttu-id="37196-118">注釈を無効にする場合は **[Never]** 、注釈を必要に応じて有効にする場合は **[AsNeeded]** 、 **[SourceName]** オプションの値を使用して自動的に注釈を付ける場合は **[SourceName]** 、 **[Name]** プロパティの値を使用して自動的に注釈を付ける場合は **[PathName]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="37196-118">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **SourceName** to automatically annotate using the value of the **SourceName** option, and **PathName** to automatically annotate using the value of the **Name** property.</span></span>  
  
 <span data-ttu-id="37196-119">**[DestinationName]**</span><span class="sxs-lookup"><span data-stu-id="37196-119">**DestinationName**</span></span>  
 <span data-ttu-id="37196-120">パスの末尾の入力を表示します。</span><span class="sxs-lookup"><span data-stu-id="37196-120">Displays the input that is the end of the path.</span></span>  
  
 <span data-ttu-id="37196-121">**[SourceName]**</span><span class="sxs-lookup"><span data-stu-id="37196-121">**SourceName**</span></span>  
 <span data-ttu-id="37196-122">パスの先頭の出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="37196-122">Displays the output that is the start of the path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37196-123">参照</span><span class="sxs-lookup"><span data-stu-id="37196-123">See Also</span></span>  
 <span data-ttu-id="37196-124">[データフローパスエディター &#40;メタデータページ&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span><span class="sxs-lookup"><span data-stu-id="37196-124">[Data Flow Path Editor &#40;Metadata Page&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span></span>  
 <span data-ttu-id="37196-125">[データフローパスエディターの [データビューアー] ページ &#40;&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="37196-125">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="37196-126">[データ フロー](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="37196-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="37196-127">パッケージで注釈を使用する</span><span class="sxs-lookup"><span data-stu-id="37196-127">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  

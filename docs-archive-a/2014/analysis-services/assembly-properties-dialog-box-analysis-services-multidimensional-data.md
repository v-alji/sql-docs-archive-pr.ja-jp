---
title: '[アセンブリのプロパティ] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fdd506da42c5088b173db0981b5df94f91e5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633640"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="a832e-102">[アセンブリのプロパティ] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="a832e-102">Assembly Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a832e-103">**の** [アセンブリのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのアセンブリ参照のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a832e-103">Use the **Assembly Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of an assembly reference in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="a832e-104">**[アセンブリのプロパティ]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** でアセンブリを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a832e-104">You can display the **Assembly Properties** dialog box by right-clicking an assembly in **Object Explorer** and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a832e-105">Options</span><span class="sxs-lookup"><span data-stu-id="a832e-105">Options</span></span>  
  
|<span data-ttu-id="a832e-106">期間</span><span class="sxs-lookup"><span data-stu-id="a832e-106">Term</span></span>|<span data-ttu-id="a832e-107">定義</span><span class="sxs-lookup"><span data-stu-id="a832e-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="a832e-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="a832e-108">**Name**</span></span>|<span data-ttu-id="a832e-109">変更するアセンブリ参照の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a832e-109">Type to change the name of the assembly reference.</span></span><br /><br /> <span data-ttu-id="a832e-110">注: この値を変更しても、アセンブリ参照が参照するアセンブリの名前は変更されませんが、アセンブリ参照を参照する際に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスまたはデータベースが使用する名前が変更されます。</span><span class="sxs-lookup"><span data-stu-id="a832e-110">Note: Changing this value does not change the name of the assembly referred to by the assembly reference, but instead changes the name used the by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or database when referring to the assembly reference.</span></span>|  
|<span data-ttu-id="a832e-111">**ID**</span><span class="sxs-lookup"><span data-stu-id="a832e-111">**ID**</span></span>|<span data-ttu-id="a832e-112">アセンブリ参照が参照するアセンブリの ID を表示します。</span><span class="sxs-lookup"><span data-stu-id="a832e-112">Displays the identifier of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="a832e-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="a832e-113">**Description**</span></span>|<span data-ttu-id="a832e-114">変更するアセンブリ参照の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="a832e-114">Type to change the description of the assembly reference.</span></span>|  
|<span data-ttu-id="a832e-115">**[タイムスタンプの作成]**</span><span class="sxs-lookup"><span data-stu-id="a832e-115">**Create Timestamp**</span></span>|<span data-ttu-id="a832e-116">アセンブリ参照が作成された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="a832e-116">Displays the date and time the assembly reference was created.</span></span>|  
|<span data-ttu-id="a832e-117">**[スキーマの最終更新]**</span><span class="sxs-lookup"><span data-stu-id="a832e-117">**Last Schema Update**</span></span>|<span data-ttu-id="a832e-118">アセンブリ参照のメタデータが最後に更新された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="a832e-118">Displays the date and time the metadata for the assembly reference was last updated.</span></span>|  
|<span data-ttu-id="a832e-119">**Type**</span><span class="sxs-lookup"><span data-stu-id="a832e-119">**Type**</span></span>|<span data-ttu-id="a832e-120">アセンブリ参照の種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="a832e-120">Displays the type of the assembly reference.</span></span> <span data-ttu-id="a832e-121">次の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a832e-121">The following values are displayed:</span></span><br /><br /> <span data-ttu-id="a832e-122">**.Net アセンブリ**: アセンブリ参照は .NET Framework アセンブリを参照し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a832e-122">**.NET Assembly**: The assembly reference refers to a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework assembly.</span></span><br /><br /> <span data-ttu-id="a832e-123">**COM DLL**: アセンブリ参照は com ライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="a832e-123">**COM DLL**: The assembly reference refers to a COM library.</span></span>|  
|<span data-ttu-id="a832e-124">**ソース**</span><span class="sxs-lookup"><span data-stu-id="a832e-124">**Source**</span></span>|<span data-ttu-id="a832e-125">アセンブリ参照のソースを表示します。</span><span class="sxs-lookup"><span data-stu-id="a832e-125">Displays the source of the assembly reference.</span></span> <span data-ttu-id="a832e-126">このプロパティは通常、アセンブリ参照が参照するアセンブリの完全なパスおよびファイル名を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="a832e-126">This property typically contains the full path and file name of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="a832e-127">**[権限セット]**</span><span class="sxs-lookup"><span data-stu-id="a832e-127">**Permission Set**</span></span>|<span data-ttu-id="a832e-128">アセンブリ参照へのアクセスの決定に使用される権限セットを選択します。</span><span class="sxs-lookup"><span data-stu-id="a832e-128">Select the permission set used to determine access to the assembly reference.</span></span> <span data-ttu-id="a832e-129">このプロパティで使用できる値の詳細については、「」を参照してください <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a832e-129">For more information about the available values for this property, see <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.</span></span>|  
|<span data-ttu-id="a832e-130">**[権限借用情報]**</span><span class="sxs-lookup"><span data-stu-id="a832e-130">**Impersonation Info**</span></span>|<span data-ttu-id="a832e-131">アセンブリ参照へのアクセス時に使用する権限借用情報を選択します。</span><span class="sxs-lookup"><span data-stu-id="a832e-131">Select the impersonation information to use when accessing the assembly reference.</span></span> <span data-ttu-id="a832e-132">このプロパティで使用可能な値の詳細については、「[ImpersonationInfo 要素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a832e-132">For more information about the available values for this property, see [ImpersonationInfo Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a832e-133">参照</span><span class="sxs-lookup"><span data-stu-id="a832e-133">See Also</span></span>  
 <span data-ttu-id="a832e-134">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a832e-134">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a832e-135">多次元モデルのアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="a832e-135">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  

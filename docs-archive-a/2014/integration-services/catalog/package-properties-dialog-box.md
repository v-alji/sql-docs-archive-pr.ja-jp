---
title: '[パッケージのプロパティ] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b386bf4e75ff784cd8d4a96363515786d242d2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639604"
---
# <a name="package-properties-dialog-box"></a><span data-ttu-id="841b9-102">[パッケージのプロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="841b9-102">Package Properties Dialog Box</span></span>
  <span data-ttu-id="841b9-103">**[パッケージのプロパティ]** ダイアログ ボックスでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに格納されているパッケージのプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="841b9-103">Use the **Package Properties** dialog box to view properties for packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="841b9-104">詳細については、「[Integration Services &#40;SSIS&#41; Packages](integration-services-ssis-server-and-catalog.md)」(Integration Services &#40;SSIS&#41; のパッケージ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="841b9-104">For more information, see [Integration Services &#40;SSIS&#41; Server](integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="841b9-105">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="841b9-105">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="841b9-106">[[パッケージのプロパティ] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="841b9-106">[Open the Package Properties dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="841b9-107">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="841b9-107">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-package-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="841b9-108">[パッケージのプロパティ] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="841b9-108">Open the Package Properties dialog box</span></span>  
  
1.  <span data-ttu-id="841b9-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="841b9-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="841b9-110">SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="841b9-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="841b9-111">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="841b9-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="841b9-112">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="841b9-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="841b9-113">プロパティを表示するパッケージが格納されているフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="841b9-113">Expand the folder that contains the package you want to view properties for.</span></span>  
  
5.  <span data-ttu-id="841b9-114">パッケージを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="841b9-114">Right-click the package, and then select **Properties**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="841b9-115">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="841b9-115">Configure the Options</span></span>  
 <span data-ttu-id="841b9-116">**[全般]** ページでは、選択されているパッケージのプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="841b9-116">Use the **General** page to view the properties of the selected package.</span></span>  
  
 <span data-ttu-id="841b9-117">**[全般]** ページに表示されるすべてのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="841b9-117">All properties on the **General** page are read-only.</span></span>  
  
 <span data-ttu-id="841b9-118">**Name**</span><span class="sxs-lookup"><span data-stu-id="841b9-118">**Name**</span></span>  
 <span data-ttu-id="841b9-119">パッケージの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="841b9-119">Displays the name of the package.</span></span>  
  
 <span data-ttu-id="841b9-120">**識別子**</span><span class="sxs-lookup"><span data-stu-id="841b9-120">**Identifier**</span></span>  
 <span data-ttu-id="841b9-121">パッケージ ID を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="841b9-121">Lists the package ID.</span></span>  
  
 <span data-ttu-id="841b9-122">**エントリ ポイント**</span><span class="sxs-lookup"><span data-stu-id="841b9-122">**Entry Point**</span></span>  
 <span data-ttu-id="841b9-123">値 `True` は、パッケージが直接起動されることを示します。</span><span class="sxs-lookup"><span data-stu-id="841b9-123">The value of `True` indicates that the package is started directly.</span></span> <span data-ttu-id="841b9-124">値 `False` は、パッケージ実行タスクを使用して、パッケージが別のパッケージによって起動されることを示します。</span><span class="sxs-lookup"><span data-stu-id="841b9-124">The value of `False` indicates that the package is started by another package using the Execute Package task.</span></span> <span data-ttu-id="841b9-125">既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="841b9-125">The default value is `True`.</span></span>  
  
 <span data-ttu-id="841b9-126">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で親パッケージと子パッケージの両方に対してこのプロパティを設定するには、ソリューション エクスプローラーでパッケージを右クリックし、 **[エントリ ポイント パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="841b9-126">You set this property in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for both the parent package and the child packages by right-clicking the package in Solution Explorer and then clicking **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="841b9-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="841b9-127">**Description**</span></span>  
 <span data-ttu-id="841b9-128">省略可能なパッケージの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="841b9-128">Displays the optional description of the package.</span></span>  
  
  

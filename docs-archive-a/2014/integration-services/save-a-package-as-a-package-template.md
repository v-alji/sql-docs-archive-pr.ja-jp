---
title: パッケージをパッケージテンプレートとして保存する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30bddb5a343e7c7aef279bc66c25be30a2cf1a12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714505"
---
# <a name="save-a-package-as-a-package-template"></a><span data-ttu-id="894e4-102">パッケージをパッケージ テンプレートとして保存する</span><span class="sxs-lookup"><span data-stu-id="894e4-102">Save a Package as a Package Template</span></span>
  <span data-ttu-id="894e4-103">このトピックでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で新しい Integration Services パッケージを作成する際に、カスタム パッケージをテンプレートとして指定および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="894e4-103">This topic describes how to designate and use custom packages as templates when you create new Integration Services packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="894e4-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトに新しいパッケージを追加する場合に、既定で、新しいパッケージを作成するパッケージ テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="894e4-104">By default, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] uses a package template that creates an empty package when you add a new package to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="894e4-105">この既定のテンプレートを置き換えることはできませんが、新しいテンプレートを追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="894e4-105">You cannot replace this default template, but you can add new templates.</span></span>  
  
 <span data-ttu-id="894e4-106">テンプレートとして、複数のパッケージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="894e4-106">You can designate multiple packages to use as templates.</span></span> <span data-ttu-id="894e4-107">カスタム パッケージをテンプレートとして実装するには、そのパッケージをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e4-107">Before you can implement custom packages as templates, you must create the packages.</span></span>  
  
 <span data-ttu-id="894e4-108">カスタム パッケージをテンプレートとして使用してパッケージを作成すると、新しいパッケージの名前と GUID は、テンプレートと同じになります。</span><span class="sxs-lookup"><span data-stu-id="894e4-108">When you create package using custom packages as templates, the new packages have the same name and GUID as the template.</span></span> <span data-ttu-id="894e4-109">パッケージを区別するには、`Name` プロパティの値を更新して、`ID` プロパティの新しい GUID を生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e4-109">To differentiate among packages you should update the value of the `Name` property and generate a new GUID for the `ID` property.</span></span> <span data-ttu-id="894e4-110">詳細については、「 [SQL Server データ ツールでのパッケージの作成](create-packages-in-sql-server-data-tools.md) 」および「 [パッケージのプロパティを設定する](set-package-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="894e4-110">For more information, see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) and [Set Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a><span data-ttu-id="894e4-111">カスタム パッケージをパッケージ テンプレートとして指定するには</span><span class="sxs-lookup"><span data-stu-id="894e4-111">To designate a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="894e4-112">ファイル システムで、テンプレートとして使用するパッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="894e4-112">In the file system, locate the package that you want to use as template.</span></span>  
  
2.  <span data-ttu-id="894e4-113">パッケージを DataTransformationItems フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="894e4-113">Copy the package to the DataTransformationItems folder.</span></span> <span data-ttu-id="894e4-114">既定では、このフォルダーは、C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject にあります。</span><span class="sxs-lookup"><span data-stu-id="894e4-114">By default this folder is in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
3.  <span data-ttu-id="894e4-115">テンプレートとして使用する各パッケージについて、手順 1. と手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="894e4-115">Repeat steps 1 and 2 for each package that you want to use as a template.</span></span>  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a><span data-ttu-id="894e4-116">カスタム パッケージをパッケージ テンプレートとして使用するには</span><span class="sxs-lookup"><span data-stu-id="894e4-116">To use a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="894e4-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="894e4-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="894e4-118">ソリューション エクスプローラーで、プロジェクトを右クリックして **[追加]** をポイントし、 **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="894e4-118">In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
3.  <span data-ttu-id="894e4-119">**[新しい項目の追加 - \<project name>]** ダイアログ ボックスで、テンプレートとして使うパッケージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="894e4-119">In the **Add New Item -\<project name>** dialog box, click the package that you want to use as a template.</span></span>  
  
     <span data-ttu-id="894e4-120">テンプレートの一覧には、"新しい SSIS パッケージ" という名前の既定のパッケージ テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="894e4-120">The list of templates includes the default package template named New SSIS Package.</span></span> <span data-ttu-id="894e4-121">パッケージ テンプレートとして使用できるテンプレートは、パッケージ アイコンで示されます。</span><span class="sxs-lookup"><span data-stu-id="894e4-121">The package icon identifies templates that can be used as package templates.</span></span>  
  
4.  <span data-ttu-id="894e4-122">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="894e4-122">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894e4-123">参照</span><span class="sxs-lookup"><span data-stu-id="894e4-123">See Also</span></span>  
 <span data-ttu-id="894e4-124">[SQL Server データ ツールでのパッケージの作成](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="894e4-124">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="894e4-125">Integration Services &#40;SSIS&#41; パッケージ</span><span class="sxs-lookup"><span data-stu-id="894e4-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  

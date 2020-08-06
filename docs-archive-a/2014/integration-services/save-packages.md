---
title: パッケージを保存する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 102e2c3eab001c230722bf3485d6ea9731aa99a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738514"
---
# <a name="save-packages"></a><span data-ttu-id="dab55-102">パッケージを保存する</span><span class="sxs-lookup"><span data-stu-id="dab55-102">Save Packages</span></span>
  <span data-ttu-id="dab55-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用してパッケージを構築し、XML ファイル (.dtsx ファイル) としてファイル システムに保存します。</span><span class="sxs-lookup"><span data-stu-id="dab55-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] you build packages by using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and save the packages to the file system as XML files (.dtsx files).</span></span> <span data-ttu-id="dab55-104">パッケージ XML ファイルのコピーは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の msdb データベースまたはパッケージ ストアに保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="dab55-104">You can also save copies of the package XML file to the msdb database in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="dab55-105">パッケージ ストアとは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するファイル システムの場所にあるフォルダーのことです。</span><span class="sxs-lookup"><span data-stu-id="dab55-105">The package store represents the folders in the file system location that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
 <span data-ttu-id="dab55-106">ファイル システムに保存したパッケージは、後で [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] またはパッケージ ストアにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="dab55-106">If you save a package to the file system, you can later use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to import the package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="dab55-107">詳細については、「[パッケージをインポートおよびエクスポートする (SSIS サービス)](../../2014/integration-services/import-and-export-packages-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dab55-107">For more information, see [Import and Export Packages &#40;SSIS Service&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md).</span></span>  
  
 <span data-ttu-id="dab55-108">また、コマンド プロンプト ユーティリティの **dtutil**を使用して、ファイル システムと msdb 間でパッケージをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="dab55-108">You can also use a command prompt utility, **dtutil**, to copy a package between the file system and msdb.</span></span> <span data-ttu-id="dab55-109">詳細については、「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dab55-109">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-save-a-package"></a><span data-ttu-id="dab55-110">パッケージを保存するには</span><span class="sxs-lookup"><span data-stu-id="dab55-110">To save a package</span></span>  
  
-   [<span data-ttu-id="dab55-111">パッケージをファイルシステムに保存する</span><span class="sxs-lookup"><span data-stu-id="dab55-111">Save a Package to the File System</span></span>](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [<span data-ttu-id="dab55-112">パッケージのコピーを保存する</span><span class="sxs-lookup"><span data-stu-id="dab55-112">Save a Copy of a Package</span></span>](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  

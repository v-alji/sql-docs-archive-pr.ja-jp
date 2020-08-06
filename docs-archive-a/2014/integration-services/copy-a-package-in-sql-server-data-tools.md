---
title: SQL Server Data Tools でのパッケージのコピー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6ed4dd66ee4755181f5df6f3c1b5466b3f26b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641800"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a><span data-ttu-id="5d130-102">SQL Server Data Tools でのパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="5d130-102">Copy a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="5d130-103">このトピックでは、既存のパッケージをコピーして新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを作成する方法、および新しいパッケージの `Name` プロパティと `GUID` プロパティを更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d130-103">This topic describes how to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package by copying an existing package, and how to update the `Name` and `GUID` properties of the new package.</span></span>  
  
### <a name="to-copy-a-package"></a><span data-ttu-id="5d130-104">パッケージをコピーするには</span><span class="sxs-lookup"><span data-stu-id="5d130-104">To copy a package</span></span>  
  
1.  <span data-ttu-id="5d130-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、コピーするパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5d130-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to copy.</span></span>  
  
2.  <span data-ttu-id="5d130-106">ソリューション エクスプローラーで、パッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d130-106">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="5d130-107">コピーするパッケージがソリューション エクスプローラーで選択されていること、またはパッケージが含まれている SSIS デザイナーのタブがアクティブになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5d130-107">Verify either the package to copy is selected in Solution Explorer or the tab in SSIS Designer that contains the package is the active tab</span></span>  
  
4.  <span data-ttu-id="5d130-108">**[ファイル]** メニューの **[名前を付けて \<package name> を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d130-108">On the **File** menu, click **Save \<package name> As**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d130-109">**[ファイル]** メニューに **[名前を付けて保存]** オプションを表示するには、SSIS デザイナーでパッケージを開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d130-109">The package must be opened in SSIS Designer before the **Save As** option appears on the **File** menu.</span></span>  
  
5.  <span data-ttu-id="5d130-110">必要に応じて、別のフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="5d130-110">Optionally, browse to a different folder.</span></span>  
  
6.  <span data-ttu-id="5d130-111">パッケージ ファイルの名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="5d130-111">Update the name of the package file.</span></span> <span data-ttu-id="5d130-112">ファイル拡張子は、必ず .dtsx のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="5d130-112">Make sure that you retain the .dtsx file extension.</span></span>  
  
7.  <span data-ttu-id="5d130-113">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d130-113">Click **Save**.</span></span>  
  
8.  <span data-ttu-id="5d130-114">プロンプトで、パッケージ オブジェクトの名前をファイル名と一致するように更新するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="5d130-114">At the prompt, choose whether to update the name of the package object to match the file name.</span></span> <span data-ttu-id="5d130-115">[**はい**] をクリックすると、 `Name` パッケージのプロパティが更新されます。</span><span class="sxs-lookup"><span data-stu-id="5d130-115">If you click **Yes**, the `Name` property of the package is updated.</span></span> <span data-ttu-id="5d130-116">新しいパッケージが [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトに追加され、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで開かれます。</span><span class="sxs-lookup"><span data-stu-id="5d130-116">The new package is added to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
9. <span data-ttu-id="5d130-117">必要に応じて、 **[制御フロー]** タブの背景をクリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d130-117">Optionally, click in the background of the **Control Flow** tab, and the click **Properties**.</span></span>  
  
10. <span data-ttu-id="5d130-118">[プロパティ] ウィンドウで、ID プロパティの値をクリックし、ドロップダウン リストの **[\<Generate New ID>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d130-118">In the Properties window, click the value of the ID property, and then in the drop-down list click **\<Generate New ID>**.</span></span>  
  
11. <span data-ttu-id="5d130-119">**[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックし、新しいパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="5d130-119">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d130-120">参照</span><span class="sxs-lookup"><span data-stu-id="5d130-120">See Also</span></span>  
 <span data-ttu-id="5d130-121">[パッケージのコピーを保存する](../../2014/integration-services/save-a-copy-of-a-package.md) </span><span class="sxs-lookup"><span data-stu-id="5d130-121">[Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md) </span></span>  
 <span data-ttu-id="5d130-122">[SQL Server データ ツールでのパッケージの作成](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5d130-122">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="5d130-123">Integration Services &#40;SSIS&#41; パッケージ</span><span class="sxs-lookup"><span data-stu-id="5d130-123">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  

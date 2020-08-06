---
title: リソースの更新 (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- updating resources
- resources [Reporting Services], updating
ms.assetid: d21f7493-bcf7-4e9e-9886-55ebdc1f1037
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0fca59e476c2820b715ff46729784edc562f74d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640579"
---
# <a name="update-a-resource-report-manager"></a><span data-ttu-id="7f7eb-102">リソースの更新 (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="7f7eb-102">Update a Resource (Report Manager)</span></span>
  <span data-ttu-id="7f7eb-103">リソースを新しいバージョンに置換すると、リソースを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-103">You can update a resource by replacing it with a newer version.</span></span> <span data-ttu-id="7f7eb-104">リソースは、レポート サーバーに格納されたアイテムです。このアイテムには、アップロードするファイルのコンテンツが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-104">Resources are items stored on a report server that contain content from a file that you upload.</span></span> <span data-ttu-id="7f7eb-105">新しいコンテンツまたは異なるコンテンツをインポートすると、既存のリソースを置換できます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-105">You can replace an existing resource by importing new or different file content into the existing resource.</span></span> <span data-ttu-id="7f7eb-106">リソースの更新は、既存のプロパティやリソース上のセキュリティ設定を保持しながらコンテンツを更新する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-106">Updating a resource provides a way to update content while preserving existing properties and security settings on the resource.</span></span>  
  
### <a name="to-update-a-resource"></a><span data-ttu-id="7f7eb-107">リソースを更新するには</span><span class="sxs-lookup"><span data-stu-id="7f7eb-107">To update a resource</span></span>  
  
1.  <span data-ttu-id="7f7eb-108">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="7f7eb-109">レポート マネージャーで、更新するリソースへの移動またはリソースの検索を行います。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-109">In Report Manager, navigate to or search for the resource you want to update.</span></span>  
  
3.  <span data-ttu-id="7f7eb-110">**[表示]** ページでリソースをクリックして、そのリソースを開きます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-110">Click the resource to open it in the **View** page.</span></span>  
  
4.  <span data-ttu-id="7f7eb-111">**[プロパティ]** をクリックすると、 **[全般]** プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-111">Click **Properties** to open the **General** properties page.</span></span>  
  
5.  <span data-ttu-id="7f7eb-112">**[置換]** をクリックすると、 **[リソースのインポート]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-112">Click **Replace** to open the **Import Resource** page.</span></span>  
  
6.  <span data-ttu-id="7f7eb-113">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-113">Click **Browse**.</span></span>  
  
7.  <span data-ttu-id="7f7eb-114">使用するファイルを選択して、現在のリソースを置換します。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-114">Select the file that you want to use to replace the current resource.</span></span> <span data-ttu-id="7f7eb-115">更新されたバージョンのリソース ファイルを使用したり、名前やファイル タイプの異なるファイルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-115">You can use an updated version of the resource file, or specify a file with a different name or file type.</span></span>  
  
8.  <span data-ttu-id="7f7eb-116">**[OK]** をクリックして、リソース ファイルをアップロードします。次に、 **[リソースのインポート]** ページを閉じ、レポート サーバーに変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-116">Click **OK** to upload the resource file, close the **Import Resource** page, and save your changes to the report server.</span></span>  
  
 <span data-ttu-id="7f7eb-117">更新するリソースにレポートで使用する画像が含まれる場合、更新された画像を表示するにはレポートを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f7eb-117">If the resource you are updating contains an image that is used in a report, you need to refresh the report to see the updated image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7eb-118">参照</span><span class="sxs-lookup"><span data-stu-id="7f7eb-118">See Also</span></span>  
 <span data-ttu-id="7f7eb-119">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7f7eb-119">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="7f7eb-120">[[ファイルのアップロード] ページ &#40;レポートマネージャー&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7f7eb-120">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 <span data-ttu-id="7f7eb-121">[フォルダーへのファイルのアップロード](upload-files-to-a-folder.md) </span><span class="sxs-lookup"><span data-stu-id="7f7eb-121">[Upload Files to a Folder](upload-files-to-a-folder.md) </span></span>  
 [<span data-ttu-id="7f7eb-122">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="7f7eb-122">Report Manager F1 Help</span></span>](../report-manager-f1-help.md)  
  
  

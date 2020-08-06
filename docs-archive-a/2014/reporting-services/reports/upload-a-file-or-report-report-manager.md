---
title: ファイルまたはレポートをアップロードする (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 119e2b22976dc227e017b81a59b698cf9eb7457f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633740"
---
# <a name="upload-a-file-or-report-report-manager"></a><span data-ttu-id="18c82-102">ファイルまたはレポートをアップロードする (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="18c82-102">Upload a File or Report (Report Manager)</span></span>
  <span data-ttu-id="18c82-103">レポート マネージャーには、レポート、モデル、およびその他のファイルをクライアント アプリケーションからパブリッシュしなくてもレポート サーバーに追加できるアップロード機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="18c82-103">Report Manager provides an upload feature so that you can add reports, models, and other files to a report server without having to publish those items from a client application.</span></span> <span data-ttu-id="18c82-104">ファイル システムからアップロードしたファイルは、レポート サーバー上のアイテムとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="18c82-104">Files that you upload from the file system are stored as items on the report server.</span></span> <span data-ttu-id="18c82-105">ファイルがどのように格納されるかは、アップロードするファイルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="18c82-105">The type of file you upload determines how it is stored:</span></span>  
  
-   <span data-ttu-id="18c82-106">.rdl ファイルはレポートとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="18c82-106">.rdl files are stored as reports.</span></span>  
  
-   <span data-ttu-id="18c82-107">.smdl ファイルはレポート モデルとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="18c82-107">.smdl files are stored as report models.</span></span>  
  
-   <span data-ttu-id="18c82-108">共有データ ソース (.rds) ファイルなど、その他すべてのファイルはリソースとしてアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="18c82-108">All other files, including shared data source (.rds) files, are uploaded as resources.</span></span> <span data-ttu-id="18c82-109">リソースはレポート サーバーでは処理されませんが、レポート サーバーが MIME タイプのファイルをサポートしていれば、レポート マネージャーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="18c82-109">Resources are not processed by a report server, but can be viewed in Report Manager if the report server supports the MIME type of the file.</span></span>  
  
### <a name="to-upload-a-file-or-report"></a><span data-ttu-id="18c82-110">ファイルまたはレポートをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="18c82-110">To upload a file or report</span></span>  
  
1.  <span data-ttu-id="18c82-111">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="18c82-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="18c82-112">レポート マネージャーで **[コンテンツ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="18c82-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="18c82-113">アイテムを追加するフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="18c82-113">Navigate to the folder to which you want to add an item.</span></span>  
  
3.  <span data-ttu-id="18c82-114">**[ファイルのアップロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18c82-114">Click **Upload File**.</span></span>  
  
4.  <span data-ttu-id="18c82-115">**[参照]** をクリックして、アップロードするファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="18c82-115">Click **Browse** to select a file to upload.</span></span> <span data-ttu-id="18c82-116">レポート定義ファイル、画像、ドキュメント、またはレポート サーバーで利用できるようにする任意のファイルをアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="18c82-116">You can upload a report definition file, an image, a document, or any file that you want to make available on the report server.</span></span>  
  
5.  <span data-ttu-id="18c82-117">新しいアイテムの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="18c82-117">Type a name for the new item.</span></span> <span data-ttu-id="18c82-118">アイテム名ではスペースを使用できます。ただし、予約文字 (; ? :) は使用できません</span><span class="sxs-lookup"><span data-stu-id="18c82-118">An item name can include spaces, but cannot include the reserved characters: ; ?</span></span> <span data-ttu-id="18c82-119">: \@ & = +、$/\* \< > |。</span><span class="sxs-lookup"><span data-stu-id="18c82-119">: \@ & = + , $ / \* \< > |.</span></span>  
  
6.  <span data-ttu-id="18c82-120">既存のアイテムを新しいアイテムに置き換える場合は、 **[アイテムが存在する場合は上書きする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18c82-120">If you want to replace an existing item with the new item, select **Overwrite item if it exists**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="18c82-121">参照</span><span class="sxs-lookup"><span data-stu-id="18c82-121">See Also</span></span>  
 <span data-ttu-id="18c82-122">[共有データソース &#40;レポートマネージャーの作成、削除、または変更&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="18c82-122">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="18c82-123">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="18c82-123">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="18c82-124">[[ファイルのアップロード] ページ &#40;レポートマネージャー&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="18c82-124">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 [<span data-ttu-id="18c82-125">フォルダーへのファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="18c82-125">Upload Files to a Folder</span></span>](../report-server/upload-files-to-a-folder.md)  
  
  

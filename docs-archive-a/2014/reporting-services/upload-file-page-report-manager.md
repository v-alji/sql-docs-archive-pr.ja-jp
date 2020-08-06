---
title: '[ファイルのアップロード] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7bb3166f-9374-4449-b66a-ffb77298507d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de03c6c6bd03cbe083d5e1edfd320264d2cc3bde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719406"
---
# <a name="upload-file-page-report-manager"></a><span data-ttu-id="ae22a-102">[ファイルのアップロード] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="ae22a-102">Upload File Page (Report Manager)</span></span>
  <span data-ttu-id="ae22a-103">ファイル システムからレポート サーバー データベースにファイルをパブリッシュするには、[ファイルのアップロード] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="ae22a-103">Use the Upload File page to publish a file from the file system into the report server database.</span></span> <span data-ttu-id="ae22a-104">アップロードされたファイルは、レポート サーバーのフォルダー階層に、アイテムとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-104">Uploaded files are represented as items in the report server folder hierarchy.</span></span>  
  
-   <span data-ttu-id="ae22a-105">アップロードされた .rdl ファイルは、レポートとしてレポート サーバーにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-105">Uploaded .rdl files are published to a report server as reports.</span></span>  
  
-   <span data-ttu-id="ae22a-106">アップロードされた .smdl ファイルにデータ ソース ビュー情報が含まれていた場合、このファイルはレポート モデルとしてパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-106">Uploaded .smdl files are published as report models if they contain data source view information.</span></span> <span data-ttu-id="ae22a-107">データ ソース ビューへの参照が失われると、アップロード中にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ae22a-107">If they are missing a data source view reference, an error occurs during the upload.</span></span> <span data-ttu-id="ae22a-108">レポートモデルプロジェクトから smdl ファイルをアップロードすると、データソースビューの情報が失われる場合があり [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-108">Data source view information might be missing if you upload an .smdl file from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] report model project.</span></span> <span data-ttu-id="ae22a-109">レポート モデル プロジェクトでは、データ ソース ビュー情報は、.smdl ファイル自体ではなく、独立したファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-109">In report model projects, data source view information is stored in a separate file rather than in the .smdl file itself.</span></span>  
  
     <span data-ttu-id="ae22a-110">データ ソース ビュー情報を含む (およびアップロードが正常に実行される) モデル ファイルは、以前にレポート サーバーにパブリッシュされて、サーバーからファイル システムのファイルに保存されたものです。</span><span class="sxs-lookup"><span data-stu-id="ae22a-110">Model files that do contain data source view information (and can therefore be successfully uploaded) are those that have been previously published to a report server and then saved from the server to a file on the file system.</span></span> <span data-ttu-id="ae22a-111">モデルの [全般プロパティ] ページを開き、 **[編集]** をクリックしてモデルを開くと、モデルをファイルに保存できます。その後、そのファイルを新しいモデルとしてレポート サーバーにアップロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-111">If you open the General Properties page of a model and click **Edit** to open the model, you can save it to a file and then upload it as a new model on the report server.</span></span> <span data-ttu-id="ae22a-112">次にアップロードした .smdl ファイルには、モデルのパブリケーションに必要な情報がすべて含められます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-112">The .smdl file that you subsequently upload will have all of information that is necessary for model publication.</span></span>  
  
-   <span data-ttu-id="ae22a-113">アップロードする他のすべてのファイルの種類は、リソースとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-113">All other file types that you upload are stored as resources.</span></span> <span data-ttu-id="ae22a-114">これには、レポート データ ソース接続情報を含む .rds ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-114">This includes .rds files that contain report data source connection information.</span></span> <span data-ttu-id="ae22a-115">.rds ファイルをアップロードしても、レポート サーバーで共有データ ソース アイテムは生成されません。</span><span class="sxs-lookup"><span data-stu-id="ae22a-115">Uploading an .rds file does not produce a shared data source item on the report server.</span></span>  
  
 <span data-ttu-id="ae22a-116">アイテムをアップロードすると、そのアイテムは現在のフォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-116">When you upload an item, it is placed in the current folder.</span></span> <span data-ttu-id="ae22a-117">アップロードの完了後、異なる場所にアイテムを移動できます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-117">After the upload is complete, you can move the item to a different location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae22a-118">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ae22a-118">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ae22a-119">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae22a-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ae22a-120">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="ae22a-120">Navigation</span></span>  
 <span data-ttu-id="ae22a-121">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ae22a-121">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-upload-file-page"></a><span data-ttu-id="ae22a-122">[ファイルのアップロード] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="ae22a-122">To open the Upload File page</span></span>  
  
1.  <span data-ttu-id="ae22a-123">レポート マネージャーを開き、ファイルをアップロードするフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="ae22a-123">Open Report Manager, and navigate to the folder in which you want to upload a file.</span></span>  
  
2.  <span data-ttu-id="ae22a-124">ツール バーの **[ファイルのアップロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae22a-124">In the toolbar, click **Upload File**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ae22a-125">Options</span><span class="sxs-lookup"><span data-stu-id="ae22a-125">Options</span></span>  
 <span data-ttu-id="ae22a-126">**[アップロードするファイル]**</span><span class="sxs-lookup"><span data-stu-id="ae22a-126">**File to Upload**</span></span>  
 <span data-ttu-id="ae22a-127">ファイル システムからコピーするファイルへの完全修飾パスを表示します。</span><span class="sxs-lookup"><span data-stu-id="ae22a-127">Displays the fully qualified path to the file you are copying from the file system.</span></span>  
  
 <span data-ttu-id="ae22a-128">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="ae22a-128">**Browse**</span></span>  
 <span data-ttu-id="ae22a-129">ファイル システムからファイルを選択する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae22a-129">Click to choose a file from the file system.</span></span>  
  
 <span data-ttu-id="ae22a-130">**名前**</span><span class="sxs-lookup"><span data-stu-id="ae22a-130">**Name**</span></span>  
 <span data-ttu-id="ae22a-131">ファイル名を入力します。この名前はレポート サーバーの名前空間に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-131">Type the name of the file, as it will appear in the report server namespace.</span></span> <span data-ttu-id="ae22a-132">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae22a-132">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="ae22a-133">また、スペースおよび特定の記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ae22a-133">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="ae22a-134">名前を指定するときに、; ?</span><span class="sxs-lookup"><span data-stu-id="ae22a-134">Do not use the characters ; ?</span></span> <span data-ttu-id="ae22a-135">: \@ & = +、$ \* \< > |項目名を指定する場合は。</span><span class="sxs-lookup"><span data-stu-id="ae22a-135">: \@ & = + , $ \* \< > | " or / when specifying an item name.</span></span>  
  
 <span data-ttu-id="ae22a-136">**[アイテムが存在する場合は上書きします]**</span><span class="sxs-lookup"><span data-stu-id="ae22a-136">**Overwrite item if it exists**</span></span>  
 <span data-ttu-id="ae22a-137">既存のアイテムを新しいバージョンと置き換える場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ae22a-137">Select this check box if you want to replace an existing item with a newer version.</span></span> <span data-ttu-id="ae22a-138">既存のバージョンを上書きするには、新しいアイテムと既存のアイテムの名前が完全に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae22a-138">To overwrite an existing version, the name of the new item and the existing item must be an exact match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae22a-139">参照</span><span class="sxs-lookup"><span data-stu-id="ae22a-139">See Also</span></span>  
 <span data-ttu-id="ae22a-140">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ae22a-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="ae22a-141">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ae22a-141">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="ae22a-142">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ae22a-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="ae22a-143">フォルダーへのファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="ae22a-143">Upload Files to a Folder</span></span>](report-server/upload-files-to-a-folder.md)  
  
  

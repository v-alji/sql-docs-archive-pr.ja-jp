---
title: フォルダーへのファイルのアップロード | Microsoft Docs
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
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640578"
---
# <a name="upload-files-to-a-folder"></a><span data-ttu-id="40ecd-102">フォルダーへのファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="40ecd-102">Upload Files to a Folder</span></span>
  <span data-ttu-id="40ecd-103">ファイル システムからファイルをアップロードし、それらを管理対象アイテムとしてレポート サーバー データベースに格納できます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-103">You can upload files from the file system and store them as managed items in a report server database.</span></span> <span data-ttu-id="40ecd-104">ファイルのアップロード時に行われる処理は、ファイルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="40ecd-104">What happens when you upload a file depends on the file type.</span></span>

-   <span data-ttu-id="40ecd-105">.rdl ファイルのアップロードは、レポートのパブリッシュと同等です。</span><span class="sxs-lookup"><span data-stu-id="40ecd-105">Uploading an .rdl file is equivalent to publishing a report.</span></span>

-   <span data-ttu-id="40ecd-106">その他のファイルをアップロードすると、アップロードしたファイルが単一のバイナリ オブジェクトとしてレポート サーバー データベースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-106">Uploading any other file adds it to the report server database as a single binary object.</span></span> <span data-ttu-id="40ecd-107">これらのファイルは、リソースとしてレポート サーバーにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-107">These files are published to a report server as a resource.</span></span> <span data-ttu-id="40ecd-108">リソースのファイルの種類には指定がありません。</span><span class="sxs-lookup"><span data-stu-id="40ecd-108">Resources can be any file type.</span></span> <span data-ttu-id="40ecd-109">ファイルの拡張子が既知の MIME の種類に一致する場合、リソースの種類を識別するために、その MIME の種類のアイコンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-109">If the file extension matches a known MIME type, an icon for that MIME type is used to identify the resource type.</span></span> <span data-ttu-id="40ecd-110">ファイルの拡張子が未登録の場合、リソースは汎用ファイル アイコンで示されます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-110">Otherwise, a generic file icon indicates a resource.</span></span>

> [!NOTE]
>  <span data-ttu-id="40ecd-111">レポート データ ソース (.rds) ファイルをアップロードして共有データ ソースを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="40ecd-111">You cannot upload a report data source (.rds) file to create a shared data source.</span></span> <span data-ttu-id="40ecd-112">.rds ファイルは、レポート デザイナーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-112">An .rds file is used only in Report Designer.</span></span> <span data-ttu-id="40ecd-113">レポート マネージャーで定義および管理する共有データ ソース アイテムのコンテンツを、このファイルから提供することはできません。</span><span class="sxs-lookup"><span data-stu-id="40ecd-113">It cannot provide the content for a shared data source item that you define and manage through Report Manager.</span></span> <span data-ttu-id="40ecd-114">アップロードする代わりに、.rds ファイルを基に共有データ ソースを作成するスクリプトを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-114">As an alternative to uploading, you can write a script that creates a shared data source based on a .rds file.</span></span>

 <span data-ttu-id="40ecd-115">アップロードするアイテムの最大ファイル サイズは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]によって決まります。</span><span class="sxs-lookup"><span data-stu-id="40ecd-115">The maximum file size for uploaded items is determined by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="40ecd-116">既定の最大サイズは 4 MB です。</span><span class="sxs-lookup"><span data-stu-id="40ecd-116">By default, the maximum size is 4 megabytes (MB).</span></span>

 <span data-ttu-id="40ecd-117">視覚的には、レポート サーバー データベースにアップロードしたファイルは、以下のアイコンでフォルダー階層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-117">Visually, files that you upload to a report server database are represented in the folder hierarchy with the following icons.</span></span>

 <span data-ttu-id="40ecd-118">![レポートアイコン](../media/hlp-16doc.gif "[レポート] アイコン")レポートアイコン</span><span class="sxs-lookup"><span data-stu-id="40ecd-118">![Report icon](../media/hlp-16doc.gif "Report icon") report icon</span></span>

 <span data-ttu-id="40ecd-119">![モデルアイコン](../media/model-icon.gif "モデルアイコン")レポートモデルアイコン</span><span class="sxs-lookup"><span data-stu-id="40ecd-119">![Model icon](../media/model-icon.gif "Model icon") report model icon</span></span>

 <span data-ttu-id="40ecd-120">![汎用リソースアイコン](../media/hlp-16file.gif "汎用リソース アイコン")汎用リソースアイコン</span><span class="sxs-lookup"><span data-stu-id="40ecd-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon") generic resource icon</span></span>

 <span data-ttu-id="40ecd-121">ファイルをアップロードすると、ファイルは常に、現在選択しているフォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-121">When you upload a file, it is always placed in the folder that is currently selected.</span></span> <span data-ttu-id="40ecd-122">最初に、アイテムを含めるフォルダーに移動できます。また、ファイルをアップロードしてから最終的な場所にファイルを移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-122">You can navigate to the folder that you want to contain the item first, or you can upload a file and then move it to a final location later.</span></span>

 <span data-ttu-id="40ecd-123">ファイルをアップロードするには、レポート マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="40ecd-123">To upload a file, use Report Manager.</span></span> <span data-ttu-id="40ecd-124">レポート サーバーにファイルをアップロードできるかどうかは、ロールの割り当てを構成するタスクによって異なります。</span><span class="sxs-lookup"><span data-stu-id="40ecd-124">Whether you can upload files to a report server depends on tasks that are part of your role assignment.</span></span> <span data-ttu-id="40ecd-125">既定のセキュリティを使用している場合は、ローカル管理者によってレポート サーバーにアイテムを追加できます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-125">If you are using default security, local administrators can add items to a report server.</span></span> <span data-ttu-id="40ecd-126">個人用レポートが有効である場合は、個人用レポート フォルダーを持っているすべてのユーザーに、そのフォルダーへアイテムをアップロードする権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="40ecd-126">If My Reports is enabled, any user who has a My Reports folder has permission to upload items to that folder.</span></span> <span data-ttu-id="40ecd-127">カスタム ロールの割り当てを使用している場合は、フォルダー管理をサポートするタスクがロールの割り当てに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="40ecd-127">If you use custom role assignments, the role assignment must include tasks that support folder management.</span></span>

|<span data-ttu-id="40ecd-128">目的</span><span class="sxs-lookup"><span data-stu-id="40ecd-128">To do this</span></span>|<span data-ttu-id="40ecd-129">含まれるタスク</span><span class="sxs-lookup"><span data-stu-id="40ecd-129">Include these tasks</span></span>|
|----------------|-------------------------|
|<span data-ttu-id="40ecd-130">.rdl ファイルをフォルダーにアップロード</span><span class="sxs-lookup"><span data-stu-id="40ecd-130">Upload an .rdl file to a folder</span></span>|<span data-ttu-id="40ecd-131">レポートの管理</span><span class="sxs-lookup"><span data-stu-id="40ecd-131">Manage reports</span></span>|
|<span data-ttu-id="40ecd-132">任意のファイルをバイナリ オブジェクトとしてアップロード</span><span class="sxs-lookup"><span data-stu-id="40ecd-132">Upload any file as a binary object</span></span>|<span data-ttu-id="40ecd-133">リソースの管理</span><span class="sxs-lookup"><span data-stu-id="40ecd-133">Manage resources</span></span>|
|<span data-ttu-id="40ecd-134">フォルダーのコンテンツの表示</span><span class="sxs-lookup"><span data-stu-id="40ecd-134">View the contents of a folder</span></span>|<span data-ttu-id="40ecd-135">リソースの表示、レポートの表示</span><span class="sxs-lookup"><span data-stu-id="40ecd-135">View resources, View reports</span></span>|

## <a name="see-also"></a><span data-ttu-id="40ecd-136">参照</span><span class="sxs-lookup"><span data-stu-id="40ecd-136">See Also</span></span>
 <span data-ttu-id="40ecd-137">[レポートマネージャー &#40;SSRS ネイティブモード&#41;]../report-manager-ssrs-native-mode.md)[ネイティブモードのレポートサーバー](../security/granting-permissions-on-a-native-mode-report-server.md) [タスクとアクセス許可](../security/tasks-and-permissions.md)に対する権限の許可[ファイルまたはレポートをアップロードレポートマネージャー &#40;&#41;](../reports/upload-a-file-or-report-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="40ecd-137">[Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md) [Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) [Tasks and Permissions](../security/tasks-and-permissions.md) [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md)</span></span>



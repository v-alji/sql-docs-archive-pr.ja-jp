---
title: 個人用レポートの使用 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91d44c0aa8471064753d9b4fb0ecc0de89aa8396
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634269"
---
# <a name="using-my-reports-report-builder-and-ssrs"></a><span data-ttu-id="28a35-102">個人用レポートの使用 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="28a35-102">Using My Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="28a35-103">[個人用レポート] フォルダーは、ネイティブ モードで構成されたレポート サーバーにおいて、所有しているレポートを保存したり、操作することができる作業領域です。</span><span class="sxs-lookup"><span data-stu-id="28a35-103">On a report server configured in native mode, the My Reports folder is a personal workspace that you can use to store and work with reports that you own.</span></span> <span data-ttu-id="28a35-104">他のレポート サーバー フォルダーはパブリック フォルダーであり、通常、フォルダーのコンテンツの追加や変更を行うには高度な権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="28a35-104">Other report server folders are public and typically require users to have advanced permissions to add to or modify folder contents.</span></span> <span data-ttu-id="28a35-105">一方、[個人用レポート] フォルダーは、ユーザーが管理する作業領域です。</span><span class="sxs-lookup"><span data-stu-id="28a35-105">In contrast, the My Reports folder is a user-managed workspace.</span></span> <span data-ttu-id="28a35-106">個々のユーザーが独自の設定を基にレポートやフォルダーの追加や削除を行い、リンク レポートを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="28a35-106">You can add or remove reports and folders and save linked reports with personalized settings.</span></span>  
  
 <span data-ttu-id="28a35-107">概念的には、[個人用レポート] フォルダーは、Windows ファイル システムの [マイ ドキュメント] フォルダーに似ています。</span><span class="sxs-lookup"><span data-stu-id="28a35-107">Conceptually, the My Reports folder is similar to the My Documents folder in the Windows file system.</span></span> <span data-ttu-id="28a35-108">すべてのユーザーに [個人用レポート] というフォルダーがありますが、各ユーザーがアクセスする [個人用レポート] フォルダーは、他のすべてのユーザーが使用するフォルダーとは異なる [個人用レポート] フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="28a35-108">Although each user has a folder called My Reports, the folder that each accesses is different from all other users.</span></span> <span data-ttu-id="28a35-109">ある特定のユーザーが所有する [個人用レポート] フォルダーのコンテンツに対し、レポート サーバー管理者を除く他のユーザーがアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="28a35-109">Except for report server administrators, other users cannot access the contents of the My Reports folder that belongs to you.</span></span>  
  
 <span data-ttu-id="28a35-110">個人用レポート機能は、必須機能ではなく、レポート サーバー管理者が無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="28a35-110">The My Reports feature is optional and can be disabled by a report server administrator.</span></span> <span data-ttu-id="28a35-111">有効になっている場合、[ホーム] フォルダー内に [個人用レポート] フォルダーが表示されます。[個人用レポート] フォルダーには、レポート マネージャーまたは Web ブラウザーを使用してアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="28a35-111">If it is enabled, you will see a My Reports folder in the Home folder, which you can access using the Report Manager or a Web browser.</span></span> <span data-ttu-id="28a35-112">詳細については、「[レポート マネージャーを使用したレポートの検索と表示 &#40;レポート ビルダーおよび SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a35-112">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="28a35-113">SharePoint 統合モードで構成されたレポート サーバーには、個人用レポート フォルダーに相当するフォルダーは存在しません。</span><span class="sxs-lookup"><span data-stu-id="28a35-113">On a report server configured in SharePoint integrated mode, there is no equivalent to the My Reports folder.</span></span> <span data-ttu-id="28a35-114">詳細については、「 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a35-114">For more information, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a><span data-ttu-id="28a35-115">個人用レポートの使用方法</span><span class="sxs-lookup"><span data-stu-id="28a35-115">Ways to Use My Reports</span></span>  
 <span data-ttu-id="28a35-116">[個人用レポート] フォルダーは、ユーザーがレポートやフォルダー、その他のアイテムを追加するまでは空になっています。</span><span class="sxs-lookup"><span data-stu-id="28a35-116">My Reports is empty until you add reports, folders, and other items.</span></span> <span data-ttu-id="28a35-117">[個人用レポート] フォルダーにコンテンツを追加する方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="28a35-117">Here are some ways to add content to My Reports.</span></span>  
  
-   <span data-ttu-id="28a35-118">個人のリンク レポートを作成し、これを [個人用レポート] に保存します。</span><span class="sxs-lookup"><span data-stu-id="28a35-118">Create a personal linked report and store it in My Reports.</span></span> <span data-ttu-id="28a35-119">すべてのレポートから、リンク レポートを作成できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="28a35-119">Not all reports are available for linking.</span></span> <span data-ttu-id="28a35-120">詳細については、「 [リンク レポートを作成する](../reports/create-a-linked-report.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a35-120">For more information, see [Create a Linked Report](../reports/create-a-linked-report.md).</span></span>  
  
-   <span data-ttu-id="28a35-121">レポート定義 (.rdl) ファイル、レポート モデル (.smdl) ファイルなどのファイルをファイル システムからアップロードします。</span><span class="sxs-lookup"><span data-stu-id="28a35-121">Upload a report definition (.rdl) file, report model (.smdl) file, or other files from the file system.</span></span> <span data-ttu-id="28a35-122">どんなファイルでもアップロードできますが、レポート サーバーで処理できるのは、ファイル拡張子が .rdl または .smdl のレポート ファイルのみです。</span><span class="sxs-lookup"><span data-stu-id="28a35-122">You can upload any file, but the report server only processes report files that have an .rdl or .smdl file extension.</span></span> <span data-ttu-id="28a35-123">詳細については、SQL Server オンライン ブックの [Reporting Services ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312)の「レポート定義」と「[ファイルまたはレポートをアップロード &#40;レポート マネージャー&#41;](../reports/upload-a-file-or-report-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a35-123">For more information, see Report Definitions" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  
-   <span data-ttu-id="28a35-124">独自のレポートを作成し、個人用レポートにパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="28a35-124">Create and publish your own reports to My Reports.</span></span> <span data-ttu-id="28a35-125">詳細については、「[レポート デザイン ビュー &#40;レポート ビルダー&#41;](report-design-view-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a35-125">For more information, see [Report Design View &#40;Report Builder&#41;](report-design-view-report-builder.md).</span></span>  
  
 <span data-ttu-id="28a35-126">通常、[個人用レポート] フォルダーには、ユーザー自身によるフォルダーの管理を許可する権限が設定されています。</span><span class="sxs-lookup"><span data-stu-id="28a35-126">Usually, permissions on My Reports allow you to manage the folder yourself.</span></span> <span data-ttu-id="28a35-127">ただし、最終的には、レポート サーバー管理者により、ユーザーが実行できる作業が決定されます。</span><span class="sxs-lookup"><span data-stu-id="28a35-127">However, the report server administrator ultimately determines which tasks users can perform.</span></span> <span data-ttu-id="28a35-128">権限が十分でないために [個人用レポート] フォルダーでの作業が行えない場合は、レポート サーバー管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="28a35-128">If insufficient permissions prevent you from working with My Reports, see your report server administrator.</span></span>  
  
## <a name="searching-my-reports"></a><span data-ttu-id="28a35-129">[個人用レポート] の検索</span><span class="sxs-lookup"><span data-stu-id="28a35-129">Searching My Reports</span></span>  
 <span data-ttu-id="28a35-130">レポート サーバー データベースを検索する場合、検索を行うユーザーの [個人用レポート] フォルダーのコンテンツは検索対象になりますが、他のユーザーの [個人用レポート] フォルダーのコンテンツは検索対象から除外されます。</span><span class="sxs-lookup"><span data-stu-id="28a35-130">When you search a report server database, the contents of your My Reports folder are included in the search, while the contents of other user's My Reports folders are excluded.</span></span> <span data-ttu-id="28a35-131">検索結果には、アクセス権が与えられているレポートのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="28a35-131">Search results list only the reports to which you have access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a35-132">参照</span><span class="sxs-lookup"><span data-stu-id="28a35-132">See Also</span></span>  
 [<span data-ttu-id="28a35-133">レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="28a35-133">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  

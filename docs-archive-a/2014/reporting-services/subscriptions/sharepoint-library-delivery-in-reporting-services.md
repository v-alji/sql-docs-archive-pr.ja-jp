---
title: Reporting Services での SharePoint ライブラリへの配信 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], report delivery
- delivering reports [Reporting Services]
- subscriptions [Reporting Services], SharePoint library delivery
ms.assetid: cb4e4f71-f2d5-475a-9284-ea324c93c7de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5ff109781233ca0c56db0c03ed37bdd13e6e75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739102"
---
# <a name="sharepoint-library-delivery-in-reporting-services"></a><span data-ttu-id="a2aa6-102">Reporting Services での SharePoint ライブラリへの配信</span><span class="sxs-lookup"><span data-stu-id="a2aa6-102">SharePoint Library Delivery in Reporting Services</span></span>
  <span data-ttu-id="a2aa6-103">SharePoint 統合用に構成されているレポート サーバーでは、レポートを SharePoint ライブラリに送信する配信拡張機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-103">A report server that is configured for SharePoint integration includes a delivery extension that you can use to send a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="a2aa6-104">SharePoint 配信拡張機能を使用するには、SharePoint サイトのアプリケーション ページからサブスクリプションを作成し、配信の種類を **[SharePoint ドキュメント ライブラリ]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-104">To use the SharePoint delivery extension, you must create a subscription from an application page on a SharePoint site, and then select **SharePoint document library** as the delivery type.</span></span> <span data-ttu-id="a2aa6-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] またはレポート マネージャーで作成したサブスクリプションに対して、SharePoint 配信拡張機能を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-105">You cannot use the SharePoint delivery extension for subscriptions that you create in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or Report Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2aa6-106">レポート サーバーがネイティブ モードで動作している場合、配信拡張機能では SharePoint サイトへのレポートの配信がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-106">The delivery extension does not support the delivery of reports to a SharePoint site if the report server is running in native mode.</span></span> <span data-ttu-id="a2aa6-107">ネイティブ モードのレポート サーバーに対して、プログラムから配信拡張機能を呼び出そうとすると、サーバーは `rsDeliveryExtensionNotFound` エラーを返し、レポート サーバーのログ ファイルに `rsOperationNotSupportedSharePointMode` エラーが記録されます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-107">If you attempt to call the delivery extension programmatically for a native mode report server, the server will return the `rsDeliveryExtensionNotFound` error and log the `rsOperationNotSupportedSharePointMode` error in the report server log files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2aa6-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="a2aa6-108">Requirements</span></span>  
 <span data-ttu-id="a2aa6-109">作成済みレポートをライブラリに配信するための要件を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-109">Requirements for delivering rendered reports to a library include the following:</span></span>  
  
-   <span data-ttu-id="a2aa6-110">レポート サーバーは SharePoint 統合モードに構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-110">The report server must be configured for SharePoint integration mode.</span></span>  
  
-   <span data-ttu-id="a2aa6-111">レポート サーバーに SharePoint 配信拡張機能をインストールして構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-111">The report server must have the SharePoint delivery extension installed and configured.</span></span>  
  
-   <span data-ttu-id="a2aa6-112">レポートはレポート定義 (.rdl) ファイルにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-112">The report must be a report definition (.rdl) file.</span></span> <span data-ttu-id="a2aa6-113">サブスクリプションを利用して、モデルやリソースなど、他の種類のレポート サーバー コンテンツを配信することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-113">You cannot deliver other report server content types, such as models or resources, through a subscription.</span></span> <span data-ttu-id="a2aa6-114">データ ソースとしてモデルが使用されているアドホック レポートをサブスクライブすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-114">You cannot subscribe to ad hoc reports that use models as a data source.</span></span>  
  
-   <span data-ttu-id="a2aa6-115">レポートでは保存されている資格情報を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-115">The report must use stored credentials.</span></span> <span data-ttu-id="a2aa6-116">これは、配信の種類に関係なく、レポートに対してどのようなサブスクリプションを作成する場合でも必須です。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-116">This is a prerequisite for creating any subscription on a report, regardless of the delivery type.</span></span>  
  
-   <span data-ttu-id="a2aa6-117">配信先は SharePoint ライブラリである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-117">The destination must be a SharePoint library.</span></span> <span data-ttu-id="a2aa6-118">対象ライブラリを選択する際には、同じ SharePoint サイト上のライブラリを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-118">When choosing a target library, you must choose one that is on the same SharePoint site.</span></span> <span data-ttu-id="a2aa6-119">同じサイト コレクション内の別のサーバーや別のサイト上のライブラリにレポートを配信することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-119">You cannot deliver a report to a library on another server or another site within the same site collection.</span></span>  
  
 <span data-ttu-id="a2aa6-120">プロパティおよびメタデータは、レポートの配信に含まれません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-120">Properties and metadata are not part of report delivery.</span></span> <span data-ttu-id="a2aa6-121">レポートが最初に配信されるときに、レポートが含まれているフォルダーまたはリストのセキュリティ設定がレポートに継承されます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-121">When the report is delivered for the first time, it inherits the security settings of the folder or list that contains it.</span></span> <span data-ttu-id="a2aa6-122">その後でセキュリティ設定を変更したり、レポート プロパティを設定したりしても、設定は維持されます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-122">If you subsequently modify security settings or set report properties, those settings are retained.</span></span> <span data-ttu-id="a2aa6-123">サブスクリプションでは、指定された場所に格納されているレポートのみが更新されます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-123">The subscription just refreshes the report that is stored at the specified location.</span></span>  
  
## <a name="sharepoint-permissions"></a><span data-ttu-id="a2aa6-124">SharePoint 権限</span><span class="sxs-lookup"><span data-stu-id="a2aa6-124">SharePoint Permissions</span></span>  
 <span data-ttu-id="a2aa6-125">サブスクリプションを作成するには、レポートに対する "アイテムの表示" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-125">To create the subscription, you must have View Items permission on the report.</span></span> <span data-ttu-id="a2aa6-126">レポートを配信するには、レポートの配信先のライブラリに対する "アイテムの追加" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-126">To deliver the report, you must have Add Items permission on the library to which the report is delivered.</span></span>  
  
## <a name="how-to-create-modify-and-delete-subscriptions"></a><span data-ttu-id="a2aa6-127">サブスクリプションの作成、変更、および削除を行うには</span><span class="sxs-lookup"><span data-stu-id="a2aa6-127">How to Create, Modify and Delete Subscriptions</span></span>  
  
1.  <span data-ttu-id="a2aa6-128">レポートへのアクセス元となる SharePoint サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-128">Go to the SharePoint site from which you access the report.</span></span>  
  
2.  <span data-ttu-id="a2aa6-129">レポートを選択し、レポートの横にある下向きの矢印をクリックして、 **[サブスクリプションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-129">Select the report, click the down arrow next to the report, and select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="a2aa6-130">**[作成]** 、 **[編集]** 、または **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-130">Click **Create**, **Edit**, or **Delete**.</span></span>  
  
 <span data-ttu-id="a2aa6-131">[サブスクリプションの管理] リストの状態メッセージに、サブスクリプションの現在の情報が表示されます。この情報には、サブスクリプションの状態や、サブスクリプションの最終実行日時などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-131">A Status message on the Manage Subscriptions list displays current information about the subscription, including whether it succeeded and the date and time the subscription last ran.</span></span>  
  
## <a name="setting-delivery-options"></a><span data-ttu-id="a2aa6-132">配信オプションの設定</span><span class="sxs-lookup"><span data-stu-id="a2aa6-132">Setting Delivery Options</span></span>  
 <span data-ttu-id="a2aa6-133">レポートを SharePoint ライブラリに配信するサブスクリプションには、次の配信オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-133">You can set the following delivery options on a subscription that delivers a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="a2aa6-134">[出力形式のレンダリング]</span><span class="sxs-lookup"><span data-stu-id="a2aa6-134">Render output format</span></span>  
 <span data-ttu-id="a2aa6-135">レポートの配信に使用されるアプリケーション形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-135">Specify the application format in which you want the report delivered.</span></span> <span data-ttu-id="a2aa6-136">レポートはこの形式へのレンダリング後に配信されます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-136">The report is rendered in this format before delivery.</span></span> <span data-ttu-id="a2aa6-137">選択した出力形式によって、既定のファイル拡張子が決まります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-137">The output format you select will determine the default file extension.</span></span>  
  
 <span data-ttu-id="a2aa6-138">選択できる出力形式は、レポート サーバーにインストールされている一連の表示拡張機能によって決まります。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-138">The list of output formats you can select from is the set of rendering extensions that are installed on the report server.</span></span>  
  
 <span data-ttu-id="a2aa6-139">内部での使用に限られる出力形式や、SharePoint 統合モードで実行中のレポート サーバーでサポートされない出力形式は指定できません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-139">Note that you cannot specify output formats that are for internal use only, or that are not supported for report servers that run in SharePoint integrated mode.</span></span> <span data-ttu-id="a2aa6-140">指定できない形式は、Null、RGDI、および HTMLOWC などです。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-140">These formats include Null, RGDI and HTMLOWC.</span></span>  
  
 <span data-ttu-id="a2aa6-141">ファイル名と拡張子</span><span class="sxs-lookup"><span data-stu-id="a2aa6-141">File name and extension</span></span>  
 <span data-ttu-id="a2aa6-142">対象ライブラリでレポートが表示されるときのファイル名と拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-142">Specify the file name and extension of the report as you want it to appear in the target library.</span></span> <span data-ttu-id="a2aa6-143">ファイル拡張子を指定しなければ、レポートの出力形式に基づいてレポート サーバーで拡張子が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-143">If you do not specify a file extension, the report server will create one based on the report output format.</span></span> <span data-ttu-id="a2aa6-144">この値は必須です。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-144">This value is required.</span></span> <span data-ttu-id="a2aa6-145">ファイル名に使用できない文字は、: \ / \* ? " < > | # { } % です。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-145">The file name must not include the following characters: : \ / \* ?</span></span> <span data-ttu-id="a2aa6-146">" \< > | # { } %</span><span class="sxs-lookup"><span data-stu-id="a2aa6-146">" \< > | # { } %</span></span>  
  
 <span data-ttu-id="a2aa6-147">タイトル</span><span class="sxs-lookup"><span data-stu-id="a2aa6-147">Title</span></span>  
 <span data-ttu-id="a2aa6-148">対象ライブラリ内のレポートの `Title` プロパティ (オプション) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-148">Specifies an optional `Title` property for the report in the target library.</span></span> <span data-ttu-id="a2aa6-149">これは、ライブラリに格納されているすべてのアイテムに対する標準プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-149">This is a standard property for all items stored in a library.</span></span> <span data-ttu-id="a2aa6-150">ユーザーは、SharePoint サイトでライブラリ コンテンツを表示するときに、このプロパティを表示するか非表示にするかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-150">Users can specify whether to show or hide this property when viewing library contents on a SharePoint site.</span></span>  
  
 <span data-ttu-id="a2aa6-151">Path</span><span class="sxs-lookup"><span data-stu-id="a2aa6-151">Path</span></span>  
 <span data-ttu-id="a2aa6-152">SharePoint ライブラリへの完全修飾 URL (SharePoint Web アプリケーションおよびサイトを含む) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-152">Specifies a fully qualified URL to the SharePoint library, including the SharePoint Web application and site.</span></span> <span data-ttu-id="a2aa6-153">たとえば、 <http://mySharePointWeb/MySite/MyDocLib> " <http://mySharePointWeb> " は Web アプリケーションを示し、"個人用サイト" は sharepoint サイト、"MyDocLib" はレポートが配信される sharepoint ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-153">For example: <http://mySharePointWeb/MySite/MyDocLib>; where "<http://mySharePointWeb>" indicates the Web application, "MySite" is the SharePoint site, and "MyDocLib" is the SharePoint library where the report will be delivered.</span></span>  
  
 <span data-ttu-id="a2aa6-154">ページ、サイト、またはリストを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-154">You cannot specify a page, site, or list.</span></span> <span data-ttu-id="a2aa6-155">対象コンテナーは、同じサイトまたはファームにあるライブラリであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-155">The target container must be a library in the same site or farm.</span></span>  
  
 <span data-ttu-id="a2aa6-156">[上書きのオプション]</span><span class="sxs-lookup"><span data-stu-id="a2aa6-156">Overwrite options</span></span>  
 <span data-ttu-id="a2aa6-157">同じファイル名と拡張子を持つファイルは、サブスクリプションの処理時に新しい方のバージョンに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-157">Specifies whether a file with the same name and extension is replaced by a newer version when the subscription is processed.</span></span> <span data-ttu-id="a2aa6-158">既存のファイルを新しいバージョンに置き換える場合、 **[上書き]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-158">Choose **Overwrite** if you want to replace an existing file with a newer version.</span></span> <span data-ttu-id="a2aa6-159">サブスクリプションでファイルを置き換えない場合には、 **[なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-159">Choose **None** if you do not want the subscription to replace a file.</span></span> <span data-ttu-id="a2aa6-160">この場合、対象ファイルと名前と拡張子が同じであるファイルが存在すると、配信が実行されません。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-160">In this case, no delivery will occur if a file exists with the target name and extension.</span></span> <span data-ttu-id="a2aa6-161">ファイル名の末尾に数値を付加して、同じファイルの連続するバージョンを追加する場合は、 **[自動増分]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-161">Choose **Autoincrement** if you want to add successive versions of the same file by appending a number at the end of the file name.</span></span>  
  
 <span data-ttu-id="a2aa6-162">[自動コピー]</span><span class="sxs-lookup"><span data-stu-id="a2aa6-162">Autocopy</span></span>  
 <span data-ttu-id="a2aa6-163">[自動コピー] 機能を使用して、最新バージョンのファイルを複数の場所に自動コピーする場合、 **[上書き]** が有効な場合にのみファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-163">If you are using the Autocopy feature to automatically copy the latest version of a file to multiple locations, the file will be copied if **Overwrite** is enabled.</span></span> <span data-ttu-id="a2aa6-164">**Autoincrement**または**None**を使用した場合、配信は失敗し、エラーが `rsDeliveryError` 発生します。</span><span class="sxs-lookup"><span data-stu-id="a2aa6-164">If you used **Autoincrement** or **None**, the delivery will fail and the `rsDeliveryError` error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2aa6-165">参照</span><span class="sxs-lookup"><span data-stu-id="a2aa6-165">See Also</span></span>  
 <span data-ttu-id="a2aa6-166">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="a2aa6-166">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="a2aa6-167">[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2aa6-167">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="a2aa6-168">レポート データ ソースに関する資格情報と接続情報を指定する</span><span class="sxs-lookup"><span data-stu-id="a2aa6-168">Specify Credential and Connection Information for Report Data Sources</span></span>](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  

---
title: サーバーの全体管理で PowerPivot サイト用の信頼できる場所を作成する |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70b1317db7ce413f3a593056f3b8a140b3bdc446
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643535"
---
# <a name="create-a-trusted-location-for-powerpivot-sites-in-central-administration"></a><span data-ttu-id="73e61-102">サーバーの全体管理での PowerPivot サイト用の信頼できる場所の作成</span><span class="sxs-lookup"><span data-stu-id="73e61-102">Create a trusted location for PowerPivot sites in Central Administration</span></span>
  <span data-ttu-id="73e61-103">Excel Services では、SharePoint サーバーで開いたブックの有効なリポジトリの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="73e61-103">Excel Services lets you specify which locations are valid repositories for workbooks that you open on a SharePoint server.</span></span> <span data-ttu-id="73e61-104">これは「信頼できる場所」と呼ばれ、作成したそれぞれの信頼できる場所について異なる構成設定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="73e61-104">These locations are called 'trusted locations', and you can use different configuration settings for each trusted location you create.</span></span> <span data-ttu-id="73e61-105">PowerPivot for SharePoint の配置の場合、PowerPivot ブックが含まれるサイト用に信頼できる場所を作成し、ファームのその他の部分に対する既定値を保持しながら PowerPivot データ アクセスに対しては最適な設定を適用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="73e61-105">For a deployment of PowerPivot for SharePoint, you might consider creating a trusted location for sites that contain PowerPivot workbooks so that you can apply the settings that work best for PowerPivot data access, while preserving default settings for the rest of the farm.</span></span>  
  
  
  
## <a name="prerequisites"></a><span data-ttu-id="73e61-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="73e61-106">Prerequisites</span></span>  
 <span data-ttu-id="73e61-107">URL を信頼できる場所として指定するには、ファームまたはサービスの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="73e61-107">You must be a farm or service administrator to designate a URL as a trusted location.</span></span>  
  
 <span data-ttu-id="73e61-108">PowerPivot ギャラリー、またはブックが保存されている他のライブラリが含まれる SharePoint サイトの URL アドレスがわかっていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="73e61-108">You must know the URL address of the SharePoint site that contains the PowerPivot Gallery or other library that stores your workbooks.</span></span> <span data-ttu-id="73e61-109">アドレスを取得するには、ライブラリが含まれているサイトを開き、[ **PowerPivot ギャラリー**] を右クリックします。次に、[**プロパティ**] を選択し、サーバー名とサイトパスを含むアドレス (URL) の最初の部分をコピーします。</span><span class="sxs-lookup"><span data-stu-id="73e61-109">To get the address, open the site that contains the library, right-click **PowerPivot Gallery**, select **Properties**, and then copy the first part of the Address (URL) that contains the server name and site path.</span></span>  
  
##  <a name="overview"></a><a name="overview"></a> <span data-ttu-id="73e61-110">概要</span><span class="sxs-lookup"><span data-stu-id="73e61-110">Overview</span></span>  
 <span data-ttu-id="73e61-111">Excel Services の最初のインストールでは、'http://' が信頼できる場所として指定されます。このため、ファームのどのサイトからアクセスしたブックもサーバーで開くことができます。</span><span class="sxs-lookup"><span data-stu-id="73e61-111">An initial installation of Excel Services specifies 'http://' as its trusted location, which means that workbooks from any site in the farm can be opened on the server.</span></span> <span data-ttu-id="73e61-112">信頼できると見なされる場所の制御を厳しくする必要がある場合は、ファームの特定のサイトにマップする信頼できる場所を新しく作成し、各場所の設定とアクセス許可を変更します。</span><span class="sxs-lookup"><span data-stu-id="73e61-112">If you require tighter control over which locations are considered trustworthy, you can create new trusted locations that map to specific sites in your farm, and then vary the settings and permissions for each one.</span></span>  
  
 <span data-ttu-id="73e61-113">PowerPivot ブックをホストするサイト用に新しい信頼できる場所を作成すると、ファームのその他の部分に対する既定値を保持しながら PowerPivot データ アクセスに対しては最適な別の設定を適用する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="73e61-113">Creating a new trusted location for sites that host PowerPivot workbooks is especially useful if you want to preserve default values for the rest of the farm, while applying different settings that work best for PowerPivot data access.</span></span> <span data-ttu-id="73e61-114">たとえば、PowerPivot ブック用に最適化された信頼できる場所で最大ブック サイズを 50 MB にし、ファームの残りで既定値の 10 MB を使用するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="73e61-114">For example, a trusted location that is optimized for PowerPivot workbooks could have a maximum workbook size of 50 MB, while the rest of the farm uses the default value of 10MB.</span></span>  
  
 <span data-ttu-id="73e61-115">PowerPivot ギャラリー ライブラリを使用してパブリッシュ済みのブックをプレビューする場合に、予想したプレビュー イメージの代わりにデータ更新の警告が表示されるときは、信頼できる場所を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73e61-115">Creating a trusted location is recommended if you are using PowerPivot Gallery libraries to preview published workbooks and you encounter data refresh warnings instead of the preview image you expect.</span></span> <span data-ttu-id="73e61-116">PowerPivot ギャラリーは、ドキュメント内のデータおよび表示情報を使用して、レポートとブックのサムネイル画像を表示します。</span><span class="sxs-lookup"><span data-stu-id="73e61-116">PowerPivot Gallery renders thumbnail images of reports and workbooks using data and presentation information within the document.</span></span> <span data-ttu-id="73e61-117">信頼できる場所で [データ更新に関する警告を表示する] が有効である場合は、PowerPivot ギャラリーに更新を実行するための十分な権限がなく、その結果、サムネイル画像の代わりにエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="73e61-117">If Warn on Data Refresh is enabled for a trusted location, PowerPivot Gallery might not have sufficient permissions to perform the refresh, causing an error to appear instead of the thumbnail image.</span></span> <span data-ttu-id="73e61-118">PowerPivot ギャラリーを新しい信頼できる場所に持つサイトを追加すると、この問題は解消できます。</span><span class="sxs-lookup"><span data-stu-id="73e61-118">Adding a site that contains PowerPivot Gallery as a new trusted location can eliminate this problem.</span></span>  
  
##  <a name="create-a-trusted-location-for-powerpivot-data-access"></a><a name="create"></a><span data-ttu-id="73e61-119">PowerPivot データアクセス用の信頼できる場所を作成する</span><span class="sxs-lookup"><span data-stu-id="73e61-119">Create a Trusted Location for PowerPivot Data Access</span></span>  
  
1.  <span data-ttu-id="73e61-120">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73e61-120">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="73e61-121">Excel Services サービス アプリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="73e61-121">Click the Excel Services Service Application.</span></span>  
  
3.  <span data-ttu-id="73e61-122">**[信頼できるファイル保存場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73e61-122">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="73e61-123">**[信頼できるファイル保存場所の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73e61-123">Click **Add Trusted File Location**.</span></span>  
  
5.  <span data-ttu-id="73e61-124">PowerPivot ギャラリー ライブラリがあるサイトの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="73e61-124">Enter the URL of a site that contains a PowerPivot Gallery library.</span></span>  
  
6.  <span data-ttu-id="73e61-125">[場所の種類] で、 **[Microsoft SharePoint Foundation]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="73e61-125">In Location Type, select **Microsoft SharePoint Foundation**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="73e61-126">UNC および HTTP の場所の種類は PowerPivot データ アクセスではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="73e61-126">UNC and HTTP location types are not supported for PowerPivot data access.</span></span>  
  
7.  <span data-ttu-id="73e61-127">[セッションの管理]、[ブックのプロパティ]、および [計算動作] のプロパティの既定の設定をすべてそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="73e61-127">Accept all of the default settings for properties in Session Management, Workbook Properties, and Calculation Behavior.</span></span>  
  
8.  <span data-ttu-id="73e61-128">[ブックのプロパティ] で、 **[ブックの最大サイズ]** を「 **50**」に設定します。</span><span class="sxs-lookup"><span data-stu-id="73e61-128">In Workbook Properties, set **Maximum Workbook Size** to **50**.</span></span> <span data-ttu-id="73e61-129">これにより、ブックのファイル サイズの上限が、親 Web アプリケーションへのファイル アップロードの上限と同じになります。</span><span class="sxs-lookup"><span data-stu-id="73e61-129">This aligns the upper limit for workbook file size to the upper limit for file uploads to the parent web application.</span></span> <span data-ttu-id="73e61-130">ブックのサイズが 50 MB を超える場合は、ファイル サイズの上限をさらに増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="73e61-130">If your workbooks are larger than 50 megabytes, you must further increase the file size limit.</span></span> <span data-ttu-id="73e61-131">詳細については、「 [PowerPivot for SharePoint&#41;&#40;最大ファイルアップロードサイズを構成する](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73e61-131">For more information, see [Configure Maximum File Upload Size &#40;PowerPivot for SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).</span></span>  
  
9. <span data-ttu-id="73e61-132">[外部データ] で、[外部データの許可] が **[信頼できるデータ接続ライブラリと、埋め込まれている接続]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="73e61-132">In External Data, verify that Allow External Data is set to **Trusted data connection libraries and embedded**.</span></span> <span data-ttu-id="73e61-133">この設定は、ブックでの PowerPivot データ アクセスに必要です。</span><span class="sxs-lookup"><span data-stu-id="73e61-133">This setting is required for PowerPivot data access in a workbook.</span></span>  
  
10. <span data-ttu-id="73e61-134">また、[外部データ] の [更新時の警告] で、 **[更新時の警告の有効化]** のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="73e61-134">Also in External Data, for Warn on Refresh, clear the checkbox for **Refresh warning enabled**.</span></span> <span data-ttu-id="73e61-135">このチェック ボックスをオフにすると、PowerPivot ギャラリーで、定型の警告メッセージの代わりにブックのプレビュー イメージが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="73e61-135">Clearing the checkbox allows PowerPivot Gallery to bypass routine warning messages and show preview images of a workbook instead.</span></span>  
  
11. <span data-ttu-id="73e61-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73e61-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e61-137">参照</span><span class="sxs-lookup"><span data-stu-id="73e61-137">See Also</span></span>  
 [<span data-ttu-id="73e61-138">PowerPivot ギャラリー</span><span class="sxs-lookup"><span data-stu-id="73e61-138">PowerPivot Gallery</span></span>](../../index.yml)  
 <span data-ttu-id="73e61-139">[PowerPivot ギャラリーの作成とカスタマイズ](create-and-customize-power-pivot-gallery.md) </span><span class="sxs-lookup"><span data-stu-id="73e61-139">[Create and Customize PowerPivot Gallery](create-and-customize-power-pivot-gallery.md) </span></span>  
 [<span data-ttu-id="73e61-140">PowerPivot ギャラリーの使用</span><span class="sxs-lookup"><span data-stu-id="73e61-140">Use PowerPivot Gallery</span></span>](use-power-pivot-gallery.md)  
  
  

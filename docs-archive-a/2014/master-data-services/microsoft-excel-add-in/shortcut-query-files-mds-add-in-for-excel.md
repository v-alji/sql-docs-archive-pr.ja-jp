---
title: ショートカット クエリ ファイル (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe1bdbdadabe0e6448ed3bdc65316104fb26ba43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714469"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a><span data-ttu-id="2639f-102">ショートカット クエリ ファイル (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="2639f-102">Shortcut Query Files (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="2639f-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、よく使用するデータにすばやく接続して読み込むために、ショートカット クエリ ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="2639f-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use shortcut query files to quickly connect and load frequently-used data.</span></span> <span data-ttu-id="2639f-104">MDS データを他のユーザーと共有する場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2639f-104">You can also use them when you want to share MDS data with others.</span></span> <span data-ttu-id="2639f-105">ワークシートを保存して電子メールで送信する代わりに、ショートカット クエリ ファイルを保存して電子メールで送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2639f-105">Instead of saving the worksheet and emailing it, you should save a shortcut query file and email that instead.</span></span> <span data-ttu-id="2639f-106">これにより、両者が MDS リポジトリに接続して最新のデータを取得するようになります。</span><span class="sxs-lookup"><span data-stu-id="2639f-106">This ensures that you are both connecting to the MDS repository to get the latest data.</span></span>  
  
 <span data-ttu-id="2639f-107">ショートカット クエリ ファイルは、次の情報を含む XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="2639f-107">Shortcut query files are XML files that contain information about:</span></span>  
  
-   <span data-ttu-id="2639f-108">MDS リポジトリ接続。</span><span class="sxs-lookup"><span data-stu-id="2639f-108">The MDS repository connection.</span></span>  
  
-   <span data-ttu-id="2639f-109">モデル、バージョン、およびエンティティ。</span><span class="sxs-lookup"><span data-stu-id="2639f-109">The model, version, and entity.</span></span>  
  
-   <span data-ttu-id="2639f-110">ショートカットが作成されたときに適用されたフィルター。</span><span class="sxs-lookup"><span data-stu-id="2639f-110">Any filters that were applied when the shortcut was created.</span></span>  
  
-   <span data-ttu-id="2639f-111">ショートカットが作成されたときの列の順序 (左から右)。</span><span class="sxs-lookup"><span data-stu-id="2639f-111">The left-to-right order of the columns when the shortcut was created.</span></span>  
  
 <span data-ttu-id="2639f-112">リストにこれらのファイルを保存し、アドインを開くときにその中から選択できます。</span><span class="sxs-lookup"><span data-stu-id="2639f-112">You can save these files in a list and choose from them when you open the Add-in.</span></span> <span data-ttu-id="2639f-113">コンピューターまたは共有の場所にエクスポートするか、他のユーザーに送信することができます。</span><span class="sxs-lookup"><span data-stu-id="2639f-113">You can export them to your computer or to a shared location, or you can send them to others.</span></span>  
  
## <a name="queryopener-application"></a><span data-ttu-id="2639f-114">QueryOpener アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2639f-114">QueryOpener Application</span></span>  
 <span data-ttu-id="2639f-115">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] をインストールすると、QueryOpener というアプリケーションが必ずインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2639f-115">All users who install the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] have an application called QueryOpener installed.</span></span> <span data-ttu-id="2639f-116">このアプリケーションを使用して、 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]でショートカット クエリ ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2639f-116">This application is used to open shortcut query files in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)].</span></span> <span data-ttu-id="2639f-117">ショートカット クエリ ファイルをダブルクリックすると、このアプリケーションが自動的に使用され、アドインでファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="2639f-117">If you double-click a shortcut query file, this application is automatically used to open the file in the Add-in.</span></span>  
  
 <span data-ttu-id="2639f-118">このアプリケーションでショートカット クエリ ファイルを開くときに、接続を "安全な" 接続にするように求めるメッセージが表示されます。これは、この場所からの内容を信頼することを意味します。</span><span class="sxs-lookup"><span data-stu-id="2639f-118">When you open a shortcut query file with this application, you are prompted to make the connection a "safe" connection, which means you trust content from this location.</span></span> <span data-ttu-id="2639f-119">接続を安全としてマークするたびに、接続がリストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2639f-119">Each time you mark a connection as safe, it is added to a list.</span></span> <span data-ttu-id="2639f-120">このリストをクリアする場合は、 **[設定]** ダイアログ ボックスを開き、 **[セーフ リストに追加されたサーバー]** セクションで **[すべてクリア]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2639f-120">If you want to clear this list, open the **Settings** dialog box and in the **Servers Added to Safe List** section, click **Clear All**.</span></span>  
  
 <span data-ttu-id="2639f-121">アプリケーションの既定の場所は、*ドライブ*:、Services\Excel、および Master Data Add-In\Microsoft.MasterDataServices.QueryOpener.exe です。</span><span class="sxs-lookup"><span data-stu-id="2639f-121">The default location for the application is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.</span></span>  
  
 <span data-ttu-id="2639f-122">ショートカット クエリ ファイルを開く方法には、ファイルをインポートする方法と、ダブルクリックして自動的に開くようにする方法の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="2639f-122">There are two ways to open shortcut query files: you can import them or you can double-click them and they are opened automatically.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2639f-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="2639f-123">Related Tasks</span></span>  
  
|<span data-ttu-id="2639f-124">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="2639f-124">Task Description</span></span>|<span data-ttu-id="2639f-125">トピック</span><span class="sxs-lookup"><span data-stu-id="2639f-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="2639f-126">アクティブなワークシートの内容をショートカット クエリ ファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="2639f-126">Save the contents of the active worksheet as a shortcut query file.</span></span>|[<span data-ttu-id="2639f-127">ショートカット クエリ ファイルの保存 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="2639f-127">Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|<span data-ttu-id="2639f-128">アクティブなワークシートの内容を表すショートカット クエリ ファイルを電子メールで送信します。</span><span class="sxs-lookup"><span data-stu-id="2639f-128">Email a shortcut query file that represents the contents of the active worksheet.</span></span>|[<span data-ttu-id="2639f-129">ショートカット クエリ ファイルの電子メールでの送信 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="2639f-129">Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="2639f-130">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="2639f-130">Related Content</span></span>  
  
-   [<span data-ttu-id="2639f-131">接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="2639f-131">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="2639f-132">Microsoft Excel 用マスター データ サービス アドイン</span><span class="sxs-lookup"><span data-stu-id="2639f-132">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="2639f-133">セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2639f-133">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  

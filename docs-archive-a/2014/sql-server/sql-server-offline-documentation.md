---
title: SQL Server 2014 のオフラインドキュメント
description: SQL Server 2014 のオフラインドキュメントをインストールする方法について説明します。 オフライン コンテンツを表示するには、SQL Server Management Studio (SSMS) を使用します。
ms.prod: sql
ms.technology: install
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.date: 07/19/2020
ms.openlocfilehash: bfd4adc658a203f8e2d22ef77ce0381084e36363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640335"
---
# <a name="install-sql-server-2014-offline-documentation"></a><span data-ttu-id="0ce15-104">SQL Server 2014 オフラインドキュメントをインストールする</span><span class="sxs-lookup"><span data-stu-id="0ce15-104">Install SQL Server 2014 offline documentation</span></span>

<span data-ttu-id="0ce15-105">この記事では、オフラインの SQL Server 2014 コンテンツをダウンロードして表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-105">This article describes how to download and view offline SQL Server 2014 content.</span></span> <span data-ttu-id="0ce15-106">オフライン コンテンツを使用すると、インターネットに接続しなくてもドキュメントにアクセスできます (ただし、ダウンロードするにはインターネット接続が必要です)。</span><span class="sxs-lookup"><span data-stu-id="0ce15-106">Offline content enables you to access the documentation without an internet connection (although an internet connection is initially required to download it).</span></span>

<span data-ttu-id="0ce15-107">この手法では、SQL Server Management Studio (SSMS) の [**ヘルプ**] メニューを使用して、ヘルプビューアーユーティリティ (HlpViewer.exe) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0ce15-107">The technique involves using the **Help** menu of SQL Server Management Studio (SSMS), to access the Help Viewer utility (HlpViewer.exe).</span></span>

<span data-ttu-id="0ce15-108">オフラインドキュメントは、2012-2019 の範囲の SQL Server のバージョンで利用でき、場合によっては以降のバージョンでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-108">Offline documentation is available for versions of SQL Server in the range of 2012-2019, and perhaps for additional later versions too.</span></span> <span data-ttu-id="0ce15-109">[以前のバージョンのコンテンツをオンラインで](https://docs.microsoft.com/previous-versions/sql/)表示することができますが、オフライン オプションを使用すると、以前のコンテンツに簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-109">Although you can view content for [previous versions online](https://docs.microsoft.com/previous-versions/sql/), an offline option provides a convenient way to access the older content.</span></span>

- [<span data-ttu-id="0ce15-110">SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="0ce15-110">SQL Server 2014</span></span>](#sql-server-2014-offline-content)
- [<span data-ttu-id="0ce15-111">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="0ce15-111">SQL Server 2012</span></span>](#sql-server-2012-offline-content)

<span data-ttu-id="0ce15-112">SQL Server 2016 以降のバージョンについては、バージョン固有のドキュメントを参照して、これらのバージョンがオフラインドキュメントを処理する方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-112">For SQL Server 2016 and later versions, see their version-specific documentation to learn how those versions handle their offline documentation.</span></span>

## <a name="sql-server-2014-offline-content"></a><span data-ttu-id="0ce15-113">SQL Server 2014 オフライン コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0ce15-113">SQL Server 2014 offline content</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ce15-114">SQL 2014 Transact-SQL コンテンツは、オフラインでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-114">SQL 2014 Transact-SQL content is only available offline.</span></span>

<span data-ttu-id="0ce15-115">次の手順では、SQL Server 2014 のオフライン コンテンツを読み込む方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="0ce15-115">The following steps explain how to load offline content for SQL Server 2014.</span></span>

1. <span data-ttu-id="0ce15-116">「[ファイアウォールとプロキシで制限された環境向けの Microsoft SQL Server 2014 の製品ドキュメント](https://www.microsoft.com/download/details.aspx?id=42557)」をダウンロード センターからダウンロードし、フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-116">Download the [Product Documentation for Microsoft SQL Server 2014 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=42557) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="0ce15-117">ファイルを解凍して、 *msha*ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-117">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2014 ヘルプ ドキュメントのセットアップ ファイル](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. <span data-ttu-id="0ce15-119">SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-119">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="0ce15-121">ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-121">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="0ce15-122">最新のヘルプ コンテンツをインストールするには、[インストール元] で **[ディスク]** を選択し、省略記号 (...) を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-122">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![ヘルプ ビューアーの [コンテンツの管理] のディスクのインストール元](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="0ce15-124">[コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-124">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="0ce15-125">場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-125">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="0ce15-126">ローカル ストア パスの変更後、ヘルプのインストールに失敗した場合、ヘルプ ビューアーを閉じ、再び開いてください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-126">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="0ce15-127">新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-127">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="0ce15-128">コンテンツを解凍したフォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-128">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="0ce15-129">フォルダーで **HelpContentSetup.msha** ファイルを選択し、 **[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-129">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![SQL Server 2014 の Help Content Setup.msha ファイルを開く](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. <span data-ttu-id="0ce15-131">検索バーに「*sql server 2014*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-131">Type in *sql server 2014* in the search bar.</span></span> <span data-ttu-id="0ce15-132">入手できる 2014 のコンテンツが表示されたら、ヘルプ ビューアーにインストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、 **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-132">Once you see the 2014 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![ヘルプ ビューアーでの SQL Server 2014 ブックの検索](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![ヘルプ ビューアーでの SQL Server 2014 ブックの追加と更新](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="0ce15-135">コンテンツの追加中にヘルプビューアーがフリーズ (ハング) した場合は、 \<mm/dd/yyyy> HlpViewer_SSMSx_en%localappdata%\microsoft\helpviewer2.x\ ファイルまたは HlpViewer_VisualStudiox_en-us. 設定ファイルのキャッシュ LastRefreshed = "00:00:00" 行を将来の日付に変更します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-135">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="0ce15-136">この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-136">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="0ce15-137">SQL Server 2014 のコンテンツがインストールされたことを確認するには、左側のコンテンツ ペインで「*sql server 2014*」を検索します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-137">You can verify that the SQL Server 2014 content installed by searching under the content pane on the left for *sql server 2014*.</span></span>

   ![自動的に更新された SQL Server 2014 ブック](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a><span data-ttu-id="0ce15-139">SQL Server 2012 オフライン コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0ce15-139">SQL Server 2012 offline content</span></span>

<span data-ttu-id="0ce15-140">次の手順では、SQL Server 2012 のオフライン コンテンツを読み込む方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="0ce15-140">The following steps explain how to load offline content for SQL Server 2012</span></span>

1. <span data-ttu-id="0ce15-141">「[ファイアウォールとプロキシで制限された環境向けの Microsoft SQL Server 2012 の製品ドキュメント](https://www.microsoft.com/download/details.aspx?id=35750)」をダウンロード センターからダウンロードし、フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-141">Download the [Product Documentation for Microsoft SQL Server 2012 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=35750) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="0ce15-142">ファイルを解凍して、 *msha*ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-142">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2012 のヘルプ コンテンツ セットアップ ファイル](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. <span data-ttu-id="0ce15-144">SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-144">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="0ce15-146">ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-146">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="0ce15-147">最新のヘルプ コンテンツをインストールするには、[インストール元] で **[ディスク]** を選択し、省略記号 (...) を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-147">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![ヘルプ ビューアーの [コンテンツの管理] のディスクのインストール元](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="0ce15-149">[コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-149">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="0ce15-150">場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-150">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="0ce15-151">ローカル ストア パスの変更後、ヘルプのインストールに失敗した場合、ヘルプ ビューアーを閉じ、再び開いてください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-151">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="0ce15-152">新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-152">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="0ce15-153">コンテンツを解凍したフォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-153">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="0ce15-154">フォルダーで **HelpContentSetup.msha** ファイルを選択し、 **[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-154">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![SQL Server 2012 の Help Content Setup.msha ファイルを開く](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. <span data-ttu-id="0ce15-156">検索バーに「*sql server 2012*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-156">Type in *sql server 2012* in the search bar.</span></span> <span data-ttu-id="0ce15-157">入手できる 2012 のコンテンツが表示されたら、ヘルプ ビューアーにインストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、 **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-157">Once you see the 2012 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![ヘルプ ビューアーでの SQL Server 2012 ブックの検索](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![ヘルプ ビューアーでの SQL Server 2012 ブックの追加と更新](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="0ce15-160">コンテンツの追加中にヘルプビューアーがフリーズ (ハング) した場合は、 \<mm/dd/yyyy> HlpViewer_SSMSx_en%localappdata%\microsoft\helpviewer2.x\ ファイルまたは HlpViewer_VisualStudiox_en-us. 設定ファイルのキャッシュ LastRefreshed = "00:00:00" 行を将来の日付に変更します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-160">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="0ce15-161">この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ce15-161">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="0ce15-162">SQL Server 2012 のコンテンツが読み込まれたことを確認するには、左側のコンテンツ ペインで「*sql server 2012*」を検索します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-162">You can verify that the SQL Server 2012 content is loaded by searching under the content pane on the left for *sql server 2012*.</span></span>

   ![自動的に更新された SQL Server 2012 ドキュメント](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a><span data-ttu-id="0ce15-164">オフライン ドキュメントを表示する</span><span class="sxs-lookup"><span data-stu-id="0ce15-164">View offline documentation</span></span>

<span data-ttu-id="0ce15-165">SQL Server Management Studio (SSMS) の最新バージョンの [**ヘルプ**] メニューを使用して、SQL Server ヘルプコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-165">You can view SQL Server help content using the **HELP** menu in the latest version of SQL Server Management Studio (SSMS).</span></span>

### <a name="view-offline-help-content-in-ssms"></a><span data-ttu-id="0ce15-166">SSMS でオフライン ヘルプ コンテンツを表示する</span><span class="sxs-lookup"><span data-stu-id="0ce15-166">View offline help content in SSMS</span></span>

<span data-ttu-id="0ce15-167">インストールされているヘルプを SSMS で表示するには、[ヘルプ] メニューから **[ヘルプ ビューアーで起動]** を選択してヘルプ ビューアーを起動します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-167">To view the installed help in SSMS, select **Launch in Help Viewer** from the Help menu, to launch the Help Viewer.</span></span>

   ![ヘルプ ビューアーで起動](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

<span data-ttu-id="0ce15-169">ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。このタブの左側のペインにインストールされたヘルプの目次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-169">Help Viewer opens to the Manage Content tab, with the installed help table of contents in the left pane.</span></span> <span data-ttu-id="0ce15-170">目次内の記事を選択すると、右側のペインに該当するトピックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ce15-170">select articles in the table of contents to display them in the right pane.</span></span>

> [!Important]
> <span data-ttu-id="0ce15-171">コンテンツ ペインが表示されない場合は、左余白の [コンテンツ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ce15-171">If the contents pane is not visible, select Contents on the left margin.</span></span> <span data-ttu-id="0ce15-172">プッシュピン アイコンを選択すると、コンテンツ ペインは開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="0ce15-172">select the pushpin icon to keep the contents pane open.</span></span>  

   ![コンテンツが表示されたヘルプ ビューアー](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)

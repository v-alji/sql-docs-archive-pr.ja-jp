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
# <a name="install-sql-server-2014-offline-documentation"></a>SQL Server 2014 オフラインドキュメントをインストールする

この記事では、オフラインの SQL Server 2014 コンテンツをダウンロードして表示する方法について説明します。 オフライン コンテンツを使用すると、インターネットに接続しなくてもドキュメントにアクセスできます (ただし、ダウンロードするにはインターネット接続が必要です)。

この手法では、SQL Server Management Studio (SSMS) の [**ヘルプ**] メニューを使用して、ヘルプビューアーユーティリティ (HlpViewer.exe) にアクセスします。

オフラインドキュメントは、2012-2019 の範囲の SQL Server のバージョンで利用でき、場合によっては以降のバージョンでも使用できます。 [以前のバージョンのコンテンツをオンラインで](https://docs.microsoft.com/previous-versions/sql/)表示することができますが、オフライン オプションを使用すると、以前のコンテンツに簡単にアクセスできます。

- [SQL Server 2014](#sql-server-2014-offline-content)
- [SQL Server 2012](#sql-server-2012-offline-content)

SQL Server 2016 以降のバージョンについては、バージョン固有のドキュメントを参照して、これらのバージョンがオフラインドキュメントを処理する方法を確認してください。

## <a name="sql-server-2014-offline-content"></a>SQL Server 2014 オフライン コンテンツ

> [!IMPORTANT]
> SQL 2014 Transact-SQL コンテンツは、オフラインでのみ利用できます。

次の手順では、SQL Server 2014 のオフライン コンテンツを読み込む方法について説明しています。

1. 「[ファイアウォールとプロキシで制限された環境向けの Microsoft SQL Server 2014 の製品ドキュメント](https://www.microsoft.com/download/details.aspx?id=42557)」をダウンロード センターからダウンロードし、フォルダーに保存します。

2. ファイルを解凍して、 *msha*ファイルを表示します。

   ![SQL Server 2014 ヘルプ ドキュメントのセットアップ ファイル](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

4. 最新のヘルプ コンテンツをインストールするには、[インストール元] で **[ディスク]** を選択し、省略記号 (...) を選択します。

   ![ヘルプ ビューアーの [コンテンツの管理] のディスクのインストール元](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツの場所が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。
   ローカル ストア パスの変更後、ヘルプのインストールに失敗した場合、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

5. コンテンツを解凍したフォルダーを見つけます。 フォルダーで **HelpContentSetup.msha** ファイルを選択し、 **[開く]** を選択します。

   ![SQL Server 2014 の Help Content Setup.msha ファイルを開く](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. 検索バーに「*sql server 2014*」と入力します。 入手できる 2014 のコンテンツが表示されたら、ヘルプ ビューアーにインストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、 **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2014 ブックの検索](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![ヘルプ ビューアーでの SQL Server 2014 ブックの追加と更新](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > コンテンツの追加中にヘルプビューアーがフリーズ (ハング) した場合は、 \<mm/dd/yyyy> HlpViewer_SSMSx_en%localappdata%\microsoft\helpviewer2.x\ ファイルまたは HlpViewer_VisualStudiox_en-us. 設定ファイルのキャッシュ LastRefreshed = "00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

7. SQL Server 2014 のコンテンツがインストールされたことを確認するには、左側のコンテンツ ペインで「*sql server 2014*」を検索します。

   ![自動的に更新された SQL Server 2014 ブック](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a>SQL Server 2012 オフライン コンテンツ

次の手順では、SQL Server 2012 のオフライン コンテンツを読み込む方法について説明しています。

1. 「[ファイアウォールとプロキシで制限された環境向けの Microsoft SQL Server 2012 の製品ドキュメント](https://www.microsoft.com/download/details.aspx?id=35750)」をダウンロード センターからダウンロードし、フォルダーに保存します。

2. ファイルを解凍して、 *msha*ファイルを表示します。

   ![SQL Server 2012 のヘルプ コンテンツ セットアップ ファイル](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. SSMS で、[ヘルプ] メニューの **[ヘルプ コンテンツの追加と削除]** を選択します。

   ![ヘルプ ビューアーの [ヘルプ コンテンツの追加と削除]](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

4. 最新のヘルプ コンテンツをインストールするには、[インストール元] で **[ディスク]** を選択し、省略記号 (...) を選択します。

   ![ヘルプ ビューアーの [コンテンツの管理] のディスクのインストール元](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツの場所が表示されます。 場所を変更するには、 **[移動]** を選択し、 **[宛先]** に別のフォルダー パスを入力し、 **[OK]** を選択します。
   ローカル ストア パスの変更後、ヘルプのインストールに失敗した場合、ヘルプ ビューアーを閉じ、再び開いてください。 新しい場所がローカル ストア パスに表示されることを確認し、インストールをもう一度試してください。

5. コンテンツを解凍したフォルダーを見つけます。 フォルダーで **HelpContentSetup.msha** ファイルを選択し、 **[開く]** を選択します。

   ![SQL Server 2012 の Help Content Setup.msha ファイルを開く](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. 検索バーに「*sql server 2012*」と入力します。 入手できる 2012 のコンテンツが表示されたら、ヘルプ ビューアーにインストールする各コンテンツ パッケージ (ブック) の横にある **[追加]** を選択し、 **[更新]** を選択します。

   ![ヘルプ ビューアーでの SQL Server 2012 ブックの検索](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![ヘルプ ビューアーでの SQL Server 2012 ブックの追加と更新](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > コンテンツの追加中にヘルプビューアーがフリーズ (ハング) した場合は、 \<mm/dd/yyyy> HlpViewer_SSMSx_en%localappdata%\microsoft\helpviewer2.x\ ファイルまたは HlpViewer_VisualStudiox_en-us. 設定ファイルのキャッシュ LastRefreshed = "00:00:00" 行を将来の日付に変更します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](/visualstudio/welcome-to-visual-studio)」を参照してください。

7. SQL Server 2012 のコンテンツが読み込まれたことを確認するには、左側のコンテンツ ペインで「*sql server 2012*」を検索します。

   ![自動的に更新された SQL Server 2012 ドキュメント](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>オフライン ドキュメントを表示する

SQL Server Management Studio (SSMS) の最新バージョンの [**ヘルプ**] メニューを使用して、SQL Server ヘルプコンテンツを表示できます。

### <a name="view-offline-help-content-in-ssms"></a>SSMS でオフライン ヘルプ コンテンツを表示する

インストールされているヘルプを SSMS で表示するには、[ヘルプ] メニューから **[ヘルプ ビューアーで起動]** を選択してヘルプ ビューアーを起動します。

   ![ヘルプ ビューアーで起動](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。このタブの左側のペインにインストールされたヘルプの目次が表示されます。 目次内の記事を選択すると、右側のペインに該当するトピックが表示されます。

> [!Important]
> コンテンツ ペインが表示されない場合は、左余白の [コンテンツ] を選択します。 プッシュピン アイコンを選択すると、コンテンツ ペインは開いたままになります。  

   ![コンテンツが表示されたヘルプ ビューアー](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)

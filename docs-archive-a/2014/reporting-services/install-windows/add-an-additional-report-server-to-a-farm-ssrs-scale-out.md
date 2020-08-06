---
title: ファームへのレポート サーバーの追加 (SSRS スケールアウト) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31fd7809c4085a90dc487f9091a7f9bd0aeab58e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632985"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a>ファームへのレポート サーバーの追加 (SSRS スケールアウト)
  2 台目以降の SharePoint モードのレポート サーバーを SharePoint ファームに追加すると、レポート サーバーのパフォーマンスと応答時間を向上させることができます。 ユーザー、レポート、またはその他のアプリケーションをレポート サーバーに追加したときにパフォーマンスが低下する場合は、レポート サーバーを追加することでパフォーマンスを向上できます。 ハードウェアに問題がある場合、または環境内の個々のサーバーに対して全般的なメンテナンスを行う場合も、2 台目のレポート サーバーを追加してレポート サーバーの可用性を向上させることをお勧めします。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のリリースでの SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 環境をスケールアウトする手順では、標準の SharePoint ファーム配置に従い、SharePoint の負荷分散機能を活用します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の一部のエディションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスケールアウトがサポートされません。 詳細については、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)のセクションを参照してください。  
  
> [!TIP]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、サーバーの追加およびレポート サーバーのスケールアウトに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用しません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを使用する SharePoint サーバーがファームに追加されると、SharePoint 製品では Reporting Services のスケールアウトを管理します。  
  
 ネイティブ モードのレポート サーバーをスケールアウトする方法の詳細については、「[ネイティブ モード レポート サーバーのスケールアウト配置の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)」を参照してください。  
  
-   [負荷分散](#bkmk_loadbalancing)  
  
-   [前提条件](#bkmk_prerequisites)  
  
-   [手順](#bkmk_steps)  
  
-   [追加の構成](#bkmk_additional)  
  
##  <a name="load-balancing"></a><a name="bkmk_loadbalancing"></a>負荷分散  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの負荷分散は、カスタムまたはサードパーティの負荷分散ソリューションが環境に含まれていない限り、SharePoint によって自動的に管理されます。 SharePoint の既定の負荷分散動作では、各 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーション サービスは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを開始したすべてのアプリケーション サーバー間で分散されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスがインストールされていて開始されていることを確認するには、SharePoint サーバーの全体管理で **[サーバーのサービスの管理]** をクリックします。  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> 前提条件  
  
-   SQL Server セットアップを実行するには、ローカル管理者である必要があります。  
  
-   コンピューターがドメインに参加する必要があります。  
  
-   SharePoint の構成データベースとコンテンツ データベースをホストしている既存のデータベース サーバーの名前を把握しておく必要があります。  
  
-   データベース サーバーは、リモート データベース接続を許可するように構成されている必要があります。  構成されていない場合は、新しいサーバーが SharePoint 構成データベースに接続できないため、新しいサーバーをファームに参加させることができません。  
  
-   新しいサーバーのバージョンは、現在のファーム サーバーが実行されているインストール済みの SharePoint のバージョンと同じである必要があります。 たとえば、SharePoint 2010 Service Pack 1 (SP1) が既にファームにインストールされている場合は、新しいサーバーをファームに参加させる前に、新しいサーバーにも SP1 をインストールする必要があります。  
  
-   次の追加トピックを確認し、システムとバージョンの要件を理解してください。  
  
     [SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイド](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="steps"></a><a name="bkmk_steps"></a>よう  
 このトピックの手順では、SharePoint ファームの管理者がサーバーをインストールして構成すると想定しています。 この図は標準的な 3 層環境を示しています。次に、図の番号付き項目の説明を示します。  
  
-   (1) 複数の Web フロントエンド (WFE) サーバー。 WFE サーバーには、SharePoint 2010 用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。  
  
-   (2) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と Web サイトを実行している単一のアプリケーション サーバー。たとえば、サーバーの全体管理などです。 次の手順では、この層に 2 つ目のアプリケーション サーバーを追加します。  
  
-   (3) 2 つの SQL Server データベース サーバー。  
  
-   (4) ソフトウェアまたはハードウェアのネットワーク負荷分散ソリューション (NLB) を表します。  
  
 ![Reporting Services アプリケーション サーバーの追加](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Reporting Services アプリケーション サーバーの追加")  
  
 次の手順では、管理者がサーバーをインストールして構成すると想定しています。 サーバーは、新しいアプリケーション サーバーとしてファームにセットアップされ、Web フロントエンド (WFE) としては使用されません。  
  
|手順|説明とリンク|  
|----------|--------------------------|  
|SharePoint 2010 製品準備ツールを実行します。|SharePoint 2010 のインストール メディアが必要です。 準備ツールは、のインストールメディアに**PrerequisiteInstaller.exe**ます。|  
|SharePoint 2010 製品をインストールします。|1)**サーバーファーム**のインストールの種類を選択します。<br /><br /> 2) サーバーの種類として [**完全**] を選択します。<br /><br /> 3) 既存の SharePoint ファームに SharePoint 2010 SP1 がインストールされている場合は、インストールが完了したときに SharePoint 製品構成ウィザードを実行しないでください。 SharePoint 製品構成ウィザードを実行する前に SharePoint SP1 をインストールする必要があります。|  
|SharePoint Server 2010 SP1 をインストールします。|既存の SharePoint ファームに SharePoint 2010 SP1 がインストールされている場合は、から SharePoint 2010 SP1 をダウンロードしてインストールし [https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697) ます。<br /><br /> SharePoint 2010 SP1 の詳細については、「 [Office 2010 SP1 および SharePoint 2010 SP1 インストール時の既知の問題](https://support.microsoft.com/kb/2532126)」を参照してください。|  
|SharePoint 製品の構成ウィザードを実行して、ファームにサーバーを追加します。|1) **Microsoft sharepoint 2010 製品**のプログラムグループで、[ **Microsoft Sharepoint 2010 製品構成ウィザード**] をクリックします。<br /><br /> 2) [**サーバーファームへの接続**] ページで、[**既存のファームへの接続**] を選択し、[**次へ**] をクリックします。<br /><br /> 3) [**構成データベースの設定の指定**] ページで、既存のファームに使用するデータベースサーバーの名前と構成データベースの名前を入力します。 **[次へ]** をクリックします。<br />** \* \* 重要 \* 次 \* **のようなエラーメッセージが表示され、アクセス許可があることを確認した場合は、「 **SQL server Configuration Manager**: "データベースサーバーに接続できませんでした。」の SQL Server ネットワーク構成に対して有効になっているプロトコルを確認します。 データベースが存在し、Sql Server であること、およびサーバーにアクセスするための適切なアクセス許可があることを確認してください。 "<br />** \* \* 重要 \* : \* ** [**サーバーファームの製品と修正プログラムの状態**] ページが表示された場合は、ファームへのサーバーの参加を続行する前に、ページ上の情報を確認し、必要なファイルでサーバーを更新する必要があります。<br /><br /> 4) [**ファームのセキュリティ設定の指定**] ページで、ファームのパスフレーズを入力し、[**次へ**] をクリックします。 確認ページで **[次へ]** をクリックして、ウィザードを実行します。<br /><br /> 5) [**次へ**] をクリックして、**ファーム構成ウィザード**を実行します。|  
|サーバーが SharePoint ファームに追加されたことを確認します。|1) SharePoint サーバーの全体管理で、 **[システム設定]** の **[このファームのサーバーの管理]** をクリックします。<br /><br /> 2) 新しいサーバーが追加され、状態が正しいことを確認します。<br /><br /> 3) サービス**SQL Server Reporting Services サービス**が実行されていないことを確認してください。 このサービスは次の手順でインストールされます。<br /><br /> 4) このサーバーを WFE ロールから削除するには、[**サーバーのサービスの管理**] をクリックし、 **Microsoft SharePoint Foundation Web アプリケーション**サービスを停止します。|  
|Reporting Services SharePoint モードをインストールして構成します。|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストールを実行します。 Sharepoint モードのインストールの詳細につい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ては、「 [sharepoint 2010 用 Reporting Services sharepoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」を参照してください。サーバーをアプリケーションサーバーとしてのみ使用し、サーバーを WFE として使用しない場合は、 **sharepoint 製品用の Reporting Services アドイン**を選択する必要はありません。<br /><br /> [**セットアップロール**] ページで、[ **SQL Server 機能のインストール**] を選択します。<br /><br /> [**機能の選択**] ページで、[ **Reporting Services-SharePoint** ] を選択します。<br /><br /> \- または -<br /><br /> [ **Reporting Services の構成**] ページでは**Reporting Services SharePoint モード**に [**インストールのみ**] オプションが選択されていることを確認します。|  
|Reporting Services が動作することを確認します。|1) SharePoint サーバーの全体管理で、 **[システム設定]** の **[このファームのサーバーの管理]** をクリックします。<br /><br /> 2) **SQL Server Reporting Services サービス**を確認します。<br /><br /> 詳細については、「 [Reporting Services のインストールの検証](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)」を参照してください。|  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional"></a>追加の構成  
 スケールアウト配置では、個々の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバーを最適化して、バックグラウンド処理のみを実行できます。そのため、リソースの確保を求めて対話型のレポート実行との競合が発生することはありません。 バックグラウンド処理には、スケジュール、サブスクリプション、およびデータ警告が含まれます。  
  
 個々のレポートサーバーの動作を変更するには、 **\<IsWebServiceEnable>** **RSreportServer.config**構成ファイルでを false に設定します。  
  
 既定では、レポートサーバーは、 \<IsWebServiceEnable> を TRUE に設定して構成されます。 TRUE の設定を使用してすべてのサーバーが構成されている場合は、対話型処理とバックグラウンド処理がファーム内のすべてのノード間で負荷分散されます。  
  
 を False に設定してすべてのレポートサーバーを構成すると \<IsWebServiceEnable> 、機能を使用しようとすると、次のようなエラーメッセージが表示され [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。  
  
 Reporting Services Web サービスが無効です。 を true に設定するように、Reporting Services SharePoint サービスのインスタンスを少なくとも1つ構成し \<IsWebServiceEnable> ます。 詳細については、「[Reporting Services の構成ファイルの変更 &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SharePoint 2013 でファームに web サーバーまたはアプリケーションサーバーを追加する](https://technet.microsoft.com/library/cc261752.aspx)   
 [サービスを構成する (SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  

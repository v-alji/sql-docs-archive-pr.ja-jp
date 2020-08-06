---
title: アップグレード処理中にすべてのデータファイルとログファイルで自動拡張が有効になっていることを確認する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], size
- data files [SQL Server], size
- tempdb [SQL Server], size
- autogrow [SQL Server]
ms.assetid: a5860904-e2be-4224-8a51-df18a10d3fb9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ca12075598bce210a905cbdfba89f2d879cf09b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742746"
---
# <a name="verify-autogrow-is-turned-on-for-all-data-and-log-files-during-the-upgrade-process"></a>アップグレード処理中、すべてのデータ ファイルとログ ファイルの自動拡張が有効になっていることを確認する
  アップグレード アドバイザーによって、自動拡張に設定されていないデータまたはログ ファイルが検出されました。 新機能と強化された機能では、ユーザーデータベースおよび**tempdb**システムデータベース用に追加のディスク領域が必要になります。 アップグレード中およびその後の運用操作中に、リソースがサイズの増加に対応できるようにするには、アップグレードする前に、すべてのユーザーデータファイルとログファイル、および**tempdb**データとログファイルに対して自動拡張を ON に設定することをお勧めします。  
  
 アップグレードを完了し、作業負荷をテストした後、必要に応じてユーザー データ ファイルとログ ファイルの自動拡張をオフにしたり、FILEGROWTH 増分値を調整してください。 **Tempdb**システムデータベースの自動拡張をオンのままにすることをお勧めします。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「tempdb に使用するディスク領域の計画」を参照してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 **データファイル**  
  
 次の表に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能変更では、ユーザー定義データ ファイル用に追加ディスク領域が必要となります。  
  
|特徴量|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から導入された変更|  
|-------------|-----------------------------------------------------|  
|フルテキスト|ドキュメント ID (DOCID) マップは、フルテキスト カタログではなく、データ ファイルに格納されます。|  
|`text`、`ntext`、`image` の各列|`text`、`ntext`、または `image` のデータ型として定義されるラージ オブジェクト (LOB) 列には、列ごとに 40 バイトのディスク領域を追加する必要があります。 この 1 回限りの領域増加は、各 LOB 列の初回更新時に発生します。|  
|metadata|追加のシステム メタデータが、データベース オブジェクトおよびユーザー権限の各ユーザー データベースの PRIMARY ファイル グループに作成および保持されます。 たとえば、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、権限を与えるユーザーまたは権限が与えられるユーザーに関連する権限は、ビットマップとして 1 つの行に格納されます。 そのビットマップが複数の行に拡張されます。<br /><br /> そのため、アップグレード時に、古いメタデータと新しいメタデータの両方を格納するのに十分なディスク領域を確保する必要があります。 古いメタデータは、アップグレード完了後に削除されます。|  
  
 **トランザクション ログ ファイル**  
  
 次の表に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能変更では、ユーザー定義トランザクション ログ ファイル用に追加ディスク領域が必要となります。  
  
|特徴量|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から導入された変更|  
|-------------|-----------------------------------------------------|  
|復元および復旧|クラッシュ復旧の元に戻すフェーズの間、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用してデータベースにアクセスできます。 これは、クラッシュの発生時にコミットされなかったトランザクションに、クラッシュ前に保持されたロックが必要であるためです。 トランザクションのロールバック中に、トランザクションのロックによってユーザーによる介入からトランザクションが保護されます。 このロックに関する追加情報は、トランザクション ログに保持されます。|  
  
 **tempdb データとログ ファイル**  
  
 以前のバージョンので [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、 **tempdb**データベースを使用して次のオブジェクトが格納されていました。  
  
-   テーブル、ストアド プロシージャ、テーブル変数、カーソルなどの明示的に作成される一時オブジェクト  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]によって作成される内部作業テーブル  
  
-   インデックスの作成や再構築時の一時ソートによる結果 (SORT_IN_TEMPDB を指定した場合)  
  
 その他のオブジェクトも**tempdb**データベースを使用します。 次の表に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tempdb**のデータファイルとログファイルに必要な追加のディスク領域を生成する機能の変更または追加機能を示します。  
  
|特徴量|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から導入された変更|  
|-------------|-----------------------------------------------------|  
|行のバージョン管理|行のバージョン管理は、の一般的なフレームワークであり、次のような場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に使用されます。<br /><br /> サポートトリガー: トリガーで inserted テーブルと deleted テーブルを作成します。 トリガーによって変更された行はすべて、バージョン化されます。 これには、トリガーによりデータが変更された行だけでなく、トリガーを起動したステートメントにより変更された行も含まれます。 AFTER トリガーは、 **tempdb**のバージョンストアを使用して、トリガーによって変更された行の前のイメージを保持します。 トリガーを有効にしてデータを一括読み込みする場合、各行のコピーをバージョン ストアに追加する。<br /><br /> 複数のアクティブな結果セット (MARS) をサポートする。 アクティブな結果セットが存在するときに、MARS セッションでデータ変更ステートメント (INSERT、UPDATE、DELETE など) が実行された場合、その変更ステートメントの影響を受けた行はバージョン化されます。<br /><br /> ONLINE オプションを指定するインデックス操作をサポートする。 オンライン インデックス操作では、行のバージョン管理を使用して、他のトランザクションによる変更がインデックス操作に影響を与えないようにしています。 そのため、読み取った行の共有ロックを要求する必要がなくなります。 さらに、オンラインインデックス操作中のユーザーの更新および削除操作の同時実行には、 **tempdb**のバージョンレコード用の領域が必要です。<br /><br /> 行のバージョン管理に基づくトランザクション分離レベルのサポート: 行のバージョン管理を使用してステートメントレベルの読み取りの一貫性を提供する、read committed 分離レベルの新しい実装。 新しい分離レベルであるスナップショット。このレベルにより、トランザクションレベルの読み取り一貫性を実現します。<br /><br /> <br /><br /> 行バージョンは、行のバージョン管理に基づく分離レベルで実行されるトランザクションの要件を満たすのに十分な**tempdb**バージョンストアに保持されます。<br /><br /> 行バージョンおよびバージョン ストアの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「行のバージョン管理に基づく分離レベルについて」を参照してください。|  
|一時テーブルおよび一時変数メタデータのキャッシュ|によってメタデータキャッシュにキャッシュされた一時テーブルおよび一時変数のすべてのメタデータについて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 **tempdb**に2つの追加ページが割り当てられます。<br /><br /> ストアド プロシージャまたはトリガーで一時テーブルまたは一時変数を作成する場合、そのプロシージャまたはトリガーによる実行が完了しても、一時オブジェクトは削除されません。 その代わりに、一時オブジェクトが 1 ページに切り詰められ、そのプロシージャまたはトリガーを次回に実行するときに再利用されます。|  
|パーティション テーブルのインデックス|で [!INCLUDE[ssDE](../../includes/ssde-md.md)] パーティションインデックスを構築するために並べ替えを実行する場合、SORT_IN_TEMPDB インデックスオプションを指定した場合、 **tempdb**には、各パーティションの中間の並べ替え実行を格納するための十分な領域が必要です。|  
|[!INCLUDE[ssSB](../../includes/sssb-md.md)]|[!INCLUDE[ssSB](../../includes/sssb-md.md)]メモリに保持できない既存のダイアログコンテキストを保持する場合、 **tempdb**を明示的に使用します (ダイアログあたり約 1 KB)。<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]では、クエリ実行のコンテキストでオブジェクトのキャッシュによって**tempdb**を暗黙的に使用します。 たとえば、タイマー イベントに使用される作業テーブルおよびバックグラウンド送信メッセージ交換で使用します。<br /><br /> DBMail、イベント通知、およびクエリ通知の機能では、[!INCLUDE[ssSB](../../includes/sssb-md.md)] を暗黙的に使用します。|  
|ラージ オブジェクト (LOB) のデータ型<br /><br /> LOB の変数およびパラメーター|データ型、 `varchar(max)` `nvarchar(max)` 、 **varbinary (max) テキスト**、 `ntext` 、 `image,` およびは、 `xml` ラージオブジェクト型です。<br /><br /> データベースで行のバージョン管理に基づくトランザクション分離レベルが有効になっていて、ラージオブジェクトの変更が行われると、変更された LOB のフラグメントが**tempdb**のバージョンストアにコピーされます。<br /><br /> ラージオブジェクトデータ型として定義されるパラメーターは、 **tempdb**に格納されます。|  
|共通テーブル式 (Cte)|共通テーブル式のクエリが実行されると、スプール操作の一時作業テーブルが**tempdb**に作成されます。|  
  
## <a name="corrective-action"></a>修正措置  
 データまたはログ ファイルを自動拡張に設定するには、データベースのデータおよびログを指定するように以下のステートメントを変更してください。 また FILEGROWTH 増分値を、使用している環境で適切な値に調整する必要があります。  
  
```  
ALTER DATABASE tempdb  
MODIFY FILE  
    (NAME = tempdev,  
    FILEGROWTH = 20MB);  
GO  
ALTER DATABASE tempdb  
MODIFY FILE  
    (NAME = templog,  
    FILEGROWTH = 10MB);  
```  
  
 データ ファイルの既定の拡張増分値が 1 MB になります。 ログ ファイルの既定値は 10% です。 FILEGROWTH 増分値を設定するときは、次の一般的なガイドラインに従うことをお勧めします。  
  
|ファイル サイズ|FILEGROWTH 増分値|  
|---------------|--------------------------|  
|0 ～ 50 MB|10 MB|  
|100 ～ 200 MB|MB|  
|500 MB 以上|10%|  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
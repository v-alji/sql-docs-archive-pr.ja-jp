---
title: トランザクションパブリケーションでのストアドプロシージャの実行のパブリッシュ (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44310d45a7049701a6aecfa73301b15b0021ac6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633059"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>トランザクション パブリケーションでのストアド プロシージャの実行のパブリッシュ (SQL Server Management Studio)
  **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスで、ストアド プロシージャの単なる定義ではなく、その実行をパブリッシュすることを指定します。 このダイアログ ボックスは、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで使用できます。 ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
 プロシージャの定義 (CREATE PROCEDURE ステートメント) はサブスクリプションが初期化されるときにサブスクライバーにレプリケートされます。プロシージャがパブリッシャーで実行されるときに、レプリケーションは対応するプロシージャをサブスクライバーで実行します。  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>ストアド プロシージャの実行をパブリッシュするには  
  
1.  パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、ストアド プロシージャを選択します。  
  
2.  **[アーティクルのプロパティ]** をクリックしてから、 **[反転表示されたストアド プロシージャのプロパティを設定]** をクリックします。  
  
3.  **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスで、 **[レプリケート]** オプションに対して次のいずれかの値を指定します。  
  
    -   **[ストアド プロシージャの実行]**  
  
    -   **[SP のシリアル化されたトランザクションでの実行]**  
  
         これは、推奨オプションです。このオプションを指定すると、プロシージャがシリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、プロシージャの実行がレプリケートされます。 ストアド プロシージャがシリアル化可能なトランザクションの外から実行される場合、パブリッシュされたテーブルのデータに対する変更は一連の DML (データ操作言語) ステートメントとしてレプリケートされます。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーションにおけるパブリッシング ストアド プロシージャの実行](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  

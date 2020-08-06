---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7f3484d9344a203ca8c44fee6b79605163ea069
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630930"
---
# <a name="mssql_eng014120"></a>MSSQL_ENG014120
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14120|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|ディストリビューション データベース '%s' を削除できませんでした。 このディストリビューション データベースはパブリッシャーに関連付けられています。|  
  
## <a name="explanation"></a>説明  
 ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションに対するトランザクションが格納されます。 このエラーは、1 つ以上のパブリッシャーに関連付けられているディストリビューション データベースを削除しようとした場合に発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 ディストリビューション データベースを削除するには、まずディストリビューターとパブリッシャーの関連付けを解除する必要があります。 詳細については、「[sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)   
 [[ディストリビューションの構成]](configure-distribution.md)  
  
  

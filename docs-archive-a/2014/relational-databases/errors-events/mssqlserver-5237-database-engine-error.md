---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 224317e290ce15aaed979129733b6273b3b663df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643849"
---
# <a name="mssqlserver_5237"></a>MSSQLSERVER_5237
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5237|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|メッセージ テキスト|オブジェクト 'NAME' (オブジェクト ID O_ID) で、内部クエリ エラーにより、DBCC クロス行セットのチェックに失敗しました。|  
  
## <a name="explanation"></a>説明  
 内部エラーが発生したため、DBCC は、クエリを実行してインデックス付きビューをチェックすることができませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 DBCC コマンドを再実行します。  
  
  

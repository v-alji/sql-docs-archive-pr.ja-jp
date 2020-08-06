---
title: '[警告のプロパティ]: [新しい警告] ([オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737495"
---
# <a name="alert-properties-new-alert-options-page"></a>[警告のプロパティ]:[新しい警告] ([オプション] ページ)
  このページを使用すると、エージェントの警告のオプションを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。  
  
## <a name="options"></a>Options  
 **メッセージ**  
 イベントからのエラー テキストがある場合は、それを電子メール通知に含めます。  
  
 **ポケットベル**  
 イベントからのエラー テキストがある場合は、それをポケットベル通知に含めます。  
  
 **Net send**  
 イベントからのエラー テキストがある場合は、それを Net Send 通知に含めます。  
  
 **[送信する付加通知メッセージ]**  
 通知メッセージに含める追加のテキストを入力します。  
  
 **[応答の遅延]**  
 反復的に発生するイベントの遅延を指定します。 イベントの中には、短時間に頻繁に発生するものがあります。 そのようなイベントに対しては、その発生を認識するだけで、すべてのイベントについて応答を返さないようにする場合があります。 このオプションを使用して、タイムアウトを指定します。遅延が発生すると、警告がイベントに応答した後、エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントが遅延中に発生したかどうかに関係なく、指定された遅延を待機してからもう一度応答します。  
  
 **分**  
 遅延を分単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
 **Seconds**  
 遅延を秒単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
## <a name="see-also"></a>参照  
 [アラート](alerts.md)  
  
  

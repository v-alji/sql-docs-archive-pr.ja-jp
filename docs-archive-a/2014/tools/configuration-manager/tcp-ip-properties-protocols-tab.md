---
title: '[TCP-IP のプロパティ] ([プロトコル] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d5bc28faddae9a86a6636b56b907b57a2d8711a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632252"
---
# <a name="tcp---ip-properties-protocols-tab"></a>[TCP-IP のプロパティ] ([プロトコル] タブ)
  **[TCP/IP のプロパティ]** ダイアログ ボックスは、TCP/IP プロトコルのオプションを構成するために使用します。 左ペインで **[TCP/IP]** をクリックすると、詳細ペインに個々の IP アドレス構成が表示されます。  
  
 変更を有効にするには、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。  
  
## <a name="options"></a>オプション  
 **有効**  
 可能な値は、 **[はい]** と **[いいえ]** です。  
  
 **[Keep Alive]**  
 接続のリモート側のコンピューターが使用可能かどうかを確認するために、Keep Alive パケットを送信する間隔 (ミリ秒) を指定します。  
  
 **[すべて受信待ち]**  
 コンピューター上のネットワーク カードに割り当てられているすべての IP アドレスで SQL Server がリッスンするかどうかを指定します。 **[いいえ]** に設定した場合は、各 IP アドレスのプロパティ ダイアログ ボックスを使用して、IP アドレスごとに個別の構成を行ってください。 **[はい]** に設定した場合は、 **[IPAll]** プロパティ ボックスの設定がすべての IP アドレスに適用されます。 既定値は **[はい]** です。  
  
 **[遅延なし]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このプロパティに対する変更は実装されません。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [TCP/IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  

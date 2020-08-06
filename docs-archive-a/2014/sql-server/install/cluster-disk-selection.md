---
title: クラスターディスクの選択 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0f53d6d3f623254d2b17996be7fd5b8235dca223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640468"
---
# <a name="cluster-disk-selection"></a>クラスター ディスクの選択
  **フェールオーバー クラスターの共有クラスター ディスク リソースを選択するには、** インストール ウィザードの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [クラスター ディスクの選択] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページを使用します。 クラスター ディスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データが配置される場所です。  
  
 共有クラスターディスクは、クラスターのインストールには必要ありません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。 SMB ファイルサーバーは、フェールオーバークラスターインストールでサポートされている記憶域であり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] インストールを完了する前に [**データベースエンジンデータディレクトリ**] ページを使用して指定できます。  
  
> [!WARNING]  
>  Analysis Services のインストールを選択した場合は、共有クラスター ディスクを指定する必要があります。  
>   
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスで FILESTREAM を有効にする場合は、共有クラスター ディスクを指定する必要があります。  
  
## <a name="options"></a>Options  
 **共有ディスク**  
 単一のディスクを一覧から選択します。 クラスター ディスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データが配置される場所です。  
  
 1 つのディスクのみを指定できます。 クラスター クォーラム リソースを含んでいるグループを選択すると、警告が表示されます。 クラスター クォーラム リソースにインストールすることはお勧めしません。  
  
 **[使用可能な共有ディスク]**  
 使用可能なディスクの一覧、各ディスクが共有ディスクに適しているかどうか、および各ディスク リソースの説明が表示されます。  
  
  

---
title: '[コマンド] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
ms.openlocfilehash: c766ed5408de96b6a2305ce377f9031947618a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644415"
---
# <a name="command-window"></a>[コマンド] ウィンドウ
  **[コマンド]** ウィンドウを使用すると、現在デバッグ中の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対してデバッグ コマンドや編集コマンドなどのコマンドを実行できます。 **[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。 詳細については、 [Visual Studio のコマンド ウィンドウに関するページ](https://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[コマンド] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
 **変数の値を出力するには**  
  
-   **コマンドウィンドウ**で、「 **Debug. Print \<VariableName> **」と入力し、enter キーを押します。  
  
 **現在のスレッドに関する情報を一覧表示するには**  
  
-   **コマンドウィンドウ**で、「」と入力し、enter `Debug.ListThread` キーを押します。  
  
 **[クイック ウォッチ] ウィンドウに変数を追加するには**  
  
-   **コマンドウィンドウ**で、「 **Debug. クイックウォッチ \<VariableName> **」と入力し、enter キーを押します。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](transact-sql-debugger.md)  

---
title: タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21e334faff95e63e59bbf9c40fdf7e479de949da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633223"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする
  この手順では、パッケージ、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーにブレークポイントを設定する方法について説明します。  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>パッケージ、タスク、またはコンテナーにブレークポイントを設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ブレークポイントを設定するパッケージをダブルクリックします。  
  
3.  SSIS デザイナーで、次の操作を行います。  
  
    -   パッケージ オブジェクトにブレークポイントを設定するには、 **[制御フロー]** タブをクリックし、デザイン画面の背景の任意の場所にカーソルを置いて右クリックし、 **[ブレークポイントの編集]** をクリックします。  
  
    -   パッケージ制御フローにブレークポイントを設定するには、 **[制御フロー]** タブをクリックし、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーを右クリックし、 **[ブレークポイントの編集]** をクリックします。  
  
    -   イベント ハンドラーにブレークポイントを設定するには、 **[イベント ハンドラー]** タブをクリックし、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーを右クリックし、 **[ブレークポイントの編集]** をクリックします。  
  
4.  **[ブレークポイント \<container name> の設定]** ダイアログ ボックスで、有効にするブレークポイントを選択します。  
  
5.  必要に応じて、各ブレークポイントのヒット カウントの種類とヒット カウント数を変更します。  
  
6.  パッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [パッケージ開発のトラブルシューティング ツール](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [スクリプトタスクとスクリプトコンポーネントにブレークポイントを設定してスクリプトをデバッグする](data-flow/transformations/script-component.md)   
 [スクリプトタスクのコーディングおよびデバッグ](control-flow/script-task.md)   
 [スクリプト コンポーネントのコーディングおよびデバッグ](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  

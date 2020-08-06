---
title: Excel 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f66de13b710e5ccb577e6f2d67c215572e34767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641764"
---
# <a name="excel-connection-manager-editor"></a>Excel 接続マネージャー
  **[Excel 接続マネージャー]** ダイアログ ボックスを使用すると、既存または新規の [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] ブック ファイルへの接続を追加できます。  
  
 Excel 接続マネージャーの詳細については、「 [Excel Connection Manager](connection-manager/excel-connection-manager.md)」を参照してください。  
  
> [!NOTE]  
>  パスワードで保護された Excel ファイルには接続できません。  
  
## <a name="options"></a>Options  
 **[Excel ファイル パス]**  
 既存または新規の Excel ブック ファイル (.xls) のパスおよびファイル名を入力します。  
  
> [!WARNING]  
>  Excel**変換先エディター**では、存在しないファイルをポイントする**excel 接続**を選択すると、excel ファイルが自動的に作成されます。その後、[ **excel シートの名前**] で [**新規**] をクリックします。  
  
 **[参照]**  
 **[開く]** ダイアログ ボックスを使用して、Excel ファイルが存在するフォルダー、または新しいファイルを作成するフォルダーを指定します。  
  
 **Excel のバージョン**  
 ファイルを作成するために使用した Microsoft Excel のバージョンを指定します。  
  
|オプション|説明|  
|------------|-----------------|  
|[Microsoft Excel 97-2005]|ファイルは Excel 97 以降を使用して作成されています。|  
|Excel 3.0|ファイルは Excel 3.0 を使用して作成されました。|  
|Excel 4.0|ファイルは Excel 4.0 を使用して作成されています。|  
|Excel 5.0|ファイルは Excel 95 (7.0) を使用して作成されています。|  
  
 **最初の行に列名がある**  
 選択されているワークシートのデータの 1 行目に列名が含まれているかどうかを指定します。 このオプションの既定値は **[true]** です。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](control-flow/foreach-loop-container.md)  
  
  

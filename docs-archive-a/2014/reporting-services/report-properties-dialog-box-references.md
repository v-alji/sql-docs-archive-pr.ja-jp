---
title: '[参照] ([レポートのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b28ea0865d37bdc56054d6b23dc8c82d9279b08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717384"
---
# <a name="report-properties-dialog-box-references"></a>[参照] ([レポートのプロパティ] ダイアログ ボックス)
  **[レポートのプロパティ]** ダイアログ ボックスの **[参照]** を選択すると、レポート定義内の式で使用される、カスタム アセンブリまたは他の外部アセンブリ、およびカスタム クラスのインスタンスへの参照を追加または削除できます。  
  
## <a name="options"></a>Options  
 **[アセンブリの追加または削除]**  
 レポートで参照されるアセンブリを一覧表示します。 アセンブリは、レポートのデザインに使用するツールがインストールされているコンピューターおよびレポート サーバー上で使用できる必要があります。 参照の名前は、 **\<CodeModule>** レポート定義言語 (.rdl) ファイルのタグの内容と正確に一致している必要があります。  
  
 **[追加]**  
 アセンブリを追加します。 省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なアセンブリを選択します。  
  
 **削除**  
 アセンブリの参照を一覧から削除するには、削除するアセンブリ名を選択し、 **[削除]** ボタンをクリックします。  
  
 **[クラスの追加または削除]**  
 レポートで使用されるクラスのインスタンスを一覧表示します。 クラスの一覧は、静的メンバーではなく、インスタンス ベースのメンバーでのみ使用されます。  
  
 **[追加]**  
 クラスの参照を追加します。 省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なクラスを選択します。  
  
 **削除**  
 クラスのインスタンスを削除するには、削除するインスタンスを選択し、 **[削除]** ボタンをクリックします。  
  
 **設定**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の上方に移動できます。  
  
 **[下へ]**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の下方に移動できます。  
  
## <a name="see-also"></a>参照  
 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [レポート変数コレクションとグループ変数コレクションは &#40;レポートビルダーと SSRS&#41;を参照します。](report-design/built-in-collections-report-and-group-variables-references-report-builder.md)   
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  

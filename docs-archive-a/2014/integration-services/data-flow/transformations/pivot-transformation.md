---
title: ピボット変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.pivottrans.f1
helpviewer_keywords:
- Pivot transformation
- normalized data [Integration Services]
- PivotUsage property
- datasets [Integration Services], normalized data
- less normalized data set [Integration Services]
ms.assetid: 55f5db6e-6777-435f-8a06-b68c129f8437
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43bdc5be709ea00d4be4601f52c38e96fe3f1ce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743410"
---
# <a name="pivot-transformation"></a>ピボット変換
  ピボット変換は、入力データを列の値でピボットすることにより、正規化されたデータセットを、正規化の度合は低いがより圧縮された形に設定します。 たとえば、顧客名、製品、購入した数量を一覧表示する、正規化された **Orders** データセットには、通常、複数の製品を購入した顧客に対して複数の行があり、その顧客に対する各行には製品ごとに注文の詳細が示されています。 ピボット変換では、データセットを製品列でピボットすることにより、各顧客のデータセットを単一行で出力できます。 その行では顧客のすべての購入情報が一覧となり、列名に製品名が表示され、製品列の値には購入した数量が表示されます。 すべての顧客がすべての製品を購入するわけではないので、多くの列に NULL 値が含まれることがあります。  
  
 データセットがピボットされる場合、ピボット処理において入力列はさまざまに機能します。 列が果たす役割には、次のものがあります。  
  
-   列は、変更されずに出力に渡されます。 入力行は 1 つの出力行のみに渡される場合が多いため、変換により列の最初の入力値のみがコピーされます。  
  
-   列は、レコードのセットを識別するためのキーまたはキーの一部として機能します。  
  
-   列は、ピボットを定義します。 この列の値は、ピボットされたデータセットの列に関連付けられます。  
  
-   列には、ピボットにより作成される列に配置する値が含まれます。  
  
 この変換は、1 つの入力、1 つの標準出力、および 1 つのエラー出力をとります。  
  
## <a name="sort-and-duplicate-rows"></a>並べ替えおよび重複する行  
 データを効率よくピボットする、つまり、出力データセットで作成されるレコード数をできるだけ少なくするには、入力データをピボット列で並べ替える必要があります。 データが並べ替えられていない場合、ピボットの変換では、設定キーの各値に対して複数のレコードが生成されることがあります。ここで設定キーとは、設定されたメンバーシップを定義する列のことです。 たとえば、データセットを **Name** 列でピボットする際に名前が並べ替えられていない場合、出力データセットには、各顧客の行が複数含まれることがあります。これは、 **Name** 列の値が変わるたびにピボットが発生するためです。  
  
 入力データには重複する行が含まれる場合があります。重複する行があると、ピボット変換は失敗します。 "重複する行" とは、設定キー列およびピボット列に同じ値を持つ行のことです。 エラーを回避するには、エラー行をエラー出力にリダイレクトするように変換を構成するか、重複する行が存在しないように値を事前に集計しておくことができます。  
  
##  <a name="options-in-the-pivot-dialog-box"></a><a name="options"></a> [ピボット] ダイアログ ボックスのオプション  
 ピボット操作を構成するには、 **[ピボット]** ダイアログ ボックスのオプションを設定します。 **[ピボット]** ダイアログ ボックスを開くには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でパッケージにピボット変換を追加し、コンポーネントを右クリックして **[編集]** をクリックします。  
  
 **[ピボット]** ダイアログ ボックスのオプションは次のとおりです。  
  
 **ピボット キー**  
 テーブルの先頭行 (ヘッダー行) の値に使用する列を指定します。  
  
 **設定キー**  
 テーブルの左の列の値に使用する列を指定します。 入力日はこの列で並べ替える必要があります。  
  
 **ピボット値**  
 ヘッダー行と左の列の値以外のテーブル値に使用する列を指定します。  
  
 **一致しないピボット キー値を無視して DataFlow の実行後に報告する**  
 パッケージが実行されるときに、 **[ピボット キー]** 列に不明な値が含まれている行を無視して、ピボット キーの値をすべてログ メッセージに出力するようにピボット変換を構成するには、このオプションを選択します。  
  
 `PassThroughUnmatchedPivotKeys` カスタム プロパティを `True` に設定することで、値を出力するように変換を構成することもできます。  
  
 **値からピボット出力列を生成**  
 ピボット変換によって出力列が値ごとに作成されるようにするには、このボックスにピボット キーの値を入力します。 パッケージを実行する前に値を入力するか、または次の操作を実行できます。  
  
1.  **[一致しないピボット キー値を無視して DataFlow の実行後に報告する]** オプションを選択し、 **[ピボット]** ダイアログ ボックスの **[OK]** をクリックして、ピボット変換に対する変更を保存します。  
  
2.  パッケージを実行します。  
  
3.  パッケージの実行が成功したら、 **[進行状況]** タブをクリックして、ピボット キーの値を含むピボット変換の情報ログ メッセージを確認します。  
  
4.  メッセージを右クリックして、 **[メッセージ テキストのコピー]** をクリックします。  
  
5.  **[デバッグ]** メニューの **[デバッグの停止]** をクリックしてデザイン モードに切り替えます。  
  
6.  ピボット変換を右クリックして、 **[編集]** をクリックします。  
  
7.  **[一致しないピボット キー値を無視して DataFlow の実行後に報告する]** オプションをオフにして、 **[値からピボット出力列を生成]** ボックスに、次の形式を使用してピボット キーの値を貼り付けます。  
  
     [value1],[value2],[value3]  
  
 **今すぐに列を生成**  
 クリックすると、 **[値からピボット出力列を生成]** ボックスに表示されるピボット キーの値ごとに出力列を作成できます。  
  
 出力列は、 **[既存のピボット出力列]** ボックスに表示されます。  
  
 **[既存のピボット出力列]**  
 ピボット キーの値の出力列が一覧表示されます。  
  
 次の表は、データが **Year** 列でピボットされる前のデータセットを示しています。  
  
|年|製品名|合計|  
|----------|------------------|-----------|  
|2004|HL Mountain Tire|1504884.15|  
|2003|Road Tire Tube|35920.50|  
|2004|Water Bottle - 30 oz.|2805.00|  
|2002|Touring Tire|62364.225|  
  
 次の表は、データが **Year** 列でピボットされた後のデータセットを示しています。  
  
||2002|2003|2004|  
|-|----------|----------|----------|  
|HL Mountain Tire|141164.10|446297.775|1504884.15|  
|Road Tire Tube|3592.05|35920.50|89801.25|  
|Water Bottle - 30 oz.|*NULL*|*NULL*|2805.00|  
|Touring Tire|62364.225|375051.60|1041810.00|  
  
 上記のように、 **Year** 列でデータをピボットするために、 **[ピボット]** ダイアログ ボックスでは次のオプションが設定されます。  
  
-   **[ピボット キー]** ボックスでは [Year] が選択されます。  
  
-   **[設定キー]** ボックスでは [Product Name] が選択されます。  
  
-   **[ピボット値]** ボックスでは [Total] が選択されます。  
  
-   **[値からピボット出力列を生成]** ボックスには、次の値が入力されます。  
  
     [2002],[2003],[2004]  
  
## <a name="configuration-of-the-pivot-transformation"></a>ピボット変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [Common Properties](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
## <a name="related-content"></a>関連コンテンツ  
 このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ピボット解除変換](pivot-transformation.md)   
 [データ フロー](../data-flow.md)   
 [Integration Services の変換](integration-services-transformations.md)  
  
  
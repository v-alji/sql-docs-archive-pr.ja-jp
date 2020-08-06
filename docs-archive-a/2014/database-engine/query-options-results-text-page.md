---
title: '[クエリオプション] の [結果] ([テキスト] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: rothja
ms.author: jroth
ms.openlocfilehash: 45019450c8fc959b440aac5bf1e9098e59cecefc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644125"
---
# <a name="query-options-results-text-page"></a>[クエリ オプション] の [結果] ([テキスト] ページ)
  このページを使用すると、クエリ結果セットをテキスト形式で表示するオプションを指定できます。 このページの設定は、 **[結果をファイルに出力]** が選択されているときにも使用できます。  
  
 **出力形式**  
 既定では、スペースを埋め込んで作成された結果が列に表示されます。 他のオプションは、コンマ、タブ、またはスペースを使用して列を区切るオプションです。 **[独自の区切り記号]** ボックスに他の区切り記号を指定するには、 **[独自の区切り記号]** チェック ボックスをオンにします。  
  
 **[独自の区切り記号]**  
 列を区切るために使用する文字を指定します。 このオプションは、 **[出力形式]** ボックスの **[独自の区切り記号]** チェック ボックスをオンにした場合にのみ利用できます。  
  
 **[列のヘッダーを結果セットに含める]**  
 各列に列タイトルのラベルを付けない場合は、このチェック ボックスをオフにします。  
  
 **[受け取った順に結果をスクロールする]**  
 末尾の最新の取得レコードに常に表示フォーカスを置く場合は、このチェック ボックスをオンにします。 常に、取得した最初の行に表示フォーカスを置く場合は、このチェック ボックスをオフにします。  
  
 **[数値を右揃えにする]**  
 数値を列の右揃えにする場合は、このチェック ボックスをオンにします。 これにより、固定小数点数の数値を簡単に調べることができます。  
  
 **[クエリの実行後に結果を破棄する]**  
 画面表示が、クエリ結果を受け取った後にクエリ結果を破棄することによって、メモリを解放します。  
  
 **[結果を別のタブに表示する]**  
 クエリ ドキュメント ウィンドウの下部ではなく、新しいドキュメント ウィンドウに結果セットを表示する場合は、このチェック ボックスをオンにします。  
  
 **[クエリ実行後に [結果] タブに切り替える]**  
 画面のフォーカスを自動的に結果セットに設定するには、これをクリックします。  
  
 **[各列に表示される最大文字数]**  
 この値は既定で 256 になっています。 この値を大きくすると、結果セットが切り詰めなしで大きく表示されます。  
  
 **既定値にリセット**  
 このページ上のすべての値を元の既定値にリセットします。  
  
## <a name="saving-a-text-result-set-with-headers"></a>ヘッダーを含めたテキスト結果セットの保存  
 クエリ結果をヘッダーを含めてテキスト ファイルに保存するには、 **[列のヘッダーを結果セットに含める]** チェック ボックスをオンにし、区切り出力形式を選択します。 これにより、ツール バーの **[結果をファイルに出力]** をクリックしたとき、またはクエリ結果を右クリックして **[結果に名前を付けて保存]** をクリックし、ファイル名を入力して **[保存]** をクリックしたときに、レポート ファイルにヘッダーが含まれます。  
  
  
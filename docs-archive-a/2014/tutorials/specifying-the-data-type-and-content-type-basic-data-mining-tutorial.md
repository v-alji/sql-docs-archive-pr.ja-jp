---
title: データ型とコンテンツの種類の指定 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 73ff61dbe439b9f2fb50f3a8004f4e7bcad8369a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720445"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>データ型およびコンテンツの種類の指定 (基本的なデータ マイニング チュートリアル)
  前の作業では、構造の作成およびモデルのトレーニングに使用する列を選択しました。次の作業では、ウィザードによって設定されたデータ型およびコンテンツの種類を変更します。  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>各列のコンテンツの種類とデータ型の確認および変更  
  
1.  [**列のコンテンツおよびデータ型の指定**] ページで、[**検出**] をクリックして、各列の既定のデータ型とコンテンツの種類を決定するアルゴリズムを実行します。  
  
2.  [**コンテンツの種類**] 列と [**データ型**] 列のエントリを確認し、必要に応じて変更して、次の表に示されている設定と同じになるようにします。  
  
     通常は、ウィザードによって数値が検出され適切な数値データ型が割り当てられますが、数値をテキストとして処理することが必要なシナリオも数多くあります。 たとえば、 **Geographykey**は、この識別子に対して数学的演算を実行するのは不適切であるため、テキストとして処理する必要があります。  
  
    |列|コンテンツの種類|データ型|  
    |------------|------------------|---------------|  
    |**アドレス Line1**|**離散**|**[テキスト]**|  
    |**アドレス Line2**|**離散**|**[テキスト]**|  
    |**変更**|**継続的**|**Long**|  
    |**Bike Buyer**|**離散**|**Long**|  
    |**Commute Distance**|**離散**|**[テキスト]**|  
    |**CustomerKey**|**[キー]**|**Long**|  
    |**DateLastPurchase**|**継続的**|**日付**|  
    |**メール アドレス**|**離散**|**[テキスト]**|  
    |**English Education**|**離散**|**[テキスト]**|  
    |**English Occupation**|**離散**|**[テキスト]**|  
    |**FirstName**|**離散**|**[テキスト]**|  
    |**性別**|**離散**|**[テキスト]**|  
    |**Geography Key**|**離散**|**[テキスト]**|  
    |**House Owner Flag**|**離散**|**[テキスト]**|  
    |**[Last Name]**|**離散**|**[テキスト]**|  
    |**Marital Status**|**離散**|**[テキスト]**|  
    |**Number Cars Owned**|**離散**|**Long**|  
    |**子供の子供の数**|**離散**|**Long**|  
    |**[リージョン]**|**離散**|**[テキスト]**|  
    |**Total Children**|**離散**|**Long**|  
    |**Yearly Income**|**継続的**|**Double**|  
  
3.  **[次へ]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [構造 &#40;基本的なデータマイニングチュートリアルのテストデータセットの指定&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [「基本的なデータマイニングチュートリアル」 &#40;「対象のメーリングマイニングモデル構造の作成&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [コンテンツの種類 &#40;データマイニング&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [データ型 (データ マイニング)](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  

---
title: 絞り込みメール配信構造への新しいモデルの追加 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b83dfc6c9e218eecf3f2abe636b8c24d69d1b507
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720541"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>絞り込みメール配信構造への新しいモデルの追加 (基本的なデータ マイニング チュートリアル)
  このタスクでは、データマイニングデザイナーの [**マイニングモデル**] タブを使用して、2つの追加のモデルを定義します。 モデルの作成には、Microsoft クラスタリング アルゴリズムと Microsoft Naive Bayes アルゴリズムを使用します。 この 2 つのアルゴリズムを選択する理由は、不連続値 (自転車の購入) を予測できるためです。 これらのアルゴリズムの詳細については、「 [Microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)」と「 [Microsoft Naive Bayes algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md) 」を参照してください。  
  
### <a name="to-create-a-clustering-mining-model"></a>クラスター マイニング モデルを作成するには  
  
1.  のデータマイニングデザイナーで [**マイニングモデル**] タブに切り替え [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。  
  
     デザイナーには、マイニング構造用と、 `TM_Decision_Tree` 前のレッスンで作成したマイニングモデル用の2つの列が表示されていることに注意してください。  
  
2.  [**構造**] 列を右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
3.  [**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に「」と入力 `TM_Clustering` します。  
  
4.  [**アルゴリズム名**] で、[ **Microsoft クラスタリング**] を選択します。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 データマイニングデザイナーの [**マイニングモデル**] タブに新しいモデルが表示されるようになりました。 クラスタリングアルゴリズムを使用して構築されたこのモデルで [!INCLUDE[msCoName](../includes/msconame-md.md)] は、類似した特性を持つ顧客をクラスターにグループ化し、各クラスターの自転車の購入を予測します。 新しいモデルの列の使用法とプロパティを変更することはできますが、 `TM_Clustering` このチュートリアルではモデルを変更する必要はありません。  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>Naive Bayes マイニング モデルを作成するには  
  
1.  データマイニングデザイナーの [**マイニングモデル**] タブで、[**構造**列] を右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
2.  [**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に「」と入力 `TM_NaiveBayes` します。  
  
3.  [**アルゴリズム名**] で [ **Microsoft Naive Bayes**] を選択し、[ **OK**] をクリックします。  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes アルゴリズムでは、継続している**Age**と**年収**の列がサポートされていないことを示すメッセージが表示されます。  
  
4.  [**はい**] をクリックしてメッセージを確認し、続行します。  
  
 データマイニングデザイナーの [**マイニングモデル**] タブに新しいモデルが表示されます。 このタブでは、すべてのモデルの列の使用法とプロパティを変更できますが、このチュートリアルではモデルを変更する必要はありません `TM_NaiveBayes` 。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [「&#40;基本的なデータマイニングチュートリアル」では、対象となるメーリングの構造でのモデルの処理&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Analysis Services データマイニング &#40;構造へのマイニングモデルの追加&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [データ マイニング オブジェクトの移動](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  

---
title: 相互検証レポートのメジャー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
author: minewiskan
ms.author: owend
ms.openlocfilehash: b71c04551efc17b52f969a9a632241e7d235afd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645919"
---
# <a name="measures-in-the-cross-validation-report"></a>相互検証レポートのメジャー
  相互検証では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はマイニング構造のデータを複数のセクションにパーティション分割し、構造および関連マイニング モデルのテストを反復的に実行します。 この分析に基づき、構造および各モデルの標準の精度のメジャーを出力します。  
  
 レポートでは、データ内のフォールドの数や各フォールド内のデータの量に関するいくつかの基本情報に加えて、データの分布を示す一連の一般的な基準が表示されます。 それぞれのセクションに対する一般的な基準を比較することで、構造またはモデルの信頼性を評価できます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、マイニング モデルの一連の詳細メジャーも表示されます。 これらのメジャーは、分析するモデルの種類や、不連続であるか連続であるかなど属性の型によって異なります。  
  
 ここでは、 **[相互検証]** レポートに含まれるメジャーおよびその意味の一覧を示します。 各メジャーの計算方法の詳細については、「 [クロス検証の式](cross-validation-formulas.md)」を参照してください。  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>相互検証レポートのメジャーの一覧  
 次の表は、相互検証レポートに表示されるメジャーの一覧を示します。 メジャーは、表の左の列に表示されている *テストの種類*でグループ化されています。 右の列には、レポートに表示されるメジャーの名前、および意味に関する簡単な説明を示します。  
  
|テストの種類|基準と説明|  
|---------------|-------------------------------|  
|クラスタリング|クラスターモデルに適用されるメジャー:<br /><br /> **ケースの確率**: このメジャーは、通常、ケースが特定のクラスターに属している可能性を示します。 <br />                      相互検証の場合、スコアが集計された後、ケースの数で割られます。スコアは、ケースの平均確率となります。|  
|分類|分類モデルに適用されるメジャー:<br /><br /> **真陽性**/<br />                      **真の負の値** / **偽陽性** / **False 陽性**: 予測された状態が対象の状態と一致するパーティション内の行または値の数と、予測確率が指定したしきい値を超えています。 対象の属性の不足値があるケースは除外されます。つまり、すべての値のカウントが加算されない可能性があります。|  
||**成功/失敗**: 予測された状態が対象の状態と一致し、予測確率値が0より大きいパーティション内の行または値の数。|  
|Likelihood|複数のモデルの種類に適用される確率メジャー:<br /><br /> **リフト**: テストケースの確率に対する実際の予測確率の比率。 対象の属性の不足値があるケースは除外されます。 通常、モデルが使用されるときに対象の結果の確率がどれだけ向上するかを示します。<br /><br /> **平方根平均二乗誤差**: パーティション内のケースの数で割った、すべてのパーティションケースの平均誤差の平方根。対象の属性の不足値がある行は除外されます。 RMSE は、予測モデルの一般的な推定機能です。 スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。<br /><br /> **ログスコア**: 集計された各ケースの実際の確率の対数。入力データセットの行数で割った値 (対象の属性の欠損値がある行は除く)。 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近い数値ほど、良いスコアになります。 生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。|  
|推定|連続する数値属性を予測する推定モデルにのみ適用されるメジャー:<br /><br /> **平方根平均二乗誤差**: 予測値が実際の値と比較されるときの平均誤差。 RMSE は、予測モデルの一般的な推定機能です。 スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。<br /><br /> **平均絶対誤差**: 予測値が実際の値と比較されるときの平均誤差。誤差の絶対合計の平均として計算されます。 平均絶対誤差は、予測全体が実際の値にどの程度近いかを判断するときに便利です。 小さいスコアは、予測が正確だったことを意味します。<br /><br /> **ログスコア**: 集計された各ケースの実際の確率の対数。入力データセットの行数で割った値 (対象の属性の欠損値がある行は除く)。 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近い数値ほど、良いスコアになります。 生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。|  
|集計|集計メジャーは、各パーティションの結果における分散を示します。<br /><br /> **平均**: 特定のメジャーのパーティション値の平均。<br /><br /> **標準偏差**: モデル内のすべてのパーティションにわたる、特定のメジャーの平均値からの偏差の平均です。 相互検証の場合、このスコアの値が高いことは、フォールドの間の変動が大きいことを意味します。|  
  
## <a name="see-also"></a>参照  
 [テストおよび検証 &#40;データ マイニング&#41;](testing-and-validation-data-mining.md)  
  
  
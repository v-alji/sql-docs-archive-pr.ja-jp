---
title: 行の制限 (パーティションウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b0acc9ab24cfe92877d9abcd86353c85b4f8905
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633398"
---
# <a name="restrict-rows-partition-wizard"></a>[行の制限] (パーティション ウィザード)
  **[行の制限]** ページを使用すると、指定したテーブルから取得、集計されて、パーティションに含まれる行を制限できます。  
  
> [!NOTE]  
>   このページは、 **[基になる情報の指定]** ページでテーブルを 1 つ選択した場合にのみ表示されます。  
  
> [!CAUTION]  
>   他のパーティションで使用されている **[基になる情報の指定]** ページの **[使用できるテーブル]** でテーブルを指定した場合は、 **[行の制限]** ページでクエリを指定するか、キューブでリスクの複製データを指定する必要があります。  
  
## <a name="options"></a>Options  
 **[クエリを指定して行を制限する]**  
 **[クエリ]** ボックスに、行を制限するクエリを入力します。  
  
 このオプションを選択していて **[クエリ]** が空の場合、以前に選択したテーブルからすべての列と行を取得する SQL ステートメントと共に、オプションが設定されます。  
  
 **クエリ**  
 パーティションの処理時に、テーブルから行を取得する場合に使用される SQL ステートメントを、入力または変更します。  
  
> [!IMPORTANT]  
>  WHERE 句を指定することにより、レコードのサブセットをこのパーティションで使用できます。 複数のパーティションが 1 つのファクト テーブルに基づいている場合は、データを複製しないでください。  
  
 **確認事項**  
 **[クエリ]** のステートメントが有効な SQL ステートメントであることを確認します。  
  
## <a name="see-also"></a>参照  
 [パーティション (Analysis Services - 多次元データ)](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  

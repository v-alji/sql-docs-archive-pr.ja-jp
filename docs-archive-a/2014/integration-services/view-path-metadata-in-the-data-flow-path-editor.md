---
title: データフローパスエディターでパスのメタデータを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d84e14c2bc42ac4b831a4d1a3321d3e8b4acf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631140"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a>データ フロー パス エディターでパスのメタデータを表示する
  パスは、2 つのデータ フロー コンポーネントを連結します。 パスのメタデータを表示する場合、データ フローには、2 つ以上の連結されたデータ フロー コンポーネントをあらかじめ含めておく必要があります。 詳細については、「 [データ フローでコンポーネントを追加または削除する](data-flow/add-or-delete-a-component-in-a-data-flow.md) 」と「 [データ フロー内でコンポーネントを連結する](data-flow/connect-components-in-a-data-flow.md)」を参照してください。  
  
### <a name="to-view-path-metadata"></a>パスのメタデータを表示するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、パスをダブルクリックします。  
  
4.  **[データ フロー パス エディター]** ダイアログ ボックスで、 **[メタデータ]** をクリックします。  
  
5.  パスのメタデータが表示されます。メタデータには、各列の列名、データ型、有効桁数、小数点以下桁数、データ長、コード ページ、および基になるコンポーネントの名前が含まれます。  
  
6.  メタデータをコピーするには、 **[クリップボードにコピー]** をクリックします。  
  
7.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Integration Services のパス](data-flow/integration-services-paths.md)   
 [データ フロー](data-flow/data-flow.md)  
  
  

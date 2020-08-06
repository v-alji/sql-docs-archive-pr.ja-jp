---
title: バージョンをコミットする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715538"
---
# <a name="commit-a-version-master-data-services"></a>バージョンをコミットする (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをコミットして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。 コミットしたバージョンはロック解除できません。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   バージョンのステータスは、 **[ロック済み]** である必要があります。 詳細については、「 [バージョンをロックする (マスター データ サービス)](../../2014/master-data-services/lock-a-version-master-data-services.md)」を参照してください。  
  
-   すべてのメンバーが正常に検証されている必要があります。  
  
### <a name="to-commit-a-version"></a>バージョンをコミットするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  **[バージョンの管理]** ページのメニュー バーの **[バージョンの検証]** をクリックします。  
  
3.  **[バージョンの検証]** ページで、コミットするモデルおよびバージョンを選択します。  
  
4.  **[コミット]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [バージョン フラグを作成する (マスター データ サービス)](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [バージョンにフラグを割り当てる (マスター データ サービス)](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [バージョンをコピーする (マスター データ サービス)](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [バージョン (マスター データ サービス)](../../2014/master-data-services/versions-master-data-services.md)  
  
  

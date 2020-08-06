---
title: トランザクションを破棄する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fb5b1b0932b65b1d6f8fe7b1bc842836e21aaca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714450"
---
# <a name="reverse-a-transaction-master-data-services"></a>トランザクションを破棄する (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、管理者は、アクションを元に戻す必要があるときにトランザクションを破棄できます。 トランザクションの例としては、属性値の変更、階層の移動、メンバーの削除などがあります。  
  
## <a name="prerequisites"></a>前提条件  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-reverse-a-transaction"></a>トランザクションを破棄するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]** をクリックします。  
  
2.  メニュー バーの **[トランザクション]** をクリックします。  
  
3.  **[トランザクション]** ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
5.  破棄するトランザクションのグリッド内の行をクリックします。  
  
6.  **[トランザクションの破棄]** をクリックします。  
  
7.  確認のダイアログ ボックスで **[OK]** をクリックします。 破棄されたトランザクションを記録するために、別のトランザクションがグリッドに追加されます。  
  
## <a name="see-also"></a>参照  
 [トランザクション &#40;マスターデータサービス&#41;](../../2014/master-data-services/transactions-master-data-services.md)   
 [メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  

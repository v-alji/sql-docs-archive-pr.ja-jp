---
title: '[権限借用情報] ダイアログボックス (テーブルのインポートウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712606"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>[権限借用情報] ダイアログ ボックス (テーブル インポート ウィザード)
  **[権限借用情報]** ページを使用して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がデータ ソースに接続する際に使用される資格情報を指定します。 資格情報の偽装の詳細については、「[権限借用 &#40;SSAS 表形式&#41;](tabular-models/impersonation-ssas-tabular.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **[特定の Windows ユーザー名とパスワード]**  
 表形式モデルで指定した Windows ユーザー アカウントのセキュリティ資格情報を使用するには、このオプションを使用します。  
  
 **ユーザー名**  
 使用するユーザー アカウントのドメインと名前を入力します。 次の形式を使用します。  
  
 *\<Domain name>* **\\** *\<User account name>*  
  
 このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。  
  
 **パスワード**  
 テーブル モデルで使用するユーザー アカウントのパスワードを入力します。  
  
 このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。  
  
 **サービス アカウント**  
 このオプションを選択すると、モデルを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サービスに関連付けられているセキュリティ資格情報が使用されます。  
  
## <a name="see-also"></a>参照  
 [権限借用 (SSAS テーブル)](tabular-models/impersonation-ssas-tabular.md)  
  
  

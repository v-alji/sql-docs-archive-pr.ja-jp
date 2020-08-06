---
title: 分散再生クライアントの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 53124029483c25ed7894b279283e1de02c647350
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645368"
---
# <a name="distributed-replay-client-configuration"></a>分散再生クライアントの構成
  **インストール ウィザードの** [分散再生クライアントの構成] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページを使用して、分散再生クライアント サービスに対する管理権限を付与するユーザーを指定します。  
  
 管理権限を持つユーザーには、分散再生クライアント サービスへの無制限のアクセス許可が与えられます。  
  
## <a name="options"></a>Options  
 **[コントローラー名]**  
 これは省略可能なパラメーターで、既定値は \<*blank*> です。  
  
 分散再生クライアント サービスと通信するクライアント コンピューターであるコントローラーの名前を入力します。 次のことを考慮してください。  
  
-   名前は完全修飾ドメイン名 (FQDN) である必要があります。 たとえば、Microsoft の製品階層の server1 というホストに、server1.products.microsoft.com という FQDN を設定できます。  
  
-   コントローラーを既にセットアップしてある場合は、各クライアントを構成するときにコントローラーの名前を入力します。  
  
-   コントローラーをまだセットアップしていない場合は、コントローラー名を空白にしておくことができます。 ただし、コントローラー名を **クライアント構成** ファイルに手動で入力する必要があります。  
  
 **作業ディレクトリ**  
 分散再生クライアント サービス用の作業ディレクトリを指定します。  
  
 既定の作業ディレクトリは、\<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\ です。  
  
 **[結果ディレクトリ]**  
 分散再生クライアント サービス用の結果ディレクトリを指定します。  
  
 既定の結果ディレクトリは、\<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\ です。  
  
  

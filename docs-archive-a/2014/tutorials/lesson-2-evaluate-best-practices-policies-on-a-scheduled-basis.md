---
title: 'レッスン 2: スケジュールに基づくベストプラクティスポリシーの評価 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a454e38ec2f07bf9867183a3894ac4ea001a942e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634181"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a>レッスン 2: スケジュールに基づくベスト プラクティス ポリシーの評価
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスについて、スケジュールに基づくベスト プラクティス ポリシーの評価を構成できます。 ベスト プラクティス ポリシーをスケジュールに基づいて実行するよう構成するには、ポリシーを対象インスタンスにインポートする必要があります。  
  
 スケジュールされたポリシーを複数のサーバーに配置するには、ポリシーを 1 つのインスタンスにインポートして、各ポリシーのスケジュールを構成し、スケジュールされたポリシーをフォルダーにエクスポートし、登録済みサーバーを通じてスケジュールされたポリシーを対象インスタンスに配置します。  
  
> [!IMPORTANT]  
>  対象インスタンスは、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョンを実行している必要があります。 オートメーションではポリシーがインスタンス上にローカルに格納されている必要がありますが、これは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ではサポートされていません。  
  
 このレッスンでは、次の作業を行います。  
  
-   ベスト プラクティス ポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスにインポートします。  
  
-   ポリシーをスケジュールに基づいて実行するよう構成します。  
  
-   スケジュールされたベスト プラクティス ポリシーを登録済みサーバーを通じて複数のインスタンスに配置します。  
  
 このレッスンの内容は次のとおりです。  
  
-   [単一インスタンスへのポリシーのインポート](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [ポリシーのスケジュール設定](../../2014/tutorials/schedule-the-policies.md)  
  
-   [スケジュールされたポリシーの複数インスタンスへの配置](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a>参照  
 [中央管理サーバーを使用して複数のサーバーを管理する](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  

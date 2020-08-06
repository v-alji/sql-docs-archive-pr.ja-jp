---
title: SharePoint サーバーの全体管理でレポートサーバーの File Sync 機能をアクティブにする |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642627"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする

[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバー ファイル同期機能では、SharePoint イベント ハンドラーを利用して、レポート サーバー カタログをドキュメント ライブラリのアイテムと同期します。 この機能は、ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合に役立ちます。 ファイル同期機能がアクティブ化されていない場合でも、コンテンツは同期されますが、頻繁には同期されません。  
  
ファイル同期機能は、SharePoint 製品用 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] アドインをインストールしてから SharePoint サイトの管理でアクティブ化できます。  
  
この機能は、サイトごとに手動でアクティブ化および非アクティブ化できますが、サイト コレクション レベルではアクティブ化および非アクティブ化することはできません。  
  
## <a name="prerequisites"></a>前提条件  
 SharePoint 用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。 アドインがインストールされていない場合、ファイル同期機能はサイト機能の一覧に表示されません。  
  
 インストールを確認するには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows の **コントロール パネル**でインストール済みアプリケーションの一覧を表示します。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインがインストールされている場合は、このトピックの手順に従ってレポート サーバー ファイル同期機能をアクティブ化できます。  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>サイトの Reporting Services ファイル同期機能をアクティブ化または非アクティブ化するには  
  
1.  サイトのメインページで、[**サイトの操作**] メニューをクリックし、[**サイトの設定**] をクリックします。  
  
2.  [**サイトの操作**] で、[サイトの**機能の管理**] をクリックします。  
  
3.  一覧で **[レポート サーバー ファイル同期]** を見つけます。  
  
4.  **[アクティブ化]** をクリックします。  
  
> [!NOTE]  
>  レポート サーバー ファイル同期機能を非アクティブ化するには、 **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
## <a name="see-also"></a>参照  
 [レポートパーツ &#40;レポートビルダーと SSRS&#41;のトラブルシューティング](report-parts-report-builder-and-ssrs.md)   
 [SharePoint でのレポートサーバーと Power View の統合機能のアクティブ化](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  

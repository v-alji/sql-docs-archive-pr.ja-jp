---
title: SharePoint ライブラリへのレポートの保存 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49878a0d7115a11e804382cb5139aa0ec7b3d254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640738"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a>SharePoint ライブラリへのレポートの保存 (レポート ビルダー)
  SharePoint 統合用に構成されているレポート サーバーにレポートを保存するには、SharePoint サーバーを参照して、レポート サーバーへの接続を確立する必要があります。 レポート定義では、レポートに関連するアイテムへのすべての参照で、SharePoint レポート サーバー固有の値を使用する必要があります。 関連するアイテムには、サブレポート、詳細レポート、および Web ベースの画像などのリソースがあります。 詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。  
  
 プロジェクトにプロパティを設定するには、SharePoint サイトの **メンバー** 権限または **所有者** 権限が必要です。  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a>SharePoint サイトにレポートを保存するには  
  
1.  レポート ビルダーのボタンの **[保存]** をクリックします。 [**名前を付けて保存** _\<Report Item>_ ] ダイアログボックスが表示されます。  
  
    > [!NOTE]  
    >  レポートを再保存すると、自動的に以前の場所に再保存されます。 場所を変更するには、 **[名前を付けて保存]** を使用します。  
  
2.  必要に応じて、 **[最近使ったサイトとサーバー]** をクリックし、最近使用したレポート サーバーと SharePoint サイトの一覧を表示します。  
  
3.  SharePoint サイトを参照して指定し、 **[保存]** をクリックします。  
  
    > [!NOTE]  
    >  レポートを変更した後、保存せずに 10 時間経過すると、サーバーから切断されます。変更内容は保存されません。 その場合は、右下のステータス バーで **[切断]** をクリックしてから **[接続]** をクリックします。 使用可能なサーバーのリストに、直近のサーバーが表示されます。 それを選択すると、レポートが再度接続されます。  
  
## <a name="see-also"></a>参照  
 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  

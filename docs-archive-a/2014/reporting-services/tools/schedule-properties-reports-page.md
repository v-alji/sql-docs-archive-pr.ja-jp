---
title: '[スケジュールのプロパティ] ([レポート] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da0b5255e73522572fa22da8668329a28f108104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634820"
---
# <a name="schedule-properties-reports-page"></a>[スケジュールのプロパティ] ([レポート] ページ)
  このページを使用すると、共有データ ソースを使用するすべてのレポートの一覧を表示できます。 スケジュールを使用して、レポート スナップショットの更新、レポート履歴の生成、サブスクリプションのトリガー、またはレポートのキャッシュされたコピーの期限の終了を実行できます。 スケジュールがどのように使用されているかを確認するには、レポートのプロパティおよびサブスクリプション情報を参照します。  
  
 このページには共有スケジュールを使用する各レポートが表示されますが、1 つのレポート内で共有スケジュールが何回使用されるかについては示されません。 たとえば、Company Sales レポートの 20 の異なるサブスクライバーがすべて同じ共有スケジュールを使用してサブスクリプション処理を開始するとします。 この場合、Company Sales レポートでは共有スケジュールの参照が 20 回行われますが、この一覧には 1 回しか表示されません。  
  
 このページを開くには、を起動し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] てレポートサーバーに接続し、[**共有スケジュール**] フォルダーを開きます。共有スケジュールを右クリックし、[**プロパティ**] を選択し、[**レポート**] をクリックします。  
  
> [!NOTE]  
>  この機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。  
  
## <a name="options"></a>Options  
 **フォルダー**  
 レポートのパスを指定します。  
  
 **Report**  
 スケジュールを使用するレポートの名前を指定します。  
  
## <a name="see-also"></a>参照  
 [Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md)   
 [[スケジュール]](../subscriptions/schedules.md)   
 [Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md)   
 [Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [レポート &#40;レポートマネージャーの全般プロパティの構成&#41;](../configure-general-properties-for-a-report-report-manager.md)  
  
  

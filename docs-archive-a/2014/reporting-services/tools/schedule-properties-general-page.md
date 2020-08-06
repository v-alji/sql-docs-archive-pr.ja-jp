---
title: '[スケジュールのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a61837cd977526021be948d8c74a93eba6506e67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634824"
---
# <a name="schedule-properties-general-page"></a>[スケジュールのプロパティ]\([全般] ページ)
  このページを使用すると、共有スケジュールを表示したり変更したりできます。 共有スケジュールは、レポート固有のスケジュールやサブスクリプション固有のスケジュールの代わりに使用できます。 スケジュールに対する変更は、スケジュールを保存した後に適用されます。 スケジュールを編集しても、現在実行中のジョブには影響しません。 使用中のスケジュールを編集すると、そのスケジュールからトリガーされた現在処理中のレポートおよびサブスクリプションはすべて終了できるようになります。  
  
 1 つのスケジュールの中で、複数の頻度を組み合わせて使用することができない場合があります。 たとえば、毎週金曜日の正午と 午後 4 時 00 分まで レポートを実行する場合、実行日を金曜日に指定した日単位のスケジュールを 2 つ作成し、1 つは開始時刻を正午に、 もう 1 つは開始時刻を午後 4 時に設定する必要があります。  
  
 スケジュールは、そのスケジュールをホストおよび処理するレポート サーバーのローカル時間に基づいて処理されます。  
  
 このページを開くには、を起動し、レポートサーバーに接続します。次に、[ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **共有スケジュール**] フォルダーを開き、共有スケジュールを右クリックして、[**プロパティ**] を選択します。  
  
> [!NOTE]  
>  この機能は、すべてのエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるわけではなく、この機能がないエディションを実行している場合は、このページが表示されません。 の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。  
  
## <a name="options"></a>Options  
 **名前**  
 共有スケジュールの名前を指定します。  
  
 **[このスケジュールの実行開始日]**  
 このスケジュールの開始日を指定します。  
  
 **[このスケジュールの終了日]**  
 このスケジュールの終了日を指定します。  
  
 **Type**  
 定期的なパターンが主に時間、日、週、月のどの単位に基づくか、または一度だけ実行するかを指定します。  
  
 **[時間]\([定期的なパターン])**  
 スケジュール設定した操作を一定時間ごとに実行する (たとえば 6 時間ごとにレポートを実行する) ためのオプションを指定します。 間隔は時間と分で指定できます。  
  
 **[日] ([定期的なパターン])**  
 スケジュール設定した操作を数日間隔で実行する (たとえば 2 日ごとにレポートを実行する) ためのオプションを指定します。 間隔は日数で指定し、スケジュールを実行する時と分を指定できます。  
  
 **[週] ([定期的なパターン])**  
 スケジュール設定した操作を毎週実行するか、繰り返しのパターンが週単位 (たとえば隔週でレポートを実行する) の場合のオプションを指定します。 週間スケジュールについて、スケジュールを実行する日、時、分を指定できます。  
  
 **[月]\([定期的なパターン])**  
 スケジュール設定した操作を毎月実行するか、繰り返しのパターンが月単位の場合のオプションを指定します。 月間スケジュールについて、スケジュールを実行する日、時、分を指定できます。 スケジュールでは特定の月を指定しなくてもかまいません。  
  
 **1 度**  
 特定の日時に 1 回のみスケジュールを実行するように指定します。  
  
## <a name="see-also"></a>参照  
 [Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md)   
 [Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md)   
 [スケジュール](../subscriptions/schedules.md)  
  
  

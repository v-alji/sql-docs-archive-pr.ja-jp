---
title: '[資格情報] ([データソースのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e47ba571e2b0adf2738499c1d027a4edde86e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642599"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a>[資格情報] ([データ ソースのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  **[データ ソースのプロパティ]** ダイアログ ボックスの **[資格情報]** を選択すると、レポート内の埋め込みデータ ソースに接続するための資格情報を表示および変更できます。 指定した資格情報は、レポートのプレビュー時、データ ソースにアクセスする際に使用されます。 詳細については、「 [レポート ビルダーでの資格情報の指定](../../2014/reporting-services/specify-credentials-in-report-builder.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **[Windows 認証 (統合セキュリティ) を使用する]**  
 Windows 認証を使用します。  
  
 **[次のユーザー名とパスワードを使用]**  
 特定のユーザー名とパスワードを指定します。 埋め込みデータ ソースの場合、レポート サーバー プロジェクトをターゲット サーバーにパブリッシュするときに、データベース用の保存された資格情報としてユーザー名とパスワードが保存されます。 ユーザー名とパスワードを Windows 資格情報として使用する場合は、ターゲット サーバーにパブリッシュされた共有データ ソースのプロパティを変更できます。 詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ドキュメントの「[共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)」を参照してください。  
  
 **ユーザー名**  
 データ ソースへのログオンに使用するユーザー名を入力します。  
  
 **パスワード**  
 データ ソースへのログオンに使用するパスワードを入力します。  
  
 **資格情報を要求する**  
 レポートの実行時に資格情報の入力を要求します。  
  
 **[プロンプト文字列の入力]**  
 データ ソースのログイン資格情報を指定するようユーザーに指示する文を入力します。  
  
 **資格情報がありません**  
 データ ソースの資格情報を指定しません。 このオプションは、データ ソースで資格情報が不要な場合、または他の方法で資格情報を渡している場合にのみ機能します。  
  
 同じデータ拡張機能から、レポート サーバーで自動実行アカウントを構成する必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ドキュメントの「[外部データ ソースのデータを追加する (SSRS)](report-data/add-data-from-external-data-sources-ssrs.md)」および「[自動実行アカウントの構成 (SSRS 構成マネージャー)](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」で、対応するデータ ソースの種類に関するトピックを参照してください。  
  
## <a name="see-also"></a>参照  
 [ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [[データソースのプロパティ] ダイアログボックスの [全般 &#40;レポートビルダー&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md)   
 [データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)  
  
  

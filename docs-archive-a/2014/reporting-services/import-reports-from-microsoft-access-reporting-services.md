---
title: Microsoft Access からレポートをインポートする (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643715"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Microsoft Access からレポートをインポートする (Reporting Services)
  レポートデザイナーで [!INCLUDE[msCoName](../includes/msconame-md.md)] は、Access データベースまたはプロジェクトからレポートをインポートできます。 レポート デザイナーがインストールされているコンピューターに、Access 2002 以降のバージョンがインストールされている必要があります。  
  
 インポート機能を使用すると、Access データベースまたはプロジェクト ファイルのすべてのレポートがインポートされます。 Access ファイルに多数のレポートが含まれている場合は、レポートのインポート先に別のレポート プロジェクトを作成し、その後各 RDL ファイルをメインのレポート プロジェクトで開くことをお勧めします。 レポートは、レポート デザイナーにインポートした後に、編集できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Access のレポート オブジェクトがすべてサポートされているわけではありません。 変換されていない項目は、[**タスク一覧**] ウィンドウに表示されます。 詳細については、「[サポートされているアクセスレポート機能 &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)」を参照してください。  
  
### <a name="to-import-reports-from-microsoft-access"></a>Microsoft Access からレポートをインポートするには  
  
1.  レポートをインポートするプロジェクトを開くか、作成します。  
  
2.  [**プロジェクト**] メニューの [**レポートのインポート**] をポイントし、[ **Microsoft access**] をクリックします。 または、ソリューションエクスプローラーでプロジェクトを右クリックして [**レポートのインポート**] をポイントし、[ **Microsoft access**] をクリックします。  
  
3.  [**開く**] ダイアログボックスで、レポートが格納されている Access データベース (.mdb、.accdb) またはプロジェクト (.adp) を選択し、[**開く**] をクリックします。 データベースまたはプロジェクト ファイルのすべてのレポートがインポートされて、ソリューション エクスプローラーの [レポート] フォルダーに一覧表示されます。  
  
4.  [**タスク一覧**] ウィンドウでビルドエラーを確認します。 **タスク一覧**ウィンドウを表示するには、[**表示**] メニューの [**その他のウィンドウ**] をポイントし、[**タスク一覧**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  

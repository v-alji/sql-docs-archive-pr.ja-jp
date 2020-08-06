---
title: レポートのパブリッシュ |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb54308a6b15260d4c336950f231d0ee40836430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631623"
---
# <a name="publish-reports"></a>レポートのパブリッシュ
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]から、プロジェクトを配置してレポート サーバーにレポート サーバー プロジェクト内のすべてのレポートおよび共有データ ソースをパブリッシュしたり、単一のレポートをパブリッシュしたりできます。 レポートをパブリッシュする前に、ターゲット レポート サーバーの URL を指定する必要があります。 詳細については、「[配置プロパティを設定する (Reporting Services)](tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] バージョンを使用すると、 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] と [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] の両方のレポートを開くことや、変更、プレビュー、保存、およびパブリッシュを行うことができます。 詳細については、「 [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)には含まれていません。  
  
### <a name="to-publish-all-reports-in-a-project"></a>プロジェクトのすべてのレポートをパブリッシュするには  
  
-   [**ビルド**] メニューの [**配置 \<report project name> **] をクリックします。 または、ソリューション エクスプローラーでレポート プロジェクトを右クリックして、 **[配置]** をクリックします。 パブリッシュ処理の状態が、[出力] ウィンドウに表示されます。  
  
    > [!NOTE]  
    >  レポート サーバー プロジェクトを配置すると、レポート プロジェクトの共有データ ソースも配置されます。  
  
### <a name="to-publish-a-single-report"></a>1 つのレポートをパブリッシュするには  
  
-   ソリューション エクスプローラーで、レポートを右クリックし、 **[配置]** をクリックします。 パブリッシュ処理の状態が、[出力] ウィンドウに表示されます。  
  
    > [!NOTE]  
    >  レポートをパブリッシュするときは、レポートが使用する共有データ ソースを配置する必要もあります。  
  
## <a name="see-also"></a>参照  
 [データソースとレポートのパブリッシュ](reports/publishing-data-sources-and-reports.md)   
 [レポートのプレビュー](reports/previewing-reports.md)   
 [レポートサーバーへのレポートのパブリッシュ](reports/publishing-reports-to-a-report-server.md)   
 [レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  

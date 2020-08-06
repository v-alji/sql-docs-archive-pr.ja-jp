---
title: RDL スキーマから生成されたクラスを使用したレポートの更新 (SSRS チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f3972b8e1af6d50ccc6f5188c8f671fe333ebce8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632821"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>RDL スキーマから生成されたクラスを使ったレポートの更新 (SSRS チュートリアル)
  このチュートリアルでは、XML スキーマ定義ツール (Xsd.exe) を使用して、クラスを使用してレポート定義ファイル (.rdl および .rdlc) をシリアル化および逆シリアル化できるクラスを生成する方法について説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> ます。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルの過程で、次のアクティビティを完了します。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]コンソールアプリケーションプロジェクトテンプレートを使用してアプリケーションを作成し [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ます。  
  
-   **Xsd**ツールを使用して、レポート定義言語 (RDL) スキーマからクラスを生成します。  
  
-   レポート サーバーに接続し、レポート定義を取得する。  
  
-   レポート定義ファイルを更新するコードを記述する。  
  
-   更新したレポート定義をレポート サーバーに保存する。  
  
-   RDL スキーマ アプリケーション (VB/C#) を実行する。  
  
> [!NOTE]  
>  このチュートリアルのコード サンプルでは、レポートに説明がないため失敗する場合があります。 失敗する理由は、説明が指定されていないレポートには説明のプロパティが存在しないためです。  
  
## <a name="requirements"></a>必要条件  
 このチュートリアルを完了するには次の準備が必要です。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   レポート サーバーが配置されているコンピューター上のレポート サーバー Web サービスにアクセスし、レポートをパブリッシュできる十分な権限。  
  
-   [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] のインスタンスにインストールされた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サンプル データベース。  
  
-   レポート サーバーにインストールされているレポート。 このチュートリアルでは、サンプル レポート Company Sales 2012 を使用します。 サンプルレポートの詳細については、「 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。  
  
> [!NOTE]  
>  サンプルはセットアップ中に自動的にインストールされませんが、いつでもインストールできます。 サンプルの詳細については、「 [SQL Server Product samples](https://go.microsoft.com/fwlink/?LinkId=182887)」を参照してください。  
  
 **チュートリアルの推定所要時間:** 30 分  
  
## <a name="tasks"></a>タスク  
 [レッスン 1 : RDL スキーマ Visual Studio プロジェクトの作成](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [レッスン 2: xsd ツールを使用して RDL スキーマからクラスを作成](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [レッスン 3 : レポート サーバーからのレポート定義の読み込み](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [レッスン 4: プログラムによるレポート定義の更新](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [レッスン 5: レポート サーバーへのレポート定義のパブリッシュ](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [レッスン 6: RDL スキーマアプリケーションを実行する &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>参照  
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  

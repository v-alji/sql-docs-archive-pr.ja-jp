---
title: データ処理拡張機能をレポート デザイナーに配置する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56bd56e9d8eeeeff1781f22b42cf0eb1ce706fa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741598"
---
# <a name="how-to-deploy-a-data-processing-extension-to-report-designer"></a>データ処理拡張機能をレポート デザイナーに配置する方法
  レポートを設計する際、レポート デザイナーは、データ処理拡張機能を使用してデータを取得し、処理します。 データ処理拡張機能アセンブリは、プライベート アセンブリとしてレポート デザイナーに配置する必要があります。 さらに、レポート デザイナー構成ファイル RSReportDesigner.config にエントリを作成する必要があります。  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>データ処理拡張機能のアセンブリを配置するには  
  
1.  ステージング場所から Report Designer ディレクトリにアセンブリをコピーします。 Report Designer ディレクトリの既定の場所は、C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。  
  
2.  アセンブリ ファイルをコピーした後、RSReportDesigner.config ファイルを開きます。 RSReportDesigner.config ファイルも Report Designer ディレクトリにあります。 データ処理拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。 構成ファイルは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] またはメモ帳などのシンプルなテキスト エディターを使用して開くことができます。  
  
3.  RSReportDesigner.config ファイルで **Data** 要素を探します。 新しく作成したデータ処理拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  、、および属性の値を持つ**extension**要素を含む、データ処理拡張機能のエントリを追加し `Name` `Type` `Visible` ます。 このエントリは、次のようになります。  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     `Name` の値は、データ処理拡張機能の一意な名前です。 `Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスおよび <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前が続きます。.dll ファイル拡張子は付けません。 既定では、データ処理拡張機能が表示されます。 レポートデザイナーなどのユーザーインターフェイスから拡張機能を非表示にするには、 `Visible` **拡張**要素に属性を追加し、それをに設定し `false` ます。  
  
5.  最後に、拡張機能の **FullTrust** アクセス許可を与えるカスタム アセンブリのコード グループを追加します。 これを行うには、既定では C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies にある rspreviewpolicy.config ファイルにコード グループを追加します。 このコード グループは、次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL 構成要素は、データ処理拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。 [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)] のコード アクセス セキュリティの詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)」を参照してください。  
  
## <a name="generic-query-designer"></a>汎用クエリ デザイナー  
 レポート デザイナーには、カスタム データ処理拡張機能で使用できる汎用クエリ デザイナーが用意されています。 このデザイナーは、クエリ ペインと結果ペインの 2 つのペインで構成されます。 この汎用デザイナーは、上記のグラフィカル インターフェイスでサポートされていないクエリの記述に使用できます。 グラフィカル クエリ デザイナーと異なり、汎用クエリ デザイナーでは、クエリ構文のチェックやクエリの再構成は行われません。  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a>カスタム拡張機能で汎用クエリ デザイナーを有効にするには  
  
-   次のエントリを**デザイナー**要素の下の RSReportDesigner.config ファイルに追加し、 `Name` 属性を前のエントリで指定した名前に置き換えます。  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a>デプロイの確認  
 配置を検証するには、ローカル コンピューターの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインスタンスをすべて閉じておく必要があります。 現在のセッションをすべて終了したら、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で新しいレポート プロジェクトを作成します。これによって、データ処理拡張機能がレポート デザイナーに正常に配置されたかどうかを確認できます。 レポート用の新しいデータセットを作成するとき、使用可能なデータ ソースの種類の一覧に新しい拡張機能が表示されます。  
  
## <a name="see-also"></a>参照  
 [データ処理拡張機能の配置](deploying-a-data-processing-extension.md)   
 [Reporting Services の拡張機能](../reporting-services-extensions.md)   
 [データ処理拡張機能の実装](implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  

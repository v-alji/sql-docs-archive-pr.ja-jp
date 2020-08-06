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
# <a name="how-to-deploy-a-data-processing-extension-to-report-designer"></a><span data-ttu-id="2235e-102">データ処理拡張機能をレポート デザイナーに配置する方法</span><span class="sxs-lookup"><span data-stu-id="2235e-102">How to: Deploy a Data Processing Extension to Report Designer</span></span>
  <span data-ttu-id="2235e-103">レポートを設計する際、レポート デザイナーは、データ処理拡張機能を使用してデータを取得し、処理します。</span><span class="sxs-lookup"><span data-stu-id="2235e-103">Report Designer uses data processing extensions for retrieving and processing data while you are designing reports.</span></span> <span data-ttu-id="2235e-104">データ処理拡張機能アセンブリは、プライベート アセンブリとしてレポート デザイナーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2235e-104">You should deploy your data processing extension assembly to Report Designer as a private assembly.</span></span> <span data-ttu-id="2235e-105">さらに、レポート デザイナー構成ファイル RSReportDesigner.config にエントリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2235e-105">You also need to make an entry in the Report Designer configuration file, RSReportDesigner.config.</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="2235e-106">データ処理拡張機能のアセンブリを配置するには</span><span class="sxs-lookup"><span data-stu-id="2235e-106">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="2235e-107">ステージング場所から Report Designer ディレクトリにアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="2235e-107">Copy your assembly from your staging location to the Report Designer directory.</span></span> <span data-ttu-id="2235e-108">Report Designer ディレクトリの既定の場所は、C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。</span><span class="sxs-lookup"><span data-stu-id="2235e-108">The default location of the Report Designer directory is C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="2235e-109">アセンブリ ファイルをコピーした後、RSReportDesigner.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2235e-109">After the assembly file is copied, open the RSReportDesigner.config file.</span></span> <span data-ttu-id="2235e-110">RSReportDesigner.config ファイルも Report Designer ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="2235e-110">The RSReportDesigner.config file is also located in the Report Designer directory.</span></span> <span data-ttu-id="2235e-111">データ処理拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2235e-111">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="2235e-112">構成ファイルは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] またはメモ帳などのシンプルなテキスト エディターを使用して開くことができます。</span><span class="sxs-lookup"><span data-stu-id="2235e-112">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or with a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="2235e-113">RSReportDesigner.config ファイルで **Data** 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="2235e-113">Locate the **Data** element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="2235e-114">新しく作成したデータ処理拡張機能のエントリは、次の場所に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2235e-114">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="2235e-115">、、および属性の値を持つ**extension**要素を含む、データ処理拡張機能のエントリを追加し `Name` `Type` `Visible` ます。</span><span class="sxs-lookup"><span data-stu-id="2235e-115">Add an entry for your data processing extension which includes an **Extension** element with values for the `Name`, `Type`, and `Visible` attributes.</span></span> <span data-ttu-id="2235e-116">このエントリは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2235e-116">Your entry might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="2235e-117">`Name` の値は、データ処理拡張機能の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="2235e-117">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="2235e-118">`Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスおよび <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前が続きます。.dll ファイル拡張子は付けません。</span><span class="sxs-lookup"><span data-stu-id="2235e-118">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="2235e-119">既定では、データ処理拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2235e-119">By default, data processing extensions are visible.</span></span> <span data-ttu-id="2235e-120">レポートデザイナーなどのユーザーインターフェイスから拡張機能を非表示にするには、 `Visible` **拡張**要素に属性を追加し、それをに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="2235e-120">To hide an extension from user interfaces, such as Report Designer, add a `Visible` attribute to the **Extension** element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="2235e-121">最後に、拡張機能の **FullTrust** アクセス許可を与えるカスタム アセンブリのコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="2235e-121">Finally, add a code group for your custom assembly that grants **FullTrust** permission for your extension.</span></span> <span data-ttu-id="2235e-122">これを行うには、既定では C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies にある rspreviewpolicy.config ファイルにコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="2235e-122">You do this by adding the code group to the rspreviewpolicy.config file located by default in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span> <span data-ttu-id="2235e-123">このコード グループは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2235e-123">Your code group might look like the following:</span></span>  
  
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
  
 <span data-ttu-id="2235e-124">URL 構成要素は、データ処理拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="2235e-124">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="2235e-125">[!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)] のコード アクセス セキュリティの詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2235e-125">For more information about code access security in [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="generic-query-designer"></a><span data-ttu-id="2235e-126">汎用クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="2235e-126">Generic Query Designer</span></span>  
 <span data-ttu-id="2235e-127">レポート デザイナーには、カスタム データ処理拡張機能で使用できる汎用クエリ デザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2235e-127">Report Designer provides a generic query designer that you can use with custom data processing extensions.</span></span> <span data-ttu-id="2235e-128">このデザイナーは、クエリ ペインと結果ペインの 2 つのペインで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2235e-128">This designer consists of two panes: a query pane and a results pane.</span></span> <span data-ttu-id="2235e-129">この汎用デザイナーは、上記のグラフィカル インターフェイスでサポートされていないクエリの記述に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2235e-129">You can use the generic designer to write queries that are not supported by the graphical interface.</span></span> <span data-ttu-id="2235e-130">グラフィカル クエリ デザイナーと異なり、汎用クエリ デザイナーでは、クエリ構文のチェックやクエリの再構成は行われません。</span><span class="sxs-lookup"><span data-stu-id="2235e-130">Unlike the graphical query designer, the generic query designer does not check query syntax or restructure the query.</span></span>  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a><span data-ttu-id="2235e-131">カスタム拡張機能で汎用クエリ デザイナーを有効にするには</span><span class="sxs-lookup"><span data-stu-id="2235e-131">To enable the generic query designer for a custom extension</span></span>  
  
-   <span data-ttu-id="2235e-132">次のエントリを**デザイナー**要素の下の RSReportDesigner.config ファイルに追加し、 `Name` 属性を前のエントリで指定した名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2235e-132">Add the following entry to the RSReportDesigner.config file under the **Designer** element, replacing the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="2235e-133">デプロイの確認</span><span class="sxs-lookup"><span data-stu-id="2235e-133">Verifying the Deployment</span></span>  
 <span data-ttu-id="2235e-134">配置を検証するには、ローカル コンピューターの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインスタンスをすべて閉じておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2235e-134">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="2235e-135">現在のセッションをすべて終了したら、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で新しいレポート プロジェクトを作成します。これによって、データ処理拡張機能がレポート デザイナーに正常に配置されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2235e-135">After you have ended all current sessions, you can verify whether your data processing extension was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="2235e-136">レポート用の新しいデータセットを作成するとき、使用可能なデータ ソースの種類の一覧に新しい拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2235e-136">Your extension should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2235e-137">参照</span><span class="sxs-lookup"><span data-stu-id="2235e-137">See Also</span></span>  
 <span data-ttu-id="2235e-138">[データ処理拡張機能の配置](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="2235e-138">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="2235e-139">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="2235e-139">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="2235e-140">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="2235e-140">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="2235e-141">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="2235e-141">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  

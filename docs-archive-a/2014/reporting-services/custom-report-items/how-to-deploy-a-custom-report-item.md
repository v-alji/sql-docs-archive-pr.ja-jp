---
title: 方法:カスタム レポート アイテムを配置する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66519610526478caadeb41b48c9823414e88d5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741633"
---
# <a name="how-to-deploy-a-custom-report-item"></a><span data-ttu-id="659fe-102">方法:カスタム レポート アイテムを配置する</span><span class="sxs-lookup"><span data-stu-id="659fe-102">How to: Deploy a Custom Report Item</span></span>
  <span data-ttu-id="659fe-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でカスタム レポート アイテムを配置するには、レポート サーバー構成ファイルを変更し、デザイン時と実行時のコンポーネント アセンブリをレポート デザイナーとレポート サーバーの両方に対する適切なアプリケーション フォルダーにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="659fe-103">To deploy a custom report item in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the report server configuration files and copy the design-time and run-time component assemblies into the appropriate application folders for both Report Designer and the report server.</span></span>  
  
### <a name="to-deploy-a-custom-report-item"></a><span data-ttu-id="659fe-104">カスタム レポート アイテムを配置するには</span><span class="sxs-lookup"><span data-stu-id="659fe-104">To deploy a custom report item</span></span>  
  
1.  <span data-ttu-id="659fe-105">Rsreportdesigner.config ファイルを編集して、デザイナーで使用するカスタム レポート アイテムの実行時とデザイン時のコンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="659fe-105">Edit the Rsreportdesigner.config file to configure the custom report item run-time and design-time components for use in the designer.</span></span> <span data-ttu-id="659fe-106">`ReportItemName` エントリは `CustomReportItemAttribute` クラス内で使用される `CustomReportItemDesigner` 属性と一致する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="659fe-106">Note that the `ReportItemName` entry must match the `CustomReportItemAttribute` attribute used in your `CustomReportItemDesigner` class.</span></span> <span data-ttu-id="659fe-107">例:</span><span class="sxs-lookup"><span data-stu-id="659fe-107">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  <span data-ttu-id="659fe-108">Rsreportserver.config ファイルを編集して、カスタム レポート アイテムの実行時コンポーネントを登録します。</span><span class="sxs-lookup"><span data-stu-id="659fe-108">Edit the Rsreportserver.config file to register the custom report item run-time component.</span></span> <span data-ttu-id="659fe-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="659fe-109">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  <span data-ttu-id="659fe-110">Rsssrvpolicy.config ファイルを編集して、カスタム レポート アイテムに適切な権限を許可する `CodeGroup` を追加します。</span><span class="sxs-lookup"><span data-stu-id="659fe-110">Edit the Rsssrvpolicy.config file to add a `CodeGroup` that grants the proper permissions to the custom report item.</span></span> <span data-ttu-id="659fe-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="659fe-111">For example:</span></span>  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  <span data-ttu-id="659fe-112">カスタム レポート アイテムの実行時コンポーネント DLL を、%ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies ディレクトリと \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="659fe-112">Copy the custom report item run-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies and \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin directories.</span></span>  
  
5.  <span data-ttu-id="659fe-113">カスタム レポート アイテムのデザイン時コンポーネント DLL を %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="659fe-113">Copy the custom report item design-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659fe-114">参照</span><span class="sxs-lookup"><span data-stu-id="659fe-114">See Also</span></span>  
 <span data-ttu-id="659fe-115">[Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="659fe-115">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="659fe-116">カスタム レポート アイテムのクラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="659fe-116">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  

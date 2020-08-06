---
title: 配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52e137d1a866305ec6435a4940fe98448bce5778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646038"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a><span data-ttu-id="293df-102">配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用</span><span class="sxs-lookup"><span data-stu-id="293df-102">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>
  <span data-ttu-id="293df-103"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスは、レポート サーバーに関する情報を取得する場合に使用できるいくつかのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="293df-103">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface exposes several properties that you can use to retrieve information about a report server.</span></span> <span data-ttu-id="293df-104">この情報を使用して、通知とレポートを配信できます。</span><span class="sxs-lookup"><span data-stu-id="293df-104">You can use this information to deliver notifications and reports.</span></span> <span data-ttu-id="293df-105">配信拡張機能のクラスを実装する場合は、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> インターフェイスに必要な <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="293df-105">When implementing your delivery extension class, you implement the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property as required by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="293df-106"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> プロパティは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスを実装するオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="293df-106">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property returns an object that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface.</span></span> <span data-ttu-id="293df-107">このオブジェクトからは、レポート サーバーで現在サポートされる表示拡張機能の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="293df-107">From this object you can get a list of rendering extensions currently supported by the report server.</span></span>  
  
 <span data-ttu-id="293df-108">次の `for` ループを使用すると、 **ArrayList**オブジェクトのレポートサーバーで現在使用できる表示拡張機能の一覧を格納できます。</span><span class="sxs-lookup"><span data-stu-id="293df-108">The following `for` loop could be used to store a list of rendering extensions currently available on the report server in an **ArrayList** object.</span></span>  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 <span data-ttu-id="293df-109"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスの詳細については、「[配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="293df-109">For more information about the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface, see [Using the IDeliveryReportServerInformation Interface for a Delivery Extension](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="293df-110">参照</span><span class="sxs-lookup"><span data-stu-id="293df-110">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="293df-111">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="293df-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="293df-112">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="293df-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  

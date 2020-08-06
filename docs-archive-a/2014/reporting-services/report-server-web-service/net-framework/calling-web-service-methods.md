---
title: Web サービス メソッドの呼び出し | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 87f1485b4e3c0ed064e42bb3b411fece96eba8d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713822"
---
# <a name="calling-web-service-methods"></a><span data-ttu-id="03ef9-102">Web サービス メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="03ef9-102">Calling Web Service Methods</span></span>
  <span data-ttu-id="03ef9-103">プロキシクラスを使用して [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Web サービス操作を呼び出す場合は、そのクラスのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="03ef9-103">When you use a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class to call Web service operations, you do so by using the methods of that class.</span></span> <span data-ttu-id="03ef9-104">これらのメソッドは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] クラス ライブラリにあるクラスの他のメソッドと同じように応答します。</span><span class="sxs-lookup"><span data-stu-id="03ef9-104">These methods respond like any other method of a class in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="03ef9-105">すべての Web サービス メソッドにはパブリック アクセスがあり、適切な数の引数および引数の型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03ef9-105">All Web service methods have public access and require you to supply the appropriate number of arguments and argument types.</span></span> <span data-ttu-id="03ef9-106">プロジェクトにプロキシ クラスのインスタンスを作成した後は、メソッドを呼び出し、レポート サーバー経由でレポートの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="03ef9-106">After you have created an instance of the proxy class in your project, you can call the methods to perform reporting operations via the report server.</span></span> <span data-ttu-id="03ef9-107">次の C# コードは、<xref:ReportService2010.ReportingService2010> プロキシ クラスの <xref:ReportService2010.ReportingService2010.ListChildren%2A> メソッドの使用方法を表しています。</span><span class="sxs-lookup"><span data-stu-id="03ef9-107">The following C# code illustrates the use of the <xref:ReportService2010.ReportingService2010.ListChildren%2A> method of the <xref:ReportService2010.ReportingService2010> proxy class.</span></span> <span data-ttu-id="03ef9-108">このコードは、Web サービスの再帰呼び出しに使用します。Web サービスでは、レポート サーバー データベースのすべてのアイテムの一覧が入った <xref:ReportService2010.CatalogItem> オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="03ef9-108">The code is used to make a recursive call to the Web service that returns an array of <xref:ReportService2010.CatalogItem> objects that contains a list of all items in the report server database:</span></span>  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a><span data-ttu-id="03ef9-109">参照</span><span class="sxs-lookup"><span data-stu-id="03ef9-109">See Also</span></span>  
 <span data-ttu-id="03ef9-110">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="03ef9-110">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="03ef9-111">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="03ef9-111">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="03ef9-112">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="03ef9-112">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
